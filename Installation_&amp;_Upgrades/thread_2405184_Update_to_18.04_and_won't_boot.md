---
title: "Update to 18.04 and won't boot"
date: 2018-11-02
forum: Installation &amp; Upgrades
---

### Post by fsrtraveler on 2018-11-02
I updated recently from ubuntu 14 to 18.04 and now neither windows 10 or ubntu will boot any longer.  I selected the option to run along with windows.  I can run ubuntu from my live ubuntu cd and the partition for ubuntu is there and my windows os is still there and I can read the files on both partitions from the live cd.  I ran boot repair and it responded by asking me to run a couple of commands to move grub but it did not work.  I am afraid to experiment too much more in fear of losing my Windows OS 10.  I rarely use it anymore but I have two expensive apps on it that do not run on Ubuntu.  I did try reinstalling Ubuntu a couple of times and each time it failed to be able to install Grub.  I experimented some and the boot rescue error quit coming up so I quit experimenting.  

I am posting the results of the boot repair if any of you have time to look at and make recommendations I would certainly appreciate it.  Here is the location:
htp://paste.ubuntu.coom/p/fQFQSffpBv/

Thank you for any help.

---

### Post by fsrtraveler on 2018-11-02
Correct updated report address [https://paste.ubuntu.com/p/fQFQSffpBv/](https://paste.ubuntu.com/p/fQFQSffpBv/)

---

### Post by ubfan1 on 2018-11-02
You have a legacy install of Windows on a dos partitioned disk, so you should be in legacy/csm mode, not UEFI.  Change this in your BIOS/UEFI settings (some key at power-up).

---

### Post by oldfred on 2018-11-02
Windows may not like this in sda2:
/Boot/bcd /Boot/BCD 

Linux is case sensitive, but FAT & NTFS is not. So you may only be able to delete one or the other from Ubuntu live installer. Back up first. Duplicate may have come from Boot-Repair, as most users do not know Windows uses a Boot partition (your sda1) and delete it. Then they are missing bootmgr & BCD files. So Boot-Repair normally copies those to sda2. But you must have had copies, but different case on names.

Also move boot flag back to sda1 with gparted or Windows repair disk (make active command).

Make sure Windows fast start up is off, and make Windows repair flash drive.
Grub only boots working Windows. And that means fast start up must be off and NTFS cannot need chkdsk.
And then you have to repair Windows from repair disk or maybe restore Windows boot loader and fix internally.

You do have newer UEFI system, but both Windows & Ubuntu installed in the old BIOS/MBR configuration.
Reboot Ubuntu live installer in BIOS/CSM/Legacy boot mode and install grub to MBR of sda, after you make sure Windows boots & has fast start up off.

Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options
[/URL]
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 
    
Windows 10 works better in UEFI mode as when it turns on fast start up or needs chkdsk and grub will not boot it, you normally can directly boot from UEFI menu.
With BIOS, you have to have separate repair flash drive and/or temporarily restore Windows boot loader to MBR, fix Windows and then restore grub to MBR.
Or always have both Ubuntu live installer & Windows repair disk.
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

### Post by fsrtraveler on 2018-11-03
I finally got win10 to boot again.  I tried to change in bios to the legacy setting and windows would no longer boot.  I tried to reinstall ubuntu 16,04 and got this message "this machine firmware has started the installer in UEFI and the existing OS is in the (BIOS compatibility mode" if you continue it might be difficult to boot to bios mode later"  In windows start up I disabled UEFI mode and set startup for legacy.  It would not boot.  Got an error saying no OS found or have disk failure.  Had to turn back on UEFI and win 10 would boot.  When I tried in the boot menu to boot Ubuntu, windows now boots.  Very frustrating.

---

