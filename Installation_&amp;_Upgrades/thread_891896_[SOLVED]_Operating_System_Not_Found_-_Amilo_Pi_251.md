---
title: "[SOLVED] Operating System Not Found - Amilo Pi 2515 Laptop"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Yorper on 2008-08-16
I'm really stuck and need some help here. I'm trying to install Ubuntu 8.04.1 (Desktop) to my Fujitsu Siemens Amilo Pi 2515 Laptop.

It boots the live CD fine, and seems to install everything fine. Yet once it asks me to reboot and remove the CD, the system just reboots and halts on text saying...

Operating System Not Found.

This is really annoying me now as 7.10 installs perfectly, yet 8.04.1 will not, not even for Kubuntu (havent tried xubuntu). My CD images are good, hashes match up and i've even re-downloaded 3 times, each time from a differant mirror.

Is there some sort of bug with the install or something, its like GRUB isnt even being set to the MBR?

Any ideas would be great.

---

### Post by Yorper on 2008-08-16
Ok here's a quick update, if i put the live CD back into my system and select from the menu "boot from first hdd". Then everything seems to load fine, untill i reboot again.

So anyone know a way i can sort this problem out properly, without having to keep selecting the option from the live CD?

EDIT: Forgot to mention, i've tried reinstalling grub, although it says it worked, once i reboot i get the same issues as my first post.

---

### Post by Yorper on 2008-08-16
Ok, this is weird but after trying to reinstall grub a couple ways i've managed to get it working, for those interested this is what i did from a terminal...

```
sudo grub
find /boot/grub/stage1
```

Whatever the outcome of the find was is then used next...


```
root (hd0,0)
setup (hd0)
quit
```

That alone didnt fix my problem after a reboot, i then did the following from another terminal...

```
sudo grub-install /dev/sda
sudo grub-install /dev/sda1
```

It seems to have been this second step that fixed my problem. Hope anyone else reading this with the same or similar problem can get something from it.

---

### Post by Leslie Viljoen on 2010-07-25
With Lucid Lynx (Ubuntu 10.04), there is no "grub" command. I solved the problem by booting into the live CD (selecting "Try Ubuntu"), then going to the command line.

I ran "sudo fdisk -l" to look for the main partition. There were only three, Linux, Extended and Swap (which is inside the Extended). The Linux partition was the large main one, on /dev/sda1

So then I could run:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda1

This gave me a warning about blocklists, so I had to add "--force" to the command line and then it worked. After that I could boot. I have no idea why the Amilo doesn't boot properly from the MBR.

---

### Post by Leslie Viljoen on 2010-07-25
Oh, pardon me, that grub-install only seems to work once, until the computer is rebooted again, and then the "Operating System Not Found" message comes back. If anyone knows what is going on here, please help.

---

### Post by Leslie Viljoen on 2010-07-29
Finally got it working permanently by following the instructions here: [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

First, you boot from the Lucid live CD and open a terminal. The commands assume there is one main partition, and its on /dev/sda1, the fdisk -l is to check on that. Also note that I added the command to load Grub on the first partition (/dev/sda1) right after installing it on the MBR (/dev/sda).

[LIST=1]
[*]**sudo fdisk -l**
[*]**sudo mount /dev/sda1 /mnt**
[*]**sudo mount --bind /dev /mnt/dev**
[*]**sudo mount --bind /proc /mnt/proc**
[*]**sudo mount --bind /sys /mnt/sys**
[*]**sudo chroot /mnt**
[*]**grub-mkconfig -o /boot/grub/grub.cfg**
[*]**grub-install /dev/sda** (try **grub-install --recheck /dev/sda** if it fails)
[*]**grub-install /dev/sda1 --force **(should be ok despite the warning)
[*]**Ctrl+D** (to exit out of chroot)
[*]**sudo umount /mnt/dev**
[*]**sudo umount /mnt/proc**
[*]**sudo umount /mnt/sys**
[*]**sudo umount /mnt**
[/LIST]

Then shut down and remove the Live CD. When you boot again, it should boot into Ubuntu.

---

