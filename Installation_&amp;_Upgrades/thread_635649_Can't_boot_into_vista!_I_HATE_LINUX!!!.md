---
title: "Can't boot into vista! I HATE LINUX!!!"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by TV-VCR on 2007-12-08
```
# Modified by YaST2. Last modification on Sat Dec  8 22:03:59 CST 2007
default 0
timeout 10
gfxmenu (hd1,1)/boot/message


###Don't change this comment - YaST2 identifier: Original name: windows 1###
title Microsoft Windows Vista
    rootnoverify (hd1,1)
    chainloader (hd0,0)+1


###Don't change this comment - YaST2 identifier: Original name: linux###
title Novell OpenSUSE 10.3
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_ST3500630AS_9QG3F9PA-part2 vga=0x314 resume=/dev/sdb1 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default


###Don't change this comment - YaST2 identifier: Original name: failsafe###
title OpenSUSE (safe mode)
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_ST3500630AS_9QG3F9PA-part2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default
```

This is what I get when I try to boot into windows! I can press any key I want but nothing happens so I have to reboot!!

[[img]http://img459.imageshack.us/img459/3051/sany0076nj3.th.jpg[/img]](http://img459.imageshack.us/my.php?image=sany0076nj3.jpg)

Please help!!  :(

---

### Post by PmDematagoda on 2007-12-09
You are asking the question on the wrong forums, you should ask the [OpenSUSE forum]("http://suseforums.net/") to help you out.
But anyway, try changing the entry to this:-

```
title Microsoft Windows Vista
rootnoverify (hd1,1)
makeactive
chainloader +1
```

---

