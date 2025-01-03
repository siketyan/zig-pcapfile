# zig-pcapfile
A pure Zig library for reading and writing PCAP files

_The main branch targets Zig 0.13.0_

## Status
Full support for reading and writing PCAP version 2.4 files (.pcap extension)  
No support for PCAPNG files (.pcapng extension)  

## Usage
```zig
// PCAP reading
var in_file = try std.fs.cwd().openFile("test.pcap", .{});
var it = try pcap.iterator(allocator, .{}, in_file.reader());
defer it.deinit(allocator);

while (try it.next()) |rec| {
    try std.debug.print("packet with len = {d}\n", .{rec.data.len});
}
```
