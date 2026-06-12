---
title: "Problem installing Feisty Fawn on External Hard Drive"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by tubaybb321 on 2007-08-13
Hi,

I'm trying to install Feisty Fawn on an external hard drive (A Seagate Free Agent) and tried to follow DaBruGro's recipe for installing Breezy. Tragically, not everything went as planned.

I was OK until I hit step 6. I opened the new terminal, but got a Bus error when I tried typing the commands from step 7. This was OK. I shut my computer down, booted up the Linux on my internal drive and proceeded to edit files as directed. My questions/problems are as follows:

1. DBG refers to the /etc/mkinitramfs/modules & /etc/mkinitramfs/imitramfs.conf files. I didn't find an /etc/mkinitramfs directory, but did find a /etc/initramfs-tools directory, which seemed to have the correct files in it. Am I correct in believing this?

2. I have no idea how I should now run the mkinitramfs -o /boot/initrd.img-xxx /lib/modules/xxx command. Should I:
    a. Run it from my Internal hard drive's Linux and somehow redirect the arguments to the correct directories? If so would the new command be something along the lines of 
mkinitramfs -o /mnt/sda/boot/initrd.img-xxx /mnt/sda/lib/modules/xxx command (assuming I'm mounted on /mnt/sda)
   b. Go back to the LiveCD Ubuntu and attempt to mount & chroot to the external drive and enter the mkinitramfs command as originally given? The external drive seems to be mounted as /media/disk. Yet, when I type "sudo mount -t proc /media/disk/proc" I get an error message that's attempting to instruct me as to the proper usage of the mount command. It appears to want something of the form "mount -t type dev dir", which would imply I should be giving it one more argument.

Any suggestions, or pointers to relevant posts would be greatly appreciated. I'm going to pass out now.

Thanks

---

