---
title: "updated try to load in /boot partition"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2015-03-28
My grand daughter's computer when trying to upgrade it trys to upgrade into the /boot partition instead of the / (root) partition.  It upgraded once or twice the frirst times correctly into the / (root) partition and now it wants to update into the /boot partition.  The /boot partition is just less than 200 MB and the / (root) partition is 30 GB.  It also has a /home partition and an 8 GB swap partition.

What has happened and how do it repair the system to upgrade in the / (root) partition like it is supposed to?

Should I backup all her data and reinstall Ubuntu 14.04 LTS and then reinstall all the applications I had origionally put on the computer for her?  OR is there some other way to correct the problem.

---

### Post by grahammechanical on 2015-03-28
How do you know this is happening? Are you getting an error message saying that /boot is full?

If an update brings with it an upgrade to the kernel and we have a /boot partition then the update will put the new kernel into /boot. Over time we can get a collection of kernels that can fill up the /boot partition.

This does not happen if we do not have a boot partition because the kernels are put into the boot folder in the /partition. At the grub boot menu in the Advanced Options sub-menu we can load in Recovery Mode. At the recovery menu select clean - try to make free space. That may remove some of the earlier kernels.

Regards.

---

### Post by ubfan1 on 2015-03-29
Well, backup never hurts, but you shouldn't need to reinstall anything.  The basic problems is the tiny /boot partition fililing up with the third or fourth kernel.  If the aforementioned "clean" does not remove the old kernels, you can do it yourself:
look at /boot
ls /boot
then list all the packages associated with an old kernel
apt-cache pkgnames | fgrep 3.13.0.<oldest kernel number>
If they all start with linux, just purge the ones which are actually installed:
sudo apt-get purge `!!`
You will get a list of the packages to be installed, and space saved if you confirm.

You might try to get the latest kernel (or just take all of them) onto the /boot on the root system, then just dont mount the /boot partition (comment out the line in /etc/fstab).  I suppose you could try to just remount the /boot device onto /mnt or a /mnt/directory
then see what's in /boot.  It may be empty, it may have an old kernel. You should just be able to copy all the files in the mounted boot partition back to the root /boot.  Then comment out the /boot mount in /etc/fstab.  The update should work then, since you have a 30G root to use for kernels.  I've never had a separate /boot partition, so I think a running kernel would not care if it were dismounted, but worst I'd expect is a crash, nothing permanent done, but backup anyway.

---

### Post by jlh68 on 2015-03-29
Yes, a notice that the /boot does not have enough room.  Otherwise I would not have known.  I will clean out all the old linux kernals except the current one and the one before it and then try the upgrade.

I will report back how it goes, and if I need further help.  I will have the laptop until Friday to work on it.

---

### Post by jlh68 on 2015-03-29
I removed the old Linux kernals and the upgrade went smoothly.

My grand daughter lives almost 200 miles away so it is hard for me to maintain her Linux system.  My son uses her laptop some but does not know how to take care of a Linux system.  He is a MAC guy and expects everything to be done by the OS for him.  On the other hand I like tinkering with the variious part of the computer.  So I guess I will have to try to educate my son first on the Linux operation, and then my granddaughter as she gets older (she is 12 now).

Thanks for hte help.

---

### Post by ubfan1 on 2015-03-29
Sounds like you could use an ssh connection to the remote machine.  I couldn't make any recommendations myself, since I don't use it and am not sure what security issues might arise, but something to check out to make your life easier.

---

