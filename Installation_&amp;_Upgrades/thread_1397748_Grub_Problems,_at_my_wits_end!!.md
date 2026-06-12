---
title: "Grub Problems, at my wits end!!"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by carz181 on 2010-02-03
Hello, i am trying to triple boot xp, osx and Ubuntu. Here is my set up:

hd(0,0) windows xp
hd(0,3) ubuntu

hd(1,1) osx

I am trying this on a dell precision workstation 530. (yes i know that i can't install regular osx on a non-apple computer, but this is patched and works fine)

My problem:
I am using grub to boot everything. I have added osx to the list by this:
title mac osx tiger
root  hd(0,3)
kernel boot/boot_v10

when i press this, i get: error 17 can't mount partition. help!

---

### Post by ubername on 2010-02-03
title mac osx tiger
root hd(0,3)
kernel boot/boot_v10

Why root hd(0,3)? That looks like your Ubuntu partition


Are you using grub or grub2?

---

### Post by darkod on 2010-02-03
Are you sure that is how you are supposed to boot osx? I know for windows, grub usually just "jumps" to the windows loader and it takes over. Process called chainloading. If it's similar for osx, it would look like:

title mac osx
root (hd1,1)
chainloader +1

Also, why are you trying with root (hd0,3), isn't that your ubuntu?
And make sure you are using grub1, and not grub2. If you have clean install of 9.10 that comes with grub2 which has different structure and files.

---

### Post by carz181 on 2010-02-03
i have tried that, it gives me error 13 cant execute file. This tells it to boot to boot_v10 which is able to recognize the mac partition, (i think). anyways somethings wrong =(

---

### Post by carz181 on 2010-02-03
how would i check the grub version?

---

### Post by audiomick on 2010-02-03
The only way I know is the Boot Info Script that meiefra made available. I am sure there is single command, but I think running it wont hurt you anyway. It tells you a lot about the current state of your setup, and might give you a hint how to proceed.
Follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
The  grub version and where it is shows up right at the top of the output file.

---

### Post by carz181 on 2010-02-03
thank you for the link. I am currently installing osx on the same hard drive with xp, and ubuntu with take the second one. Im not sure if this will make a difference but its worth a shot. Ill post my findings soon.

---

### Post by carz181 on 2010-02-03
I have re-installed everything, and I am now getting a HFS+ partition error when booting to osx

---

### Post by ubername on 2010-02-04
Maybe try re-installing grub-pc. The version in Lucid has just been upgraded and now asks where you would like grub to be installed. This may be true of other versions of Ubuntu. If you are not using Ubuntu for production stuff, maybe consider going to Lucid? (I have been using it since pre-alpha and it has been fine, but there will be plenty of chances for it to go wrong, however it is a tremendous learning experience!)

(Just realised you are booting from USB - does that upgrade the same way as a normal distro anyone?)


edit-- Sorry - Posted this in the wrong thread! Might be of some use though. Ignore the bit about USB!

---

### Post by carz181 on 2010-02-06
ok, different plan. I need to make a partition and set id=af, does anyone know how to do this?

---

### Post by carz181 on 2010-02-12
never mind i got it working with a different boot loader thanks!

---

### Post by kansasnoob on 2010-02-12
> **carz181 said:**
> never mind i got it working with a different boot loader thanks!

How about some feedback so it might help someone else in the future?

---

### Post by raymondh on 2010-02-12
glad you got it working.

I use grub-legacy and here is a visual of my menu.lst 3-booting win7, osx and 9.04.  They say GRUB2 ought to be more flexible and 'automatic' than grub-legacy in booting other OS'.

---

