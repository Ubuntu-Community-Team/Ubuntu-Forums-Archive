---
title: "Ubuntu crashed or hung during distribution upgrade"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by Evil Wayz on 2016-04-30
I saw that 16.04 was a LTS edition, so I ran updater.  Updater told me that 15.10 was available.  So I thought I'd hop incrementally to 16.04.  The upgrade tool had just finished fetching and was installing the packages when both my monitors went to power saver mode.  They would not come back on.  The hard drive light wa still on and it was making a bunch of noise so I thought maybe it was still working.  But now it's been two hours, and the computer is silent, the lights are all off except for power, and both screens are in no signal/ powersave mode.  

How long should I wait just in case?  And can I use dpkg  and install -f to recover the upgrade?

---

### Post by Evil Wayz on 2016-04-30
On restart, if I go to recovery , i get to a tty login, and as soon as i log in a get this error over and over again, its at 105 currently:

```
usb 1-8 clear tt 1 990a2) error 71
```

---

### Post by Evil Wayz on 2016-04-30
Ok it appears I have root access, but I don't have internet access.

---

### Post by Evil Wayz on 2016-04-30
Also when I attempt to use 

dpkg -configure -a 

it says unknown option o.  But I'm not typing o.

when I try
dpkg-reconfigure -a

It asks me what package.  I don't know hte command for all broken packages.

---

### Post by Evil Wayz on 2016-04-30
I'm pretty sure if I just had internet access I could recover.

---

### Post by Evil Wayz on 2016-05-01
Ok this is what I did to fix this.

First I got a Ubuntu 15.10 usb stick and started up a live session. 

First I figured out which directory was root using 
```
sudo fdisk -l
```

In this case it was ext4 filestructure and sda1

then I performed chroot:
```
cd /
sudo mount -t ext4 /dev/sda1 /mnt
sudo mount -t proc proc /mnt/proc
sudo mount -t sysfs sys /mnt/sys
sudo mount -o bind /dev /mnt/dev
```

now I needed domain resolution so I did this:

```
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
```

then I mounted the drive with root access:
```
sudo chroot /media/ubuntu
```

then I gave it access to the bash shell:
```
sudo chroot /mnt /bin/bash
```

first I updated to see if I had internet access, which I did:
```
apt-get update
```

and then I forced installed the programs that were fetched but not unpacked and installed. 
```
apt-get install -f
```

Then I updated again, and tried to download the rest of the distribution upgrade.
```
apt-get update && apt-get dist-upgrade -y
```

Then I configured any package that might have been missed because of the interruption:
```
dpkg &#8211;configure -a
```

Then I cleaned up the system:
```
apt-get autoremove
```

then I exited the shell:
```
exit
```

and unmounted the drive:
```
umount /mnt/{proc,sys,dev}
umount /mnt
```

and then rebooted.  WHen I restarted, I got a message asking if I wanted to upgrade to 16.04, and i used that to finish up.  Now, in between now and 2021, I'm going to stick with 16.04 and buy a large drive to backup my data on.

---

