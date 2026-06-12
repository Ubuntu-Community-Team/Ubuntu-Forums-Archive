---
title: "Convert remote Debian Sarg to Ubuntu Hoary (via debootstrap?)"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by C38a7r1zvl on 2005-07-08
Hi everybody.

I want to replace the Debian Sarge installation on a remote machine with Ubuntu Hoary. AS far as I understand it debootstrap is the best (the only?) possibility to do so but I don't fully understand how to do it. The basic idea is to create a new partition, extract an Ubuntu base system in there, do some configuration work, boot into that partition and install "the rest", right? Now I've read [this guide](http://racon.net/misc/DebianRemoteInstall/debremote.html) but I don't quite get the partitioning.

Currently I only have one big partition. In order to install Ubuntu I have to resize it so that another partition fits on the disk, right? After I've installed the base system, configured it and stuff will I be able to partition the bigger part of the disk as I want and copy the Ubuntu system over to another partition? 

I hope you understand my problem, what my disk looks like now is:
|------only partition with the whole system------|

During the process it will be
|--old system--|--temp partition for ubuntu--|

And what I want it to look like after everything is finished
|--ubuntu--|--var--|--usr--|--home--|

Well now.. How to do that? :D Is it possible just to copy the files from the temp partition over to the others, reboot and delete the temp partition?

Really hope you understand, thx in advance,
Niels.

Oh and btw, is there some kind of guide on how I configure the newly installed Ubuntu? I am a bit unsecure about that cos I won't use the installer. But I guess just a few dpkg-reconfigure commands will be sufficient?

---

### Post by C38a7r1zvl on 2005-07-13
*push*

---

