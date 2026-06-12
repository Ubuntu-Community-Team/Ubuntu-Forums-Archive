---
title: "Wanting Linux installation from External HD to Internal HD on Laptop."
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Souzetsu on 2007-12-12
So I wanted to try out Linux, and bought an external HD to install it on. Turns out that I love it more than Vista, and now I want to move the installation to the internal HD. I'm running this on a Gateway laptop with Windows Vista installed on my internal HD while I have Linux installed on my external Maxtor OneTouch Mini HD via USB. How should I go about doing this?

---

### Post by MeathooK427 on 2007-12-12
You should probably do a clean install on the laptop. That's my .02. If you need to swap some files, then just hook the external up to the laptop. But cloning can bring up some problems.

---

### Post by Souzetsu on 2007-12-13
Okay, but what's the best software to use for making/resizing partitions safely in Vista?

---

### Post by logos34 on 2007-12-13
> **Souzetsu said:**
> Okay, but what's the best software to use for making/resizing partitions safely in Vista?

You should use the Vista's built-in disk mgnt tool

---

### Post by MeathooK427 on 2007-12-13
IDK about Vista, but in XP I use O&O Defrag Professional, and it's excellent. Maybe they have a version compat. with Vista? Hah! Doubt it :(

---

### Post by Souzetsu on 2007-12-14
> **logos34 said:**
> You should use the Vista's built-in disk mgnt tool

That will only allow me to shrink the drive down by 6 GB, much less than what is available. Should I just use gParted?

---

### Post by logos34 on 2007-12-14
> **Souzetsu said:**
> That will only allow me to shrink the drive down by 6 GB, much less than what is available. Should I just use gParted?

you know, a number of people seem to have had the same problem lately...Did Microsoft code it that way purposely? (I wouldn't put anything past them).  Either that or you have some files scattered at the end of the disk... defrag a few times to compact them..if you have to temporarily disable hibernation file and virtual/swap memory.  (even turn down system restore or whatever vista calls it).  See if that helps.  Otherwise you'll have to use gparted.

---

### Post by Souzetsu on 2007-12-25
Well, I was able to do it a few days ago. The trick is to defrag using Vista's disk management tool. Then shrink as much as you want. If you want more, shrink, then defrag again, then shrink some more. Keep going until you get the wanted amount of space. Then use that unallocated disk space to your liking.

Thanks for the help guys.

---

