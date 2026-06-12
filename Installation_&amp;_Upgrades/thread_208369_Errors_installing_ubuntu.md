---
title: "Errors installing ubuntu"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by EEPS on 2006-07-03
Hi, I am trying to install Dapper on a machine that had Breezy on it before. Never had any problems. Now when I try to install, I keep getting errors. The md5 of the image checks out and I have burned several CD's already... so I don't think its the CD. When installing, it gets to %54 and completely freezes. Here are some errors I get in dmesg just staring up:
```

ubuntu@ubuntu:~$ dmesg | grep -i error
[  139.917783] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[  139.917796] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[  164.853355] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  164.853370] hdc: drive_cmd: error=0x04 { AbortedCommand }

``` 

does this look like dying hardware?

---

### Post by EEPS on 2006-07-05
Ok, this problem has been verry frustrating all weekend, and I believe it is some sort of driver issue with this ubuntu release. I thought I had a faulty IDE controller on my mobo since I swaped out the DVD drive with another one and got the same errors. To test this, I tried the CD on another system, with a DVD drive. I get th same errors... I have reburned the CD several times with the same results (The MD5 IS correct). I finally tried it on a CD drive, not a DVD and was able to install it. Also, I was unable to boot the CD on either of my parents TWO Fujitsu Lifebooks! (different models) One gave an error about APIC and a timer not being connected, and the other just hung there at decompressing the linux kernel. No of these got past this. I think there must be some seriouse driver/hardware detection issues going on here.

---

