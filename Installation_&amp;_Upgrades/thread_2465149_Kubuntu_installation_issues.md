---
title: "Kubuntu installation issues"
date: 2021-07-23
forum: Installation &amp; Upgrades
---

### Post by Nina_W on 2021-07-23
I'm a long term Ubuntu user and wanted to try Kubuntu but I'm struggling and don't know if the installation process should be identical to Ubuntu. (I've tried to register on the Kubuntu forum but the activation email hasn't appeared)

Firstly I've used the Start-up Disk Creator to put and ISO onto a USB stick and it has created 2 partitions, one of which is showing a mounting error, the other of which contains all the stuff I'd expect for an installation USB. So should that second partition be there and if not what is the best way to remove it, do I have to format and try again or is there an easier way?

Secondly, if I get this working (currently is won't boot from it on a Windows machine or my dual boot Windows/Ubuntu machine), can I try it before installing like you can with Ubuntu?

Thirdly, if I decide to replace my Ubuntu on a dual boot machine, how easy is that to do? Will it be able to install it into the current Ubuntu partition or do I have to remove Ubuntu first to give it a blank partition? Do I have to reinstall all my files?

Any help gratefully appreciated here!

---

### Post by grahammechanical on 2021-07-23
> So should that second partition be there and if not what is the best way  to remove it, do I have to format and try again or is there an easier  way?

I have no idea if that second partition should be there. I recently burnt a Ubuntu 20.04.2 ISO image and that has three partitions. One partition contains the packages necessary for an install of Ubuntu and it is bootable; A second partition that is a FAT-12 EFI partition and a third partition that is called writable that contains installation logs. This is something that I have not noticed before. I am only interested in the ISO image being a live session leading to a Ubuntu installer.

If your ISO image is not booting, I suggest re-burning the image to the USB stick.

> can I try it before installing like you can with Ubuntu?

Of course you can.

> Thirdly, if I decide to replace my Ubuntu on a dual boot machine, how  easy is that to do? Will it be able to install it into the current  Ubuntu partition or do I have to remove Ubuntu first to give it a blank  partition? Do I have to reinstall all my files?

This should have its own thread. It is easy to do if we know what we are doing and even then we can mess up and loose everything on the drive. Backup all the files that you do not want to loose. During the install process you select the Ubuntu partition and mark it to be formatted during the install. No need to remove any existing operating system. The newer installation will over write the existing installation.

Please ask about this as a separate question. Then you can get a more comprehensive answer. Each question in its own thread is the way we prefer to give assistance. And we are never troubled to be answering the same questions from different people.

Regards

---

### Post by guiverc on 2021-07-23
Kubuntu uses the `ubiquity` installer; which is the same installer as Ubuntu desktop (*releases up to 21.04 anyway; it's likely to be replaced for coming releases*).

Kubuntu uses a skin over it; so it looks different (and has KDE/Qt calls), but the fundamental installation is identical.  

Only little things like the install type option called "*Something else*" in `ubiquity` is called "*Manual*" when the KDE-Qt skin is being used, but they both do the same thing, ie. it's cosmetic differences and how presented on screen (*underneath it also calls  Qt libs to display instead of  GTK libs, but that's to make it more efficient on the KDE/Kubuntu system*). 

FYI: Lubuntu since 18.10 (and Ubuntu-Studio for the KDE releases) use `calamares` instead of `ubiquity` as the KDE-Qt skin is hard-coded to KDE and would display "Kubuntu" for any Lubuntu/Ubuntu-Studio install which would confuse end-users, so those teams  replaced it with another installer (`calamares`). When the new installer is ready; those teams (*particularly Ubuntu-Studio*) may move back to using the default Ubuntu desktop installer.

You can what I like to call "*Upgrade via re-install*" which will allow you to upgrade a Ubuntu system with another different Ubuntu system, of the same or different release (where Kubuntu or any other Ubuntu *flavor* is still a Ubuntu system).  eg. I had a failed upgrade from (Lubuntu) 18.04 to 20.04 and didn't want to spend the time & effort to fix (that upgrade was unsupported anyway due desktop change), so I just re-installed 20.04 over it to get it fixed in ~15 minutes (*without needing me*) which would I suspect have been faster than working out what my issue is and me manually fixing it.  No restores were needed; as my data files were not touched; and the installer added back my additional packages too (given I'd opted to no-format or *dirty* install). My actual install needed a few extra packages (*I had encrypted /home partition which is no longer the default for Ubuntu, thus I needed to add a package to the live system prior to starting the installer, so finding that package name was a couple of minutes of the process*;* I actually also installed using Xubuntu ISO too - the flavor didn't matter** as I added Lubuntu to it myself; I wanted both Xfce & LXQt*)

(this *upgrade via re-install* detail is vague; I didn't see release details for your old install, or new install - and your issue *feels* to me more like a faulty write of the ISO to your installation media)

---

