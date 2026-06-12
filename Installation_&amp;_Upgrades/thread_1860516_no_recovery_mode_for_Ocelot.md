---
title: "no recovery mode for Ocelot"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by rfbeck on 2011-10-14
I upgraded to Ocelot from Natty, and I expected the usual driver hassle with my Nvidia drivers. I booted into the "recovery mode" to re-install my Nvidia drivers for the new kernel.
However, when I went into recovery mode, I just got a blank screen.
I think I might have a botched installation, because I've never had  a problem getting into the "recovery mode" before.
Is there a way to do a repair installation for Ocelot? Or basically what's the best solution. Please help, because I kind of freakin'.

______
Robert

---

### Post by rfbeck on 2011-10-14
Well, I managered to get a CLI using a alternate install disk. From there I installed my NVIDIA driver. I'm still wondering how I get the Unity desktop, since I was stubbornly using Gnome under Natty. Now I can't switch back to Unity. Is there a CLI to do this? Thanks.
______
Robert

---

### Post by rfbeck on 2011-10-15
Still no recovery text options when I choose this during start up. That's the eastest way for me to get to the command line without booting into graphic Linux. What IS going on!

---

### Post by garvinrick4 on 2011-10-15
This is a way to use chroot and get into / of your install and update and upgrade and check for
broken packages in a live cd (install cd using Try Ubuntu). open a terminal and copy and paste one at a time. 
I am going to use sda5 for this [COLOR=Red]You USE your own[/COLOR]
```
sudo fdisk -l 
```(lower case L)
Now find your linux install and use it in place of my sda5 ([COLOR=Red]and get internet working in Live CD[/COLOR])
```
sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``````
sudo chroot /mnt
``````
dpkg --configure -a
``````
apt-get update; apt-get upgrade
``````
dpkg --configure -a
``````
apt-get -f install
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
``````
sudo reboot
```#All this is doing is checking for broken packages and any uninstalled packages and updating system
and checking for broken packages again then umounting what was mounted.
## While in chroot you can install grub, install packages, remove packages, do anything required when cannot get a boot and need this alternative method to repair.
Just do not have to use sudo because you are in root of whatever install you mounted in /mnt or your file system.

---

### Post by rfbeck on 2011-10-15
Thanks. I'm going to try it now. I also wonder why I have to log into 2D Unity. I have just installed NVIDIA's latest driver. Why no 3d Unity? I guess I'll try the above suggestion and see what happens!
_______
Robert

---

### Post by garvinrick4 on 2011-10-15
> Thanks. I'm going to try it now. I also wonder why I have to log into 2D UnityYou mean in your live cd?

---

