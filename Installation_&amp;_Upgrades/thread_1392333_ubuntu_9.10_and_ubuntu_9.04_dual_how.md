---
title: "ubuntu 9.10 and ubuntu 9.04 dual how?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by panterus on 2010-01-28
trying to get a jaunty and koala to run on one computer whats the best way to go about it dont really want lose what i have but apparently some programs don't do well in 9.10. i really haven't had much experience with unix/linux systems yet.

---

### Post by panterus on 2010-01-28
bump

---

### Post by darkod on 2010-01-28
So, you already have 9.04 running and you have spare unpartitioned space on the hdd?
If you need to repartition the existing 9.04 I don't know the best way to shrink ubuntu.
As far as installing 9.10 is concerned if you have the spare space, just install it and in the last screen before clicking Install click on Advanced and tell grub2 not to install, if you plan to keep using grub1 from 9.04 if you are more familiar with it.
On the other hand, installing grub2 to the MBR should also work and it should detect your 9.04.

---

### Post by panterus on 2010-01-28
actually im using 9.10 and want to install 9.04 as secondary without losing the what i have in 9.10. 
funny thing, i have a friend in denmark that uses darko d. as a handle online, heheh

---

### Post by lindsay7 on 2010-01-28
Just set up a partition for 9.04 and install it there using the manual option on the 9.04 install cd. You can still download in online.

---

### Post by admiralspark on 2010-01-28
You should have an option when going to install Ubuntu 9.04 that says "install alongside other OS" or some such. Check that, and if you can find it select to not install grub. If you do by accident, you can go back to using grub2 later on. 
I used to dual-boot with both because I didn't know how well karmic was going to run, but I found grub2 to be much faster loading and only a 3 second shutdown. I have a 4-5 year old laptop, so that's great news for me.

---

### Post by panterus on 2010-01-28
thanks if its that simple ill give it a go:popcorn: heheh, we'll see how this movie plays out;)

---

