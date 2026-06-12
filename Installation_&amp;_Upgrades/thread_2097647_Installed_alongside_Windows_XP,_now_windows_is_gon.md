---
title: "Installed alongside Windows XP, now windows is gone and Ubuntu won't load correctly?"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by chrisyunke on 2012-12-23
I used a live CD to install Ubuntu onto my computer running Windows XP Media Center Edition. I have done this many time before on other computers with no problems.

Now, after installing, whenever I try to run Ubuntu, it goes to a terminal screen showing errors. When I try to boot into Windows, I just get a blinking white line.

Did I somehow wipe windows?
HELP! It is my parents computer and they are likely to kill me.

---

### Post by Bucky Ball on 2012-12-23
It would help if you could provide the Ubuntu release and the errors you are getting.

Also, the output of this from a LiveCD will tell us more:
```

sudo blkid
```

---

### Post by chrisyunke on 2012-12-23
Ubuntu 12.10

blkid results:

/dev/loop0: TYPE="squashfs"
/dev/sde1: LABEL="HP_PAVILION" UUID="a89872099871D672" TYPE:ntfs"
/dev/sde2: LABEL="HP_RECOVERY" UUID="4C17-781C" TYPE="vfat"
/dev/sde5: UUID="9169f2ac-e838-4595-9af7-2bcc10dc56c2" TYPE="ext4"
/dev/sr0: LABEL="Ubuntu 12.10 i386" TYPE="iso9660"



Also, now it won't even go to the GUI to choose which OS to go to. Just goes straight to the white blinking line.

---

### Post by fdrake on 2012-12-23
> **chrisyunke said:**
> 
/dev/loop0: TYPE="squashfs"
/dev/sde1: LABEL="HP_PAVILION" UUID="a89872099871D672" TYPE:ntfs"
/dev/sde2: LABEL="HP_RECOVERY" UUID="4C17-781C" TYPE="vfat"
/dev/sde5: UUID="9169f2ac-e838-4595-9af7-2bcc10dc56c2" TYPE="ext4"
/dev/sr0: LABEL="Ubuntu 12.10 i386" TYPE="iso9660"


nope, your parents won't kill you yet. while in the live cd-section run this commands into the terminal
```
sudo apt-get install grub-pc
 sudo grub-install /dev/sde
 sudo update-grub
```
reboot and report the results.

---

### Post by chrisyunke on 2012-12-23
> **fdrake said:**
> nope, your parents won't kill you yet. while in the live cd-section run this commands into the terminal
```
sudo apt-get install grub 
 sudo grub-install /dev/sde
 sudo update-grub
```
reboot and report the results.

The first command returned error code (1) and says there are unmet dependencies.
The second and third command returns: "command not found" for both.

EDIT: I went ahead and did a FORCE install. Got: E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by oldfred on 2012-12-23
The apt-get install grub installs grub legacy not grub2. Grub2's package is grub-pc.

Windows may be in sde1, but why is it sde? Are other hard drives installed?

Lets see all the details of system. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by fdrake on 2012-12-24
> **oldfred said:**
> 

Windows may be in sde1, but why is it sde? Are other hard drives installed?

i asked myself that too but i jsut thought it's the way/order the pc is setup/ cdrom/usb.....

---

### Post by chrisyunke on 2012-12-24
> **oldfred said:**
> The apt-get install grub installs grub legacy not grub2. Grub2's package is grub-pc.

Windows may be in sde1, but why is it sde? Are other hard drives installed?

Lets see all the details of system. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

I cant really run the boot info thing because I am not using the Ubuntu GUI. I was only using the terminal. I am attempting to load the GUI now and I will report back.

---

### Post by chrisyunke on 2012-12-24
Whenever I click "Try Ubuntu" I get 

*Starting Mount network filesystems*   [OK]
*Ending Mount network filesystems*     [OK]

then all these errors flash saying "failed to idle" or "Failed to set mode on"

