---
title: "Help upgrading my eee!!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by kDDs on 2008-04-28
Ok so I have a 2G eee with 7.10 on it, but want to upgarde to 8.04.

I installed ubuntu on its super small 2GB HDD, and the upgrade needs 600mb+ free space on mount point /, which i obviously don't have!

I installed using this: [http://ubuntulite.tuxfamily.org/?q=node/2]("http://ubuntulite.tuxfamily.org/?q=node/2")

So is there a way I could:

1. use a USB flash drive to temporarily add space to upgrade?

2. get a "lite" version of 8.04?

Thanks!

---

### Post by noremac on 2008-04-28
Have you checked out the EeeUser forum? I am running eeeXubuntu (which is 7.10) on my 4G Eee right now. They have been discussing upgrading in the forum recently, but I personally don't have much interest in upgrading quite yet. 

But you may want to have a look there as well.
forum.eeeuser.com

-Cameron

---

### Post by kDDs on 2008-04-28
Yer, I thought this place would be more knowledgeable as my problem is more ubuntu related than related to the eee.

Surely it most be possible to use something like gparted and add the usb drives disk space to the internal drive, upgrade and then remove it?

Alternatively, is there a way to install ubuntu 8.04 from the live CD without having to install things like openoffice etc. to save space?

---

### Post by mrsteveman1 on 2008-04-28
If you were hell bent on doing so, you can always overlay the space on that USB stick on top of the main drive with unionfs, but i don't advise you do this.

I would advise you to just reinstall if you want to upgrade things.

---

### Post by kDDs on 2008-04-28
Yer, I think thats the way I'll go with re-installing., I think I'll also try maybe opensuse on it see how that is.

But to answer my previous question; Is there anyway to install just the core comp-onents of ubuntu, to help keep it down to about 1.3GB after installation?

---

### Post by mrsteveman1 on 2008-04-28
The core of ubuntu is around 600mb i believe, slightly less. This is without x11 or any of the GUI libraries, including gnome.

The core of opensuse is around 750mb without a GUI.


Either of them, once installed with a GUI, take up substantially more.

The opensuse installer will let you deselect certain things but it wont get you much extra space, and sometimes it doesnt work well and selects more stuff than it was originally going to install, simply because you removed something, no idea why that happens.

---

### Post by kDDs on 2008-04-28
well im currently downloading of there super slow servers, so ill see what i can do. I'm currently on my eee and it seems to me that after restoring the default theme, it 2x faster starting up! anyway still want to ty opensus, I've tried xandros (default), XP and ubuntu, and so far ubuntu wipes the floor with the others!

EDIT: How well does a ubuntu/opensuse install go with  sd card? As the eee has an SD slot I could get a 8GB and fast sd card and as long as it would install and grub would reognse it, it would be great right?

---

