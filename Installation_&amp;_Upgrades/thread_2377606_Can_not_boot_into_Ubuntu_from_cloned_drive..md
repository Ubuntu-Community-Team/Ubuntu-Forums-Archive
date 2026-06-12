---
title: "Can not boot into Ubuntu from cloned drive."
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by petrokh on 2017-11-15
Ha all.

I have cloned my system to another HDD using MiniTool Pertition wizard. It is a double boot system Ububtu/Windows 7. Now I have a problem. Computer boots directly into Windows 7. If I hit an F2 button to select booting option, there is ubuntu option but nothing happens if I select it.
Below is a picture of my partitions.
Any hints will be appreciated.
[ATTACH=CONFIG]277530[/ATTACH]

---

### Post by oldfred on 2017-11-15
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yancek on 2017-11-15
Posting the output of boot repair suggested above will probably be the best step.  I'm wondering if using the Mini-Tool software you can access the first partition shown, the EFI partition to see what is in it.  Generally, windows 7 installed the older MBR rather than UEFI/GPT.  Did you install windows yourself using UEFI/GPT.  You have an efi partition and all the partitions show as GPT.

---

### Post by petrokh on 2017-11-16
Hi, thank you. I will have to have a look on proposed links.
Here is output of boot repair.
[http://paste.ubuntu.com/25967009/](http://paste.ubuntu.com/25967009/)
A GRUB menu appeared, but when I try to boot Ubuntu. I end up with a black screen and a command line. 
Not sure where to proceed from there.

---

### Post by oldfred on 2017-11-16
UEFI uses GUID, and your ESP - efi system partition has the correct GUID for Windows, but the Ubuntu entry has a different one?
But the UUID does match?

Did you run Boot-Repair's advanced options to reinstall grub to get the UEFI entry in its NVRAM updated to correct GUID?

If you now get grub menu, can you boot recovery mode, in grub's advanced options?

---

### Post by petrokh on 2017-12-05
Hi. I solved it out, in log file it was complaining about inability to mount a swap partition. It came out that partitions were listed bu their old UUIDs in fstab. After I changed it as /dev/sda1 and so on, everything works fine.
Best.
Petro

---

