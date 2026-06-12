---
title: "Restoring data on an NTFS partition"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by zugu on 2006-03-24
Still me.

I have Ubuntu 5.04 on an old PC. The hdd configutarion is like this:

HDD0: Ubuntu erased everything I had on this HDD when it was installed. No problem here, it is the way I wanted it to be.

HDD1: This HDD has 2 NTFS partitions. One 3 GB partition for my defunct Windows XP installation, and a 12 GB partition hosting important personal data and files.

The problem is my WinXP had to be reinstalled (in the same place it was before) but now it just freezes during setup. So I decided to dump XP, and switch to Ubuntu. I plugged-in HDD0, unplugged HDD1 and installed Ubuntu.

My question is: is there any way for me to plug the both hdds, boot Ubuntu from the first one, and be able to see and copy (for restoring purposes) the NTFS content on the second one? 

Also, after backing up all the data, I want to destroy the NTFS partitions on HDD1 and make it fully usable under Ubuntu for storing files. Is this also possible?

Again, any help provided here will have a major impact on my Ubuntu/Linux career, as I am a totally newbie.

---

### Post by xenmax on 2006-03-24
Yes, you can plug both hdds, but you have to change jumper settings on hdds to configure one as primary and other as secondary.

After backing up, you can play around as much as you want.
You can install both OSes on primary partiotions of same hdd, or one in each hdd. And as you would have backed-up, you can format your partitions as any type you desire.

---

### Post by zugu on 2006-03-24
Ok, this being possible is a good thing. Now how do I do it? I heard there is involved something called "mounting" - how do I mount a hdd/partition? And why do I need to change the jumper settings on the hdds? Isn't is enough to choose the drive to boot from from the BIOS?

Sorry for all the question marks, but I feel like I need more enligtenment :D

---

### Post by xenmax on 2006-03-25
If you plug in both the hard drives simaltaneously, you need to change the jumper settings on the hdds - its a way of letting the system differentiate b/w your hdds - think of it as a numbering.
If you are not very sure about plugging your 2 hdds, i suggest you take help of somebody who does.

---

### Post by pooler on 2006-03-25
Remember that Windows should be in the disk installed as the primary master (HDD0). You could get away with a good grub configuration (see the grub docs), but I prefer to play fair with windows ;)

PD: Remember to either:
a) Install grub in the primary master ("HDD1")
b) Tell the bios to boot from the primary slave ("HDD0")

---

