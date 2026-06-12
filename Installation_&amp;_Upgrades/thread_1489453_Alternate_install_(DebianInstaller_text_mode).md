---
title: "Alternate install (DebianInstaller text mode)"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2010-05-21
Lubuntu GNU/Linux 10.04

Sometimes alternate install is needed, for example to setup RAID or LVM, and the graphical installation system requires more RAM than lubuntu needs to run.

In the wiki there is a [guide to use "minimal install" procedure]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall"), but it's based on the CD "mini.iso" to be used as a completelly network install. In some scenarios is a problem to download hundreds of MegaBytes to make the system installation.

Using the server installation CD could do the job? Kernel replacement required then?

---

### Post by Max-B on 2010-06-18
I completely agree with narcisgarcia: Lubuntu Alternate install is needed.
ciao,
Max

---

### Post by unipsycho on 2010-12-18
Came here looking for an LVM / Alternate install ISO for Lubuntu. Looks like I'm outta luck. Anyone know the status on this? or if there is any status? Didn't see much at lubuntu.org.

---

### Post by ramengirl on 2011-01-11
Found information about an Alternate Install version of Lubuntu on the Lubuntu Wiki. Here is a link to how to use it and where to get it. I haven't tried it myself but will be soon as I finish downloading it.

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall)

ramengirl

---

### Post by rexmo on 2011-01-23
It seems we really NEED a lubuntu 10.04 alternate install.  Is anyone currently working on this?  If not I would like to get my team working on this ASAP.  It is EXTREMELY unfortunate that 10.10 has dropped older CPU support as this makes the alternate 10.10 lubuntu install virtually worthless...

Many thanks,  REXMO

---

### Post by narcisgarcia on 2011-01-23
rexmo, can you explain more about the new unsupported CPUs?

---

### Post by TygerTung on 2011-03-03
I agree, it is crazy that there is no alternate install, especially as lubuntu is designed for crappy old computers.

I prefer the alternate install at all times in any case as it is much easier to use and I find it more comforting.

It runs faster and is more reliable, in fact I have never had a successful desktop installation!

Old slow computers need the alternate install and to have an operating system designed for these computers and not to have an alternate install is just crazy!

---

### Post by XP1 on 2011-05-17
I have tried to start Lubuntu 11.04 installation on 3 computers, and so far, all have had problems with the GUI.

Two old computers freeze or say "Sorry, the program 'ubiquity' closed unexpectedly." in GUI.
One modern computer won't even start the GUI. It just drops to shell, and I can't even "startx".

Where is the Lubuntu 11.04 Alternate CD? The wiki only links to the old version.

---

### Post by vanquishedangel on 2011-05-18
Ok, I totally agree with all of you here.  Lubuntu does need an alternate install cd.  I am on a Compaq armada m300 that I bought for school as a portable word processor and what ever benefit I could still use it for, I just spent like 6 hrs installing Ubuntu 11.04 not realizing that it was installing a full Ubuntu, I thought that it was installing command line only and it never gave me a choice.  I love Lubuntu for many reasons but atm I am angry at wasted time.  I know you guys are busy and I thank you for a great distro, but please put a Alternate Lubuntu on the web page you have, I could have updated from the previous one at least.

---

### Post by papu40000 on 2011-07-31
Hi,

I was having problems with Lubuntu installer because NVIDIA graphic card couldn't run properly the live iso.

So I download the xubuntu alternate install*
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

I used a Live USB to the install process (see about unetbootin)

In the installation... pay attention at selecting packages, don't select xubuntu desktop. So install only the system base of ubuntu.

Reboot. Wait the loading, go to console (control+alt+F1 for example) and configure network, follow this indications:
[https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html)

Now it's time to install 'lubuntu'
sudo apt-get update
sudo apt-get install lubuntu-desktop
(it takes a long time)

Reboot. Should appear lubuntu session login.

Hope it helps someone ;)

* if you have problems to install that xubuntu alternate installer, could try with another alternate version of ubuntu version desired (the interest is to install the base of ubuntu linux system.

---

### Post by Maro848 on 2011-11-09
for anyone that wants an update on this I'm unsure about older releases but the 11.10 release has an alternate install image available at [cdimage.ubuntu.com/lubuntu/releases/11.04/release/]("http://ubuntuforums.org/cdimage.ubuntu.com/lubuntu/releases/11.04/release/")

---

### Post by narcisgarcia on 2011-11-15
Yes, it's already released.

Torrent download (fast and cooperative):
[http://torrent.ubuntu.com/lubuntu/releases/oneiric/release/](http://torrent.ubuntu.com/lubuntu/releases/oneiric/release/)

Web download:
[http://cdimage.ubuntu.com/lubuntu/releases/oneiric/release/](http://cdimage.ubuntu.com/lubuntu/releases/oneiric/release/)

---

