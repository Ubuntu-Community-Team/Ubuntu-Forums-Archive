---
title: "&quot;GRUB _&quot; on black screen. Is my computer screwed?"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by sanelx09 on 2006-11-27
Hello, I posted a thread earlier on the same problem but didn't find an answer.
The problem is that I've installed Ubuntu 6.10 from the LiveCd, and I rebooted and now all I get is a black screen with "GRUB _" with a blinking "_" on the top left. No keyboard buttons work. Im left without a computer.
I've heard there is a way to go back to windows by using the xp cd, but I want to use/try ubuntu (however, I dont want to erase my XP, so basically dual boot).
For now, is there any way to repair back to Windows XP without the Windows XP cd currently with me, just the LiveCD?
If there is a solution to get Ubuntu to work, I would rather use that.

I think I've messed up my MBR or something, because I went on google and searched for some solutions but didn't seem to find any.

My system specs:
Toshiba , Intel Centrino 1.7ghz, 80 Gb hard drive, 512 mb ram, 15" screen.

Thanks.

---

### Post by polly1 on 2006-11-28
Hi

Try this link for help

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by polly1 on 2006-11-29
Hi

Just another thought from memory.

You can replace your Windows XP MBR by using the Recovery Consol

Reboot to your Windows XP and click the New Install button (not the Repair one)

When the install/repair screen appears after the basic system has been installed, click the Repair button (using the Recovery Consul if my memory is correct. Do not click the install button because this will install Windows and format your disk.

You may be asked for the Administrators password on the Recovery Console
screen. If one has not been allocated, press enter or type the P/W if one has. Then type Help and on the menu will appear MBR. Click replace MBR and  and then type exit and you should be able yo boot into Windows.

I think you may have installed Edgy, so this will be erased bu the new MBR.
You can retry the live cd, which will leave XP untouched, because nothing is written to your hard disk

---

### Post by akshaysrinivasan on 2006-11-29
Does ctrl+alt+del work ??If it does grub hasn't hanged ,you may be able to rectify it using the live cd.

---

### Post by sanelx09 on 2006-11-30
Hello. Thanks for the responses.

Yes, CTRL ALT DEL does work, but just restarts the computer and brings me back to the exact same black screen.

I would try the "recovery console" mentioned above, but I dont currently have the xp cd with me, and besides, I want to dual boot and try out ubuntu, not erase it.

Any other suggestions?

---

### Post by Herman on 2006-11-30
Hello sanelx09,
You should download a free [Super Grub Disk]("http://supergrub.forjamari.linex.org/") , it will only be a very small download for you, about 540 kb, that's not very big. 
You can download the files for making a Super Grub Disk CD-ROM, or a floppy disk, or a USB device. I haven't tried the USB version yet, but here's what top do with the other two,
                How to burn  your bz2 file a  CD or CD-RW Disk.....................................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#To_make_your_sgd_file_into_a_disk")
                
How Make your Super Grub Floppy Disk................................................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk")

Super Grub Disk gives you lots of ways to boot into either Linux or Windows again, and it's quite simple to use. Here is a webpage about it, [Click here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
You should be able to boot Ubuntu by going 'English Super Grub Disk'-->'Gnu/Linux'-->'Boot Gnu/Linux Directly'-->(choose IDE or SCSI hard disk type), and that's it, Ubuntu should boot right up! :-D

When you boot into Ubuntu with it, take a look in your /boot directory, it should look something like these illustrations, [Click here]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation")
My guess is either your /boot/grub directory is missing or your grub files inside there are missing or corrupt for some reason. Maybe a faulty CD, like from a bad burn or a scratched surface. (You should burn .iso software CDs at the slowest speed possible, and use the 'check CD for defects' test before beginning an install). Or maybe you did everthing right and just had bad luck, that can happen too. (Just ask me). :-D

Anyway, presuming that's what's wrong already, (I'm jumping to conclusions here), you can delete everything in your /boot/grub directory and refresh all those files with new ones with a few easy commands, I'll tell you those shortly....

here they are in this link here, 
"When I start my computer, I just get a screen with GRUB_ in the top left corner, and it freezes there...............................................................................................................................................[GO"]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_")

EDIT, I see that confused57 has posted an easier possible solution under here, you should give that one a try first and try mine if confused57's doesn't work. It's a good general rule to try the easiest things first.

Regards, Herman

---

### Post by confused57 on 2006-11-30
You could try reinstalling grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by sanelx09 on 2006-11-30
Hey Herman, thank you for your suggestion, it worked great.
I am in Ubuntu right now, and it is running pretty smoothly.
One question though, will I have to use this CD each time I start up my computer?
Because that isn't something I would wan't to go through each time I start up my computer.
However, I am still thankful for the help, glad to see something besides a completely black screen :)

---

### Post by Herman on 2006-12-01
> Hey Herman, thank you for your suggestion, it worked great.
I am in Ubuntu right now, and it is running pretty smoothly. Alright! :) 
>  One question though, will I have to use this CD each time I start up my computer?Because that isn't something I would wan't to go through each time I start up my computer. However, I am still thankful for the help, glad to see something besides a completely black screen :smile: Super Grub Disk is a great way to get your computer working, but it would be inconvenient for you to have to go through all the 'hoops' to boot that way for ever. 
The idea is to see what's wrong with your existing Grub installation and fix it if possible, and normally it's not too difficult. 
Now that you have Ubuntu up and running, take a look in your /boot directory, it should look something like these illustrations, [Click here]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation")

My guess is either your /boot/grub directory is missing or your grub files inside there are missing or corrupt for some reason, possibly your stage2 in particular.
If that is the problem, it's easy to fix if you know the right terminal commands to use.   Just remove the corrupted files and replacing them with new ones.```
sudo mkdir /boot/grub
```if you have no /boot/grub at all, you need to make the empty directory first.

These commands below here use your grub files in /sbin to refresh your possibly faulty grub files in /boot/grub with. 
```
sudo update-grub
``` If you have no menu.lst file this command (above), will generate one for you. 
To save your menu.lst, to your /home/username folder to get it in a safe place until you are ready to restore it again.  Then remove all those bad files in /boot/grub. Copy back your menu.lst, and reinstall Grub. Here are the commands,
```
sudo cp /boot/grub/menu.lst .
``` Note, be sure to include the full stop (or 'period' in Canada and the U.S.A.) at the end of this line as it is vital to the command's effectiveness. For best results, copy and paste this command.
```
              sudo rm /boot/grub/*
``` You can copy and paste this one too if you like.
```
              sudo cp menu.lst /boot/grub
```You can copy and paste this command as well if you like.
```
              sudo grub-install /dev/hda
``` Where: /dev/hda is your correct Ubuntu partition number, please feel free to alter this command according to your hard disk and partition details. Replace /dev/hda with /dev/sda if you have a Sata or SCSI disk. Replace /hda with hdb if you are booting from a second hard disk.

Be sure to keep on letting me know how you are getting along. I'll be here lurking around for a while waiting. :D

---

### Post by 1slyfox on 2007-02-12
I had a similar thing happen to me while setting up a dual boot system with Ubuntu(on ata drive) and Vista(on a sata raid).  I'm still having problems getting that to work, but while toying around with installations, sometimes the "ata" drive was made active.  When this happened, I simply entered my bios using F2, and changed the boot order of the drives back to booting my SATA raid first.  Very easy fix if your install makes the wrong drive active (because that's where it thinks the MBR is).  However, all BIOS aren't created equal, and this may not be what your problem is.

---

