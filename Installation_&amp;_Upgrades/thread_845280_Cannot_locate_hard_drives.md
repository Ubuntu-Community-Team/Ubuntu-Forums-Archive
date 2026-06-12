---
title: "Cannot locate hard drives"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by Daimanta on 2008-06-30
I was trying to install 7.04 on my Medion computer currently running Vista. So I boot up a seperate gparted liveCD but it doesn't recognise any hard drive. I have a Seagate disk but the gparted liveCD didn't recognise it. I tried to fdisk -l but it failed. fdisk /dev/hda -l fails to do anything. fdisk /dev/hdb -l shows an empty harddisk(which is nonsense). I tried another version of gparted and also the 7.04 liveCD but to no avail. What is going on? Can this be solved? I assume the burned CDs are sane since they work on other PCs.

---

### Post by Licurgo on 2008-07-01
Daimanta:
Run the live CD or DVD
Go to: Applications-Accessories-Terminal
Type: fdisk -l
Post the output
:lolflag:

---

### Post by Daimanta on 2008-07-02
> **Licurgo said:**
> Daimanta:
Run the live CD or DVD
Go to: Applications-Accessories-Terminal
Type: fdisk -l
Post the output
:lolflag:

That's the problem. There is NO output. If I fdisk all the possible devices individually I get:

Note: sector size is 2048 (not 512)

Disk /dev/hdb: 89 MB 89038848 bytes
255 heads, 63 sectors/track, 2 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Disk /dev/hdb doesn't contain a valid partition table.

That's the only disk that will work. And yes, I sudo everything.
And for the record, I do not have a 89 MB AFAIK.

---

### Post by Daimanta on 2008-07-02
I hope my hardwarespecs help: (lshw)

[http://www.vanderkaap.org/hardware.html](http://www.vanderkaap.org/hardware.html)

---

### Post by confused57 on 2008-07-02
Maybe the last post in this thread will help:
[http://ubuntuforums.org/showthread.php?t=839175&highlight=AHCI](http://ubuntuforums.org/showthread.php?t=839175&highlight=AHCI)

---

### Post by Daimanta on 2008-07-02
> **confused57 said:**
> Maybe the last post in this thread will help:
[http://ubuntuforums.org/showthread.php?t=839175&highlight=AHCI](http://ubuntuforums.org/showthread.php?t=839175&highlight=AHCI)

Well, apparently it's the old kernel of the older CD. The 7.04 CD and the gparted liveCDs all use old kernels that fail to recognize my hard disk. The new CD does not have that problem. Thanks for trying to help anyway :)

---

### Post by ashleycameron on 2008-07-02
I had same problem while loading new version of 7. But i just restarted my system now it is working fine..

---

### Post by Licurgo on 2008-07-02
Daimanta:
It's strange that you had no output, but if you solved the problem with the 8.04 version its all right
Anyway, you can ask if a new challenge appears
:guitar:

---

