---
title: "Ubuntu will not restart after shutdown."
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by JasonT76 on 2009-11-20
Greetings All, 

Brand new to Ubuntu, and recently installed 9.10 on a formerly-XP Dell desktop.  The installation went fine, and I played around for a few hours downloading the Perfect Desktop components from the repositories.  Everything went great until I shut the machine down.  When I went to turn it back on, it would not load Ubuntu, and left me with a black screen.  The hard drive light wasn't doing anything, and I had no control.  I shut the machine down by holding in the power button.  This happened several times until I put the live CD back into the CD drive and chose "boot from first hard drive".  At that point, my Ubuntu desktop came up, and I could remove the CD from the drive.  If I do a restart, Ubuntu loads with no problems.  It is only on a full shutdown that I am forced to insert the CD to gain access.  Ubuntu is the only OS on the computer, as XP was overwritten.  

Any help would be greatly appreciated.

Thank you in advance.

---

### Post by drs305 on 2009-11-20
You might try reinstalling Grub 2 from the LiveCD. Here is the community doc link. It involves use of the command line for some of the instructions, so if you aren't sure what to do just ask.

[Grub2 Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by JasonT76 on 2009-11-20
Thank you.  That seems to be exactly what I needed !!  :D

---

### Post by JasonT76 on 2009-11-20
Well, I lied.  Apparently that did not correct the problem.  It did, however, fix it for several power cycles, but after I let the computer sit for about two hours, the problem returned.  

Again, I tried reinstalling GRUB per the last response's instructions, but apparently the solution is not so simple.

Any opinions are welcome, as I'm scratching my head about this one.

Thanks.

---

### Post by efflandt on 2009-11-21
Maybe check your CMOS settings (go into CMOS setup from first screen during boot), and see if there is anything that protects your mbr.  Otherwise if that first part of your drive goes bad you are going to have boot issues.

I had an out of the box returned computer I bought for $100 years ago and had been mostly running Linux from the 2nd drive.  The boot drive was making clicking sounds at times like it was having read issues.  One day when I booted, the BIOS said "Disk Failure is Imminent".  Well the next boot it didn't.  So I just removed the Win98 drive and set up my 2nd drive to boot itself (with LILO at that time).

You could always use USB Startup Disk Creator to put the live/install iso on bootable USB.  Just avoid using a Cruzer, because that U3 file encryption thing embeds a solid state sr device (pseudo cdrom) that seems to greatly prolong (double) boot up time (about 2 min vs about 1 minute or less).

---

