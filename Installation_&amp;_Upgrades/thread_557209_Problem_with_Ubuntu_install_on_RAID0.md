---
title: "Problem with Ubuntu install on RAID0"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by FnTm on 2007-09-22
Hi all!

Im her with a little bit of a problem with ubuntu Feisty install.

Sorry for giving you a link, but I think that it would explain my problem better.
[Justlinux Link]("http://justlinux.com/forum/showthread.php?p=873910#post873910")

P.S I would like to have both OS on the same RAID0 array.

Thanks allready!

---

### Post by Pumalite on 2007-09-22
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by FnTm on 2007-09-23
Thanks for the reply, will try to install it later today, but I found something, that i dont reall understand.

What does this mean?
> mkdir /boot/grub
cp /usr/lib/grub/<your-cpu-arch>-pc/stage1 /boot/grub/
cp /usr/lib/grub/<your-cpu-arch>-pc/stage2 /boot/grub/
cp /usr/lib/grub/<your-cpu-arch>-pc/<the staging file for your boot partition's filesystem>Ok I understand, that it makes some boot sequence, but what does 
,> <your-cpu-arch>mean?

Thanks alot, 
FnTm

---

### Post by krimz on 2007-09-23
The most common problem when installing ubuntu to a fakeraid seems to be that grub (the bootloader) doesn't recognice your raid-setup and therefore fails to install properly. What you have to do then is to manually copy the files needed from the live-cd to the grub folder of your installation.

You need to get the files corresponding to your system's cpu-arch (Usually it's i386-pc if you have a non 64-bit architecture and version of Ubuntu.)

Remember that you'll have to know how many partitions you have and to what partitions you mount / and /boot (if you have a separate /boot that is), and also that grub starts counting partitions from 0.

---

### Post by FnTm on 2007-09-23
> **krimz said:**
> You need to get the files corresponding to your system's cpu-arch (Usually it's i386-pc if you have a non 64-bit architecture and version of Ubuntu.)


Ok thanks, got some things clear, but it seems, that I do have a 64-bit architecture, because I have Q6600 CPU, but im going to install 32-bit linux version. Is it going to be the same - 1376-pc - for me, or something else?

---

### Post by krimz on 2007-09-23
If you're not installing Ubuntu for 64-bit then you should probably get the i386-pc versions. Be sure to really read through the part about configuring grub manually, if you do it wrong you'll most likely end up not being able to boot your system.

---

### Post by FnTm on 2007-09-23
Ok, lets say, that I config grub wrong. What will be the consequencies?Is my system just not going to boot, or something else?

How do I get it to work again? Buy new MB?

BTW, what is > <the staging file for your boot partition's filesystem>?

---

### Post by krimz on 2007-09-23
Worst case scenario: Grub won't be able to boot either os. If you know what you're doing you can probably fix this manually (repair the bootsector?) but if you're like me you'll probably end up reformating and doing a fresh install (a grueling ordeal). I doubt you'll be forced to buy a new mb though, even I haven't been able to break that one yet.

Regarding staging file, I just did: 

cp /usr/lib/grub/i386-pc/* /boot/grub  (copied everything)

at that stage, problem solved.

---

### Post by Pumalite on 2007-09-23
I would get rid of the Raid Array. Raid0=minimal improvement, lots of trouble. Raid5=going with suspenders and a belt and nothing to show for.

---

### Post by FnTm on 2007-09-23
> **Pumalite said:**
> I would get rid of the Raid Array. Raid0=minimal improvement, lots of trouble. Raid5=going with suspenders and a belt and nothing to show for.

I was thinking about it when all of this started, but then again, I spen allmost 100$ on that thing, and i really want to put em to good use, so I think I am going to stick with this so called RAID, but if it really bothers me, im just going to put in a software raid, and get rid of Windows for good.

---

### Post by Pumalite on 2007-09-23
That's partially better.

---

