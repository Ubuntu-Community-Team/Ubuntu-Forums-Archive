---
title: "Blind spot help please ?"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by r4ik on 2006-09-06
I just installed Ubuntu on a slave drive with the master disconected.
Replugged the master and booted into Ubuntu again.
No options to choose from.
Went to the bios and set the HD boot priotity to,
Ch o M Maxtor with XP on it and
Ch o S HDs7blabla with ubuntu.

The disk i set first boots first.

Bios tells me

IDE Channel o master
IDE Channel o slave

What am i missing here ?

Thanks for youre time.

---

### Post by pyros on 2006-09-06
I'm missing what's happending here, it's booting to the drive you set first... it's supposed to to do that right?
or are you saying that it boots into ubuntu even when you set teh maxtor drive with xp first?

---

### Post by r4ik on 2006-09-06
The point is it givin' me no boot menu.
I just changed the master slave order and it i get a
grub error 18
I am not going to waste to much time on it and install on my
biggest drive and keep the slave as a spare.
Thanks anyway !

Blistering forum speed again read your answer 10 min ago !

---

### Post by pyros on 2006-09-06
yeah, these are the most active forums I've ever used.

---

### Post by Omnios on 2006-09-06
K from what I have read is that you disconnected the master hard drive before installing Ubuntu. When grub is installed it writes stuff the the BBR which on your master hard drive which it is apperently failing now. Also probably tryed writing MBR on your slave. One way of checking this is to go into biosy and choosing your slave as the boot from which will probably get you into ubuntu. 

 So it may be possible to reinstall brub onto the master MBR drive but there might be a bit of a mess on you other drive it it tryed writing MBR onto it but not shure.

---

### Post by r4ik on 2006-09-06
To Pyros,
You're right i should be an *** like this.
Enjoy Ubuntu !

---

### Post by r4ik on 2006-09-06
> **Omnios said:**
> K from what I have read is that you disconnected the master hard drive before installing Ubuntu. When grub is installed it writes stuff the the BBR which on your master hard drive which it is apperently failing now. Also probably tryed writing MBR on your slave. One way of checking this is to go into biosy and choosing your slave as the boot from which will probably get you into ubuntu. 

 So it may be possible to reinstall brub onto the master MBR drive but there might be a bit of a mess on you other drive it it tryed writing MBR onto it but not shure.

I did and it got me to ubuntu indeed. I read the suggestion to change HD's in the bios just to boot into what you need.
Not for me, like said going to install on one disk.
Thanks for you're suggestion.

---

### Post by Omnios on 2006-09-06
Hi I had a similar grub problem before, I tri boot with Ubuntu, Xp, and jst added Fedora core 5. Anyways the partition I put fedora on is planned as my try other distro partition so I did not want to install the fedora grub loader because if I removed fedora by grub would not boot. 

 One option you have is to reinstall grub with Ubuntu. I followed a how to to do this with my grub problem and it wiped my Ubuntu that I had to reinstall. ANyways there are a few articles on how to do this but be bery carefull like I said I tryed and wiped out my Ubuntu partition

---

### Post by r4ik on 2006-09-06
I will look into it when the matter comes up again.
Thanks for youre advice. :)

---

