---
title: "Ubuntu Insists on RAID"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by spectre1989 on 2010-09-26
Hi all,

It's been a while since I've played with Ubuntu, and a linux evangelist at work has talked me into trying it again.

My specs:
Motherboard: Abit FP-IN9
CPU: Intel Core 2 Quad Q6600
RAM: 2GB (one of my sticks recently went bad)
Graphics: Nvidia 8800 GTX
Hard Drives: 2 x 500GB Western Digital SATA

I happened to be wiping my machine, so my plan was to have Windows 7 and Ubuntu on one hard drive (100GB for Ubuntu, the rest for Windows), and the second hard drive for downloads, TV, films, etc.

First I installed Windows, then I torrented the x64 Ubuntu 10.04 live CD iso, and burned it to a DVD. I booted from it and installed on the second partition, but I then found when I booted back into windows that my second hard drive wasn't there any more. 

It didnt take long to work out that Ubuntu had installed using the second hard drive as a mirror. This is very confusing to me, as I've disabled RAID in my BIOS. I booted from the Ubuntu CD again and looked for options about this but didn't find any. Eventually out of frustration I just unplugged the second hard drive, but now when I boot from the CD to install, no hard drives show up for me to install to.

Can anyone help a newbie out?

Cheers!
Spec

---

### Post by tom4everitt on 2010-09-26
That sounds odd. I've never heard of Ubuntu installing a mirror... 

I would wipe the hard drives again, starting as you did with installing Windows on the first partition on _the first_ hard drive (sda or whatever). 

Then when installing Ubuntu, make sure you choose the manual (advanced) installation. Then you will have full control of what partition Ubuntu should be installed to. 

Partition the 100 gb empty space as one swap of ~2GB, and the rest as an ext4 partition with mount point: /. 

Also, in the last step you can choose where it should install the boot loader (it is kind of hidden under "extra options" or somehting). Make sure you pick the same hard drive that you installed ubuntu to (and make sure BIOS is starting from that hard drive).

---

### Post by ronparent on 2010-09-26
I think what you are encountering is raid meta data previously written to the disks in a previous life. The raid data is no longer wanted but will remain anyway until it is erased! To erase it modify the following command and write it to a terminal:

sudo dmraid -E -r /dev/name_of_your_disk

Once this is done, the system should behave normally as if no raid is present. You can also uninstall dmraid, however, this is optional and unnecessary once the raid meta data is erased.

---

### Post by spectre1989 on 2010-09-26
> **ronparent said:**
> I think what you are encountering is raid meta data previously written to the disks in a previous life. The raid data is no longer wanted but will remain anyway until it is erased! To erase it modify the following command and write it to a terminal:

sudo dmraid -E -r /dev/name_of_your_disk

Once this is done, the system should behave normally as if no raid is present. You can also uninstall dmraid, however, this is optional and unnecessary once the raid meta data is erased.

It took me a second to realise I needed to run the command on dev/sda and sdb, rather than sda1 and sda2, I seem to have forgotten the fundamentals of linux in my time away >_<

Anywho I'm up and running no problems now thanks to your advice, thanks so much =)

---

### Post by ronparent on 2010-09-26
Glad to hear your squared away. Good luck.

---

