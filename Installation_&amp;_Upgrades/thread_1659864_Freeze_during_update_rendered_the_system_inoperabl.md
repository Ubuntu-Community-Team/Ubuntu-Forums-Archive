---
title: "Freeze during update rendered the system inoperable"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Louigi Verona on 2011-01-04
What happened was a random freeze, which unfortunately occurs on my Ubuntu 10.04, during the update. At that time the downloaded software was installing, namely the linux kernel (hehehe).

I rebooted, the system performed a disc check and then loaded stripes. Instead of the cursor - a large striped square. It must be noted that during disc check Ubuntu logo was not displayed but normal text instead, saying "Ubuntu 10.04".

Tried recovery mode - however, it stops loading during bottom init scripts, on saying that it allocates swap or something like that.

What should I do to fix the system?

---

### Post by Vermind on 2011-01-04
As a first step, I recommend booting with a livecd and running
file system checks on all your partitions with the "disk utility" found in the system menu.

After that you can try to log in without the livecd, perhaps use an older kernel if you still have one installed.

The command to fix not completely installed packages is
```
sudo dpkg --configure -a
```
This can also be done through the livecd, but it will be more complicated.
In short, boot with a livecd, mount your root partition somewhere, chroot to it, and run the command above. Then exit and unmount everything and start your system normally.

---

### Post by Louigi Verona on 2011-01-05
Older kernel versions do not work as well. I have an older Ubuntu - 9.04 - and it works fine, I am writing from it now. I will try to do disc checks from it.

---

### Post by Vermind on 2011-01-06
So then,
if filesystem checks do not help, you can do this to fix not completely installed packages. Use your Ubuntu 9.04, and start a terminal.
Mount the root partition of the newer ubuntu, chroot to it, and try the fix:
```
sudo mkdir /media/temp
sudo mount /dev/sdxn /media/temp
sudo cp /etc/resolv.conf /media/temp/etc/.
sudo mount -o bind /dev  /media/temp/dev
# if you have a boot partition and the problematic package is grub or something, do
sudo mount /dev/sdym /media/temp/boot
sudo chroot /media/temp
# now you are in the system and can run commands as root.
dpkg --configure -a
# ... other commands
# when you are done:
exit
sudo umount /media/temp/dev /media/temp/boot /media/temp

```
You can also try other commands, like apt-get upgrade, apt-get -f install, and so on, if this does not help.

To make this work, you need to know the name of your root partition. use that instead of my /dev/sdxn placeholder. It could be /dev/sda1, /dev/sda6, /dev/sdb6 or /dev/sdc6, and so on, depending on how many disks you have and which partition number it is. The same goes for your boot partition if you have one.

You can also use gparted or the disk utility to see the partition numbers I think.
If you can mount the partitions automatically with gnome or disk utility, writing "mount" in the terminal will also tell you the names of everything that is mounted.

Good luck.

---

### Post by Louigi Verona on 2011-01-06
Thanks for taking the time to respond. I did just that - used chroot - and everything is back to normal once more. Thank you!

---

