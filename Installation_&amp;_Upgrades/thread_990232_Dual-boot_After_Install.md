---
title: "Dual-boot After Install"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by web250 on 2008-11-22
I currently have my whole hd with ubuntu on it. But I need to put Windows on it somewhere for a specific program.

Can I pull a few gigs off the back of the drive to do this, and how so? Also, how do I restore a GRUB bootloader after Windows in installed?

---

### Post by taurus on 2008-11-22
You can use gparted from the LiveCD in System -> Administration (it has to be LiveCD since you will need to shrink your Ubuntu's partition and you cannot resize it while you are using it) and create a partition from your Ubuntu's partition.  Format it as ntfs.  Then, reboot with the windows CD and install in that new partition.  When all of that is done, you need to recovery your GRUB since windows would wipe it off when you install it.  Otherwise, you won't be able to boot Ubuntu.  

And of course, back up your important files first before you resize anything.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Pumalite on 2008-11-22
They beat me to it

---

### Post by web250 on 2008-11-22
Ok one issue:

I already have 4 primary partitions (/, /home, /music, and swap). I can resize my /music (at the end of the drive) easily, but I can't make the new space NTFS since the max it allows is four primarys. Will Windows be able to find/format it, or do I need to delete a partition, and make an extended partition table?

---

### Post by taurus on 2008-11-22
Yes, you need to make one of those primary partitions into extended and then create logical partitions under that extended partition.

---

### Post by web250 on 2008-11-22
> **taurus said:**
> Yes, you need to make one of those primary partitions into extended and then create logical partitions under that extended partition.

Which would require me to format one of them I'm guessing?

---

### Post by taurus on 2008-11-22
Since you don't want to mess with / or you have to reinstall the whole thing and I guess you want to keep all your personally setting in /home.  Therefore, it seems like /music is the one that has to go for now.  You can still create /music again later but you need first to convert that primary partition into extended and then from that extended, create two logical partitions, one for ntfs (windows) and the other for /music again.

So, I guess it's time to backup that /music.  How large is that /music partition anyway?

---

### Post by web250 on 2008-11-22
> **taurus said:**
> Since you don't want to mess with / or you have to reinstall the whole thing and I guess you want to keep all your personally setting in /home.  Therefore, it seems like /music is the one that has to go for now.  You can still create /music again later but you need first to convert that primary partition into extended and then from that extended, create two logical partitions, one for ntfs (windows) and the other for /music again.

So, I guess it's time to backup that /music.  How large is that /music partition anyway?

I've been meaning to back it up anyway...it's like 25gb though. Even on DVDs I'm looking at like 7 discs or so.

---

### Post by meierfra. on 2008-11-22
>  create two logical partitions, one for ntfs (windows) and the other for /music again.

This will NOT work. As far as I know, it is impossible to install Windows on a logical partiton (without a primary "ntfs" or "fat" partition). So you also need to delete the swap partition. Then create a primary ntfs partition for Windows and logical partitions for Music and swap.

---

### Post by meierfra. on 2008-11-22
> I've been meaning to back it up anyway...it's like 25gb though. Even on DVDs I'm looking at like 7 discs or so.

Well, it is possible to convert a primary partition to  logical partition without formating. But I wouldn't recommend it without backup up. So backing  up and deleting the swap and music partition  is the easiest way to accomplish your task.

How about getting a small external drive?

---

