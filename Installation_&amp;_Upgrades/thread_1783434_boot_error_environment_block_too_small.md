---
title: "boot error environment block too small"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by i mat on 2011-06-15
hello
recently installed a new machine with dual boot windows 7 and ubuntu 11.04 (actually ubuntu studio dist, but i cant see how that matters in this instance)

the 2 os's are on the same (partitioned) HD. both my windows and ubuntu are 64 bit versions. bootloader is of course grub2. BIOS is ami v1.7. cpu is an i7

I can post more hardware details if needed

I actually have 2 issues that are probably related but may not be.

issue 1: after a period of inactivity on the machine (like a day), ubuntu will not boot. It is displayed by grub but when launching it, it will result in a hanging boot and a blank screen. However, when i reboot, ubuntu can be launched. I can log in and everything works fine.
(on this one i was thinking about some mainboard battery issue.. but the machine is quite new and also you would expect windows boot to also suffer from that problem. I have no problems booting windows)

issue2: before a succesfull ubuntu boot, i will always get:
error: environment block too small. Hit any key to continue
After this, ubuntu always launces fine.
(on this, i have no idea what that means and am not even sure if the error is an ubuntu or grub error, but i am betting grub. Therefore i already tried reinstalling grub but this did not fix it)

So seeing as both are boot-related you would think they are part of the same problem..

btw I am kinda new at this ubuntu game, but on the other hand no logfile scared me yet so hopefully someone could walk me through a checklist (or just telling me how to solve it would do just as well ;-)

cheers,
mat

---

### Post by i mat on 2011-06-17
please not everyone at once! :D

okay so i am definitaly convinced that the "environment block too small" error is indeed a grub error. It seems that it may be related to the fact that it was not installed in the MBR but into the root of the ubuntu partition.
Does it sound like my both problems could be related to this?
And if so: is it possible to move grub to the MBR without reinstalling ubuntu or windows?

cheers again,
mat

---

### Post by i mat on 2011-06-21
is there ANYbody out there..?

---

### Post by i mat on 2011-06-25
..the world can sometimes feel like a lonely place for a lad with an ubuntu problem ..

---

### Post by wackenroader on 2011-08-29
This affect- my installation too, before a energy down, fsck just check and fix my partition 3 times, before this this error appear. I believe is an a ext4 error.

Sorry for English.

---

### Post by wackenroader on 2011-08-29
I fix it! 

Go to directory /boot/grub and delete the file grubenv, then run the command in the terminal: sudo dpkg-reconfigure grub-pc .

Press enter and don't edit anything. 

Good luck!

---

### Post by i mat on 2011-08-29
Great, i wil try that. Will let you know how it went.
 
cheers,
Mat

---

