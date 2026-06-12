---
title: "Install on a asus P5N-E Hardware RAID"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by Frumpco on 2007-08-09
Hello

I am attempting to install Ubuntu 7.04 Desktop on a Asus P5N-E Sli board. I have the HD config in the raid using the Asus/Nvidia Raid config. I can see each drive indpendantly but I am not able to see them in the Raid. I Currently have the Raid working with a Windows install on it.

Here are my Specs to help us out.

Core2Duo 6600 OC to 3.6Ghz
2Gig Ram
2X36Gig Raptors RAID 0
Ati X1800XT
320Gig HD
LG DVD Burner
Samsung 22inch widescreen LCD

Also when installing Ubuntu I have to hook up my old CRT monitor because the display just goes black if I use my LCD.

Thanks for the HELP!!!

---

### Post by fjgaude on 2007-08-09
Okay, you have what is called fakeraid... do a Google and see what that means.

All you have to do is install dmraid using

```
sudo apt-get install dmraid
```

Then do a man dmraid to learn about dmraid.

```
sudo dmraid -tay
```

will show you that your nvidia is okay.

Now mount the /dev/mapper/nvidia_xxxxxxxxxxx

that you see as an error. It is the way software linux sees your two-drive array.

Create a point point and then mount:

```
sudo mkdir /media/raid
sudo mount /dev/mapper/nvidia_xxxxxxxxx /media/raid
```

That should do it. If not, tell us what is your stumbling block. <smile>

frank

---

### Post by Frumpco on 2007-08-09
Thanks!

I have found some info on that and I will test that out asap!

---

### Post by Frumpco on 2007-08-11
Thanks for your help that did point me in the right direction!

---

### Post by fjgaude on 2007-08-13
Let us know when you have it all up and running.

frank

---

### Post by untoldone on 2007-11-22
I have the exact same hardware (and windows already installed with nvidia software raid 1 working) but want to stick LVM on it so I'm using the alternative install cd.  I'm under the impression apt-get isn't present on the alt install disk?  Any way for me to get the raid disk running properly for the alt install partitioner?

---

