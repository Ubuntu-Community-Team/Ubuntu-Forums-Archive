---
title: "Ubuntu live cd not recognizing partitions"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by vivasvat on 2018-07-27
Hi! I recently installed ubuntu first then windows 10! All together that sums up in four partitions - one for each bootable and one for each os volume

When boot repairing in linux it says its successful but I still get error message when trying to log on using ubuntu without the live cd

in gparted nothing but the usb shows, and in the command prompt window (ubuntu) dev loop shows up and the usb only. 

In windows I have four partitions (seems right) and in linux ubuntu, one. What to do?

---

### Post by deadflowr on 2018-07-27
If running boot repair, please post te paste link it provides.
(By boot repair, I mean [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"))

---

### Post by vivasvat on 2018-07-27
[http://paste.ubuntu.com/p/WhC4VJcjmM/]("http://paste.ubuntu.com/p/WhC4VJcjmM/")

---

### Post by vivasvat on 2018-07-27
Ty

---

### Post by oldfred on 2018-07-27
Report only shows two USB drives?

      ```
 lrwxrwxrwx 1 root root  9 Jul 26 19:18 usb-SMI_USB_DISK-0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 Jul 26 19:18 usb-WD_My_Passport_25E1_575841314132384453555046-0:0 -> ../../sdb 


```

You also show UEFI Secure Boot on. Often better to have that off, UEFI fast boot off, and make sure drives are set for AHCI, not RAID nor Intel SRT. (Unless RAID 0).

---

### Post by vivasvat on 2018-07-27
Yes, that is my live usb and my external harddisk not the internal

---

### Post by oldfred on 2018-07-27
Does UEFI/BIOS show internal drive?
If not check connections. Or even settings in UEFI as those can turn off drive.

---

### Post by vivasvat on 2018-07-27
it only shows ubuntu or windows or usb -

---

### Post by oldfred on 2018-07-27
That is UEFI boot menu which still has boot entries.
What does it show about hard drives?

Similar to attached which in small print on my system shows drive and which SATA port.

---

### Post by vivasvat on 2018-07-27
Solved it by turning off secureboot and changing satamode, hold on! Now windows cant boot, should I reset?

---

### Post by vivasvat on 2018-07-27
I can't boot windows now

---

### Post by oldfred on 2018-07-27
If Windows 10 you have all the issues it creates with its always on hibernation which it calls fast start up. Since Windows boots so slow.
And Windows regularly turns fast start up back on, no matter what you do, with updates.

Grub only boots workiing Windows, or Windows that does not need chkdsk nor is hibernated. 
So you have to directly boot Windows from UEFI/BIOS. 
If UEFI, you just have to use UEFI boot manager to boot Windows directly.
But with BIOS, there is only one MBR, so only one system can directly boot.
You then need to temporarily install the Windows boot loader, turn off fast start up or make other repairs and then reinstall grub. 
You generally will want both the Windows repair/recovery flash drive and Ubuntu live installer and add Boot-Repair. Boot-Repair may let you install a Windows type boot loader in advanced option, but if it does not see the hibernated Windows, it may not. 
After you can boot Windows, then use Boot-Repair to reinstall grub to MBR.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 More explanation of NTFS driver & Windows hibernation
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

[https://www.tenforums.com/tutorials/4200-create-recovery-drive-windows-10-a.html](https://www.tenforums.com/tutorials/4200-create-recovery-drive-windows-10-a.html)
[/URL] 

    [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

