---
title: "Boot Cd not recognized-where is rawwritewin image file?"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Tom1942 on 2006-08-16
I am very new to linux.  I've been using computers, mostly windows pc's, since 1982 and have been a sparc20 unix user in the past.

I have a functioning ubuntu 6.06 lts cd.  I booted my current windows pc with it and reviewed some of the operating system.  I did not install ubuntu on my current pc.

I inherited a pentium II, 400 mhz pc from my daughter who has moved up to a newer laptop.  I removed the hard drive in the pentium II pc and installed it in an enclosure and gave it back to my daughter to use as an external drive.

I bought a new 250gb western digital eide 40 pin hard drive to use in the pentium II.  I am aware that it might be too new for the motherboard but I am hoping it will still function, but at slower speeds.  I'm not concerned if it is not a fast as it can be, just that if will function with linux.

I left the 250gb hd set for cable select and installed it.  Since ubuntu will function as a boot disk, I changed the bios so the cdrom is the first drive for booting.  I was hoping that once ubuntu was running from the cd I could format the new 250gb hard drive and then install ubuntu on it.

The ubuntu cd was not recognized as a boot disk and I was asked to put in a boot disk and press enter.

I researched the ubuntu site and found rawwritewin.exe for making a floppy boot disk.  Rawrite did not work, so I tried rawwritewin.  All went well until it told me to type in the name of the image file.  I could find nothing in the documentation for rawwritewin that mentioned an image file, so I'm stuck.

My issues are:

How do I get the Pentium II to recognize the ubuntu cd, since it won't recognize it when the bios is set for the cdrom to boot first.

How do I use rawwritewin to make a boot floppy when there is no info to tell me what image file is needed and where I get it.

If I get ubuntu to run from the cd, will I be able to format a new hard drive and then tell the cd to install ubuntu on that hard drive?  If so, any tips on how to do this?

Thanks in advance for any advice on how to proceed.

---

### Post by em3raldxiii on 2006-08-16
Alrighty, I can answer just about everything :D  Yay, I like being helpful!

About booting:
Your jumpers are possibly the cause of the trouble because I've been in your position.  Put the HD on IDE channel 0 (or primary) and put it on the END of the cable.  Change the jumpers to MASTER.  Then put the CD-Rom on IDE channel 1 (or Secondary) and put it on the END of the cable, with the jumpers ALSO saying MASTER.  In your BIOS, select your CD-ROM as your primary boot (though having HD1 and CDR2 would probably work anyway).  Now you *should* be able to boot.  HOWEVER, you MAY need to put the Hard-Drive's jumpers into "limit" mode (limits the size of the drive so that it works with some Legacy (oldschool) motherboards).

About DRIVE size:
You're right - 250GB will not be recognized by the motherboard, and the number of problems that can occur due to this are numerous and potentially unpredictable.  Assuming your Motherboard will even recognize the drive, it will probably not let you use all 250GB - in fact, it will likely only allow access to 32GB.

About DRIVE speed:
Yup, it will be slower, but should work okay.  Your motherboard is probably ATA66, though it could be as high as ATA100.  If your drive is ATA133, it will be backwards compatable and just run at a truncated transfer rate.

About rawwritewin:
I've never used this program, but it appears that it is searching for a disc image.  This is the ISO file that you may have downloaded from Ubuntu.com.  If you have a functioning installation disc, this is not what you need.  The CD Image file can be used by some software to "pretend" that you have an additional CD device, and I assume this is how the program works.  To use it, you would probably have to put the ISO image onto a disc in data format.  Basically, download the file, start your favorite burning program, burn the file to disc the same way you would burn any normal file you were backing up.  If you "burn image to disc" you will end up creating an installation disc instead of archiving the disc image.  Unfortunately, that program may require that the disc image is stored on a HD - this I don't know.

Now, if you happen to be in the Edmonton, Alberta, Canada area ... I happen to have some older hard drives that would work very happily with your hardware.  I'd be happy to part with one since they're just collecting dust anyway :D

Hope that helps.  Keep the questions coming and we'll get you ironed out.

---

### Post by confused57 on 2006-08-16
Here's a guide for older bios not recognizing large hard drives:
[http://wiki.linuxquestions.org/index.php?title=GRUB&printable=yes#Error_18](http://wiki.linuxquestions.org/index.php?title=GRUB&printable=yes#Error_18)

Some older bios do not allow boot from cd drive, but sounds like yours does.  If you're still not able to boot from your cd drive after following the excellent instructions given you by em3raldxiii, you may need Smart Boot Manager:

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by Tom1942 on 2006-08-18
em3raldxiii:  Sorry, I'm not in Canada, would be happy to get one of the older hd's but......

Thanks for the tip in jumper settings, I'll try that.  In the meantime, I can report that I downloaded the latest bios for the mobo and updated it on the pc.  I then went into bios and it detected the 250gb hd as 136gb, which is a start.  My next step is to follow instructions that came with the hd for recognizing greater than 137gb.  However, new development is that the cd-rom is not being recognized.  I have no idea why it suddenly stopped being recognized so I will have to resolve that before coming back for further advice.

confused57:  Thanks for tip on guide for older bios recognizing larger hd's.  Have not yet looked at that.  Will come back after I do.  Will also look at smart boot manager.  I had seen reference to it, but had decided to try rawwritewin.

Appreciate the help and will return after doing some work with your (plural) information.  :D

---

### Post by Tom1942 on 2006-08-18
Just as soon as I submitted my previous reply I tried changing the jumper seetings as recommended and the next boot up showed the bios recognizing the cd-rom, however, as soon as "Found CDROM" showed on the screen the boot process froze.

One small step.....

Thanks, I'm working on why the freeze-up at this point.

:confused:

---

### Post by Tom1942 on 2006-08-18
Troubleshooting why the cd-rom wasn't recognized the first step of checking all connections uncovered a loose connection.  Once that was pressed down firmly, the pc recognized the cd-rom and a cd-rw that is also installed.

Next, the pc now recognized both cd devices, but refused to boot from the cd-rom.  I then tried to boot from the cd-rw and that worked.  Ubuntu is now booted up on this pc.

Thanks for the help.  I imagine I'll return for more help as I explore Ubuntu.

:)

---

### Post by em3raldxiii on 2006-08-18
Glad you've gotten it all figured out ... well ... such as it is anyway haha.  I'll keep watching this thread, so feel free to ask away :D

---

