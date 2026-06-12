---
title: "Help! My PC has no OS!"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by netnut on 2006-10-01
Hi all,

I messed up my computer today when I deleted the Ubuntu boot and swap partitions and formatted the partition containing my windows xp. I messed it up big time, didn't I? ](*,) 

I tried reinstalling windows xp... but after copying all its file to c: when the computer restarts I get
> 
Disk error
Press any key to restart
DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER

I should remind this comes after an attempt at installing windows XP. My aim is to get this PC to run both WinXP and Ubuntu... so what should be my next course of action?

Thanks in advance,

Netnut.

---

### Post by Herman on 2006-10-01
"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

       The BIOS has looked around in the list of devices listed in the [BIOS boot sequence]("http://www.users.bigpond.net.au/hermanzone/p1.htm") you set in the CMOS and has not found a bootable device.
       
       1)Check your [BIOS boot order in CMOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm") and make sure this computer is set to boot from the device (eg, hard disk, cdrom drive, floppy drive, or the like), that you are trying to boot.
       2)After that, check that the device has a bootable media present. For example, if it is a cdrom or floppy drive, is the media bootable in some other machine?
        3)If it is a hard disk, if the drive has been newly installed, has it been plugged in and jumpered correctly and set up in the BIOS? 
       4)Is the MBR is okay?
It would seem as if Windows has done something to your MBR. If it still had Grub in it you would be getting Grub error 22 instead, (because the /boot partition does not exist anymore).

When you said you deleted your /boot partition and swap area, did you mean you had a seperate /boot partition that you deleted? (Implying that there is still a Ubuntu '/' (root) partition and possibly a /home still existing?
Or do you simply mean you deleted your entire Ubuntu installation?

Presuming the later is the case, then possibly the easiest way to fix it would be to go ahead and re-install Ubuntu and let Grub install to MBR, that should fix it for you. It would only take half an hour to do that, and it's quite easy.

Regards, Herman :D

---

### Post by bigken on 2006-10-01
use the [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD check your partions and make sure your winxp partion is bootable ;)

---

### Post by netnut on 2006-10-02
Well,
I simply deleted my Ubuntu partition... both the root and the swap partition. So, in place of my those I've got free space only! 

And yes.. I got GRUB error 22 once, but once I attempted to install WinXP... that error message didn't come up either. So I deduce that my MBR is screwed up. I'll go and check it out!

Thanks.
netnut.

---

### Post by Trifid on 2006-10-02
When you deleted XP you deleted you boot file. Not sure how to fix the problem though apart from adding the OS's your self to the boot file.

---

### Post by bigken on 2006-10-02
try this 1st boot from xp cd go to repair console and type fixmbr then fixboot then exit if this dont work go back too repair console and type [bootcfg /rebuild ]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_bootcfg.mspx?mfr=true")

---

### Post by Herman on 2006-10-02
Your MBR will most likely be okay, it probably  just doesn't have any bootloader code in it, or it has a corrupt bootloader code. But your MBR is probably not 'screwed up', only the bootloader code part of it has a problem.
 
There are three areas of code in the MBR, the first is the 446 byte area where code for a bootloader can be written, and then there are four x sixteen byte entries (64 bytes) of your partition table, plus a 55aa bootable signature at the end. (2 bytes). (512 byes= 1 sector).

Normally, when you install an operating system, most operating systems will install their own bootloader's code to 'fix' the MBR so that the  MBR points to that operating system.

So, you would have installed Windows first, and it fixed the MBR to point to it. Then , the other (larger) part of Windows bootloader takes over and boots Windows.

Then, you installed Ubuntu, and it installed Grub's code to MBR, to fix the MBR to point to Ubuntu, where the rest of Grub lived. Grub gave you a choice of booting Ubuntu, or pointing back to Windows, and chainloading Windows bootloader.

When you deleted Ubuntu, your MBR was still pointing to where Ubuntu used to be, but nothing was there anymore, so you got Grub error 22. (Because the rest of Grub was gone, you deleted it, so Grub couldn't do anything much).

Then,  when you re-installed Windows, for some reason Windows failed to install it's bootloader code to your MBR properly, but it did succeed in erasing what was left of Grub. So  now you are getting "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

You could fix that to point to Windows again if you want,  as bigken says, with your Windows XP install CD [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"). Or, you could do it with a Windows 98 boot floppy disk from [Bootdisk.com]("http://www.bootdisk.com/"), or with [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"). Any of those should work to 'fix' your MBR to point to Windows again.

Then , when you install Ubuntu, Ubuntu is going to fix it again with Grub for you right away again too, and you will also be able to see before that, what GParted thinks of your partition table, which bigken also suggested, which I also agree with. :D

Regards, Herman :D

---

