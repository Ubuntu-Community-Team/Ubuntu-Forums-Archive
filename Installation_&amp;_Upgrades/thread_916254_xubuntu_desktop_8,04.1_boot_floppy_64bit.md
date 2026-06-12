---
title: "xubuntu desktop 8,04.1 boot floppy 64bit"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by hlamborn on 2008-09-10
I've installed xubuntu desktop 8.04.1 64 bit
on my external USB hd but
did not install boot loader when Installing. What I want to do
is create a boot floppy rather than use the boot loader. So when
I want to go to xubuntu I insert my boot floppy and boot or
reboot. I found a tool on the web called NTRawrite.exe to
which I can use to create the floppy. I beleive that I
just need to have the right path and file name for the
kernel image to be on the floppy. What is the file name
for the kernel and what directory and disk is it on ?
The following are my system facts.
Existing C: HD (internal)  disk 0 NTFS IDE ONLY 1 PARTITION

NEW external HD  external  disk 1      USB 4 XUBUNTU PARTITIONS

          /     ext3 /dev/sdb5
          /boot ext3 /dev/sdb6
          swap       /dev/sdb7
          /home ext3 /dev/sdb8
Please advise what code I should have on the floppy !
Whe I execute rawrite it must reference the kernel file
on disk 1 I believe ? But what is the correct code
for disk,path & file name ? Does anything else have to be
on the floppy ?  I'm a NEWBEE...

---

