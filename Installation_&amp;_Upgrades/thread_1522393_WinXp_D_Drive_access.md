---
title: "WinXp D_Drive access"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Grovesy on 2010-07-02
Hello all

After some years messing around on virtual machines with various flavours of Linux on, I've decided to plump for Ubuntu 10.04 and have rebuilt my main PC with it on. WinXP is now running in a virtualbox machine instead ;)

So far so good and I've managed to sort most things. However, my original XP machine had a striped D_Drive (for my data). This is mountable from the "Places" menu and I can see all my files fine in Ubuntu. The problem is I have no write access to it. It's still NTFS too.

What I'd like to do is re-do this stripe in Ubuntu and then copy my data back to it. I already have a backup of the data on an external USB drive.

Anyone able to offer advice on the best way to go about this?

Regards,
Grovesy.

---

### Post by darkod on 2010-07-02
By striped do you mean raid0 array of two disks?

Or just a single disk with ntfs partition?

---

### Post by Grovesy on 2010-07-04
Yes darkod, my D_Drive is a RAID 0 stripe. I know this is not always a good idea, but I back it up regular so am not too worried about a single disk failing.

---

### Post by darkod on 2010-07-04
OK, if I understand correctly you will have ubuntu installed on a third drive, outside the array, and want to use a raid0 pair for data storage?

During the install it would have been best to use the alternate install cd and set those two disks in software raid. When you will not have a dual boot, it's better not to use the mobo falkeraid function, but instead use the ubuntu built in software raid function.

But if you use the alternate cd installer it would mean reinstalling now. There should be a way to add the raid0 now without reinstalling ubuntu. The package used for software raid is mdadm. But I don't know the exact procedure for adding them now without reinstalling.

Try searching around for how to add software raid in ubuntu, and the mdadm package.

---

