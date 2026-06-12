---
title: "kexec"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by nsabatino on 2008-11-18
What would be the correct kexec settings for booting into the Server 8.10 livecd? The only explanation I have is an example from [google code]("http://code.google.com/p/atv-bootloader/wiki/BootingLiveCD") for 7.10 desktop. I've been able to boot into the 8.10 desktop livecd with these settings:

```
kexec --load /cdrom/casper/vmlinuz \
--initrd=/cdrom/casper/initrd.gz \
--command-line="file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz nosplash vesa" 
```

Only, Server 8.10 doesn't have a casper directory.

It'd be great if someone could lend a hand with either the correct kexec command for server 8.10 or with deselecting packages when installing the desktop version from the livecd.

---

