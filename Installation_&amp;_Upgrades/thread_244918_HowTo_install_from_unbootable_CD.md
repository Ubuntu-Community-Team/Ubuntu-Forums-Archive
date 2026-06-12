---
title: "HowTo install from unbootable CD"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by bcw on 2006-08-27
This HowTo allows booting/installation from the CD when your computer won't.  The details below are for Dapper, but probably can be adapted.

For some people, the Smart Boot Manager diskette will allow this, but it does not work for USB CD drives.  This approach works if your system will boot off a floppy.  The idea is to get access to the CD from DOS, then call the installer on the CD.

Create the FreeDOS boot diskette found here:
```
http://johnson.tmfc.net/dos/index.html
```

Add the 'linld.com' program:
```
http://lwn.net/Articles/102210/
```

Now, determine what will be the next 'DOS' drive letter - the letter your CD will be when it's plugged in.  My hard disk has C: & D: partitions accessible to DOS, so my CD becomes E:\.  Use this letter when you create a script file (a batch file) containing this one line (all on one line):
```
linld image=e:\casper\vmlinuz initrd=e:\casper\initrd.gz "cl=root=/dev/ram boot=casper ramdisk_size=1048576 devfs=mount,dall"
```

I named my script 'xubuntu.bat'.  All of this goes on this one FreeDOS boot floppy.  There's plenty of room.

Now, plug everything in, and place your [K,X]ubuntu CD in the drive, and boot on the floppy.

If your CD is not USB, but appears as a drive, just go on with the rest of the instructions.

This diskette has a collection of USB device drivers & schemes, and a menu for selecting them.  I don't know if the ones that worked for me will work for all hardware - please post your own results for us all to see if you try this.  But this diskette has most of the USB device drivers available, and while it may be tedious, you will probably find a combination that works.  The menus make it relatively easy to try.

I used a USB keyboard, mouse, powered hub, and external CDROM, and all worked once I found the right device drivers.

For my hardware, I pressed (with appropriate waits for the prompts):
```
Enter
Esc
Esc
Esc
Enter
Esc
Enter
```

Verify access to the CDROM as drive E:\, or whatever drive letter you determined above - if you can't access the CD by the letter you used in the script, you can't proceed. I just used 'dir e:', but sporadically this hung, and I had to restart - maybe something to do with entering keys too quickly? So, if your process hangs, try again - it will work. I could enter the above command line manually, but I put it into a script (batch file) to avoid timeouts, tedious typing, etc.

Run the script:
```
xubuntu (or whatever you named it)
```

When the [K,X]ubuntu live desktop appears, run the install app on the desktop (the option 'System-Install' in the menu did not work for me).

At the end of installation, the system appeared to shut down, including ejecting the CD, but the screen background remained lit.  I left it alone for 5 minutes to give the journaling file system and the daemons a chance to flush their buffers before I pressed the Reset button.

Kudos to Marc Herbert, for his excellent work devising the basis of this approach.  He also mentions the instlux sourceforge project that is built on his work. ```
http://marc.herbert.free.fr/linux/win2linstall.html
```

Thanks to the fellow who assembled the FreeDOS boot diskette & drivers. I can't tell easily from his web site, but I think he's Lam Chun Sang Johnson.

A good discussion of USB boot drivers can be found at:
```
http://www.computing.net/dos/wwwboard/forum/13447.html
```

Sysadmins, if you think this should appear elsewhere, or have a better title so people can find it, feel free to do so (and let me know, please, so I can direct people to it myself).

Regards,
Bret

---

### Post by awander@verrex.com on 2007-12-13
Wow-that's quite apost-I have followed it as best I can, with my Latitude LM.

I have made the Win98 Boot disk, with the batch file containing
linld image=e:\casper\vmlinuz initrd=e:\casper\initrd.gz "cl=root=/dev/ram boot=casper ramdisk_size=1048576 devfs=mount,dall"
and I get 2 different results:

-If I use the regular Ubuntu distro, i get a message during the loading that my PNP bios caused a fatal error, and that I may have to reboot with the "pnpbios=off" option. Then it gives me a kernal panic, and then a lot of identical messages:
atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware durectly. This repeats until I kill the power.
-I did try adding
pnpbios=off
so the batch file now reads:
initrd=e:\casper\initrd.gz "cl=root=/dev/ram boot=casper ramdisk_size=1048576 devfs=mount,dall pnpbios=off"
and I get the same exact results


-If I try the alternate distro, with a properly modified batch file, I i get the same message that my PNP bios caused a fatal error, and that I may have to reboot with the "pnpbios=off" option, but then it runs the installer in low memory mode, and after I specify the keyboard etc, it can't detect the CD-ROM. it wants me to give it a floppy with drivers, or to manually select a CD-ROM module and device, which i have no idea how to do. I know the CD works because the Win98 batch file loads the kernel from it. The Win98 boot uses the OAKCDROM driver

Any ideas?

Andy

---

### Post by bcw on 2008-01-05
The HowTo was written for Dapper.  I've tried it with Edgy, but I believe it did not work with Gutsy.  You might try installing the earlier version, then upgrading immediately before you do much customization - once it's on, you're probably ok.  That's how I upgraded my Fujitsu 3400s to Gutsy.

If that doesn't work, post the issues you have.  It might yet be something specific to your laptop, but I know the version is an issue.  I'm not using the machine I wrote this for, so haven't investigated the changes to get Gutsy to install.

Cheers,
Bret

---

