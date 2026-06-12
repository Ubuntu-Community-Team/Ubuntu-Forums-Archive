---
title: "How to disable/lock persistence?"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by killybilly on 2010-12-20
Hi, i made a persistent Live USB from the Ubuntu Maverick option “Startup Disk Creator” in the live cd distro. It works really good, i’ve installed the apps and changes i wanted, but now i’d like to ‘lock’ persistency so no new changes or any data whatsoever may be stored. Is there a way to disable this capability so it may behave just like the CD  adding the changes i made?

---

### Post by C.S.Cameron on 2010-12-20
I have not been successful trying to freeze persistence.
Every mod is stored in a file named casper-rw.
I have not found a way to limit permission or make read only.

---

### Post by killybilly on 2010-12-20
Thanks for your quick reply, hope someone may come up with a solution, i couldn't find a way to change permissions either... u_u

I thought i read somewhere about an application which can 'clone' the live USB (changes included) to a CD... have you heard of it?.. it wouldn't be the best solution but it definitely serves my interests.

regards ( ^,^)/

---

### Post by Joe of loath on 2010-12-20
The casper-rw file is a block file formatted as ext2. You can mount it on another Linux system, navigate to the mountpoint, and do 'sudo chmod -R 766'. That should make it read only for anyone except root.

---

### Post by killybilly on 2010-12-20
Thanks again for you replies,

Being as noob as i am:
A strange thing for me, i've created a new (default) user account in the Live USB but is also persistent, even when permissions on casper-rw says -rx- for users... 

Is it possible to mount the casper-rw file in a new user account created in the same Live USB to obtain the same desktop/apps/changes i made on the original persistent session but being -rx-?

( *.*)/

---

