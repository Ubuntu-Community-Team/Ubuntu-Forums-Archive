---
title: "Installing Ubuntu on 9 year old dell laptop- 'segmentation fault'?"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by volvodude101 on 2009-11-14
Hey
    I have a dell laptop made in 2000, an inspiron 5000e, which I recently tried to install Ubuntu 9.04 on. However, after beginning the installation, I ran into problems. The installation seemed to be running fine at the stage where the progress bar bounces back and forth between the right and left sides, but as soon as it began to indicate a small amount of progress, the cd drive slowed down and stopped, and the computer seemed to be doing nothing. originally, after a long time waiting for something to happen, the Ubuntu logo and progress bar were replaced by and error message stating something about a segmentation fault, but now the computer just freezes and continues to say nothing. I have tried some of the special options like apci=off, but to no avail. How can I get Ubuntu to work?
Thanks

---

### Post by Richardarkless on 2009-11-14
Got a couple of questions

1.What is the specs of the laptop in question

2. What was the burn rate and have you tried burning another one at the lowest speed possible

3. Have you tried installing using the alternative install

---

### Post by volvodude101 on 2009-11-14
The laptop in question is a Pentium III-800mhz, 128mb RAM, 20gb HDD. I don't know what the burn rate was of the disc but I know i was able to install Ubuntu on one of my desktops using the same disc-maybe I should do that 'check disc for errors'?. What is an alternative install? srry im a noob Linux-wise

---

### Post by paxmark1 on 2009-11-15
Old computers cd-roms can be a little dodgy.  If you have an external cd-rom you might want to try using that.  When you burn the copy (I use cd-rw's), use your newer computer and burn at a slow speed.  Verify the md5.  You probably cannot do a usb install with an older laptop, but if you can, I have become a fan of that.  

Did you use the live cd or the alternative cd?  If you have the live cd try a test drive without installing.  For installing to older equipment, I prefer using the alternative cd.  (That is why I like rewriteable cd's for Ubuntu, I have 2 cd's I need every 6 months, repeat).

peace,  mark

---

### Post by nexes128 on 2009-11-15
You may also want to consider installing xUbuntu instead of ubuntu 9.04 as given the system specs it may have some issues running ubuntu comfortably

---

### Post by awam66 on 2009-11-15
> **nexes128 said:**
> You may also want to consider installing xUbuntu instead of ubuntu 9.04 as given the system specs it may have some issues running ubuntu comfortably

Yes I would agree with that as 128Mb ram is way too little. Ram is very cheap at he moment so a ram upgrade would be useful.

---

### Post by CharlesA on 2009-11-15
> **awam66 said:**
> Yes I would agree with that as 128Mb ram is way too little. Ram is very cheap at he moment so a ram upgrade would be useful.

Unfortunately if it's 9 years old, it'll be a pain (and expensive) to get more RAM for it.

---

### Post by howefield on 2009-11-15
You aren't likely to enjoy the experience of Ubuntu on such a machine, even if you can get 9.04 installed. Both the processor and ram are weak when set against the recommended specs.

[https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.04/installation-guide/i386/minimum-hardware-reqts.html)

As suggested, you might want to try Xubuntu, or maybe even a different distro altogether.

---

### Post by wandalalakers on 2009-11-15
For low spec machines I install Knoppix 5.1.1.  You might even try puppy.

Knoppix 5.1.1
[http://www.gtlib.gatech.edu/pub/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso](http://www.gtlib.gatech.edu/pub/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso)

Puppy
[http://www.puppylinux.com/download/index.html](http://www.puppylinux.com/download/index.html)

---

### Post by volvodude101 on 2009-11-15
I tried to upgrade the RAM with a 256mb stick, but the laptop wouldn't accept it. it wasn't because I didn't get the right stick, just this old laptop has some very strange behaviours because it would not accept any change in memory whatsoever, even removing one of the sticks already in it. I have dsl linux live disc, what is puppy like compared to dsl? I have done a bit of research about those 2 because I put dsl on my friend's old pentium 1 laptop for him

---

### Post by ????123856 on 2009-11-15
Try using DSL Linux.

---

### Post by volvodude101 on 2009-11-15
Just wondering...instead of burning yet another linux live disc, could I copy an ISO's contents to an ext2 or 3 file system and would it be bootable? I thought I could do this with puppy linux ISO just to try it. I have an ext2 driver for windows xp, which is currently on the laptop

---

### Post by ????123856 on 2009-11-15
Does your ext2 driver allow booting from ext2 volumes? If so you may if not nice try, but you failed, no offence. If unsure try anyway.

---

