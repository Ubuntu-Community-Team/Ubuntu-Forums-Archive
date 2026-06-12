---
title: "HOWTO (K/X)ubuntu Intrepid Ibex on eeepc"
date: 2008-07-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tom Mann on 2008-07-21
I've had a lot of problems with managing to do this, but have managed to get Kubuntu (with KDE4.1 RC1) onto my eeePC.

================
What you need
================

- A USB or bootable CF card (we're only going to use 16MB of it so most sizes will do)

- A boot.img.gz file for *Hardy* found [here]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/boot.img.gz")

- A cabled network connection


================
What to do
================

1. Get the image onto the USB key

Type the following into a terminal:
```
sudo -i
fdisk -l | grep Disk
``` (nb: note disk is with a capital 'D')

fdisk should have an entry with a capacity similar to the size of your USB key/CF card (note be careful that you don't have similar sized storage on the computer simultaneously as you could wipe the wrong USB key/CF card)

You should see something similar to this (1GB USB)
```
Disk /dev/sdd: 1048 MB, 1048576000 bytes
Disk identifier: 0x8ef631df
```

in my case /dev/sdd is my USB media (I will refer to USB key/CF Card as USB media for the rest of this howto), note your USB media will probably have a different path to mine, be sure to substitute this lower down the page!

In the same terminal as above, this creates the USB key (and also wipes the partition table, so back up any data!
```
zcat /path/to/downloaded/boot.img.gz > /dev/sdd
sync /dev/sdd
```

You can now pull your USB key out, and plug it into the eeePC.



2. Installation

Make sure the eeePC is plugged both into the mains as well as the network cable - wifi will not be available until the end of this tutorial.
When you boot from the USB media, you will get a boot prompt. Type 'cli' into this prompt to continue. This avoids any unnecessary packages being installed. Answer all the other questions in this part as normal.
When done reboot and log in at the console prompt.



3. Upgrading

The following code will bring your minimal Ubuntu install into Intrepid territory (NB: I spotted this trick somewhere on this forum a long time ago, I can't remember who mentioned it, but thanks :))

```
sudo sed -i /s/hardy/intrepid/g /etc/apt/sources.list
sudo apt-get update
```
NB: You will need your password for the eeePC to proceed here.

To finish off:
```
sudo apt-get dist-upgrade
```

Then depending on which desktop you'd like, one of the following:
```
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install ubuntu-desktop
```

+++

Now is always a good time to install any extra packages you need: I usually install k/ubuntu-restricted-extras here but this can be done later.

+++

The End - Reboot and Enjoy your desktop, with what seems to be a working wireless connection! :)

---

### Post by Tom Mann on 2008-07-21
Update:

Hardy based Ubuntu

If you wish to run Hardy Heron instead of Intrepid Ibex follow the tutorial above leaving out the following line:

```
sudo sed -i /s/hardy/intrepid/g /etc/apt/sources.list
```

You then also have the option of installing kubuntu-kde4-desktop.

---

### Post by Tom Mann on 2008-07-21
And screenshot...

---

### Post by Jayschwa on 2008-07-23
Thanks for the guide. A lot of time can be saved if the Intrepid netboot image is used: [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/boot.img.gz)

[Added] Well, it seems I can't get the ethernet detected with the Intrepid boot image. :(

---

