---
title: "Huge problem with Win 8 and Ubuntu"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by james6754 on 2013-03-14
Hi everyone, so I am trying to installl Ubuntu to replace my linux mint. I have Win 8 installed on my netbook as my main OS. I did something silly and deleted a couple of partitions on the netbook to free up space (recovery partiton) which made me have booting problems with windows. So I then used testdisk and restored the partitions. After this I am still having problems booting Win 8. The error I get is that winload.efi is missing or contains errors.

I have used boot-repair to try and restore the mbr and also to install grub. I am still not having any luck. The output from boot-repair summary is pasted here (I really don't understand it).

paste.ubuntu.com/5613934

If anyone could point me in the right direction and wether Windows can be saved or whether I should just reinstall to Win 7 (I don't have the disk for Win 8) I would really appreciate it as I now have a netbook which is basically a brick, will only let me run off a live cd and does not show me grub when I start it, it goes straight to Win 8 blue screen giving me an error 'A required device was missing' then press enter and I get the winload.efi missing or errors.

Thanks and sorry if it seems basic.

---

### Post by oldfred on 2013-03-14
Clickable link:
[http://paste.ubuntu.com/5613934/](http://paste.ubuntu.com/5613934/)

Did you turn off fastboot? That sometimes only lets you into UEFI menu from Windows, so if Windows does not boot you cannot get to UEFI menu.
Do you have secure boot on. It does not look like you have the shim file with grub2's copy of the Windows key to boot in secure boot mode.
You need to get to UEFI menu and see if Ubuntu will boot.

---

