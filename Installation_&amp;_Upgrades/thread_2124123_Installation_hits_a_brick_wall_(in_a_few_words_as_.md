---
title: "Installation hits a brick wall (in a few words as possible)"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by CinoxFellpyre on 2013-03-09
Ok, friend has HP computer. It has nVidia GeForce6150 LE, integrated.

CPU is AMD Athlon 64 X2 Dual Core Processor 3800+

I started off trying to partition myself, gave root partition 8 GB, then the Swap 2 GB (because it had 1GB ram in it) and the rest out of a 250 GB drive to /home.

That failed, so I tried letting the um, whatever it's called, started with an L, and that didn't work.

ThenI tried repartitioning it myself. and I completely ****** it up. Completely. Any time I try to install it now, gives me "Executing 'grub-install /dev/mapper/ubuntu-root' failed"

Head, meet brick wall. ](*,)

---

### Post by CinoxFellpyre on 2013-03-11
Bump

---

### Post by ibjsb4 on 2013-03-11
Why not just let the installer create its own partitions?

---

### Post by oldfred on 2013-03-11
/mapper is either RAID or LVM.

Did you turn RAID on?
Did you specify LVM or full disk encryption?
Or is this an UltraBook that uses RAID for the Intel SRT?

Once drive is converted to RAID or LVM, gparted and the Desktop installer do not have the drivers, nor will normally install as you have to use different partition tools appropriate for those systems.

If RAID, turn RAID off in BIOS, and remove meta-data from drive. I think with LVM you can use gparted to delete the entire LVM, but am not sure as I have never used either RAID nor LVM.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by aspergerian on 2013-03-11
> **CinoxFellpyre said:**
> Ok, friend has HP computer. It has nVidia GeForce6150 LE, integrated. CPU is AMD Athlon 64 X2 Dual Core Processor 3800+

I have an HP dv7t and an HP G71. Both have w7. Each may have HP's UEFI. What model is your friend's computer?

---

### Post by CinoxFellpyre on 2013-03-12
LVM! That's what I did the second time it didn't work.

Anyways, I had LVM, I didn't do encryption, no RAID, and it's just an HP desktop computer.

---

### Post by oldfred on 2013-03-12
LVM adds a level of complication. If you really want to regularly change partition sizes it may be something you want. But if your friend does not know Linux it may be better to start without it.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by CinoxFellpyre on 2013-03-14
WELL YOU WON'T BELIEVE THIS.

The partitions MAGICALLY TURNED BACK TO NORMAL so I can easily repartition whatever I need/want.

Gave / a primary partition with 8.1 GB, Swap is 3 GB, and the rest is for /home.

Now, gonna try to get it properly installed. One moment.

Now since I'm getting the same errors, I'm gonna assume it's a lack of Nvidia drivers so I'm following [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/) for 12.10 to get the thing working properly. AND IT WORKED.

...which means I just made this thread for nothing ;_;

---

