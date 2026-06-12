---
title: "ubuntu 14.04.1 lts side by side windows 7"
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by slenderwrist on 2015-02-14
Hi,

Bought a computer with win 8 preloaded. Switched to legacy bios, did a clean install of windows 7. Want to install ubuntu but it does not see any operating systems in my case win7.

Here s the link from boot-repair [http://paste.ubuntu.com/10220248/](http://paste.ubuntu.com/10220248/)

I think i need to delete that gpt but i dont know how thanks in advance.

---

### Post by ajgreeny on 2015-02-14
It looks as if you still have relics of gpt partitioning on your machine which is not actually being used any more but may be interfering with booting and running.

Does Win 7 work as it should?
Can you boot to a live ubuntu system without a problem?

---

### Post by oldfred on 2015-02-14
Windows does not correctly convert from gpt to MBR. It leaves the backup gpt partition table and then Linux tools see both and only assume you want to totally erase drive to make it correct.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you have new hardware there are advantages to UEFI/gpt. And Windows 7 can be installed in UEFI mode.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by slenderwrist on 2015-02-16
Fixparts did the trick thanks

---

