---
title: "Dual Boot question"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Androzani1 on 2012-12-08
Hi all.

I have a question about dual booting. If I selected "install alongside Windows XP" during the installation process, when it comes to distributing the size of Windows and Lubuntu, does the installer shrink both of my Windows partitions or just the C drive?

My HDD is laid out in a C and D drive configuration, so basically would the installer overwrite the D drive or shrink both of the drives?

Sorry for the bad wording :p

---

### Post by mlentink on 2012-12-08
Forget about C: and D:, those are Windows designations. You have one harddisk, with two partitions. The ubuntu installer will try and shrink the one with the windows operating system on it. The other one, most likely your data partition, will be left alone, which is most likely not what you want. Usually, the data partitions are the biggest, so you might want to shrink that one too.
To do this, choose the "do something else" option of the installer and shrink both partitions and subsequently make them adjacent. 


But first: MAKE BACKUPS of you valuable data

---

### Post by darkod on 2012-12-08
It's best that you create the unallocated space for ubuntu yourself manually. Especially since you are running XP.

If you let the installer shrink it, not only that you are not sure which partition it will be, but also XP will not have a chance to reboot after the shrink. And it needs to do that, otherwise it might break sometimes.

I am not sure the auto method always shrinks your system partition. It might shrink the second one, to put ubuntu at the end of the disk. In this case the second partition is probably the data one.

Since XP doesn't have a built in tool to resize partitions, you will have to use a third party software, or Gparted from the ubuntu cd running in live session. Shrink which ever partition you want, creating the unallocated space with the size you want for ubuntu. Do not try to create partitions from windows, just leave it as unallocated.
Reboot XP few times to do its disk checks.

Only after that start the ubuntu install and when using the 'along side' option it will use the unallocated space automatically.

---

### Post by Androzani1 on 2012-12-08
Thanks guys. If I do end up using Lubuntu, I'll just zip my files and put them on a USB stick, before putting Lubuntu on as the sole OS.

---

### Post by mlentink on 2012-12-08
> **Androzani1 said:**
> Thanks guys. If I do end up using Lubuntu, I'll just zip my files and put them on a USB stick, before putting Lubuntu on as the sole OS.

Since the support on XP will end soon, that is probably the wisest solution. And I'm sure that once you've gotten used to the GNU/linux environment in general, and *Ubuntu in particular, you'll never want to go back.

---

