---
title: "Multiple Linux distros - keeping menu.lst updated?"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by dorkdork777 on 2008-04-21
Hi, I'm sure this has been answered, but I can't seem to find it via search - I must be using the wrong words.

I have been thinking about installing Xubuntu as well as the Ubuntu I've got installed currently, as this PC isn't the fastest machine. It's fine for most things, but I definitely like the idea of a faster desktop. :D

What I'd like to know is this: As Ubuntu likes to add new kernel updates to GRUB's menu.lst, keeping two or more Ubuntu-based distros (Linux Mint, Xubuntu, etc) updated would involve adding a lot of stuff manually to one menu.lst, correct? I know it's possible to have several distros sharing the same /boot partition, but I have been recommended against doing this[ here]("http://ubuntuforums.org/showpost.php?p=4523682&postcount=7").

I have looked at the chainloader info, but it seems very technical and I don't want to mess around with anything that might screw this system up... It's my main box, not a test machine, and as much as I enjoy fixing problems (I'm weird that way), I don't like fixing them in a panic when I've got stuff that needs to be done on a broken box. :)

So is there a simpler way of doing this? Will sharing a seperate /boot partition do the trick if I stick to just Ubuntu variants? Would that still run the risk of a corrupted menu.lst? Or does it not really matter anyway?

Thanks a lot in advance! :D

---

### Post by owenll on 2008-04-21
> **dorkdork777 said:**
> Hi, I'm sure this has been answered, but I can't seem to find it via search - I must be using the wrong words.

I have been thinking about installing Xubuntu as well as the Ubuntu I've got installed currently, as this PC isn't the fastest machine. It's fine for most things, but I definitely like the idea of a faster desktop. :D

What I'd like to know is this: As Ubuntu likes to add new kernel updates to GRUB's menu.lst, keeping two or more Ubuntu-based distros (Linux Mint, Xubuntu, etc) updated would involve adding a lot of stuff manually to one menu.lst, correct? I know it's possible to have several distros sharing the same /boot partition, but I have been recommended against doing this[ here]("http://ubuntuforums.org/showpost.php?p=4523682&postcount=7").

I have looked at the chainloader info, but it seems very technical and I don't want to mess around with anything that might screw this system up... It's my main box, not a test machine, and as much as I enjoy fixing problems (I'm weird that way), I don't like fixing them in a panic when I've got stuff that needs to be done on a broken box. :)

So is there a simpler way of doing this? Will sharing a seperate /boot partition do the trick if I stick to just Ubuntu variants? Would that still run the risk of a corrupted menu.lst? Or does it not really matter anyway?

Thanks a lot in advance! :D
+1

Learning how to install lmultiple linux distros is something that I would also like to learn how to do. But like you I have never been able to find a suitable guide, and working with Ubuntu full time (_ie_ got rid of windows completely by now) I don't want to and can't afford to mess up my system.

---

### Post by zvacet on 2008-04-21
>  But like you I have never been able to find a suitable guide


Try [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible") one.

---

### Post by logos34 on 2008-04-21
> **dorkdork777 said:**
> 
So is there a simpler way of doing this? Will sharing a separate /boot partition do the trick if I stick to just Ubuntu variants? Would that still run the risk of a corrupted menu.lst? Or does it not really matter anyway?

Forget a /boot partition...what you want is a[ dedicated Grub partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").  Use [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") or [symlinks]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink") to point to the various OS kernels.  The link zvacet provided above has a wealth of info--you might want to read all of it!

As for adding Xubuntu, the easiest way is to just install the xubuntu-desktop.  Choose your desktop at login screen.

sudo apt-get install xubuntu-desktop

---

