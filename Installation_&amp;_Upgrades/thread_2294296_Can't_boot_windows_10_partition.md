---
title: "Can't boot windows 10 partition"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by theamazingjmo on 2015-09-10
Hey all, I've been using Ubuntu a long time but I'm a fairly novice user. I installed Windows 10 on a new partition, and deleted my old Windows 7 partition. I've tried running boot-repair and reinstalling Ubuntu but Ubuntu doesn't seem to recognize the Windows 10 partition as an OS. It is flagged as active and bootable as far as I know, I just don't know how to successfully add it to grub and so forth. Any help would be appreciated as I really need to use Windows. The partition is mounted and viewable in Ubuntu.

Edit: I have a Windows 10 recovery ISO I've tried to make bootable on a flash drive with Unetbootin, but I can't boot the drive. I've succeeded in the past using Win32DiskImager, but it is a windows binary and it fails to have the permission to access any drives when I run it with wine.

---

### Post by oldfred on 2015-09-10
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You have to have fast startup (always on hibernation) off for Linux NTFS driver to see the NTFS partition. Linux does not open hibernated or NTFS needing chkdsk.
       
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

    
Grub has not been updated to parse Windows and see Windows 10 as the name of the entry, but should add a Windows entry to your grub menu.

---

### Post by theamazingjmo on 2015-09-10
As I said the Windows 10 partition is usable in Ubuntu so I don't think there's an issue there.

[http://paste.ubuntu.com/12329521/](http://paste.ubuntu.com/12329521/)

sda2 is the NTFS partition I'm trying to boot I believe, and sdc1 is an NTFS-formatted external

---

### Post by theamazingjmo on 2015-09-10
I made a boot-repair live USB and ran the default repair, but no luck. Grub just shows the Ubuntu entries.

updated: [http://paste.ubuntu.com/12329729](http://paste.ubuntu.com/12329729)

---

### Post by oldfred on 2015-09-10
Was sda1 your Windows 7 with the boot flag before?
Windows always installs its boot files into the partition with the boot flag.
But your sda2 is missing /Boot/BCD.

       Vista/7/8/10 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You need to use a Windows repair flash drive or your Windows installer and boot in its repair console. Some third party tools also may fix the BCD. Or if you have a backup from your Windows 7 you can restore that.

Many have issues creating the Windows boot flash drives from Linux. I see many threads asking same question. Much easier to do that when Windows is working and keep that so you have a way to repair Windows. Grub only boots a working Windows, so when Windows breaks you need a way to boot & repair it.

Wine typically does not work with low level tools. It really is only for running some applications.

---

### Post by Mark Phelps on 2015-09-11
When you installed Win10, after already having Win7, the Win10 installer wrote its boot loader files to the Win7 partition.  When you removed that, you removed the boot loader files.

As Oldfred said, you need to boot from your Win10 install media and choose Startup Repair to rebuilt the boot loader files.  You may have to do that several times.

---

