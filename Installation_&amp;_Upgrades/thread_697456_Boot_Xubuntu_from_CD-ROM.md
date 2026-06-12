---
title: "Boot Xubuntu from CD-ROM"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by jis on 2008-02-15
Is it possible to install Xubuntu so that you can boot it from CD-ROM to begin with and the rest of the system would be in unbootable USB device? I suppose at least /boot partition should be on the CD-ROM. How would it affect keeping system up to date?

---

### Post by Pumalite on 2008-02-15
Use Gpaqrted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Make partitions for '/' and '/swap/ in your internal drive. Make partition for /home out of your external (all of it if you want)
Install Ubuntu, go Manual and use prepared partitions.
The inconvenience of this is that the external drive will have to be connected for this system to function.

---

### Post by jis on 2008-02-15
> **Pumalite said:**
> Use Gpaqrted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Make partitions for '/' and '/swap/ in your internal drive. Make partition for /home out of your external (all of it if you want)
Install Ubuntu, go Manual and use prepared partitions.
The inconvenience of this is that the external drive will have to be connected for this system to function.

Note that gpated live-cd is currently unmaintained: [http://gparted-livecd.tuxfamily.org/news.php](http://gparted-livecd.tuxfamily.org/news.php)

I am thinking about possibility to attach a S-ATA drive to internal USB2-bus of the USB card (attached to PCI bus) of my computer. I suppose the computer can not boot form it then since the bios of the computer does not give that option. Or does the PCI card override bios? Maybe I'll not use a mass storage attached at IDE (or P-ATA) but, if I do, I would use a 4GB flash drive. The final system would boot from CD-ROM or from the flash drive. I think I can use your directions, if I used a PATA drive, but what if I want to use a CD-ROM to boot instead?

BTW. Have you ever looked at "show features" dialog of gparted? In versioin 0.3.3 (that is available in Gutsy repositories) it shows like the following image. It shows it can not handle ntfs or xfs beyond detection. Still I have used it to shrink ntfs partition (which took long time), and I have used an earlier version to create xfs partitioin which I used later!

[IMG]http://iki.fi/8/tmp/screen.png[/IMG]

---

### Post by Pumalite on 2008-02-15
Take a look at this pages; they have lots of good tutorials:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
I'm glad I have my old Gparted. I will keep it in a Safe.

---

### Post by jis on 2008-02-15
Thanks. Although maybe it is hard to mount usb drive in such an early stage.
Please look at the link in the page for alternative live CD that contains gparted.

---

### Post by Pumalite on 2008-02-15
The Gparted that comes with the Ubuntu Live CD and the Gparted Live CD are entirely different animals. The latter is newer version, more powerful, more flexible and easier to use. It's a stand alone program that you burn to disk and boot from it. I encourage you to get one.

---

### Post by jis on 2008-02-15
Actually I have GParted live-CD 0.2.5. If I look at the "show features" window of that, there are much more features for ntfs and xfs than in 0.3.3..

---

