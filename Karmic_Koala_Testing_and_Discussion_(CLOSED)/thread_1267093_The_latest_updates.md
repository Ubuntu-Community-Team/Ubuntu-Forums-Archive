---
title: "The latest updates"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-15
I saw that the latest update is going to remove 215 packages..In theory won't that render the system unable to boot? It seems like those packages are going away with nothing to replace them with? 

Edit: not scared of it, just preparing myself for it.

---

### Post by LinuxLars on 2009-09-15
I would wait a bit - several folks (including me) are having serious issues with the update today.

---

### Post by sports fan Matt on 2009-09-15
Yeah...I cant even update if I wanted to.  If anyone has a fix for the no internet..alot would be grateful im sure:)

---

### Post by philinux on 2009-09-15
The only way to fix that now without reinstalling is using chroot from another linux partition or from a livecd.

---

### Post by kansasnoob on 2009-09-15
I just keep waiting about an hour or so and running recovery mode, then selecting "root shell w/networking" from the following menu and running sudo apt-get update && sudo apt-get dist-upgrade.

Maybe it'll get itself straightened out:)

Thinking maybe I'll add -f install to the next try.

---

### Post by sports fan Matt on 2009-09-15
Im running from a jaunty live cd so I can fix it with instructions.  :)

---

### Post by LinuxLars on 2009-09-15
I connected an ethernet cable, then ran sudo NetworkManager restart - and I can ping the outside world and run apt-get. Just waiting on the fix now :-)

---

### Post by slakkie on 2009-09-15
> **sox fan Matt said:**
> I saw that the latest update is going to remove 215 packages..In theory won't that render the system unable to boot? It seems like those packages are going away with nothing to replace them with? 

Edit: not scared of it, just preparing myself for it.

Depends on which packages will be removed. If ubuntu-(minimal|standard) packages will be removed together with all the dependencies you might run into serious issues..

I haven't had the 215 packages will be removed. Could you post the output of:

aptitude -s safe-upgrade

Am a bit curious in what will be removed...

---

### Post by Vanishing on 2009-09-15
> **sox fan Matt said:**
> Im running from a jaunty live cd so I can fix it with instructions.  :)

Im glad I had backtrack installed on another partition..:lolflag:

in my case, I updated through the ubuntu-boot PPA too...
so its more for me to fix:(
gonna try the ethernet cable method:lolflag:

---

### Post by philinux on 2009-09-15
> **sox fan Matt said:**
> Im running from a jaunty live cd so I can fix it with instructions.  :)

From my jaunty install I use chroot like this. Note my karmic install is on /dev/sdb1 so substitute your own here. From a live cd If I remember right it might be /media/disk. Do the check for yourself.
```
sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash
```

After that last command you will be in a chroot jail of karmic. From this command line you can do sudo apt-get update or upgrade etc to the karmic install. At this point there are no updates that fix my problem.

---

### Post by slakkie on 2009-09-15
psssst. Clonezilla, so you can backup and restore your OS.

---

### Post by sports fan Matt on 2009-09-15
If I do this (Im using my whole disk) I wouldnt lose anything as far as packages on my karmic install?  I'm not exactly sure if im supposed to ruin the commands as you've typed them..Im pretty new at mounting/figuring things out at breakage,as this is my 1st major break.

---

### Post by waspbr on 2009-09-15
latest updates broke my karmic too, now I got the bliking cursor of death. 

But i can still access the CLI by doing crtl + alt + F2 and a quick

```
sudo dhclient eth0
```

connects me to my network. 

I tried running with no acpi, but no cake... so if anyone figures out a work-around pls do not hesitate to post.

---

### Post by slakkie on 2009-09-15
Hehe, the upgrade broke my input devices. Mouse and keyboard are not working. I do get a nice login prompt but unable to type anything.. 

I've cloned this b0rked OS, to see if I can recover from it in a couple of days...

---

### Post by thegodsquirrel on 2009-09-15
chroot did not help I am still locked out of karmic

---

### Post by tjeremiah on 2009-09-15
im afraid to update:(

---

### Post by thegodsquirrel on 2009-09-15
> **philinux said:**
> From my jaunty install I use chroot like this. Note my karmic install is on /dev/sdb1 so substitute your own here. From a live cd If I remember right it might be /media/disk. Do the check for yourself.
```
sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash
```

After that last command you will be in a chroot jail of karmic. From this command line you can do sudo apt-get update or upgrade etc to the karmic install. At this point there are no updates that fix my problem.



Thanks for the help bud

got into the chroot and did an upgrade everything is tip top now.

---

### Post by Eestlane on 2009-09-15
Seems to be this bug: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/430091](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/430091)
At least I have it.

---

### Post by Eestlane on 2009-09-15
> **waspbr said:**
> latest updates broke my karmic too, now I got the bliking cursor of death. 

But i can still access the CLI by doing crtl + alt + F2 and a quick

```
sudo dhclient eth0
```

connects me to my network. 

I tried running with no acpi, but no cake... so if anyone figures out a work-around pls do not hesitate to post.

Thanks for the command, I couldn't do chrooted apt-get update without it.


EDIT: Yay, back in Ubuntu. Now upgrading, then Synaptics Fix Broken Packages and mark all upgrades and applying them finally removed all broken dependancies and nothing is held back anymore :)

---

### Post by berthiggins on 2009-09-16
> sudo mkdir /mnt/karmic
sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

Thanks saved my bacon saved for future use.

I found I could get online with dhclient wlan0 as my wireless was already connected

---

### Post by zika on 2009-09-16
After upgrade this morning I was unable to use my static address but I managed to make DHCP work. I get:

```
$sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
.: 14: Can't open /lib/init/mount-functions.sh
run-parts: /etc/network/if-up.d/mountnfs exited with return code 2
initctl: Event failed
run-parts: /etc/network/if-up.d/upstart exited with return code 1
[ OK ]
```

---

### Post by dino99 on 2009-09-16
> **waspbr said:**
> latest updates broke my karmic too, now I got the bliking cursor of death. 

But i can still access the CLI by doing crtl + alt + F2 and a quick

```
sudo dhclient eth0
```

connects me to my network. 

I tried running with no acpi, but no cake... so if anyone figures out a work-around pls do not hesitate to post.

try with : init=/bin/bash on the grub boot line

---

