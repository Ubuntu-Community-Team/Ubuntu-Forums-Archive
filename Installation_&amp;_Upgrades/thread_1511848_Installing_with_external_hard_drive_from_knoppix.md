---
title: "Installing with external hard drive from knoppix"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by mondomunchies on 2010-06-17
I have no blank cd's but I do have an external hard drive and a knoppix cd.  I can't install ubuntu on the external HDD because it already has data saved on it and I would not want the whole drive to be a linuxOS anyway.  

I used Knoppix to partition the hard drive on the computer I wish to install on.   I can access the internet wirelessly with knoppix on that computer. 

Would it be possible to save the ubuntu iso to the external hard drive and somehow install it to the computer from the external using knoppix?

---

### Post by Chame_Wizard on 2010-06-17
Knoppix is mostly intended to run from the live CD/DVD.

---

### Post by oldfred on 2010-06-17
If you can install grub2 to the external then you can loop mount the iso and run it.

These instructions are for converting an entire USB flash drive, but I just used some of the commands to install grub and the ISOs to an existing USB flash that I had with other data on it. I can boot 4 versions of Ubuntu, old current, future, gparted and rescue disk all directly from the ISO. It is easy just to edit the grub2 menu and copy ISO to flash and boot it. Should work the same for any external device.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

More info on grub2 in a partition:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

