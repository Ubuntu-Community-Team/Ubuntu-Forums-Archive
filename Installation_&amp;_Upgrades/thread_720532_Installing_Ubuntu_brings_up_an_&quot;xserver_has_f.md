---
title: "Installing Ubuntu brings up an &quot;xserver has failed&quot; error message. Geforce 9600gt"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by EagleWing on 2008-03-10
Hey everyone!

Here's what I'm trying to do.  My computer's 500gb hard drive is partitioned into two 250gb partitions.  One of these partitions has Windows Vista on it (and yes please don't flame me for it ;) ), and the other partition is completely empty.  Well, for some reason the master table on the Vista partition has been corrupted, which means that I have that all of my data is stuck inside that partition. 

 I want to install ubuntu on the second partition and extract the data onto it with a data recovery program.  But I keep getting the 'xserver has failed' error when I try to install it.  I have run the sudo xserver recovery thing but I can't find the 'nvidia' drivers listed. 

I have a Geforce 9600gt, which I think is part of the problem.

Sorry if this is a newbish question!

Thanks,
EW

---

### Post by Rocket2DMn on 2008-03-10
Hey, why don't you try running the reconfiguration and selecting the "vesa" driver - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) .  Then you can boot into this low graphics mode driver and install the restricted nvidia drivers from System->Administration->Restricted Drivers Manager

---

### Post by Neo0351 on 2008-03-12
I dont think the nvidia restricted drivers work.  I'm using the 171.06 driver from nvidia, which seems to work the best.  try this for x86 [ftp://download.nvidia.com/XFree86/Linux-x86/171.06](ftp://download.nvidia.com/XFree86/Linux-x86/171.06)
and this for x86_64
[ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06](ftp://download.nvidia.com/XFree86/Linux-x86_64/171.06)

---

### Post by Rocket2DMn on 2008-03-12
If you take Neo's suggestion, here is how to go about installing them:
```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
^^ignore any file not found errors ^^
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```
do CTRL+ALT+F1 to get to a tty and login there, then run
```
sudo /etc/init.d/gdm stop
sudo chmod +x /path/to/NVIDIA*
sudo sh /path/to/NVIDIA*
sudo /etc/init.d/gdm start
```
In this case /path/to/NVIDIA* is pointing you to where you svaed the .run file you downloaded from nvidia's website ( ex: your desktop path: ~/Desktop/NVIDIA* )
Now in the GUI, open a terminal and run
```
gksu nvidia-settings
```

---

