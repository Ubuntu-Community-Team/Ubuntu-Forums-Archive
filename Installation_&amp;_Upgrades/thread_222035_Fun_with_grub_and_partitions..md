---
title: "Fun with grub and partitions."
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by N84 on 2006-07-24
I'm not a linux guru, but I'm not a complete beginner either. I managed get a dual boot with Slackware, Mandrake, Knoppix, and Suse all on my first try with no problems. I liked the Ubuntu live CD and decided to try it out as my second OS. I don't know if this matters but I was dual booting slackware using lilo before I tried to install. 

I deleted my old slackware partition and created a swap partion and new linux partition for ubuntu. So my hardrive was partioned like this: hda1 – windows hda2 linux swap, hda3 ubuntu. I checked the boot option for ubuntu and had the mount point set as / (standard root directory, this comes into play later). Grub said it found the windows OS and asked if I wanted to install grub to the MBR and I selected yes. Everything looked good and I restarted. On the restart I get Loading grub... Error 17. I googled it and found some things mentioning sata drives (doesn't apply to me, I'm using a standard IDE drive) and doing something with the BIOS (couldn't find what anyone actually did in the BIOS though.) I decided to just try to reinstall. At the partition point I noticed something strange. The mount point on hda3 was set to /hda3/media. I know for a fact I didn't select this, but changed it back to / and continued. Continued the install, restarted and got the same Grub error.

I've tried to install from the live CD as well. I think the problem has to do with either grub not being able to find the linux partition (I tried to google it but didn't follow anything being said very well) or something with the mount point not setting itself to / and instead /hda3/media (Why? I specifically selected / ). Any help would be greatly appreciated.

---

### Post by zxee on 2006-07-24
Try to reinstall grub and be sure to use the correct grub notation hda3 in grub is (hd0,2). You can use the live/install cd to do that and/or you can chroot into the install and re-setup grub from there.If you need more specifics let us know. Hope that helps.

---

### Post by N84 on 2006-07-24
I used install CD's rescue option to reinstall grub to (hd0,2) but I'm still getting Error 17. I even tried (hd0) again just for kicks.

---

### Post by N84 on 2006-07-24
So I changed my BIOS from auto to the one recommended and it didn’t work. I changed it back and it still wasn’t working so I went to get something to eat. I come back, turn on the computer and it works. Must have been some Linux gnomes or something. Now I have a new problem. When I start ubuntu I get an error “Can’t read CTR” but it keeps going through the normal boot process. However when I reach the login shell the computer locks up. The curser keeps blinking but I can’t type anything and when I hit num lock the light doesn’t change. I’m moving my inquiries to a new thread in a more appropriate section than the install one. If you have any ideas please PM me.

---

