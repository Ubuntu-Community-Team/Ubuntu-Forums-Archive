---
title: "Resizing partitions in ubuntu"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Sadistic Tribble on 2008-10-09
I´ve gone through several renditions of a paragraph to explain my partitions but a diagram works better:

/dev/sda1- Windows partition, NTFS, ~80GB
/dev/sda2- Ubuntu partition, ´Extended´, ~80GB
[COLOR="White"]___[/COLOR]/dev/sda5- Main data for Ubuntu partition, ´ext3´, ~77GB
[COLOR="White"]___[/COLOR]/dev/sda6- linux-swap partition, ~3GB

I want to resize the Ubuntu partition to put in another OS, PCLinuxOS, to try it out. I have two questions to this end:

1) I need a good program to resize the Ubuntu partition to free up a good 30 - 40GB for PCLinuxOS. GParted, for some reason, has the ´resize/move´ option grayed out for sda2. When trying to install PCLinuxOS and using its partition manager, it freezes. Is there something I´m supposed to do before using a manager, and then I could just use GParted or the PCLOS manager?

2) I´m becoming more and more doubtful about this since the swap partition is in the main Ubuntu partition, but can PCLinuxOS use Ubuntu´s swap partition, or does it need its own? This is simply out of curiosity, I don´t have *that* much need for HD space.

Thanx in advance for any help!

---

### Post by divague on 2008-10-09
You can use the gparted livecd to resize your partitions.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by doas777 on 2008-10-09
if the gparted livecd doesn't work for you, gparted is part of the ubuntu livecd.

good luck,
Franklin

---

### Post by Sadistic Tribble on 2008-10-10
Those won't work for me. The GParted LiveCD shows the screen with some horrible resolution that can't even be over 320x240, in which I can't do anything, and the only Ubuntu LiveCD I have atm refuses to recognize my monitor for some strage reason. What other programs are available?

---

### Post by divague on 2008-10-10
The gparted livecd gives you the option to select the screen resolution when it's booting. If that doesn't work you could get a windows software to resize your partitions.

---

