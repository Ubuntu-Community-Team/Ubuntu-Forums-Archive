---
title: "Switch Kubuntu to Ubuntu"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by vbmark on 2010-04-26
Hello,

I'm a Linux n00b and installed the 10.04 rc of Kubuntu on a second partition as a dual boot with XP.

Now I'm thinking I would rather have Ubuntu. What is the best way to switch over?

Thanks!
Mark

---

### Post by dabl on 2010-04-26
Open a terminal:
```

sudo apt-get update && sudo apt-get install ubuntu-desktop
```

Reboot.  On the login greeter, click on the menu and pick the desktop environment that you wish to log into.

---

### Post by vbmark on 2010-04-26
Heh, wow, thanks dabl.  That easy?

I was going to reformat the partition, remove Grub, and start over.

Thanks!

---

### Post by dabl on 2010-04-26
Assuming you have a GB or so of space on your root filesystem, it should be just that easy.

> **vbmark said:**
> 

I was going to reformat the partition, remove Grub, and start over.



That can be "Plan B".  :)

---

### Post by vbmark on 2010-04-27
I ran the update and install commands last night, rebooted into gdm and WOW WOW WOW!  The Gnome desktop is awesome!  I want to take a vacation day just so I can stay home and mess with it.

Two things though:

1) When I reboot and shutdown it shows a low-res, distorted rendering of the KDE splash screen.

2) I see that all the KDE files and programs are still on my computer and I'd like to remove them.

Are there a couple more commands I can run to completely rid my system of all KDE stuff or am I better off wiping the partition and starting over?

Thanks!

---

### Post by dabl on 2010-04-27
> **vbmark said:**
> 

Two things though:

1) When I reboot and shutdown it shows a low-res, distorted rendering of the KDE splash screen. 

Reply #15 [[COLOR="SeaGreen"]**here**[/COLOR]](http://kubuntuforums.net/forums/index.php?topic=3111199.msg226647;topicseen#msg226647) has the (linked) solution to that issue.

> 
2) I see that all the KDE files and programs are still on my computer and I'd like to remove them.

Are there a couple more commands I can run to completely rid my system of all KDE stuff or am I better off wiping the partition and starting over?


Unfortunately, there is no simple way to "un-KDE" your system, at this point.  The kubuntu-desktop metapackage is what you use to pull it all in, but it is a bucket of all the Kubuntu and KDE packages and dependencies.  It doesn't work in reverse.

The kde-related packages and files on your system won't hurt anything.  But, if an attack of OCD requires you to purge it, I think you're stuck with "Plan B".  :lolflag:

---

### Post by vbmark on 2010-04-27
> **dabl said:**
> I think you're stuck with "Plan B".

Heh, ok, that's no problem.  What I'm going to do then is start from scratch on the 29th when I can download the final release.

Can you recommend the most efficient way to do a reinstall on a dual boot (XP) machine?

Can I just delete the Linux partitions, leave the boot loader, then do a clean install?  Or will I need to delete the existing GRUB 2 boot-loader too?

Thanks!

---

### Post by dabl on 2010-04-27
My experience suggests that you want to do these things:

1. Boot a Live CD that has GParted on it, and re-format the Linux partition(s) to delete all the files on them.

2. Use the 10.04 Alternate install CD, choose "manual" partitioning, and use it to select the mount points for the new installation.

3. When the installer gets to the final stage and asks you about installing Grub, tell it to install Grub on the mbr of the first hard drive.  Normally it will see the Windows OS and set up the boot menu appropriately (and automatically), sparing you the need to mess with Grub.

---

