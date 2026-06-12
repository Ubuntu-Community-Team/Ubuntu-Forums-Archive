---
title: "I just hosed my copy of Ubuntu Server...any way to recover?"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by i.wanna.corndog on 2010-09-15
I was installing a package last night and it recompiled my kernel and some other things. I restarted and am getting issues with "mounting none on /dev failed" and "general error mounting filesystems." I tried the three different kernels listed in grub (even the recovery options) and all of them crash in similar manners and the keyboard becomes unresponsive (perhaps because it is a USB keyboard?).

I am using this as a file server and have about 1TB of files. Is there any way to recover/reinstall without having to copy all of the files off and then recopy after a reinstall?

---

### Post by oldfred on 2010-09-15
You have data in the system folder?

Can you chroot into your system and reinstall a new kernal?

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

If you know what else to reinstall you should do that also.

---

### Post by i.wanna.corndog on 2010-09-16
Thanks for the input. I was able to chroot into the folder and run the update commands. I'm still having issues getting the system to boot, though (i.e. getting the exact same errors).

I suspect that this might have to do with the fact that I have a separate boot partition. When I used chroot, I didn't have the boot partition mounted to /boot, so updated kernels were placed on the boot partition (rather to a /boot folder on the main partition). I'm going to try backing up /boot and moving those files onto that partition. I'll have to try that when I get home from work.

In the meantime, any other things to try?

---

### Post by oldfred on 2010-09-16
You may want to rerun the chroot but add in the extra mount of the separate /boot. That was not included in the one line version from kansasnoob.

---

