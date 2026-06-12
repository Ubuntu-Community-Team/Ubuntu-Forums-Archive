---
title: "no windows 7 option after recent installition and grup repair"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by caracal28 on 2012-10-07
Earlier today i installed ubuntu 12.10 beta. Grub wasn't booting, but just going directly to my primary OS Windows 7. I assumed i had partitioned incorrectly, because partitioning isnt my strong suit. I used boot repair because it was well recomanded off a live usb. Afterwards, grub appeared, but i only had options for Ubuntu, Advanced Ubuntu Option, and my hidden windows 7 recovery partition. Please help me recover my access to windows partiton.
See this link for Boot-Repair report: [http://paste.ubuntu.com/1266467/](http://paste.ubuntu.com/1266467/)
ps. ran Boot-Repair a second time - no change

---

### Post by darkod on 2012-10-07
1. You shouldn't install a version that is still under development on your main system!!!

2. I notice you created a small /boot partition at the front of the hdd. Since usually the front wouldn't be empty, did you maybe move the windows partition to make empty space ahead? Windows doesn't like it at all if you move its partitions.

3. Grub2 didn't install all the way. The /grub/core.img is missing on sda3. You can enter the installation with the chroot procedure and remove and reinstall grub-pc.

---

### Post by caracal28 on 2012-10-07
thanks for the help. now how would i go about fixing #2 and executing #3 on your list?

---

### Post by darkod on 2012-10-07
#2 was only a thought. Even if you did that trying to put them back might mess it up more. Lets just hope windows works after the move.

#3, boot the cd in live mode, open terminal and then first prepare and enter the chroot:
```
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda3 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are like inside the installation. Purge grub completely, reinstall it and recreate the config files:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/boot
sudo umount /mnt
```

Reboot and hopefully all should be fine.

---

### Post by caracal28 on 2012-10-07
I just realized that windows was hibernating. After mount sda2, and deleting the hibernation files, the running sudo update-grub, windows 7 is now displayed as an option and boots. Is there any reason to still fix the /grub/core.img on sda3?

---

