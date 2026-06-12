---
title: "Windows 10 takes over GRUB"
date: 2018-06-28
forum: Installation &amp; Upgrades
---

### Post by mkuma on 2018-06-28
I want to use Windows 10 and Ubuntu on the same computer. I installed Windows 10 first, and Ubuntu later. Ubuntu works fine at first, but as soon as I log in Windows, the Ubuntu boot loader disappears, leaving only Windows 10 loader. I can access Ubuntu again by repairing GRUB, but I don't want to do it each time I need to use Linux. What could be the cause of this problem? What would be the solution?

---

### Post by oldfred on 2018-06-28
What brand & model system?
Both installed in UEFI mode?

If UEFI, have you set Ubuntu to be first in boot order in UEFI.
Some systems will work using UEFI internally, but using efibootmgr (which installer also users) does not stay set.
Some brands just do not want to boot anything other than Windows by description and we have to do work arounds.

---

### Post by yancek on 2018-06-28
You might try getting boot repair and running the option to Create BootInfo Summary and post a link to the output here which will give more details for someone to help.  Do not try to make any repairs with boot repair.  This will tell whether you have conflicting installs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cmcanulty on 2018-06-28
I was able to  make my dual boot set to boot to whichever system I want by editing
/etc/default/grub   by changing the number of this code below. Note the numbers start with zero not one. So if windows is the 4th entry at boot and you want windows to auto boot put =3, if you want the 1st on list to boot put =0

```

GRUB_DEFAULT=0
```

---

### Post by mkuma on 2018-07-01
Hello to everyone,

I don't know he exact model of motherboard (it's an assembled computer), but I'm sure it has UEFI instead of BIOS because in has a graphic interface. The problem has nothing to do with boot order. As long as I don't log in Windows, I can access the Ubuntu installation from the select boot menu. But when I enter Windows, that entry is replaced by Windows Loader, and I can no longer access Ubuntu, even changing the boot order in the UEFI. That is the problem.

I have run Boot Repair to create the summary. There you go: [http://paste.ubuntu.com/p/rtrCyNhfFd/](http://paste.ubuntu.com/p/rtrCyNhfFd/) . I am thinking about logging into Windows to crash the bootloader on purpose and send a new report.

About the GRUB configuration file, it seems to be OK, with GRUB_DEFAULT=0. So it isn't the cause of my problem.

---

### Post by mkuma on 2018-07-01
I have checked the model of my motherboard, it's an ASROCK Z77 Extreme4. I also put my idea into practice, and this is the report of the broken GRUB: [http://paste.ubuntu.com/p/5qMdrs3ygm/](http://paste.ubuntu.com/p/5qMdrs3ygm/).

---

### Post by oldfred on 2018-07-01
Have you updated UEFI from Asrock?
That is required anyway for Meltdown and Spectre CPU vulnerabilities. Ubuntu & Windows have updated kernels for most of those issues.

Many Asrock have issues with the Asmedia ports, make sure you are not using any of them, even for DVD.

Report shows Windows is still hibernated or fast start is on. You must turn that off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

    
This is very strange. From line 633
> =================== efibootmgr -v
No BootOrder is set; firmware will attempt recovery

Can you set boot order in UEFI?
Normally efibootmgr works to set boot order as part of grub install.
see also
man efibootmgr

       Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)

---

### Post by mkuma on 2018-07-02
I have deactivated the Fast Startup on Windows. I have also disconnected all SATA cable and have moved the SSD SATA connector from SATA3_A0 to SATA3_0. None of them seem to have solved my problem.

About the boot order, I have made some photo of the boot menu to show you my problem. Before starting up windows:
[ATTACH=CONFIG]280272[/ATTACH]

After starting up windows:
[ATTACH=CONFIG]280271[/ATTACH]

I am currently dealing with the BIOS update. I will tell you when I have done it.

---

### Post by oldfred on 2018-07-02
Is this an Asmedia port?
SATA3_A0

If so or if any others are used, they would be an issue.

---

### Post by yancek on 2018-07-03
You haven't responded to the question above by oldfred about setting the boot order in EFI.  Boot Ubuntu and open a terminal and run:  sudo efibootmgr -v and take a look at the output or post it here.  You can set the order  with efibootmbr -o (the Letter O in the command, lower case onlhy).  I've not seen that before so if your other attempts don't help, do this

---

### Post by mkuma on 2018-07-03
The SATA_A0 port is, indeed, a SATA port connected to the ASMedia controller, so I moved the SSD to the SATA_0, controlled by the Intel chipset.

I have run the command you told me, and the output was this: ```
No BootOrder is set; firmware will attempt recovery
```

I also tried to set the boot order through command line, with hex values 0, 1 and 2, and all of them are considered invalid, that they don't exist.

---

### Post by oldfred on 2018-07-03
Re-installing grub in UEFI boot mode should add an UEFI entry and make it first in boot order.

What does this now show?
sudo efibootmgr -v
See also 
man efibootmgr

But can you in UEFI change boot order?

---

