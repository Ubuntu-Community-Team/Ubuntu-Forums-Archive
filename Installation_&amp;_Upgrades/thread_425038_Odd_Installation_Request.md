---
title: "Odd Installation Request"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by tmanops05 on 2007-04-27
Hi All...This is an odd one, so please be patient...

I currently have a DELL D820 Latitude Notebook. It has an 80GB Drive, with Windows XP SP2 installed. It also uses a Docking Station. I have downloaded and burned the 7.04 ISO to CD, and ready to go. Here's my questions:

1. I'd like to keep the existing partition in place, and not disrupt too much. With all the things I have installed [XP, Office, etc.] I have about 60GB free. I'd like to keep 40GB free for XP [it's a work laptop/OS, so that's why]. I'd like the Ubuntu OS to use the remaining 20GB for whatever it needs [make sense?]. So how do I do this?

2. I wanted to try and mess around a little bit with the LIVE CD. I have a regular USB mouse [works fine]. However, my Bluetooth keyboard isn't recognized at boot. Is that normal? Should I not dock it to do the first step and just keep it off the docking station? Then once it's installed add that after?

Thanks in advance!!!!

---

### Post by KIAaze on 2007-04-27
> 1. I'd like to keep the existing partition in place, and not disrupt too much. With all the things I have installed [XP, Office, etc.] I have about 60GB free. I'd like to keep 40GB free for XP [it's a work laptop/OS, so that's why]. I'd like the Ubuntu OS to use the remaining 20GB for whatever it needs [make sense?]. So how do I do this?

0)It is recommended to back up all important data on your HD first.
You can try to do things directly of course, but that's at your own risk.
Resizing the windows partition usually works without any problems, but it's better to play it safe. ;)

1)Defragment the windows partition so that the last 20GB of diskspace are free.
Eventually, you might have to disable the virtual memory and hibernation to defragment completely.
see here if you have unmovable files: [http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/]("http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/")

2)Follow this [tutorial]("http://psychocats.net/ubuntu/installing").
Basically, what you will do is resize the windows partition, format the freed space as ext3 + a small swap partition and install Ubuntu on it and install the GRUB bootloader.
If you follow the tutorial, everything should be fine.

> 
2. I wanted to try and mess around a little bit with the LIVE CD. I have a regular USB mouse [works fine]. However, my Bluetooth keyboard isn't recognized at boot. Is that normal? Should I not dock it to do the first step and just keep it off the docking station? Then once it's installed add that after?

I don't know exactly how docking stations work, so I don't know how to make the bluetooth keyboard work.
From what I understood, the laptop without the docking station is just like a normal laptop.
Therefore, I suppose, it will be easier to install Ubuntu when not docked and try to get the rest to work after that.
(because you'll need a keyboard during installation, so I can't think of any other way)

---

### Post by tmanops05 on 2007-04-27
Thanks for the quick reply! I'll read the tutorial, and give it a shot. I'll do what you mentioned, install it undocked and go from there. I'm sure it will recognize it after I install, etc.

Thanks again!

---

### Post by KIAaze on 2007-04-27
Here is some more help for the partitioning part:

[http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#installonoldhdd]("http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#installonoldhdd")

With the GUI, it's quite easy:
-resize windows partition
-create ext3 partition
-create swap partition (recommended size=2*RAM)

Just back up important stuff first, if this is the first time you try this.

---

