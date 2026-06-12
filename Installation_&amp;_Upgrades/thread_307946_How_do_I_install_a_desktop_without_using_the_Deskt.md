---
title: "How do I install a desktop without using the Desktop CD?"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by kaminix on 2006-11-27
This thread is mostly critisism, but on the bottom of this post you'll find a question that I really want answered, the reason as to why I made this thread from the beginning.

So I was going to install Ubuntu today, because I was fed up with Windows' bull crap and wanted Ubuntu back (meaning I'm not a first-timer).

I downloaded Ubuntu 6.10 (the latest version), put the CD in my CD-drive and rebooted. I'm welcomed with a REALLY nice graphic installer (really, I like this part). The first thing I do is to check the CD integrity, it works out fine.

Then I move on to the installer, choosing Start/Install Ubuntu. It starts up the Live CD, I'm thinking "Come on, I'd be half way through the installation of you hadn't insisted on booting the entire operating system for me". This is the first thing I want to complain on. The graphic interface is nice, but atleast I think it's WAY too much to boot an entire live CD, my computer even froze during the installation (at the partitioning), and infact I was terrified to see the GPart "Monster Kill" Partion Manager start up. What if someone tries to actully use the resize-function? That function has ruined my partitions 100% of the times I've used it, where "my partions" means "the entire partition table".

Another thing I was sort of pissed about during the whole installation, was that I didn't get to choose if I wanted a server installation, or a desktop installation. I've always gone for the server-installations, because I want to keep things to a minimum (xserver + fluxbox = happiness).

EDIT:
The voting is serious, I've just put two kind of extreme answers because they're more fun than "You're right"/"You're wrong".

---

### Post by Buffalo Soldier on 2006-11-27
what you need is the alternate CD, not the desktop CD.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

> The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM.

---

### Post by kaminix on 2006-11-27
> **Buffalo Soldier said:**
> what you need is the alternate CD, not the desktop CD.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
Yes, I belive there has always been an alternate CD for those who wanted the smaller install and didn't feel like downloading too much. However I also belive that it's always been possible to install the server from the desktop CD. I mean, it's all in here, isn't it? The serverinstallations programs are all on the desktop CD are they not? Why not add a "basic installation"-alternative for those that want it?

---

### Post by wpshooter on 2006-11-27
No, I don't think you can install the server installation from the DESKTOP CD.

---

### Post by kaminix on 2006-11-27
> **wpshooter said:**
> No, I don't think you can install the server installation from the DESKTOP CD.
Why not?

It's not like it's the server I'm interested in, it's more of a "minimal installation".

---

### Post by phormion on 2006-11-27
kaminix, 

breathe a bit, get some coffee, and calm down. You are complaining that you can't install Ubuntu-server from the desktop CD?? The docs tell you to use another CD instead of the desktop one, this is the advertised behaviour. I don't think the presence of some script proves anything. 

The other complaint you have is one of the things I like most in the installer - that you can, for example, browse the web or IM or listen to music while you install Ubuntu. If you prefer to watch a list of packages for 15 minutes, well, you speak for yourself. All of this for the extra 2 mins of waiting for the Live CD to boot. Boo hoo.

---

### Post by yota on 2006-11-27
kaminix,

I'm an alternate-cd kind of people too; I do like the live-cd, but I think that it would need some more features and polish to be the mainstream one.
At this time the alternate IMHO is still the best installer.
By the way I suppose that this is not true for the vast majority of "human beings" that prefers to start from a confortable graphic environment with a wizard based approach.

My bottom line is that I'm happy as long as the alternate exists and is mantained with the same care as the live.

---

### Post by kaminix on 2006-11-27
> **phormion said:**
> kaminix, 

breathe a bit, get some coffee, and calm down. You are complaining that you can't install Ubuntu-server from the desktop CD?? The docs tell you to use another CD instead of the desktop one, this is the advertised behaviour. I don't think the presence of some script proves anything. 

The other complaint you have is one of the things I like most in the installer - that you can, for example, browse the web or IM or listen to music while you install Ubuntu. If you prefer to watch a list of packages for 15 minutes, well, you speak for yourself. All of this for the extra 2 mins of waiting for the Live CD to boot. Boo hoo.
I don't drink coffee, and even if I did, I think it would do anything but calm me down. ;)

You're hooking yourself up on the "You want a server! Use the server CD bitch!"-thing. I do NOT want a server, I want a DESKTOP. The definition of Desktop is not "you shall have games, which you can't uninstall. you shall have a useless uninstallable video player called totem. finally, you NEED XSANE Image Scanner, even though you don't have a scanner".

As for the live environment, it's not that bad, it's just that -I- don't like it. In fact, I dislike it, despise it if you like. That's why I want an alternative to this environment. After all, Ubuntu is made for everyone, isn't it?

---

### Post by aysiu on 2006-11-27
There's a difference between the Server CD and the Alternate CD.

The Alternate CD, as people have said before, is what you want, and it installs an actual desktop. It can also give you a minimal install (called a *server install*--it doesn't mean you're actually running a server) from which you can then install exactly the desktop you want *sans* Gnome games and Totem. You can build it exactly the way you want it.

By the way, I've removed your poll and retitled your thread to something more appropriate, so you can get some actual help. This is a support forum, after all.

[quote=Ubuntu download page]**Desktop CD**
The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 192MB of RAM to install from this CD.

**Server install CD**
The server install CD allows you to install Ubuntu permanently on a computer for use as a server. It will not install a graphical user interface.

**Alternate install CD**
The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. [/quote]

---

### Post by arunvragh on 2006-11-27
I feel the alternate CD method is the best. Edgy installed like a dream from it, but the desktop cd is way too resource hungry, frequently hangs on xserver configuration and partitioning- i remember a work around for dapper- something about increasing the swap partition size. i had a few nightmares on dapper install- maybe some quirky harware on my system aggravated it.

Anyway Edgy- I took the safe route- alternate cd- feels like ubuntu, honestly installation was best in breezy.

---

