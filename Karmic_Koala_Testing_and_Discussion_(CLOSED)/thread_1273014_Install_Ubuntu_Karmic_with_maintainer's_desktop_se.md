---
title: "Install Ubuntu Karmic with maintainer's desktop settings."
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-09-22
Hi All,

I have separate home partition. Whenever i install a new distro the old settings remain. How can i install Karmic with its own settings not my previous settings?

I have three partitions /root, /swap and /home. 

Thanks,
SK

---

### Post by oboedad55 on 2009-09-22
> **soham_1207 said:**
> Hi All,

I have separate home partition. Whenever i install a new distro the old settings remain. How can i install Karmic with its own settings not my previous settings?

I have three partitions /root, /swap and /home. 

Thanks,
SK

You'll have to make room and create a new partition. Then you can do a clean install. I don't think because of the settings that you'd want to re-use your home directory for karmic.

---

### Post by mtate5000 on 2009-09-23
After creating a new partition (either primary or extended), when the installation asks for a mount point just put a " / " (without quotes of course). That way root,home,and everything else is self contained to that partition. I would choose to create an extended partition, that way you can cut that up into more partions later.

---

### Post by donniezazen on 2009-09-23
So there is no way to do it after you have installation is complete. How about deleting the hidden setting files from the home folder.

I don't really understand what do you guys mean by create new partition. Can you guys please explain?

Appreciate it.
SK

---

### Post by mtate5000 on 2009-09-23
I think oboedad and I both assumed you wanted to install karmic along side your current installation, in which case you could dual-boot. Going by your last post I assume you are going to replace it all together. Am I correct? I wouldn't recommend a replacement yet before a final release. If you just want to play around with karmic and keep your existing setup, then you'll have to create a fourth partition. That can easily be done (or undone) using the karmic live disc. I assume the bulk of your hard drive is your /home partition, just shrink it by 5G is plenty. Then make a new one and install it with / as your mount point and everything will be self contained. There's no need to create another swap. I hope I've answered your ?, we seemed to have been on different pages.

---

### Post by oboedad55 on 2009-09-23
> **mtate5000 said:**
> I think oboedad and I both assumed you wanted to install karmic along side your current installation, in which case you could dual-boot. Going by your last post I assume you are going to replace it all together. Am I correct? I wouldn't recommend a replacement yet before a final release. If you just want to play around with karmic and keep your existing setup, then you'll have to create a fourth partition. That can easily be done (or undone) using the karmic live disc. I assume the bulk of your hard drive is your /home partition, just shrink it by 5G is plenty. Then make a new one and install it with / as your mount point and everything will be self contained. There's no need to create another swap. I hope I've answered your ?, we seemed to have been on different pages.

Matate, I'm a little confused too. Maybe the OP can clarify what he wants to do, side-by-side install or wipe the drive, start with new install. In any case you are totally right that installing karmic alpha 6 is not a good idea. I'm running it now and updates are coming every few hours and sometimes they break as many things as they fix. Go with 9.04, jaunty.

---

### Post by VMC on 2009-09-23
> **soham_1207 said:**
> Hi All,

I have separate home partition. Whenever i install a new distro the old settings remain. How can i install Karmic with its own settings not my previous settings?

I have three partitions /root, /swap and /home. 

Thanks,
SK

Why not just create a new user or format "/home" partition before installation.

---

### Post by donniezazen on 2009-09-23
Thanks a lot.

I have a dual boot with Vista. I have installed Ubuntu with separate home partition. I do not have important data on this computer so i can play around on it. So, i am planning to install karmic on my Jaunty partition and my home partition will remain same.

If i understand you are asking me to install karmic on 5 GB partition. All root, swap, home etc in same partition that is a self contained Ubuntu partition.

What do you think if i make a home partition and a swap space and two Ubuntu installation that is Jaunty and Karmic? So i will be using same home and swap space for Jaunty and Karmic. Is that possible? Is that a good idea?

Thanks.
SK

---

### Post by Bastanteroma on 2009-09-23
If you create a new user account during installation it will have all the default settings.

Then you can move whatever files you need there and delete the old account (I run the file manager as root to do this: "gksudo nautilus").

---

