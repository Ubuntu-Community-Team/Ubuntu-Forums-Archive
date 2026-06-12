---
title: "Ubuntu Wubi root.disk problem"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by xxwikkixx on 2011-08-16
hey every one...

i had ubuntu installed on my computer via wubi inside my windows 7 OS..after a while something went wrong with the partitions magic stuff and windows 7 got corrupted but ubuntu kept working :D...Love ubuntu for that......since i had my stuff backed up and saved in ubuntu...i thought i could make a backup off the root.disk file and reinstall windows and that what i did....but then i installed ubuntu again via wubi but replaced the new root.diskk with the old one that i had backed up.....but now it says it cant find disk :O ...so it takes me to a shell.....i seriously need to get that root disk to work or ima loose really important stuf.. :(

please help me.

---

### Post by Mark Phelps on 2011-08-16
What you did SHOULD have worked -- but apparently did not.

If you still have access to the original root.disk file, you might be able to get files out of it if you boot using an Ubuntu LiveCD and try opening that file.

Not a wubi user (or fan) -- so I don't know if this will work.  Only offering a suggestion.

---

### Post by coffeecat on 2011-08-16
@xxwikkixx, I don't know how to get that root.disk file booting, but in theory you should be able to loop mount it from a live Ubuntu CD and browse inside it. See here:

[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

Follow this bit:

> Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk

If you need help with that, post back. You need to know how to boot a live Ubuntu CD which you may not have done before since you have been using Wubi, and you need to know which is your Windows partition - it may or may not be /dev/sda1.

Do you have a copy of the root.disk stored outside of your Windows partition? If so, you can loop mount the file directly. Post back details, if so, and we can help you with that.

---

### Post by bcbc on 2011-08-16
You can get it booting. See this: [http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines](http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines)

It refers to moving an install between machines, but in essence the problem you have is the same: the partition and/or uuid has changed. So you need to figure out what the new values are.

From a grub prompt do:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

Report back with the result. You can enter "reboot" after that to restart the computer.

---

