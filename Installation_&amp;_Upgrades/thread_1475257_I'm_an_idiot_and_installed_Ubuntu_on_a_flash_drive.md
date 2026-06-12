---
title: "I'm an idiot and installed Ubuntu on a flash drive"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by paco42994 on 2010-05-06
It's a long story and I won't explain, but I'm having complete trouble with my computer now because I installed Ubuntu on my flash drive.

When I have it in, it loads the bootloader just fine.  I can load Windows as well (although for some reason it sometimes restarts the computer...but that may be a different matter).  My computer didn't come with a restore disk.  I don't know how this whole thing works, but it boots from the hard drive first then loads all of the boot information from the flash drive, so I can't boot...not even from Windows...without the flash drive in.  Instead, it tells me the device cannot be found and comes up with some sort of recovery command prompt.

I just wanna remove whatever is telling the computer to boot the way it is now and have it boot like it was before.  I think what I wanna do is remove GRUB, but I'm not sure because I'm a noob.

Another alternative I've thought of (but don't want to try because I don't want to screw things up anymore) is reinstalling Ubuntu on my hard drive this time.  My thoughts is that it would change whatever is booting from the flash drive to just boot from the hard drive.

What should I do?

---

### Post by quixote on 2010-05-07
The bad news is that you need some sort of windows boot medium to fix the windows bootloader.  The good news is that once you have it, it's easy to fix.  If you search for "fixmbr download" (without quotes) a whole mass of links come up for the various versions of windows.  What you'll be doing is making a bootable cd or the like.  Booting with it, and typing "fixmbr" (without quotes) at the command prompt.

What happened is that grub installed itself on the "drive" with ubuntu, ie the flash drive, and also wrote to the MBR (master boot record) on the hard drive, thus interfering with windows bootloader.  If you reinstall windows bootloader, it'll destroy the grub info and you'll need to [reinstall grub]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). Grub should respect existing OSes when you reinstall.

If the flash drive is easily removable, you could tell it to install grub purely on the flash drive and not to write to the MBR of the primary hard drive (/dev/sda) at all.  Then go into the BIOS settings, change the boot order so the flash drive has priority over the hard drive.  The fixed grub should let you choose windows on the hard drive, but if there's a problem, you can pull the flash drive and still boot into windows.

---

### Post by kansasnoob on 2010-05-08
> The bad news is that you need some sort of windows boot medium to fix the windows bootloader. 

That's not true!

---

### Post by kansasnoob on 2010-05-08
It would be best for us to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

General description of your problem here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

But I do things a bit differently, I just need to see the requested output first.

Also this:

> for some reason it sometimes restarts the computer

May be this problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But once again I need to see that output.

---

### Post by sir_nasty on 2010-05-08
Either that or you could boot into windows, install ubuntu from pendrivelinux.org onto the flash drive, reboot off the flash drive, install 10.04 onto the HDD and let it handle everything.... Just be careful, with this method if you botch the usb creation then you botch your bootloader....

Ideally do you have a burner or a spare usb drive to load a live cd onto and re-install onto your hdd?

---

### Post by wilee-nilee on 2010-05-08
> **kansasnoob said:**
> It would be best for us to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

General description of your problem here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

But I do things a bit differently, I just need to see the requested output first.

Also this:



May be this problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But once again I need to see that output.

+1 listen to this poster and others just watch how it's done. Without out more information it will just make it worse by pecking at the OS with ideas when the script will tell exactly what is needed, if you know how to read it.

---

### Post by nikefalcon on 2010-05-08
You could use BootitNG to fix your problem.
[http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html)

You do not need to buy it. Just scroll to the bottom to download from their link. When downloaded run the exe in there. You then may make a bootable floppy or cd your choice. This puts the program on you choice of media so your ready to go. (the cd option makes a cd .iso so you will need a program to burn it.) Both the floppy and cd contain the same program. Next you will restart your computer with the cd or floppy in the drive. Once you boot into the program do not install it to your HDD. Just click cancel to just run it off the cd or floppy. Then go to partion work. Click the oval on the left side of the window (yes you can use your mouse!) to go to your primary hdd.
If you installed grub the bootloader you will need to reset you mbr or else you can't boot up because grub will crash. To do this select you windows partion go to view mbr on the left. When in there select your windows partion and click std mbr. This will take grub off and set your mbr back to the way it was before. Click apply and the changes will be made. Then eject your media and use the file option at the top left to reboot. Your computer should restart normally into windows :smile: .

---

### Post by wilee-nilee on 2010-05-08
> **nikefalcon said:**
> You could use BootitNG to fix your problem.
[http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html)

You do not need to buy it. Just scroll to the bottom to download from their link. When downloaded run the exe in there. You then may make a bootable floppy or cd your choice. This puts the program on you choice of media so your ready to go. (the cd option makes a cd .iso so you will need a program to burn it.) Both the floppy and cd contain the same program. Next you will restart your computer with the cd or floppy in the drive. Once you boot into the program do not install it to your HDD. Just click cancel to just run it off the cd or floppy. Then go to partion work. Click the oval on the left side of the window (yes you can use your mouse!) to go to your primary hdd.
If you installed grub the bootloader you will need to reset you mbr or else you can't boot up because grub will crash. To do this select you windows partion go to view mbr on the left. When in there select your windows partion and click std mbr. This will take grub off and set your mbr back to the way it was before. Click apply and the changes will be made. Then eject your media and use the file option at the top left to reboot. Your computer should restart normally into windows :smile: .

No, read the thread.

---

### Post by paco42994 on 2010-05-09
Thanks all for replying.  I decided to keep trying, and because I did not have a boot disk I did not have the "fdisk" able command prompt, nor could I go into any recovery mode and use "fixmbr," this took forever.

However, Windows Vista has some software hidden in it called "mbrinstall.exe."  I just opened that (I found it searching "mbr" in the start menu), clicked "install", and everything was fixed.  Everything had me using a boot disk and going into a recovery mode and everthing :confused:

> If the flash drive is easily removable, you could tell it to install grub purely on the flash drive and not to write to the MBR of the primary hard drive (/dev/sda) at all. Then go into the BIOS settings, change the boot order so the flash drive has priority over the hard drive. The fixed grub should let you choose windows on the hard drive, but if there's a problem, you can pull the flash drive and still boot into windows.
*-quixote*

I could probably do that, but I think I'll just not take the risk and put Ubuntu on my hard drive this time. :P

---

### Post by quixote on 2010-05-12
Glad you got it sorted!  It was good thinking to search on "mbr."  All those things are pretty much of a muchness.  

And thanks to kansasnoob, #4.  Why isn't that bootinfo script part of the OS!

---

