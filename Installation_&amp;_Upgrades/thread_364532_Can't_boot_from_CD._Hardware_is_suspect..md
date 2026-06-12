---
title: "Can't boot from CD. Hardware is suspect."
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by adamgreenwell on 2007-02-18
I bought an IBM Intellistation of eBay to use as a lightweight server with Ubuntu as my OS of choice.

I am suspecting that my hardware is the cause of my problem and not the disc but here goes.

when my machine tries to boot from the disc, it says 'NON SYSTEM DISK, REPLACE AND PRESS ANY KEY'.

I can use a boot CD but I'm still a linux noob and can't figure out how to use a boot CD to help me install Ubuntu. 

I have gotten the same error with various windows discs but they aren't legit ones so I thought that may be the cause but that doesn't appear to be the case.

I also tried to boot using SuSe from a DVD and that returned the same error.

---

### Post by truck87bp on 2007-02-18
You probably aren't burning the ISO file properly.  If you are using windows, download a program called "Burn4Free",  when you run it, it has an option to BURN ISO from one of the drop down menues.  I made the same mistake.   Hope this does it!

---

### Post by adamgreenwell on 2007-02-18
I used Alcohol 120 percent to burn it. I've burnt many an ISO with alcohol before with no trouble. 

Would it have anything to do with the fact I have a SCSI hard drive?

---

### Post by budgie9 on 2007-02-18
You may need to set the BIOS boot feature  so it picks up on the CD and not the floppy or HD as being the first disk to use.

---

### Post by adamgreenwell on 2007-02-18
> **budgie9 said:**
> You may need to set the BIOS boot feature  so it picks up on the CD and not the floppy or HD as being the first disk to use.

That was the first thing I checked. The BIOS on this thing is a little different than what I'm used to though.

---

### Post by adamgreenwell on 2007-02-18
Well, after tweaking some settings and what not, I can get past the system disk error but it tries to boot from the CD and then times out. Again, my boot cd works like a champ, but all the distro's I have tried to boot (now I'm up to Ubuntu, Fedora Core 6, Suse and even Linspire) still won't boot! The discs boot just fine on my other machines.

I still can't understand why the boot CD fires right up but nothing else will.

---

### Post by forkart on 2007-02-22
> **adamgreenwell said:**
> I bought an IBM Intellistation of eBay to use as a lightweight server with Ubuntu as my OS of choice.

I am suspecting that my hardware is the cause of my problem and not the disc but here goes.

when my machine tries to boot from the disc, it says 'NON SYSTEM DISK, REPLACE AND PRESS ANY KEY'.

I can use a boot CD but I'm still a linux noob and can't figure out how to use a boot CD to help me install Ubuntu. 

I have gotten the same error with various windows discs but they aren't legit ones so I thought that may be the cause but that doesn't appear to be the case.

I also tried to boot using SuSe from a DVD and that returned the same error.

Try using magiciso to burn this iso file to dvd again. It may work out.
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

### Post by bigken on 2007-02-22
you could try swapping the cdrom from your other machine also try using 
the iso burner in my signature all you need to is right click the iso and select burn

---

