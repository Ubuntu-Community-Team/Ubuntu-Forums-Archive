---
title: "Kernel panic - not syncing: Attempted to kill init!"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by Pizmar on 2006-06-08
So, I've been trying to install Ubuntu... I already made an order for the free OS cds... but I'm impatient, and would like to figure this out.

I tried it using the desktop and server files so far, both for the amd64.  I verified the download's integrity using an md5checksum tool first.  So, I burned the image to a cd at 4x(even 1x once).  When I boot up the computer and check the disc for defects, it always gives me the message "Kernel panic - not syncing:  Attempted to kill init!".  This happened on every one of the 15 cds I tried.  And it doesn't matter which disc drive I use either.

I'm assuming the number on the left side means percentage...  The first time I tried it was at about 70, but lately its usually around 40 or 30.  It will even show up at a different number for the same CD.

As for my system: e-machine T6520 (all components are stock)
+AMD Athlon 64 3400+
+1024 MB DDR SDRAM
+DVD+/-RW 16x double layer drive
+48x CD-ROM
+Also, I'm using 700 MB OfficeMax brand CDRs.

Though my computer knowledge has decreased over the years, I want to assume the problem is with either the CDRs, the CD writer, or the CD reader... or maybe something fancier.

Thank you in advance for your help.  If you need additional information to solve this problem, let me know.

---

### Post by pak33m on 2006-06-08
Hello,

This could be two problems (and this comes straight form the Installtion Problems chapter in the Apress Beginning Ubuntu book that I'm reading):

A bad CD

or 

A bad memory module

I had the same problem last night whilst installing Ubuntu 6.06.  This was becaue of a bad memory module.  I removed it, put in another and viola.

How this helps...

---

### Post by Pizmar on 2006-06-08
So I might have to buy new memory?  Snap!


I'm gonna give the alternate install a try.  See if anything comes out of that.
Then, I will try a different brand of CD-R.  Replacing memory sounds kind of like a hassle(since I don't know any of the specifics of memory buying) so that's kind of the last thing I want to do.

---

### Post by pak33m on 2006-06-08
Hey Pizmar,

If it helps you any I have to buy a new memory module! I had only 95MB RAM in the laptop to start with and I added a 256MB module but it was detected as bad.  Mind you, I got the memory and laptop at no cost but I'm still having to buy more memory.

I also tried the alternate CD installtion with only 95MB RAM and it worked like a charm, as I found that the desktop CD would not fully install on my laptop.
Well, it's been running beautifully like Ubuntu does!
 
It's been a fun project for me anyway.  Now if I can only get that ethernet port active on the docking station...

I wish you luck with yours.

---

### Post by Pizmar on 2006-06-08
Well, I bought some sony brand CDRs, which did no good.  I also tried the alternative install, which did no good.

I did notice, however, that the first time I used a sony CDR, it went to 127, as opposed to the usual 30ish(number on the left)... 

Think the pressed CDs will make any difference? Or should I just get some new memory now?

---

### Post by kemeris on 2006-06-08
.

---

### Post by kemeris on 2006-06-08
It's quite possible that the problem has nothing to do with neither bad cds or bad memory. I'm also having "Kernel panic"-problems with a Vaio laptop and at the moment it seems to have something to do with bad kernel support for SATA-disks.

---

### Post by moleman5 on 2006-06-09
I am getting this error as well.  I had Breezy running o.k., upgraded to Dapper and the PC will not boot, giving me the "Kernel panic - not syncing :" error message.  I downloaded the Dapper Desktop CD, burned it to CD and checked the MD5 sum but it would not boot either - giving me the same error message, yet the Breezy instal CD boots ok.  I was going to reinstal Breezy but when I get home again I might try to boot from the older kernel in the Grub menu to see what happens.

Specs are Acer T5 Desktop, Semperon 3000+, 80gb hd, 1gb ram, Nvidia 6800GS.

Incidentally, Breezy didn't like any of the onboard peripherals - I had to disable onboard sound, graphics and network before I could install. I have added a video card and network card but have no sound at the minute but intend to get a Soundblaster or similar!

---

### Post by Pizmar on 2006-06-09
I solved the problem... in a really unexpected, random, and stupid way.

So I figure I'd try to install the i386 version onto my old computer.  See if it would work that way.  For the hell of it, I decided to boot this computer with the i386 disc... well, interestingly enough, it worked.  I succesfully installed the i386 version on my amd 64 computer.  Doesn't make sense to me, but at least it works.


I was happy and frustrated at the same time.  Never again shall I use logic to solve my problems.

Now you get to hear me ask questions about setting up Kubuntu!

---

