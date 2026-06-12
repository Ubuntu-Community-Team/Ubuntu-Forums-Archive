---
title: "Freeze at &quot;Mounting root file system&quot;"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Jarn on 2006-10-14
Before I begin, I would like to say that I do NOT think my problem is the same as the other thread, the 25 page long one. That's why I created a new one. They all had errors with "logical block 357298", mine is different.

Just in case this is necessary, when I try to install dapper, I have to use noapic nolapic acpi=off. If I do not, it freezes while trying to boot the kernel. To see what was going on, I removed the quiet and splash options so I could see more. This is what it says:

A lot of- 
hdc: cdrom_decode_status: error=0x51 { DriveReady SeekComplete Error}
hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
hdc: fauked opcode was: unkown

This repeats 2 or 3 times, then it does this-

hdc: ide_intr: huh? expected NULL handler on exit
hdc: ATAPI reset complete
end_request: I/O error, dev hdc, sector 1433408
Buffer I/O error on device hdc, logical block 179176

The whole sequence, the two together, repeats continuously.

EDIT: Apparently, it only repeats like 4 times... I just never waited enough. That took about 10 minutes, however. Now my question becomes: Will it take this long once I install it? :O If, once installed, it takes that long to boot I just won't bother.

---

