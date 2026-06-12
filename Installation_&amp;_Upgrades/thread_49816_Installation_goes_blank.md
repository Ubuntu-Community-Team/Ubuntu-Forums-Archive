---
title: "Installation goes blank"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by Ranfolk on 2005-07-17
I am trying to make a go at the linux world and ubuntu was getting very good reviews from over at PC world, so I decided to give it a try.  I looked at quite a few pages on the forum, and didn't find a similar problem, but forgive me if this was asked like 50 times.  I first downloaded the one for AMD 64 (as I have one) and I did the install disk and such, and it did not work, then I also tried it with the regular installer (32 bit).

Both times I put the disk (it was a DVD) in the drive and would restart the computer.  The Ubuntu installer thing would come up and ask if I wanted the base installation or the default installation, and wanting default, I just pushed "enter."  After doing this, text would flash on the screen, like it was installing, and then the screen would just go blank.  

This happened with both disks, and I am not sure what happened or what is going on.  I tried leaving it on when I went to class, to see if it just needed time, and an hour later it was still blank.  I have a HP laptop zv6000 series with 1 gig ram, 100 gig hard drive, and AMD Athlon 64 3200 processor.  Any help would be appreciated.  I also downloaded Ubuntu from the "Everywhere else" link on the Ubuntu download site.  Any help would be appreciated on what to do or what is going on.

Josh

---

### Post by Strife on 2005-07-17
Try specifying the vga=771 option when you boot the kernel. This solves these issues on most laptops.

---

### Post by Ranfolk on 2005-07-18
I put the disc in (I tried both of them) and restarted the computer.  At the first screen that comes up, where I previously just pushed enter for default installation, I typed vga=771 and it said it could not find the boot kernal "vga=771"  This is the only place  I could enter this because it is the only screen I can get to, after pressing enter it does some stuff, then goes blank.  So, with the vga=771 method mentioned by Strife, I could not load it either.  Any more help would be appreciated.

---

### Post by Ranfolk on 2005-07-18
Thanks, figured it out, I needed to type "linux vga=771" and now it works.  Again, thanks from the new guy.

Josh

---

