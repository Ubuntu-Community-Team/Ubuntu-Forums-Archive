---
title: "Is it possible to access the files on my hard drive from the liveCD?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by delsydebothom on 2010-09-21
I seem to have done something with GRUB that makes the computer boot to a nearly black screen with what looks like tiny multi-colored text at the very top of the screen, repeated in such a way that it looks like the computer is trying to draw the screen more than once. I wish I could post a picture, because it reminds me of my old DOS where I'd choose the wrong VESA driver for a game.

Anyway, I have less than 20GB free on my hard drive, and I didn't want to try to repartition it for a new install of Ubuntu unless I had to; I have a lot of valuable information in there with no backup.

I found a liveCD of Xubuntu 9.04 in my stuff. Sadly, I don't have a liveCD of Ubuntu 10.04, which is what I've been using. I've already tried using the alternate install cd to reinstall GRUB to no effect. 

I was hoping to boot the liveCD and backup the files on my hard drive before doing a fresh install of Xubuntu, and then using that to get and install Ubuntu 10.04 again. Is this possible, or am I going about this the wrong way altogether?

---

### Post by LK2H on 2010-09-21
well my thing is, DONT EVER USE XUBUNTU,

thank you.

---

### Post by TNT1 on 2010-09-21
> **delsydebothom said:**
> 

I found a liveCD of Xubuntu 9.04 in my stuff. Sadly, I don't have a liveCD of Ubuntu 10.04, which is what I've been using. I've already tried using the alternate install cd to reinstall GRUB to no effect. 

I was hoping to boot the liveCD and backup the files on my hard drive before doing a fresh install of Xubuntu, and then using that to get and install Ubuntu 10.04 again. Is this possible, or am I going about this the wrong way altogether?

Sounds like a perfectly reasonable way to go about it. Oh, and I like xubuntu, and once you have your stuff backed up, install xubuntu, and then add the gde or kde or flukbox or whatever wm works for you.

---

### Post by gnush on 2010-09-21
```

sudo mkdir /mnt/disc
mount /dev/X /mnt/disc

*Replace X with the hard drive you want to mount (sda1, sdb1, hda1, etc.).*

```

When you've done what I wrote above, you should be able to access your files in the /mnt/disc directory.



> **LK2H said:**
> well my thing is, DONT EVER USE XUBUNTU,

thank you.

Why not?

---

### Post by lasa55 on 2010-09-21
HELLO THERE!

I'VE NEVER USED A XUBUNTU LIVE CD TO BACKUP INFO IN MY HDD, I RECOMMEND YOU TO USE AN UBUNTU LIVE CD TO DO THIS. YOU CAN DOWNLOAD FOR FREE AT: [www.ubuntu.com](www.ubuntu.com) (I guess this can be do the same thing with Xubuntu)

IF YOU GOT A PORTABLE HDD, ITS SIMPLE TO DO THE BACKUP, JUSTO BOOT THE CD, GO TO PLACES IN UPPER PANEL, AND SEARCH FOR THE NAME OF THE HDD WHERE ARE THE FILES YOU NEED. IF YOU HAVE ANY TROUBLE CPYING FILES, JUS OPEN A TERMINAL (alt+F2 AND TYPE.- gnome-terminal) THEN TYPE: sudo nautilus. (maybe you'll need to write a password, its possible, even if this is a live session).

SO YOU CAN ACCES AS SUPER USER AND YOU SHOULD BE ABLE TO COPY YOUR FILES.

WHEN YOURE DONE, THEN CLICK ON INSTALL ICON AND CHOOSE DESIRED OPTIONS.

ANY QUESTION FEEL FREE TO ASK.

---

### Post by delsydebothom on 2010-09-21
> **LK2H said:**
> well my thing is, DONT EVER USE XUBUNTU,

thank you.

Umm...okay?

---

### Post by delsydebothom on 2010-09-21
> **gnush said:**
> ```

sudo mkdir /mnt/disc
mount /dev/X /mnt/disc

*Replace X with the hard drive you want to mount (sda1, sdb1, hda1, etc.).*

```

When you've done what I wrote above, you should be able to access your files in the /mnt/disc directory.





Why not?

Thank you for this; it is working like a charm. Or at least the way I've heard charms are supposed to work.

---

### Post by delsydebothom on 2010-09-21
> **lasa55 said:**
> HELLO THERE!

I'VE NEVER USED A XUBUNTU LIVE CD TO BACKUP INFO IN MY HDD, I RECOMMEND YOU TO USE AN UBUNTU LIVE CD TO DO THIS. YOU CAN DOWNLOAD FOR FREE AT: [www.ubuntu.com](www.ubuntu.com) (I guess this can be do the same thing with Xubuntu)

IF YOU GOT A PORTABLE HDD, ITS SIMPLE TO DO THE BACKUP, JUSTO BOOT THE CD, GO TO PLACES IN UPPER PANEL, AND SEARCH FOR THE NAME OF THE HDD WHERE ARE THE FILES YOU NEED. IF YOU HAVE ANY TROUBLE CPYING FILES, JUS OPEN A TERMINAL (alt+F2 AND TYPE.- gnome-terminal) THEN TYPE: sudo nautilus. (maybe you'll need to write a password, its possible, even if this is a live session).

SO YOU CAN ACCES AS SUPER USER AND YOU SHOULD BE ABLE TO COPY YOUR FILES.

WHEN YOURE DONE, THEN CLICK ON INSTALL ICON AND CHOOSE DESIRED OPTIONS.

ANY QUESTION FEEL FREE TO ASK.

Thank you. So far, though, everything seems to be going okay.

---

