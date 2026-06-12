---
title: "Repetative problems installing from Live CD"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by oxf on 2011-03-05
Hi,

Here's the situation. I'm trying to install Maverick from the live CD. If I select the straight install option it keeps reading from the Live CD and never starts to install properly.

If I select to boot from the Live CD the same thing happens, keeps reading from the CD for ever and ever.

I tried selecting "nomodeset" before booting from the CD. That starts to read the CD and then I get a huge string of errors scroll down the screen, anything from I/O errors, unable to read this that and the other, SQUASHFS errors, data cache error etc etc.

I know it's not my CD drive because I just installed Windows XP on a small partition without any problem (everything else with the CD drive was fine previously as well) So I burnt a new CD, same problem. This is the third live CD I made! I've checked the MD5 sum before burning.

I had a similar but less severe problem installing on another PC with the first Live CD I made. It wouldn't install but then if I first selected "nomodeset" and then unsellected it, installation would start as normal.

Anyone got any ideas what might be going on here???

Thanks

---

### Post by Rubi1200 on 2011-03-05
Please post the output of the following command from the LiveCD for the computer in question:

```
sudo fdisk -lu
```

To the best of your knowledge was the hard-drive ever part of a RAID setup?

If you open GParted on the LiveCD does it see the drive and/or partitions on it?

---

### Post by oxf on 2011-03-05
> **Rubi1200 said:**
> Please post the output of the following command from the LiveCD for the computer in question:

```
sudo fdisk -lu
```To the best of your knowledge was the hard-drive ever part of a RAID setup?

If you open GParted on the LiveCD does it see the drive and/or partitions on it?

Thanks for the reply..

The problem is I can't get the Live CD to boot!
The HD is new 120GB and all I have done is install Win XP on a 20GB partition.

---

### Post by Old_Grey_Wolf on 2011-03-05
> **oxf said:**
> 
I know it's not my CD drive because I just installed Windows XP on a small partition without any problem (everything else with the CD drive was fine previously as well) So I burnt a new CD, same problem. This is the third live CD I made! I've checked the MD5 sum before burning.

Have you tried the option to check the CD for errors?

It may not have burned properly. Burned at to fast a speed possibly.

---

### Post by Rubi1200 on 2011-03-05
The other option (if your BIOS allows it) is to try booting from a LiveUSB.

I recommend UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oxf on 2011-03-05
Thanks guys... Ok an update.

Initially I was wondering if there might be  problem with the CD drive on the laptop which I'm trying to install it on (and had Maverick on before I replaced the HD). However, I've ruled that out because:
1. windows and word installed without problem on its partition
2. I can boot from an older Karmic Live CD without any problem.

I checked the CD for errors from the menu on the Live CD. No errors found.

But.....

I then tried booting from the Live CD on another machine, my desktop. Unlike the laptop which keeps trying to read the CD and makes funny noises the desktop whirs a few times and then shuts the CD drive down.

However, after the initial language selection I hit F6 and toggle "nomodeset" on and then off again. Then went to boot from Live CD. It then boots up quickly.

OK then there's a problem with the Live CD. But no errors are reported, This has happened on three CD's now and why can I get it to boot on the desktop by toggling "nomodeset"? But not on my laptop..?

I'm very confused!

---

### Post by Old_Grey_Wolf on 2011-03-05
Try Rubi1200's suggestion above. I rarely use CD to install on OS. I use USB thumb drives more often.

---

### Post by oxf on 2011-03-05
> **Old_Gray_Wolf said:**
> Try Rubi1200's suggestion above. I rarely use CD to install on OS. I use USB thumb drives more often.

Unfortunately thats not an option for this laptop. There.s no USB option in the BIOS.

I have now managed to install it though. I went to another machine and made yet another live CD which now boots the laptop.. It seems that the ones burnt by the Desktop, while free of errors, are somehow tainted as a boot disk.  Why I will never know!

---

### Post by Rubi1200 on 2011-03-06
Glad you got things sorted out eventually :-)

---

### Post by oxf on 2011-03-06
> **Rubi1200 said:**
> Glad you got things sorted out eventually :-)

Thanks Rubi!. Installing all the updates this morning

I will mark this as solved even though I dont know quite how. If anyone else has this problem try burning a CD on a different PC!

~Katja

---

