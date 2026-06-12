---
title: "dual boot problem (windows xp and ubuntu 7.10)"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by badboy1234 on 2008-02-28
Hi,
I have installed ubuntu 7.10 after I have completely formatted my hard disk and built new partitions. I have made three hard drives while partitioning. 1st for swap, 2nd for ubuntu and 3rd with fat32. Then I installed windows xp with two partitions which are both ntfs. the 1st drive for windows xp and the second for applications. after rebooting, windows xp started automatically and didn't give me the choice of which operating system to use. plz guys, i need detailed answer coz I have read the dual boot problems of other ppl and tried the solutions but they didnt work.
thanks for help

---

### Post by aysiu on 2008-02-28
It's generally a good idea to install Windows first, then Ubuntu.

Ubuntu automatically adds Windows to the boot menu.
Windows, on the other hand, doesn't really care to add Ubuntu to its boot menu.

This may help:
[Recovering Ubuntu after installing Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by kieran on 2008-02-28
When installing windows, it would have overwritten the MBR of your hard disk, taking out the grub (or lilo) MBR so the microsoft mbr is booting what its being told to boot by default - windows. Hence, windows is just booting and not giving you an option of going into linux. You need to reinstall a grub mbr, and then use /boot/grub/menu.lst to specify a boot option to boot into windows. If you first installed windows, and then install linux afterward, Grub would have been written at the end of the linux install, overwriting the microsoft windows mbr -- and its nice enough to autodetect the windows installation and automatically set up a multiboot menu (including windows) so you don't have to do it manually.

I don't really have the time to go into it much more than this right now, as I'm having my own issues with NTFS-3g on 6.06LTS right now (bloody repositories don't want to work).

hope the info might at least get you going..

---

### Post by krishnagiri.fiesty on 2008-02-28
i suggest u boot through live cd and goto terminal and:
terminal-->grub-->setup (hd0)(this will rewrite the mbr)
as said above this is good enough to add windows to the list
 and then reboot
:guitar:

---

