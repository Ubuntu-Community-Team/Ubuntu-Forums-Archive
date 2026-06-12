---
title: "How should I repair the  following problem with the installation"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-08-13
I have tried a repair install over the top of the existing partition.

I can only load the system if I go in via low graphics mode. The normal way in gives me an orange  screen and a freeze.

In low graphics mode the Usb ports do not work. I have tried a serial adapter for the usb mouse but it also does not work in low graphics mode.  It is very difficult to do much without a mouse. In live CD usb and mouse does work.


In the low graphics mode both the usb mouse and usb memory stick  do not work.

I don't know how to repair this. Any ideas or pointers please.

My favoured approach would be to get the USB ports in the low graphics mode to work  and then try to install the harmony drivers for nvidia.

---

### Post by Hakunka-Matata on 2011-08-13
What Release/Version Ubuntu are you trying to install?
Is your hardware fairly new?

---

### Post by Robbyx on 2011-08-13
> **Hakunka-Matata said:**
> What Release/Version Ubuntu are you trying to install?
Is your hardware fairly new?

11.04
Yes, fairly new.

I am thinking that the safest, and easiest way forward is to buy a new HD. Install the o/s on it, but keep the old for reference. 11.04 seems to me to be a disaster, at least from what I have experienced in the last week. Would it be more sensible to go back to a long term release?

I have managed to get the package.selections onto my mem stick. I can dpkg them back from the stick to set up the applications onto the  new HD. I have also copied the source.list and fstab onto the Mem Stick for restoration to the new drive. My home is on a separate partition so I can easily copy it to a new home partition.  

Should I back up anything else for transfer to the new drive?

---

### Post by Hakunka-Matata on 2011-08-13
Instead of 11.04, either 10.10 or 10.04 LTS are good choices.

can you post a graphic of your partition setup?  GParted graphic would be nice, or the output of ```
sudo fdisk -lu
```or ```
sudo parted -l
``` You should be able to simply install 10.xx over (read "in") your current 11.04 / (root) partition, overwriting 11.04.

If you have a /home partition, you can just leave it and have the new OS use it.  Backing up important data first goes without saying, eh?

BTW, do you know why you were having the problems (usb port lockup, forced to use low graphics mode) you refer to in Post #1?   You were installing 11.04 - 32 bit Desktop then?  And if you were installing it via USBstick, what method of writing the .iso to USB was used.  Your list of troubles encountered is a bit unusual.

---

### Post by Robbyx on 2011-08-14
**Here is the fdisk results:**

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x484d5754

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    59842124    29921031   83  Linux
/dev/sdb2        59842125   122849054    31503465   83  Linux
/dev/sdb3       122849116   964815704   420983294+   5  Extended
/dev/sdb4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sdb5       122849118   337364999   107257941   83  Linux
/dev/sdb6       337365063   964815704   313725321   83  Linux

Disk /dev/sdd: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32     4014079     2007024    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```


**BTW, do you know why you were having the problems (usb port lockup, forced to use low graphics mode) you refer to in Post #1?  **

*No. The USB failure when I go into low graphics mode is beyond me to trace and I had hoped for support but no one replied to my other postings specifically asking for help on this point. *

 **You were installing 11.04 - 32 bit Desktop then?**
*I had installed 11.04 via an upgrade when it was released. I had problems installing Thunderbird 5. It would not open. I decided after getting no support as to the reason and a cure, that it must be my operating system was corrupted. I reinstalled 11.04. That caused trouble with my hardware raid drive, which is now unreadable. I also found I could not go into Ub other by repair mode using low grahics  *

[B]
  And if you were installing it via USBstick, what method of writing the .iso to USB was used.  [/B]

*I was reinstalling via a cd. The usb stick I use as a backup of crucial files for when I install the new o/s again but this time as a clean install*

---

### Post by dino99 on 2011-08-14
if you have a graphic issue then i dont see relationship with hdd.

sudo rm /etc/X11/xorg.conf

can you tell us which graphic/chipset is used and which driver is installed (is it activated ?)

---

### Post by Actonix on 2011-08-14
> **dino99 said:**
> if you have a graphic issue then i dont see relationship with hdd.

sudo rm /etc/X11/xorg.conf

can you tell us which graphic/chipset is used and which driver is installed (is it activated ?)

I can't help much here but from the brief it looks like his Hardware Raid failing is the more likely culprit and stem of all his issues - if he can get help in sorting that out under 11.04 then I reckon you'd be more than half-way to dealing with his issues.

Knowing his data is safely tucked away I presume this would probably involve knocking off the raid, getting the install done again and if that solves things one could then attempt another raid assuming there are no problems with the drives.

Btw, doesn't a hardware raid require 2 similar drives ?

---

### Post by Robbyx on 2011-08-14
> **dino99 said:**
> if you have a graphic issue then i dont see relationship with hdd.

sudo rm /etc/X11/xorg.conf

can you tell us which graphic/chipset is used and which driver is installed (is it activated ?)

I do not have xorg.conf on the sda1 partition.

Nvidia is the graphic chipset

At the moment I can not get into the HD system without going into recovery mode and using low graphics. I suspect this will mean that the driver will not be activated at that time.

---

### Post by Actonix on 2011-08-15
Have you tried booting/reinstalling with the noraid option ?

To access the options hit the spacebar when rebooting and you should be presented with a boot menu - quite like the Windows emergency boot menu which is Shift-F8 or something

---

### Post by Ubaru on 2011-09-01
Unfortunately like windows you don't have a whole lot of hardware support when you're in "low graphics/safe mode", so you're probably not going to have a lot of extra hardware support(like usb and graphics).  I upgraded to 11.04 and didn't like it too much.  I appreciate 10.10 much more, although 10.04/.10 and 11.04 are the only versions i've used so far.  But if you're going to install again, run the live cd and if you have all your important stuff backed up, erase all your partitions and start from scratch.  it's a pain, but sometimes some files are left behind and can interfere when just installing on top of old one.

---

