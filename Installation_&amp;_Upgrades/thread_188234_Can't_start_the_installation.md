---
title: "Can't start the installation"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by s0n1c on 2006-06-03
I'm trying to install Xubuntu 6.06 on a Pentium 3 600mhz 128mb.

It takes some time to start the "live" session, and when I double click the icon "Installation", the system freezes after some time.

I know this computer sucks and all, but I read on the release notes that the minimum requirementes to install with the "Desktop CD" is 64mb, and 128mb recommended.

Also, now I'm not so secure about how nice Xubuntu will run here. I'm currently running Windows XP here, and its REALLY slow, so I was going to try Linux with XFCE, but now I don't know if it worth it.

Can you guys help me with this issue, and tell me if Xubuntu will be good on my computer?

Thanks.

---

### Post by aysiu on 2006-06-03
I also have a computer with 128 MB of RAM, and I was unable to install Xubuntu from the live CD.

The live CD runs out of your computer's RAM. We're talking about an entire operating system session running off a CD and RAM--no hard drive, so it's going to be slow, and if you have too many programs open during that session or one program that sucks up a lot of resources (like the installer), your computer will freeze, especially if you don't have a swap partition.

You can play around with the live CD to see how it is, but if you want to install Xubuntu on your computer, I'd recommend the alternate install CD.

---

### Post by effoff on 2006-06-03
If you don't yet have an Xubuntu CD and you still want to install it (and install it fast), here is a step-by-step tutorial showing how is easy to get an Xubuntu box up and running. [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)
This method worked perfectly for me on an old Omnibook with a 6GB HD and 128 ram..

---

### Post by s0n1c on 2006-06-03
Hm, there aren't alternate ways of installing it with the live CD?
Some special parameter, I don't know.

I don't have any other blank CD here, and I don't know when I'll be able to buy one (lot of stuff to do for the college).

effoff, I've seen this method, but I also don't have any Ubuntu 6.06 CD's here (I got some from the previous version, but want an up-to-date system :P).

Well, thanks for the help guys.

---

### Post by s0n1c on 2006-06-04
Sorry for posting again, but, I really can't install Xubuntu on my system with the live CD?

If some of you guys can help me, it will be freaking great, because I can't take this Windows XP anymore.

Thanks.

---

### Post by aysiu on 2006-06-04
You can theoretically, but 128 MB just doesn't give you enough resources to be running a live session *and* installing at the same time. Trust me--I've tried it.

---

### Post by jdong on 2006-06-04
From my testing, 128MB of RAM is insufficient to run the LiveCD installer for Xubuntu. Instead, you should use the Alternate installer, which is text-based and far easier on RAM.

128MB is enough RAM for running Xubuntu off the hard drive after installation for sure :)

---

### Post by confused57 on 2006-06-04
[QUOTE=s0n1c]Hm, there aren't alternate ways of installing it with the live CD?
Some special parameter, I don't know.

I don't have any other blank CD here, and I don't know when I'll be able to buy one (lot of stuff to do for the college).

effoff, I've seen this method, but I also don't have any Ubuntu 6.06 CD's here (I got some from the previous version, but want an up-to-date system :P).

Well, thanks for the help guys.[/QUOTE]

Here's something someone tried, if you can get the graphical installer to start:
[http://www.ubuntuforums.org/showthread.php?t=188454](http://www.ubuntuforums.org/showthread.php?t=188454)

What is the "previous version" that you have?  If you have a Breezy install CD you can do a server install from that, dist-upgrade to dapper, then install xubuntu-desktop...if you don't have a fast internet connection, you won't be able to do this.

---

### Post by jdong on 2006-06-04
[http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/xubuntu-6.06-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/xubuntu-6.06-alternate-i386.iso)

Use the Alternate install CD, which is the traditional text-mode installer.

---

