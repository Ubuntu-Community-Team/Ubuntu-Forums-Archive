---
title: "PC won't boot Ubuntu"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by borntofish61 on 2010-02-22
I'm trying to install ubuntu on my laptop running Windows XP, and created a cd with ubuntu-9.10-desktop-i386.iso on it, about 706 Mb.  Anyway, I've tried powering off and on, and my PC doesn't try to run the install CD in the CD drive.  It just ignores it and starts windows.  I've done this several times.  I remember one time it asked how I wanted to install ubuntu, and I selected the "inside of windows" option so I can boot either Windows XP or ubuntu.  But nothing happens. 
 
Any advice appreciated.
Paul

---

### Post by zeroseven0183 on 2010-02-22
Remember to modify the boot priority in the BIOS settings. Your CD drive should go first before the hard drive.

Have you actually installed Ubuntu inside Windows already?
If you're not able to do so, what is the error message?

---

### Post by borntofish61 on 2010-02-22
zeroseven,
 
I checked the boot order by entering the the bios set-up, and the CD-Rom was ahead of the harddrive.  I moved the CD Rom to the top of the list, ahead of removable devices.  The PC booted into windows again, same as usual.
 
I had a ubuntu application installed in windows at one time, and I removed it.  Maybe I need to install it again?
 
paul

---

### Post by borntofish61 on 2010-02-22
I'm going to run the windows installer wubi again. Maybe that will fix it.  
 
Paul

---

### Post by clint0n on 2010-02-22
Make sure you are saving the changes on exit.

By the way on a lot of computers these days you won't need to change the bios settings. Most of the time their is a another option you can choose on the first computer screen called a boot menu which can do just a one time boot from a cdrom. Sometimes it's Esc, F10, F2 or F8.

---

### Post by zeroseven0183 on 2010-02-22
> **borntofish61 said:**
> I'm going to run the windows installer wubi again. Maybe that will fix it.  
 
Paul

Ok. Let's wait and see what happens.


> **clint0n said:**
> Make sure you are saving the changes on exit.

By the way on a lot of computers these days you won't need to change the bios settings. Most of the time their is a another option you can choose on the first computer screen called a boot menu which can do just a one time boot from a cdrom. Sometimes it's Esc, F10, F2 or F8.

Yes, that's right. In most HP machines I used, it's F9.

---

### Post by borntofish61 on 2010-02-22
I'm running umbutu now, thanks.
 
Paul

---

### Post by zeroseven0183 on 2010-02-22
> **borntofish61 said:**
> I'm running umbutu now, thanks.
 
Paul

Good. I'm glad to know that. Just don't hesitate to try things, it's part of learning.
Have a great Ubuntu experience!

---

