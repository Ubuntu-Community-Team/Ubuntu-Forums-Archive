---
title: "No option to install Ubuntu 12.04 64-bit alongside Win 7"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by andrew1992 on 2012-06-05
Hi all,

I'm trying to dual boot Windows 7 and Ubuntu 12.04 (64-bit) on my desktop at work.  I can run the live CD, but when I try to install it doesn't actually know that Windows is installed...so there is no option to install alongside it.  This worries me, because although I could try to manually resize and format the partitions myself, I don't think I would be able to boot into Windows after.  I really want to have this option, and from the reading I've done it may have something to do with the difference between GPT and MBR.  I realize this isn't enough information to get a solution right away, but would someone be able to help me troubleshoot and correct any issues so I can install properly?

Thanks in advance!

---

### Post by dino99 on 2012-06-05
well there is several questions here:
- size of hdd, is it over 2 TB ?
- on hdd < 2 TB, mbr is used
- is it a bios or uefi motherboard ?

here is my way for installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

about gpt:
[http://askubuntu.com/questions/120009/how-to-install-gpt-fdisk-8-4-in-kubuntu-12-04](http://askubuntu.com/questions/120009/how-to-install-gpt-fdisk-8-4-in-kubuntu-12-04)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[http://stackoverflow.com/questions/9797351/converting-gpt-to-mbr-without-loss-of-data](http://stackoverflow.com/questions/9797351/converting-gpt-to-mbr-without-loss-of-data)

[https://www.linuxquestions.org/questions/debian-26/unable-to-boot-fresh-install-on-2tb-harddrive-debian-ubuntu-838681/page2.html](https://www.linuxquestions.org/questions/debian-26/unable-to-boot-fresh-install-on-2tb-harddrive-debian-ubuntu-838681/page2.html)

---

### Post by darkod on 2012-06-05
You can start by running in live mode (Try Ubuntu), opening terminal and posting the output of:
sudo fdisk -l (small L)

You are right, if it doesn't detect windows now, it will not include it on the grub2 boot menu. The reason can be different, corruption in the partition table, dynamic disk, etc. Lets see what fdisk says first.

---

### Post by andrew1992 on 2012-06-05
Here is the output from the command.
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e226e31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

```

---

### Post by darkod on 2012-06-05
It seems you do have GPT table, although sometimes it can also happen that you have gpt leftovers if you tried to convert gpt disk to msdos using windows. In that case it doesn't delete the backup gpt table which can be detected by linux tools.

If you do use GPT that would mean you use EFI too since windows can work on gpt only with EFI.

If that is the case I have to mention that this combination of dual boot is complex right now, and difficult. The gpt + efi + dual boot doesn't seem easy to install successfully. I haven't used any of that and don't have links but you can try googling around for a solution that works.

---

### Post by andrew1992 on 2012-06-05
Thanks for the response.  As it turns out, the manual resize/install seems to have worked out just fine, and I have no troubles booting into both Windows and Linux. I'm not exactly sure as to why it worked, but it did, so I will go ahead and mark this as solved.

---

### Post by gregb49 on 2012-06-05
> **andrew1992 said:**
> Thanks for the response.  As it turns out, the manual resize/install seems to have worked out just fine, and I have no troubles booting into both Windows and Linux. I'm not exactly sure as to why it worked, but it did, so I will go ahead and mark this as solved.Worked fine for me as well. Now as for Win8, that seems to be another story for some reason, having just spent a day and a half to get it to dual boot with 12.04.

---

