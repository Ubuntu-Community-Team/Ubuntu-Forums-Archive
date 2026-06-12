---
title: "Issues with Intrepid RC"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gone fishing on 2008-10-26
Just installed Intrepid RC and had quite a few issues most of them minor and solvable only one serious at least for me and possibly not a fault with intrepid:

1.The old network manager seems to be removed and replaced with an improved networking applet on the top panel, however, although it is much improved as far as wireless networking on laptops it only loads the wireless on login (I think). The old manual set up was better me and this is now only possible by hand editing  /etc/network/interfaces

2.The installer for propitiatory hardware drivers (System>Administration>Hardware drivers) didn't work for me. I'm behind a proxy and the settings were added to synaptic and in preferences. The wizard failed to download the driver, this was simply solved by installing using Synaptic

3.Installing the Ubuntu restricted extras had problems with the error “msttcorefonts: subprocess post-installation script returned error exit status 1” This seems to be a failure of the msttcorefonts script to use the proxy. I fixed it by editing /var/lib/dpkg/info/msttcorefonts.postinst and changing the proxy settings like so:>  db_get msttcorefonts/http_proxy

http_proxy=192.168.4.1:3128 and installing using apt-get

4.For me the biggest problem is that I can't read any of the ext3 partitions that Intrepid made in Windows using Ex2IFS – anyone know why this might be? I might solve the problem by backing up the home folder and recreating the partition using gparted.

---

### Post by mrjohnston on 2008-10-26
Have you tried to use Ext2FSD as see if that works to see the ext3?  I have had issues in the past with Ext2IFS messing with my disks and switched over without issue thus far to ext2fsd.

---

### Post by Gone fishing on 2008-10-26
Thanks mrjohnston - no I haven't tried Ext2FSD but I might have a look, however, I've been using Ex2IFS for a few years and and not had a problem before.

It seems that its got something to do with Intrepid's partitioning I created a new partition (to make a new home partition) in Intrepid (using partition editor) and Ex2IFS couldn't mount it in Windows did the same thing using a mint install disk and no problem.

So I've solved the problem with a new home partition, however, my experiences with Intrepid have been a bit of a battle.

So question 1) what gives with Intrepid's ext3 formating? I guess this is just a problem with Ex2IFS because Intrepid uses the latest updates to the format? 

2) What about ext4?

3) What happened to Intrepid's funky new artwork? Can it be downloaded?

---

### Post by Naddiseo on 2008-10-26
Is this your #3: [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/274421](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/274421)

---

### Post by Gone fishing on 2008-10-26
Yep that looks like it but after editing the script it seems fine and only the msfonts seemed to give a problem

---

### Post by Gone fishing on 2008-10-27
OK last issue, just booted up and had a scratched cd in the drive. Instead of the normal boot screen I go a terrifying text screen all full of IO errors (I though a HD had crashed for a minute). Possibly not the user friendly-est way for the OS to react to a scratched cd.

---

