---
title: "xp/ubuntu dualboot on an ide drive.remove ubuntu?"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by doughed2003 on 2010-01-26
I have a dual boot setup of XP/Ubuntu on an ide drive.I was given a new 500gb sata drive.My mobo has both ide and sate connections.Now what i want to do is wipe the Ubuntu out and give xp the whole drive and load Super Ubuntu on the sata drive and make it dual boot.Can I install the sata and load Super to it b4 I remove the Ubuntu from the ata so that I can transfer files to the new drive? will I have issues with the boot loader after I remove the Ubuntu?

---

### Post by audiomick on 2010-01-26
I think you should be able to install to the new drive, do your transfers and then remove the old Ubuntu. You will then have to update the boot loader. How that works depends on which one it is.

---

### Post by oldfred on 2010-01-26
Some BIOS have issues with mixed PATA and SATA drives. If you can set the new SATA drive first in BIOS and install Ubuntu, it should install grub the the new drive's BIOS and see all three operating systems on update-grub.

After you decide to remove the old Ubuntu your system will still work, but you will have a grub in the old drive that wants to boot to a non-existing Ubuntu. Just for future use, you may want to make the old drive first in BIOS and run the windows repairs to make the old drive bootable on its own. Switch BIOS back and and update-grub and the grub in the new drive will only see the remaining systems.

I would not expand windows, but put in a NTFS partition for data. It makes it easy to share data between windows & Ubuntu and some even recommend that you have a separate data partition for windows even if you are only running windows. That way if the operating system has issues you can still get to data. Of course you separately need to occasionly do maintenance on the NTFS partition, defrag, houseclean, etc.

---

### Post by acho on 2010-01-26
I had using dual boot for xp and ubuntu... i hope this tutor can help u... it just for beginner tutorial...

[http://yadi1blogs.wordpress.com/2010/01/17/split-your-pc-with-dual-operating-systems/]("http://yadi1blogs.wordpress.com/2010/01/17/split-your-pc-with-dual-operating-systems/")

---

### Post by doughed2003 on 2010-01-28
thank you for your replies so far.I will be working on this for a few days as my time for it is limited.when I first set up the dual boot I had grub issues but got them fixed with the help of the irc channels.they were very helpful to me and I greatly apreciate the help as I'm very much still a noob even after a year and a half.So I most likely will be posting again.Any other suggestions are welcome or links to some howto's but in English please.    P.S.Sorry for any typo's

---

### Post by acho on 2010-01-30
sory bro....

i think just an image can help u...lol.

---

### Post by doughed2003 on 2010-02-03
just an update as to hardware I have on hand to work with 1)500gb hdd,1)110gb ext.hdd,my original drive is a 160 hdd win XP at 68gb and the rest is ubuntu .using grub as boot loader (I think < noob>)a dvd+rw drive and a cd+rw drive.

---

