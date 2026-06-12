---
title: "ASUS M3N78-VM Motherboard Installation"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by alvalente on 2010-01-29
Hi folks,
 
I just purchased a Brand new ASUS M3N78-VM Motherboard with the AMD 64 Bit processor, 1TB HD and 2GB of RAM.
 
I have downloaded the Ubuntu Server v 9.10 and transferred the files from the ISO image to CD.
 
I know the disk is good because on another machine using a slighly earlier ASUS motherboard the disk check routine works and verifies that the disk is without errors.
 
Booting up back on the new machine from the install CD I get the Ubunto logo and then I get the "Choose Language" menu and then I get the menu to:
Install Ubuntu
Check disk for errors
etc.
 
No matter what option I choose I get a few flashes on the CD and then the screen goes blank and nothing further happens.
 
I know the HD and CD is good because I took the hard drive out of the new machine, plugged it into the older AMD machine (Still 64 bit) and it installed flawlessly. So now that I have an installed copy of the new 9.10 Server on the HD I re-plugged the HD back into the new machine and it still absolutely refuses to boot. I still get the blank screen and then nothing.
 
Has anyone had such problems with the new ASUS Motherboard.
 
AL Valente
[EMAIL="avalent3@nycap.rr.com"]avalent3@nycap.rr.com[/EMAIL]

---

### Post by Bright_View on 2010-01-29
Hi Alvalente,

First a question: can you run the live CD for any length of time?

I just had a problem that sounds somewhat similar to this, although I'm not sure that it's exactly the same.  You can see the thread here:

[http://ubuntuforums.org/showthread.php?t=1371462](http://ubuntuforums.org/showthread.php?t=1371462)

My problem ended up being that one of the memory modules was faulty in some way, even though it passed memtest many times.  If you have some spare ram that will work in the system, I'd throw it in and see what happens.  If your 2GB stick is actually 2 sticks of 1GB, then put each one in separately and see if you can install.

Also check your BIOS settings, because the ram that I had was supposed to run at 2.1V, rather than the 1.8V standard, so setting the system to default settings (generally the safest) was wrong for me.  I had to adjust the voltage manually in the BIOS.  

More info on the hardware may be of use to me and others on the board.

Hope this helps.

Dave.

---

### Post by doas777 on 2010-01-29
I've got 3 boxes with that mobo, and had no problems. I suspect your optical drive. they only last 1-2 years with regular use, and get really crochety when they start getting older.

---

### Post by alvalente on 2010-02-01
Problem Solved.
 
It's great when my brain wakes up and finally decides to do what it should have done in the first place.
 
UPDATE THE [EMAIL="#$@@%"]#$@@%[/EMAIL] BIOS
 
Once the BIOS was updated Ubuntu could not load fast enough.
 
Thank you for your reply.
 
Al Valente

---

