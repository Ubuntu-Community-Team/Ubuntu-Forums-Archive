---
title: "Installing to system with no external boot device"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by JohnBN on 2011-06-01
Instructional post - medium difficulty.
 
Installing on an older notebook (or other system) with no external bootable device available:
[LIST]
[*]No CD/DVD drive
[*]No floppy
[*]No boot to USB capability
[*]No (usable) OS on HD
[/LIST]Solution went like this:
[LIST=1]
[*]Remove target HD from notebook.*
[*]Disconnect HD from a desktop.**
[*]Use adapter cable set to install target drive in desktop.***
[*]Boot desktop to Ubuntu install CD or USB stick.
[*]Install to target HD.
[*]When install tells you to restart your system, shut it down (you may have to do it manually).
[*]Remove target HD from desktop and re-install in notebook.
[*]Boot notebook to HD.
[*]Enjoy Ubuntu.
[/LIST]* - Or other system; if a desktop, I'd suggest (at least temporarily) installing a CDROM drive instead.
** - Not necessary, but a little safer!
*** - A PATA (IDE) adapter cable set would work too.  I used a USB adapter so there's no obvious reason this wouldn't work with another notebook or externally on a desktop - just make sure you install onto the right drive! 
*** - Also your opportunity to backup anything on the target drive as Ubuntu install will erase/format the drive.

---

### Post by Mark Phelps on 2011-06-01
Two comments ...

First, if the desktop in use already has an internal hard drive (and I presume it does), and that is the "first" drive as seen by the Ubuntu installer, it will install GRUB to THAT drive -- NOT to the other drive.  Not only will this overwrite whatever you have setup on the desktop drive, it will also mean the the other drive will NOT boot when replaced back into the laptop.

Safer option is to NOT have any other drive connected to the desktop when installing Ubuntu.  That will force GRUB to be installed to that drive.

Second, when you install to the desktop, the installer sees THAT hardware and will install the associated drivers.  When you put the drive back into the laptop, it will have different hardware.  Ubuntu will then have to detect the new hardware and load new drivers, instead.

While this might not pose a problem, it is not always guaranteed to work.  So, do not be surprised if, after you put the drive back into the laptop, one or more hardware devices does not work.

Also, if the laptop is using ATI or Nividia video hardware, you will  have to install the restricted drivers AFTER replacing the drive back into the laptop.  Same is likely to be true of any other restricted drivers -- for example, wired or wireless networking.

---

### Post by JohnBN on 2011-06-01
Noted!  The installer did ask me which drive I wanted to install to, but considering I was really just using the desktop as a big clunky CDROM drive, it seemed prudent to pull the HD out of the equation.
 
I think the age of the notebook was a key factor - any newer machine would boot to USB.  Case in point, many netbooks: no external drives, but able to boot from USB.  Voila, life is good.  My recent experience was pretty dire; the notebook was obviously meant to be mated with a docking station, which was nowhere to be found.  That being said, needing "high end" drivers weren't worrying me!
 
As an aside, Ubuntu installed both networking drivers and went through the whole process eventually asking me to join a wireless network.  It also loaded the correct video driver and set the right screen resolution.  I was pretty impressed!  I guess seasoned veterans wouldn't find this surprising, but I'm not one so I did!  The only interaction I had was to enter the wireless key and open Firefox and I was browsing.  (BillG, are you reading this?)

I see more Ubuntu in my future. :wink:

---

