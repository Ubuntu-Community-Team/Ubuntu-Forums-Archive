---
title: "Hard disk not booting at all after trying to install dual boot Win10/Linux Mint"
date: 2018-04-08
forum: MINT
---

### Post by andbb on 2018-04-08
After (attempting to) installing linuxmint-18.3-cinnamon-64bit in dual boot with Windows 10 Pro on my Fuijitsu E744 PC my hard-disk won’t boot. I am booting fine via USB and all files are present and accessible on the hard-disk.

 
 
 I Installed linuxmint-18.3-cinnamon-64bit and read the warning regarding BIOS/UEFI conflict, but decided (in error ) to Force UEFI installation.

 
 
 BIOS boot is currently Compatibility Enabled, but I have also tried booting disabling this.

 
 
 Safe boot, Fast boot are both disabled.

    	 	 	 	   

 
 Windows/Panther/Setupact.log:

 2017-12-16 12:19:44, Info                  IBS    Callback_BootEnvironmentDetect: Detected boot environment: BIOS  
 I have tried repairing MBR to GPTMBR/Windows

 [http://paste.ubuntu.com/p/GCJXDR5cwX/](http://paste.ubuntu.com/p/GCJXDR5cwX/)

 
 
 I have tried repairing MBR to GPTMBR/Linux

 [http://paste.ubuntu.com/p/BCwVT2Sf6F/](http://paste.ubuntu.com/p/BCwVT2Sf6F/) 

 
 
 Default boot/repair

 [http://paste.ubuntu.com/p/FCFbtZpHyb/](http://paste.ubuntu.com/p/FCFbtZpHyb/)

 
I am a Linux noob, and do not want to loose my Windows 10, which is my main workhorse, so I hope you may help me restore that.

Thanks!
Anders

---

### Post by oldos2er on 2018-04-08
Moved to MINT.

---

### Post by oldfred on 2018-04-08
Moved to Mint Sub-forum.

Not seeing anything related to UEFI boot (a good thing) with your installs.
But you booted live installer in UEFI mode and your hardware is UEFI based.
Since Windows is in the now 35 year old BIOS/MBR configuration, you need to boot live installer only in BIOS boot mode.

Windows in BIOS boot mode only boots from MBR(msdos) partitioned drives. And only in UEFI boot mode from gpt partitioned drives.
Or drive partitioning has to match boot mode.
You show dos or MBR type partitioning on sdc.

Also Windows only boots from a primary NTFS partition with the boot flag. 
While you show boot files in sdc1, it also is labeled Recovery, so often is not the standard BCD but one just for restoring system from recovery partition(s). Some totally erase & recreate, some newer ones try to preserve some of your data. But backups required.

Did you convert main install, now sdc5 from a primary partition to logical. That may still work, but only if you still have the Windows boot partition as primary NTFS which normally is a 100MB NTFS partition with boot flag and separate from recovery partition.

Grub does not use boot flag, so boot flag should not be on sdc8. But not sure where it should be. Often if you start recovery (boot flag on recovery sda1), it further damages partitions as it is attempting to restore system to "as purchased". And then may erase your changes. Boot flag should be on the Windows boot partition.
Or make sure you have good backups.

If you have UEFI off, or CSM/Legacy/BIOS boot mode on, does booting sdc boot your Linux Mint install?

Is hard drive not in SATA0 port. Your two flash drives are promoted to sda & sdb which often happens if open SATA port before used SATA port is available. But some systems just promote removable drives. You need to pay attention to any command that uses device like /dev/sdc as if a flash drive is unplugged the device may change. Always double check with fdisk or parted before running any device based command. And when installing Linux always only use Something Else install option, so you can specify drive for grub install.

Since sda5 is your main Windows partition, you may be able to move it back to a primary partition. Primary partitions are sda1 thru sda4 with any one of them as an extended partition which can hold an unlimited number of logical partitions which start at sda5.
Only since sda5's sectors are at beginning of extended you may be able to reconfigure extended to not include current sda5 to sda3 (probably). Then you could run Windows repairs to add BCD and boot flag to make it bootable. You can use fixparts to convert logical to primary, do not convert to gpt. And boot repair or comamnd line or gparted, or Windows tools to move boot flag to Windows partition.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sdc

Boot-Repair is primarily for Linux repairs and cannot do most Windows repairs.
Windows will boot from one primary partition if NTFS with boot flag and all the Windows boot files are there. You are missing BCD.
So you need Windows repair disk or install disk's repair/recovery console. You probably also need to run chkdsk.
You will need your Windows repair disk or third party Windows repair tools.

---

### Post by TheFu on 2018-04-08
Ninja'd by oldfred who has 1000x more experience with this stuff.

I dno't know anything about mint.

1st, backup anything you don't want to lose with a 100% know-you-can-restore backup.  Messing with partitions, installations, is a common time for bad choices and failures. Backup first!

2nd, I'd remove all storage that isn't the install media and the HDD you want installed.  There appear to be 3 storage devices connected which aren't needed.  These could be confusing the installer.  1 flash installer and 1 HDD for the target.  No SD cards. No CDROMs, no other flash sticks.. No external USB spinning disks. Simplify.

The 400+G disk has Windows + MBR partitioning.  That means it isn't UEFI. You need to install using Legacy BIOS, like Windows is currently installed.  So ... reinstall Ubuntu/Mint and this time don't use UEFI when that is asked.  Should only take 15min.

If that doesn't solve it, then run bootrepair, don't repair anything and post a fresh, new, boot-info URL.

Please.

---

### Post by andbb on 2018-04-08
Thanks to Oldfred for details and to TheFu for simplicity. At first I went for simplicity and followed the advice of TheFu, but unfortunately without luck. I am unable too boot Linux Mint from the HD.

The boot-repair output is here:
[http://paste.ubuntu.com/p/Xmd2qyCbv4/](http://paste.ubuntu.com/p/Xmd2qyCbv4/) 

 
 Second I picked one recommendation from OldFred and went to Gparted to configure the flags of my main HD (now sda) as lba and boot.
 
 
 To document the boot-repair bootinfo output is here:
[http://paste.ubuntu.com/p/X7tzKnJgRT/](http://paste.ubuntu.com/p/X7tzKnJgRT/)
 
So still no further…. What to try next?
 
 
 OldFred - you recommend booting BIOS not UEFI from Live/USB - how do I do this? I set up my USB with LiLi USB (ww.**linuxlive**usb.com) in Windows, but did not notice an option for this... 
Anders

---

### Post by TheFu on 2018-04-08
If you use MBR/DOS disk partitioning for Windows, then Windows cannot boot in UEFI mode.  That means legacy boot.  If Windows uses Legacy Boot, then you really need to use it for Linux too.
To boot in UEFI mode, Windows requires GPT partitioning.

I only looked at the 2nd bootinfo - everything seems fine, except did you say to install grub into the MBR area of sda?  You should. Besides that, I don't see anything obviously wrong.  If you didn't, you can boot off the install disk/flash drive, go into the live session, open a terminal and run **sudo grub-install /dev/sda && sudo update-grub**.  Of course, this assumed that sda **is** the correct device.

---

### Post by oldfred on 2018-04-08
You moved boot flag to sda2 which is the extended partition. It should only be on NTFS formated primary partitions.

And for Windows to boot it will need the BCD and chkdsk from your Windows repair/recovery disk or install media.

In BIOS mode does not Mint boot?

---

### Post by andbb on 2018-04-09
Nope - nothing is booting from the harddisk (and I am having trouble with persistence on my USB, so it is quite tiresome to troubleshoot :().
I will moved the boot flag to NTFS and copy BCD and chkdsk after work and report.
Reading the input from TheFu, it also seems installing Grub should make sense when Windows (sda) is configured to boot.
So far thanks to both of you!

---

### Post by andbb on 2018-04-17
As pointed out by oldfred the issue had to be solved in Windows - but his solution was unfortunately too simple for Windows :-) - nevertheless thanks for pointing me in the right direction.

Solved with the aid of the free Windows boot utility Macrium Reflect and Windows 10 forum user topgundcp.

[https://www.tenforums.com/installation-upgrade/108057-win10-not-booting-after-linux-installation-uefi-bios-conflict.html](https://www.tenforums.com/installation-upgrade/108057-win10-not-booting-after-linux-installation-uefi-bios-conflict.html)

I had temporary access to an ISO with Macrium uploaded in the Win10 forum - but it seems that the free edition may be downloaded here [http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html](http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html)

---

### Post by oldfred on 2018-04-17
Did you end up converting drive to UEFI/gpt or did you just fix the BIOS/MBR?
Windows only boots in BIOS mode from MBR, and if you have an extended partition, it must be MBR(msdos).
And Windows only boots in UEFI mode from gpt partitioned drives.

If BIOS your Windows fixes should have worked and I think the same fixes work with UEFI, but repair disk (and install) must be UEFI.

---

### Post by andbb on 2018-04-22
I kept the HDD in BIOS mode, and this worked.

---

