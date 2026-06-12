---
title: "Unable to boot to installer"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by Saut de Chat on 2012-08-08
Hi all,
I am  trying to set up a dual-boot with Windows 7.
Steps taken so far:
1) Downloaded 12.04(x64) and created USB install.
2) Altered bios to boot from USB
Screen shows:
[INDENT]SYSLINUX 4.06 EDD 4.06-pre1 Copyright (c) 1994-2011 H.Peter Anvinet al
No valid file system found![/INDENT]
3) Restarted and tried changing Linux partition in Windows from unallocated space, RAW, FAT, NTFS, all no luck.
4) Tried using the wubi installer from Windows.
This boots into the loader but just shows:
[INDENT]Mount is denied because the NTFS volume is already exclusively opened.
Could not mount partition /dev/sha1
Run chkdsk /r

Busybox...
(initramfs)[/INDENT]

Asus P7P55d-e lx with overclocked i5
8GB Ram
2x WD 1TB Blacks in RAID0
nVidia gtx260, if it counts.

Any help/suggestions would be greatly appreciated.
Thanks in advance.

---

### Post by oldfred on 2012-08-09
The desktop version does not include RAID drivers as that is uncommon on desktops (or was).

You need the alternative installer which installs the same system but is text based. Without gui it has more room for extra drivers. It is not a liveCD which is worth having if you need to make repairs, but have to load the RAID drivers each time you boot.


[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

I do not know RAID.
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

With nVidia you may have video issues. I have to use nomodeset on liveCD and on first boot. LIveCD install offers option to install proprietary drivers now, so the issue may be less if you install them as part of the install, if the alternative is the same on that.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

