---
title: "how do i make a fresh install of wine?"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Maniac Matt on 2007-08-26
I was wondering how to completely remove wine and its applications, and then reinstall it.

I would like to try this because i tried to install the program steam and it seems that i made an error or something in the process..so every time i try to run it, i get the message that it is already running...which confuses me because i can't find it running anywhere.. :(



thanks, Matt

---

### Post by Dark Star on 2007-08-26
Try ```
sudo apt-get remove wine
``` To download latest ver. [http://www.winehq.org/](http://www.winehq.org/) else to install Wine type ```
sudo apt-get install wine
```

---

### Post by Maniac Matt on 2007-08-26
but will this remove everything having to do with wine?

---

### Post by robotii on 2007-08-26
Open a terminal and do

rm -R ./.wine

This will remove all of the settings for wine, but keep the actual program installed.

---

### Post by n0ctem on 2007-08-27
How would I go about removing the programs, or the entire .Wine directory?

---

### Post by mikebn2 on 2007-08-27
I have a Dell Pentium 4, 2 gb ram, drive 0 is 160gb and xp, drive 1 is brand new 300 gb, both sata.  Bios is set to recognize same.  Belarc recognizes existence of second hard drive.

I downloaded the Ubuntu 7.04 iso to the hard disk in xp, then copied it to a cd.  Changed the bios to boot from the cd and not it says the device is not bootable.  Did I do something wrong in creating the Ubuntu cd?

In xp explorer it can see the file on the cd.  

Help, why can't I get the pc to boot from the cd?

I have been looking for some detailed information and everything I find doesn't answer this type of problem.

Thanks for your help,

Mike Schneider
Louisville, KY

---

### Post by splatmatic on 2007-08-28
> **mikebn2 said:**
> 
In xp explorer it can see the file on the cd.  

Help, why can't I get the pc to boot from the cd?


Did you just drag and drop the file right onto the CD and then burn the cd? (since you said explorer can see the "file" im assuming you just dropped the file on the cd) What you need to do is use nero, or another CD burner to burn the ISO file to the CD.

---

### Post by mikebn2 on 2007-08-29
I copied the cd from the hard disk to the cd by using the software within xp.  I right clicked on the file and chose copy then right clicked on the drive and chose paste.  At that point I then right clicked again on the drive and selected write to cd.

Will that produce the same effect as clicking and dragging, in other words a non working boot disc?

Thanks,

---

