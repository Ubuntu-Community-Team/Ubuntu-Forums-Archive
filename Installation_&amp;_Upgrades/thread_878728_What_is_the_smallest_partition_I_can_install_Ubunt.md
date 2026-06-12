---
title: "What is the smallest partition I can install Ubuntu on?"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by jmelton on 2008-08-03
I updated Windows XP on my son's computer the other day.  It's an older laptop with only about a 19 gig hard drive, and the XP partition we set up is 16 gigs.  Can the current version of Ubuntu run on the 3 gigs we have left, or should I install an older version, or would some other distro work better for a small partition?

---

### Post by insane_alien on 2008-08-03
technically yes, though 4GB is the recommended minimum.

---

### Post by sisco311 on 2008-08-03
I've installed ubuntu on my 1GB mp3 player.


command line system + xorg + openbox + 
seamonkey (flash, mplayer plugin) + 
mplayer (media player, tv) + xfe (file manager
+gui text editor+image viewer) +
xfce4-panel, xfce4-terminal, alsamixer

>  df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             912M  851M   13M  99% /
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by powerpleb on 2008-08-03
> **jmelton said:**
> Can the current version of Ubuntu run on the 3 gigs we have left, or should I install an older version, or would some other distro work better for a small partition?

You could resize the partition (use the live CD and gparted) to give Ubuntu some more space.

You could put a mini distro like [Damn Small Linux]("http://www.damnsmalllinux.org/"), [Puppy Linux]("http://www.puppylinux.org/") or [AntiX]("http://antix.mepis.org/index.php/Main_Page") on that much space quite comfortably.

You could do as another poster suggested and install a [barebones Ubuntu]("http://www.psychocats.net/ubuntu/minimal") and build a minimal system from that. Better still, you could use [Arch Linux]("http://www.archlinux.org").

---

### Post by wpshooter on 2008-08-03
My suggestion would be to get rid of XP altogether and install only Ubuntu.

Your son would have a much better computer & O/S.

---

### Post by logos34 on 2008-08-03
I see yet another way to free up space:

--reduce xp down to ~10 gb.  Put My Documents on a separate fat32 or ntfs partition, which you can share as a data storage area with ubuntu.

--Give ubuntu / the rest (+ swap no larger than ~512 MB).  Download all the updates and any desired packages, then run **apt-get clean.  **Do that periodically.  That right there will free up ~ half gig.

---

### Post by jmelton on 2008-08-03
> **powerpleb said:**
> You could resize the partition (use the live CD and gparted) to give Ubuntu some more space.

You could put a mini distro like [Damn Small Linux]("http://www.damnsmalllinux.org/"), [Puppy Linux]("http://www.puppylinux.org/") or [AntiX]("http://antix.mepis.org/index.php/Main_Page") on that much space quite comfortably.

You could do as another poster suggested and install a [barebones Ubuntu]("http://www.psychocats.net/ubuntu/minimal") and build a minimal system from that. Better still, you could use [Arch Linux]("http://www.archlinux.org").

Thanks to everyone for the suggestions.  

Shrinking the XP partition isn't an option because he has some game programs that take up a lot of space--I just wiped his hard drive which previously had about 13 gigs devoted to XP and the rest to Ubuntu, and there just wasn't enough room on XP, which he uses far more than Linux.  So, we'll probably go with a bare-bones Ubuntu or one of the other distros suggested.

---

### Post by Ptero-4 on 2008-08-03
Or you could also put linux in an external HD (USB enclosures are pretty cheap and a 40GB 3.5 IDE HD is bargain basement this days).

---

