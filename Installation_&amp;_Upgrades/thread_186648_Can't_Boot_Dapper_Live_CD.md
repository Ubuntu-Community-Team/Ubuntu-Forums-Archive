---
title: "Can't Boot Dapper Live CD"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by musther on 2006-06-02
I'm happy to say I've been with Dapper for many months now, and as the final is out I'm very pleased, but I am also a little concerned.

The Dapper live CD won't boot on either of the two computers I happen to have lying around (they are completely different systems).  It gets to 'mounting root file system' and then freezes, after about 10 minutes the upsplash is replaced with text, a few lines suggesting it's having trouble with the CD or the drive (I've tested the CD, it's fine).  I've never had any problems (on either of these systems) with previous live CD's, so I'm not sure what has changed.  I intend to do some more testing soon to see how many machines I have this problem on.  

Anyone else had this problem, or know what's causing it?

I'm worried that a potential new user, sticking in the CD and getting what I got, won't even bother to try to get past it, they'll just give up.  The Ubuntu live CD is a wondeful (and I've always thought robust) thing, but only when it's working ;) 

Cheers

---

### Post by drewster4590 on 2006-09-16
I am having the same problem with my machine.  I know the disc works, but it has stopped working on my computer.

---

### Post by musther on 2006-09-16
Not quite sure when it happened, but certainly the latest CD's work on my machines now, so get the latest and try those...  Good luck.

---

### Post by drawab on 2006-09-17
Well I'm a newbie downloaded the Desktop live CD just a few hours ago version 6.06 I have the same problem, attempted to install it on two laptops (Toshiba Satellite P20-S103  & HP Pavilion ZT1175) on the Toshiba the computer stops accessing the CD after "adding live user" then after 10 minutes displays text --> 10 min later blank screen --> forever

On the HP machine CD loads up freezes at 14% loading Kernel --> forever.

I did a CD check and it showed a few files as mismatch, i was unable to note down the file details could that be an issue.

Any clues or help out my way...

---

### Post by musther on 2006-09-17
If the CD check shows some problems then I'd expect to see errors as you are.  First thing to do is check the md5sum of the file you downloaded, I'm in a rush right now, so I haven't got time to find the md5sum for you, but this link provides an overview of the process for windows users.

[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)

md5sum is a way to check that the file downloaded correctly, if it did you'll need to try burning another cd, do it on a low speed (so if you have a 30x burner, try burning at 2x), that should work.  If the iso file didn't download correctly you'll need to download it again, using a download manager may help.

Let me know if you need more help with the md5sum business..

---

### Post by BlaineM on 2006-09-18
Im having what sounds like the same prob.  The live cd boots, then tries to mount the file system... then hang.  I dont think that the problem is with the cd...  I ran the image with the md5, and it was perfect.  I just got a new computer, and the difference between the old and the new for me is that the new has a hyperthreading enabled processor, new motherboard, and a SATA drive.  The old ran Ubuntu on two different hard drives, and two different videocards.  The new computer has integrated video, so Im going to try to do some research about the new machine and find out what I can.  If it has to do with SATA, I'll let anyone know... If anyone is still following this thread.  Any ideas are welcome.

---

### Post by BlaineM on 2006-09-18
found what it was that was the matter for the install.  hope that this has something to do with what you are talking about.  [http://ubuntuforums.org/showthread.php?p=1516889#post1516889](http://ubuntuforums.org/showthread.php?p=1516889#post1516889)

---

### Post by drawab on 2006-09-19
@ MUSTHER = Thank you for the recommendation - seems like it was not a download error as I was able to get a clear md5sum.

But instead it was CD burning issue, finally burned a working copy using a 4x burning speed to avoid errors.  So for people who may have this problem in the future its highly recommended to reduce the burn rate so that burning errors can be avoided

---

### Post by musther on 2006-09-19
Glad to help.  I hope you're enjoying Dapper now!

---

### Post by tommycai on 2006-09-25
i'm getting the the error when it starts booting up it stops at "adding live cd user" and it has not worked since i've tried burning it with nero 3 different times and roxio 3 different times at 4x speed and then I even downloaded it 3 more times also and tried burning those but I seem to still run  into the same problem and then I just burned kubuntu with nero with 4x and still it stops at "adding live cd user"

---

