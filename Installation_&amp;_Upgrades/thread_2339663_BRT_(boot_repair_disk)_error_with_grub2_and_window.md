---
title: "BRT (boot repair disk) error with grub2 and windows 10 loader (dual boot)"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by abudhabi2 on 2016-10-11
[http://paste.ubuntu.com/23308587/](http://paste.ubuntu.com/23308587/)


Today I deleted a windows 7 partition and installed windows 10 64 bit. during this process windows killed the grub boot loader. but the laptop started to windows boot loader and I had the choice between win10 32 and win10 64 edition as well as grub. unfortunately grub was in a minimal rescue modus and I could not start my linux distribution. I tried the boot repair disk but now I cant start nothing.

Before I changed the system the grub2 boot loader started and I could choose between linux and windows. Is it possible to roll back the change which was done by the boot repair tool? I made a mbr backup before starting the repair.

---

### Post by oldfred on 2016-10-11
Windows has to have boot flag on the one NTFS partition with boot files. Even with multiple installs, Windows always installs boot files into that one partition.
Your boot flag is now on sda4, but does not show a BCD. Where sda1 shows bootmgr & BCD. I would move boot flag back to sda1.
If you have another full install of Windows in sda4, I might run repairs on it with Windows tools to add a /boot/BCD so it can be seen by grub and directly booted. But you can only run Windows boot repairs on partition with boot flag.

And your sda5 Linux partition looks like it has corruption.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes w
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5 

      
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by abudhabi2 on 2016-10-11
Thank you for fast response. Im a beginner and my first and most important aim is to bring the windows installation back. 

how to move the boot flag back to sda1?

could you please tell it including every single step?

was running the boot info tool again, maybe it is useful
[http://paste.ubuntu.com/23309290/](http://paste.ubuntu.com/23309290/)

---

### Post by abudhabi2 on 2016-10-11
I found the option on the boot repair tool...

I set now to sda1

[http://paste.ubuntu.com/23309351/](http://paste.ubuntu.com/23309351/)

will report

---

### Post by oldfred on 2016-10-11
You can also use gparted, command line tools and Windows own tools to move boot flag. In Windows you use command line and "make active" after selectiong correct partition.

If primarily a Windows user you must also have a Windows repair tool.
       f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[URL="http://www.sevenforums.com/tutorials/666-advanced-boot-options.html"]http://www.sevenforums.com/tutorials/666-advanced-boot-options.html
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://www.sevenforums.com/tutorials/666-advanced-boot-options.html"]
[/URL]

---

### Post by abudhabi2 on 2016-10-11
> **abudhabi2 said:**
> I found the option on the boot repair tool...

I set now to sda1

[http://paste.ubuntu.com/23309351/](http://paste.ubuntu.com/23309351/)

will report

YES!! it helped! thank you!


Im now at the same point before using the boot repair disk.

Is there something safe I can try to reactivate grub2 without risking loosing access to the windows partitions?


the windows boot loader gives the option to boot into grub but only some terminal rescue mode. which command can I try there?

---

### Post by abudhabi2 on 2016-10-11
I was overwriting the windows repair tool with the boot repair disk because I had only one usb stick((

---

### Post by oldfred on 2016-10-11
That Windows option is EasyBCD and using the very old grub4dos. I do not recommend it, but a few do use it. It requires you to install grub2 in a mode not recommended by grub2 as it does not really fit and has to convert to blocklists which are not reliable.

I suggest using Boot-Repair to install grub to MBR and then use grub.
But the corruption on sda4 seems to prevent Boot-Repair from seeing your install. 
Have you run the fsck as posted in #2 above?

---

### Post by abudhabi2 on 2016-10-11
> **oldfred said:**
> That Windows option is EasyBCD and using the very old grub4dos. I do not recommend it, but a few do use it. It requires you to install grub2 in a mode not recommended by grub2 as it does not really fit and has to convert to blocklists which are not reliable.

I suggest using Boot-Repair to install grub to MBR and then use grub.
But the corruption on sda4 seems to prevent Boot-Repair from seeing your install. 
Have you run the fsck as posted in #2 above?


yes, sure I would prefer to use grub. I just need to do it step by step.

I got the following when run fsck>

/dev/sda5 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!

what to do?

the newest:
[http://paste.ubuntu.com/23309674/](http://paste.ubuntu.com/23309674/)


which,  sda4 or sda5 need a check?

---

### Post by oldfred on 2016-10-11
What version of live installer are you using.
Newest or 16.04 should have a new e2fsck, that should work.
But this has another way to get newer e2fsck:
[https://askubuntu.com/questions/747656/ext4-broken-file-system-on-ubuntu-14-04-4](https://askubuntu.com/questions/747656/ext4-broken-file-system-on-ubuntu-14-04-4)

Report is not showing anything from your Linux partition, without repairs then it cannot reinstall grub.

---

### Post by abudhabi2 on 2016-10-12
> **oldfred said:**
> What version of live installer are you using.
Newest or 16.04 should have a new e2fsck, that should work.
But this has another way to get newer e2fsck:
[https://askubuntu.com/questions/747656/ext4-broken-file-system-on-ubuntu-14-04-4](https://askubuntu.com/questions/747656/ext4-broken-file-system-on-ubuntu-14-04-4)

Report is not showing anything from your Linux partition, without repairs then it cannot reinstall grub.

its the BRT boot repair tool...

got the following info trying to mount sda5
Error mounting /dev/sda5 at /media/lubuntu/ab6912b6-68c5-4403-b746-70055136c00f: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda5" "/media/lubuntu/ab6912b6-68c5-4403-b746-70055136c00f"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[33016.150718] JBD2: Unrecognised features on journal
[33016.150742] EXT4-fs (sda5): error loading journal

can I fix it with e2fsck?

---

### Post by oldfred on 2016-10-12
Normally e2fsck is the fix, not sure of any other way.
Download newest Ubuntu 16.04 LTS or even 16.10 if you want to experiment.
I use 16.04 as main working install since LTS and it works with my hardware, but also install newer versions to see what changes.

---

