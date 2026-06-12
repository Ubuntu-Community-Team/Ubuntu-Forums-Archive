---
title: "Can't Install Ubuntu.  Period."
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-03-16
I tried 3 CDs to make sure it wasn't a corrupted CD and downloaded twice.  

I resized my partition and gave Ubuntu 13 Gigs in gparted.(It still says unnallocated if that means anything)

I was expecting Ubuntu to pick up the rest and see that thats available.. But anyway.. before I get to ahead of myself..

I put in the CD for Ubuntu. Everything seems to work fine.  I hit the first option for install or boot and then the Ubuntu logo comes up with a loading bar that goes back n forth.  This stays on the screen forever.

What should I do?


(I have a feeling I didn't do something correctly with the partitioning..)  Should I make it a format or something?

Thanks,

Dominick

---

### Post by massivevoid on 2007-03-16
I have the same problem too, but with Kubuntu. I burned a CD and DVD. Both freezing at that loading bar.

---

### Post by mmilitia9 on 2007-03-16
This sucks too.  I Partitioned Mandrake, Suse, Red hat to make them all work with XP at one point along time ago.. They all were blah.  I'm dieing to try Ubuntu because everytime I use Stumble Upon I atelast get 2 sites hyping it up..Soo, The first time I gave it a shot was about 3 months ago(I just never posted about it until now)  I finally am that desperate to get this baby on the harddrive so I can check it out.  Ubuntu!!! RUN FOR ME!! AHH!! lol 


thank you for the help in advance! :)

---

### Post by Kateikyoushi on 2007-03-16
Tell us about your hardware, and what exactly did you do ?
There are a few step what you have to do while partitioning the drive so we have to know where to pick it up.

You have to create 2 partitions, one for swap with swap filesystem make it 1GB and a bigger one at least 6GB if you want to try other desktop environments softwares, make it ext3, format both there is a checkbox on the right, finally set the mount points for them swap as swap and the big ext as /.

You can find more detailed instructions with screenshts here. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by massivevoid on 2007-03-16
Now this is weird. I tried both the CD and DVD on another desktop computer that I have and both works just fine. Even so on my laptop. 

Don't understand why it won't load on my primary desktop. A year ago I had Ubuntu on it.

AMD 3000+
1GB PC3200
ATI x800XL 256MB

---

### Post by Kateikyoushi on 2007-03-16
Because of your video card, read this guide to fix it. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by massivevoid on 2007-03-16
Thanks for the info. :)

---

### Post by mmilitia9 on 2007-03-16
Heres my hardware:


Intel® Pentium® 4 CPU 2.80GHz @ 2799MHz (Intel Corporation D845GVSR mainboard) 
(RAM) 1GB 
(HDDs) 120 GB 
 (VGA2) NVIDIA GeForce FX 5500 (OS) Microsoft Windows XP Home Edition (SP2),

I Followed your instructions except for one part. In GpartEd, I couldn't name any of the new partitions I created.  I changed them to Ext3 though.. But thats all I could do.  I haven't tried booting Ubuntu after change.. Going to give it a shot right now.. Maybe Ubuntu will pick up 2 empty slots for it to use and not stay forever on the load bar? Hopefully.




Update:

It didn't work.

---