EDIT: GOT it loaded. Summary url is [http://paste.ubuntu.com/1461179](http://paste.ubuntu.com/1461179)

ANOTHER EDIT: So, I am an idiot and have been typing "sde" this whole time when it is "sda" but when I tryed running the commands I got "Path '/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

Yet another EDIT: I did a recommended repair. Got this url [http://paste.ubuntu.com/1461208](http://paste.ubuntu.com/1461208)

Going to try restarting and see what happens.

---

### Post by chrisyunke on 2012-12-24
OK! After all that, I got the Boot Menu to show again. But even still, when I select Windows, I just get a black screen with a flashing white horizontal line in the top left corner. When I try to run Ubuntu I get those errors again. [drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:10]

---

### Post by chrisyunke on 2012-12-24
PLEASE?! If someone could interpret those summaries for me and provide me with answers, I would forever be in your debt. I need this fixed ASAP. The summary says something about "Partition outside the disk detected". Is that the problem? If so, how do I fix? Sorry to post so much, I just need help ASAP.

---

### Post by oldfred on 2012-12-24
The CD is oversized so you get a partition outside of disk error. Not related to anything.

So the error is with Windows. Does Ubuntu boot ok?

And when directly booting from MBR, did you get same boot error with Windows?

Everything looks ok with sda1, your Windows install from what script can show.

But when you resize Windows it wants to run chkdsk, usually it runs automatically on reboot, but sometimes you have to run it from a repairCD. Then sometimes other Windows repairs are needed. Files look ok, but some have had to update them.

Run chkdsk first and rerun if any errors.  And then see if it boots, if not run the other repairs. Do not run fixMBR unless you want the Windows boot loader in the MBR not grub.

       Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by chrisyunke on 2012-12-24
> **oldfred said:**
> The CD is oversized so you get a partition outside of disk error. Not related to anything.

So the error is with Windows. Does Ubuntu boot ok?

And when directly booting from MBR, did you get same boot error with Windows?

Everything looks ok with sda1, your Windows install from what script can show.

But when you resize Windows it wants to run chkdsk, usually it runs automatically on reboot, but sometimes you have to run it from a repairCD. Then sometimes other Windows repairs are needed. Files look ok, but some have had to update them.

Run chkdsk first and rerun if any errors.  And then see if it boots, if not run the other repairs. Do not run fixMBR unless you want the Windows boot loader in the MBR not grub.

       Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

No, Ubuntu doesnt boot properly. Sometimes it will boot to an all Terminal screen only. But that is only sometimes. As far as a boot error with Windows, I just get a blinking white line when I attempt to boot Windows. 

I do not have the original Windows XP disk. I tried to access the Recovery Console from  the PC Recovery that I am able to get to on startup via F10. To no avail. At least pressing R did nothing.

Is there another way to get the Windows Recovery CD? Or another way to get to Command Prompt? It will not even let me boot Windows in Safe Mode.

---

### Post by oldfred on 2012-12-24
You need the XP disk.

I have run chkdsk from a Windows 7 repair flash drive and it actually worked better, but converted PBR - partition boot sector to Windows 7. I then had to use bootsect.exe from Windows 7 to restore the XP type PBR.

They used to have a free download, but Microsoft complained about copyright, so they started charging $10, I see they now charge $20. 
      
We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


You can make a Windows 7 repair CD or flash drive if you have access to another computer with Windows 7. Work, school, neighbor, other computer?

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by chrisyunke on 2012-12-24
> **oldfred said:**
> You need the XP disk.

I have run chkdsk from a Windows 7 repair flash drive and it actually worked better, but converted PBR - partition boot sector to Windows 7. I then had to use bootsect.exe from Windows 7 to restore the XP type PBR.

They used to have a free download, but Microsoft complained about copyright, so they started charging $10, I see they now charge $20. 
      
We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


You can make a Windows 7 repair CD or flash drive if you have access to another computer with Windows 7. Work, school, neighbor, other computer?

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

OK, I have the Windows 7 disc being created right now. Should be done in a few minutes. So, I just run it and do the recovery thing (pressing R on main screen), run those commands and that is it? You mentioned something about having to fix the PBR from 7 to XP? Do I have to do that? If so, how?

---

### Post by oldfred on 2012-12-24
The commands are different for Windows 7 and you cannot use the automatic repairs on XP from Windows 7. You can run chkdsk from command line and run bootsec.exe /nt52 to fix PBR for XP systems.

      You need to use command prompt. Check what diskpart it shows your XP as and use that.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

    
       chkdsk c: /r
    It may not be c:, you have to see what partition/drive is is mounted as.

       [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by chrisyunke on 2012-12-24
> **oldfred said:**
> The commands are different for Windows 7 and you cannot use the automatic repairs on XP from Windows 7. You can run chkdsk from command line and run bootsec.exe /nt52 to fix PBR for XP systems.

      You need to use command prompt. Check what diskpart it shows your XP as and use that.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

    
       chkdsk c: /r
    It may not be c:, you have to see what partition/drive is is mounted as.

       [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

OK, so I ran bootsect.exe and it said it was successfull. But when I reboot and try to boot windows, I still just get the blinking white line.

EDIT: Booted from recovery disk again, I get the message "The file or directory C: is corrupt or unreadable. Please run the Chkdsk utility."
Ran CHKDSK and it says there were no problems but ends with "Failed to transfer logged messages to the event log with status 50.

EDIT: Forgot to add "c: /r" parameters the first time. Ran again with them and it is just stickin at 8%. The file numbers are changing though. Just very slowly.

---

### Post by LostFarmer on 2012-12-24
oldfred--  looks like the start of sda2 is overlapping with the end of sda3.

```
/dev/sda2         606,674,**880**   625,136,399    18,461,520   c W95 FAT32 (LBA)
 /dev/sda3         341,147,646   606,672,**895 **  265,525,250   5 Extended
```

---

### Post by chrisyunke on 2012-12-24
> **LostFarmer said:**
> oldfred--  looks like the start of sda2 is overlapping with the end of sda3.

```
/dev/sda2         606,674,**880**   625,136,399    18,461,520   c W95 FAT32 (LBA) /dev/sda3         341,147,646   606,672,**895 **  265,525,250   5 Extended
```

Now how do I fix that?

---

### Post by LostFarmer on 2012-12-24
wait for oldfred's advice, he is mush better at giving instructions then me.

---

### Post by chrisyunke on 2012-12-24
Just got some results. Several. 
"File record segment 153692, 153693, 153694, 153695 is unreadable."
I am sure more will come up in time.

EDIT: "File verification completed"
"828 large file records processed."
_

Just started stage 2.

---

### Post by Bucky Ball on 2012-12-24
Stick with it and keep reporting as you are. ;)

I see you are still alive so the parents must be in a reasonable xmas mood ...

oldfred is an expert with this stuff, as mentioned, but you might try googling some of the errors in his absence and see what you dig up ...

---

### Post by chrisyunke on 2012-12-24
When it is done, do you want me to reboot and try to start windows? Or do you want me to leave it up and wait on word from ya'll?

---

### Post by Bucky Ball on 2012-12-24
This thread is serving to keep a log of your error messages so just make sure you include anything else that pops up, or pops up when completed. Post those last error messages, if any, back here then reboot and tell us what happens. 

xmas is upon us so many of us will be in and out over the next 24/48 hours (11:30AM xmas morn here) ... ;)

---

### Post by chrisyunke on 2012-12-24
> **Bucky Ball said:**
> This thread is serving to keep a log of your error messages so just make sure you include anything else that pops up, or pops up when completed. Post those last error messages, if any, back here then reboot and tell us what happens. 

xmas is upon us so many of us will be in and out over the next 24/48 hours (11:30AM xmas morn here) ... ;)

Thanks and will do! Happy Christmas! Still several more hours for me.

---

### Post by LostFarmer on 2012-12-24
disregard what I wrote before, had the wrong glasses on.  

 Happy Christmas to all.

---

### Post by oldfred on 2012-12-25
First backup partition table, use your drive  sda or  sdb, sdc etc.
sudo sfdisk -d /dev/sda > parts.txt

The issue then is, does the overlap belong to sda2 or sda3. Often the extended partition gets written incorrectly by either Windows or testdisk and it has something to do with the old CHS - cylinders, heads, sectors and how the conversion is rounded (incorrectly). 

Post this in code tags to preserve formatting. 
sudo parted /dev/sda unit s print

We may have to manually edit parts.txt and reread it back into partition table with sfdisk, but lets see all the details by sector.

---

### Post by LostFarmer on 2012-12-25
The overlap between sda2 and sda3 was an error on my part, there is NO overlap.  Did not look at the 4th digit correctly.

---

