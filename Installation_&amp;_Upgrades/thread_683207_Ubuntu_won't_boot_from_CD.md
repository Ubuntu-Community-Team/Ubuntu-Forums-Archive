---
title: "Ubuntu won't boot from CD"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Ohioan on 2008-01-30
I just got a copy of Ubuntu 7.1 from a friend.  I tried to load the CD on my Toshiba laptop and it won't load up.  It boots to the selection screen from the BIOS, but then it takes forever to load up. 
After about 20 minutes I finally get the GNOME interface, but there is an error window that pops up, but there is no text.  The interface never fully loads either.

What could be causing this? 
I can boot from the CD on other computers so it's not the CD.

Thanks

---

### Post by apaciq on 2008-01-30
What are the specs of your laptop? How ram, hard drive, video...
Gutsy needs at least 256mb to live cd...if not..there are alternates out there...

---

### Post by jrthom444 on 2008-02-01
Can you boot from the CD on your computer?  and pls post your hardware specs.  If you don't know just flip your computer over and on the bottom there should be a sticker with the toshiba model number.  just post that.

---

### Post by Ohioan on 2008-02-06
It has 256 of RAM, but it shares that with the vid card so it was only registering 196.  I coul dload Xubuntu on the computer so I did that, then used Gpart to create a 1 gig swap partition.  That allows me to now run Ubuntu perfectly fine!

Thanks for the help!

---

### Post by klemens on 2008-02-06
do you have an floppy drive?

Got the same problem while trying to access the floppy drive that isn't there, it got in a sort of loop.
If you don't have any try to disable it in you're bios (what probably won't work, while it is an laptop).

---

