---
title: "Partition and grub issues"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by NickMcRump on 2007-02-13
I partitioned my SATA hard drive using the gparted live cd before installing Ubuntu. I mounted as follows:

50 gig..........Primary.....ext3......../........boot flag set
under extended:
250 gig........Logical......ext3......./home
2 gig.............linux-swap

After installing Ubuntu I installed gparted to check out the partitions. The Primary partition had ~3 gigs used and the logical mounted to /home had ~4 gigs used. 

Should the home directory have this much data after a clean install (with updates)? It almost seems as if some things that were supposed to be installed in the primary partition were placed in the logical one. What leads me to believe this is when I'm booting, grub shows two separate instances of Ubuntu (along with XP which is on a different hard drive).

Any idea what's going on here? Thanks for the help.

---

### Post by IgnorantGuru on 2007-02-13
Doesn't sound right.  5-10G is plenty for /.  /home will contain very little with a fresh install (as in a few MB at most).  

Try using your file manager to see how much is in the folders.  (I don't use Gnome so I can't give you the details.)  Maybe GParted is misreporting.

I believe grub will normally have two ubuntu - one is a recovery mode.  I don't think that's a problem.

---

### Post by NickMcRump on 2007-02-13
> **IgnorantGuru said:**
> Doesn't sound right.  5-10G is plenty for /.  /home will contain very little with a fresh install (as in a few MB at most).  

Try using your file manager to see how much is in the folders.  (I don't use Gnome so I can't give you the details.)  Maybe GParted is misreporting.

I believe grub will normally have two ubuntu - one is a recovery mode.  I don't think that's a problem.

When you install packages wouldn't they be put on the partition mounted to / ? I guess 50 GB is a bit overkill but it seems like 5-10 might not be enough if you use a lot of apps. I looked at the properties of the /home folder and it says there's ~8 MB being used but only 230 GB of free space. It doesn't quite add up.

Also, I know about the recovery mode in grub. My list looks like this:

Ubuntu
Ubuntu (recovery)
Ubuntu
Ubuntu (recovery)
memtest
win xp

---

### Post by IgnorantGuru on 2007-02-13
> **NickMcRump said:**
> When you install packages wouldn't they be put on the partition mounted to / ?

Yeah.

> I guess 50 GB is a bit overkill but it seems like 5-10 might not be enough if you use a lot of apps.

Linux apps tend to take up far less room than windows ones.  There are larger ones too, and games, of course.  I tend to have a lighter system and no games.  But I have never had a linux system go beyond 5G, including SUSE (with KDE's games), which is somewhat bloated by linux standards.  My Kubuntu / partition is 5G and is 50% full.  I can't imagine you would need more than 10G.  Personally, I would split that into a few partitions for testing purposes.  My partitioning recommendations are here if you're interested...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

You young kids don't appreciate what 50G is!  ;)

>  I looked at the properties of the /home folder and it says there's ~8 MB being used but only 230 GB of free space. It doesn't quite add up.

8MB sounds about right (most of that is probably your browser cache).  Also remember that 250GB formatted is less than 250GB available - that may explain the difference.  For example my 500G drive comes out to 460G formatted.

> Also, I know about the recovery mode in grub. My list looks like this:

Ubuntu
Ubuntu (recovery)
Ubuntu
Ubuntu (recovery)
memtest
win xp

That is odd.  You might search for the file menu.lst (in a grub folder) and have a look at the details.  It might be explained by the recent kernel update - I'm told that Ubuntu will add both kernels to grub so you can boot into the old kernel if necessary.  That should be apparent in menu.lst.

I'm not the best person to answer that because my grub is still on my old SUSE partition, so it doesn't get updated automatically.  I get a SUSE boot menu that takes me to Kubuntu.  :)  Hey, it works - I'm not messing with it.

---

### Post by NickMcRump on 2007-02-14
I figured I'd start from scratch, so I erased the partitions and created three primaries for /, /home, and swap. I attached a screen of gparted showing what it looks like after a clean install and updates. 

I'm still not sure why the /home partition has so much in it. I have Windows XP on a separate hard drive and I'm curious if grub was installed to it and that's what is causing these problems. I recall when Ubuntu was installing it said it was going to install grub to hd0, I'm not sure what that is.

---

### Post by housam on 2007-02-14
Your grub menu is ok . this is normal after ubdating the system. a new kernel was installed ,that is way you have this new line ( with recovery ) in your grub menu.

---

### Post by NickMcRump on 2007-02-14
> **housam said:**
> Your grub menu is ok . this is normal after ubdating the system. a new kernel was installed ,that is way you have this new line ( with recovery ) in your grub menu.

I didn't 'update' my system though, I simply reinstalled Ubuntu a couple times. I've only started using it the past few weeks. 

Also, does anyone know why the /home partition is starting off with ~4GB in it?

---

