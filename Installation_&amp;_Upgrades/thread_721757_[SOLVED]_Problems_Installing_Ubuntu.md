---
title: "[SOLVED] Problems Installing Ubuntu"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Literati on 2008-03-11
Alright, first a bit of backstory.
I've wanted to install Ubuntu for a little while, and recently, my C:/ drive seems to have gone Kaput, so I decided that might be a good enough excuse to do so.
So, I disconnected my C:/ drive and left my D:/ drive connected.
However, in my BIOS, it still lists the D:/ drive as my IDE Slave Drive, and I don't know if this could pose problems, hence why I'm letting you all know.

Now, my problem is, I'm trying to install Ubuntu, and I choose the default option (Install or Start Ubuntu) 
From here, it brings me to the loading screen with the orange bar bouncing from side to side. 

From here, I get an error:

Buffer I/O Error on Device sr0
followed by two other lines (began with an S, I can't remember now) 

This is my second copy of Ubuntu (Ordered one, and just now finished downloading one) and I just want the damn thing to work :P 

Any help would be appreciated. :)

P.S. I'm thinking it might be my CD ROM Drive itself, it's about 5 years old now, and I noticed that depending on the try, different things might happen.

Try 1: CD Doesn't Load. Get error before even booting into Ubuntu Directory
Try 2: CD Loads, freezes at 7% while loading Linux Kernel
Try 3: CD Loads, give above-described error
Try 4: CD Loads, gets PAST above error, shows a mouse on screen, loads a pale tan background, freezes.

What gives?

---

### Post by Pumalite on 2008-03-11
If you are going to have just your 2nd drive, make sure is Master: cables, jumpers, BIOS.

---

### Post by Literati on 2008-03-11
> **Pumalite said:**
> If you are going to have just your 2nd drive, make sure is Master: cables, jumpers, BIOS.

Okay, I switched the jumper to Master, and I'm usingMaster cabls. Now the only problem isthat my BIOS isn't detecting it.

EDIT: The cable just wasn't in secure. However, when I went into the BIOS, it still lists it as Slave!
[THIS]("http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1227&p_created=1031610289&p_sid=Ep46et-i&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9NDEwJnBfY2F0cz0wJnBfcHY9MS40MTAmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9leCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTZZMDgwTDA*&p_li=&p_topview=1") is the drive that I'm using. And I put the jumper in the Maser position...
DOUBLE EDIT: Wow. I got it. I'l try the CD again and post back...

---

### Post by Literati on 2008-03-11
Okay, this is the eror I'm geting again...

[166.808718] (this number changes a lot) Buffer I/O Eror on device sr0, logical block 329679.
I get the same eror for logical block 329680

Then I get the following:

SQUASHFS error: sb_bread failed reading block 0xa067f
SQUASHFS error: unable to read fragment index table

EDIT: While trying again I got the previously mentioned errors along with 

SQUASHFS error: Unable to read Cache Block
SQUASHFS eror: Unable to read inode

*sigh*

---

### Post by Pumalite on 2008-03-11
Try the Alternate CD. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on your iso, burn at 4x or less, on CD-R.

---

