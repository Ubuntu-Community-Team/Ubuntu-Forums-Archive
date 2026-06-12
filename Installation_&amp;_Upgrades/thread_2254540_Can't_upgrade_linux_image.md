---
title: "Can't upgrade linux image"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by adrigmail on 2014-11-27
I have  a little problem installing the latest automatic kernelupgrade in ubuntu12.04

This is the message:

E: /var/cache/apt/archives/linux-image-3.2.0-72-generic-pae_3.2.0-72.107_i386.deb: unable to create `/lib/modules/3.2.0-72-generic-pae/kernel/drivers/input/touchscreen/max11801_ts.ko.dpkg-new' (while processing `./lib/modules/3.2.0-72-generic-pae/kernel/drivers/input/touchscreen/max11801_ts.ko'): No space left on device
E: /var/cache/apt/archives/linux-headers-3.2.0-72_3.2.0-72.107_all.deb: unable to create `/usr/src/linux-headers-3.2.0-72/arch/m32r/include/asm/futex.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-72/arch/m32r/include/asm/futex.h'): No space left on device
E: /var/cache/apt/archives/linux-headers-3.2.0-72-generic-pae_3.2.0-72.107_i386.deb: unable to create `/usr/src/linux-headers-3.2.0-72-generic-pae/include/config/input/adxl34x/i2c.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-72-generic-pae/include/config/input/adxl34x/i2c.h'): No space left on device
E: /var/cache/apt/archives/linux-headers-3.2.0-72-generic_3.2.0-72.107_i386.deb: error creating directory `./usr/src/linux-headers-3.2.0-72-generic/include/config/input/gpio/rotary': No space left on device

Message is no space on device, so I removed some of the old kernels

Anyway I then checked the space on my disk ,df -h 
and there is 6 GB available now, this should be enough for a 130 mb download, right?

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   12G  6.0G  67% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           297M  832K  296M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  152K  1.5G   1% /run/shm
/dev/sda6       891G  803G   43G  95% /home

Nothing happened so I then checked my disk on errors, sudo touch/forcefsck
but fsck did not find any errors.
Removing seems to be impossible too because of dependencies..

Anyone ideas how to proceed? :confused:

---

### Post by Bashing-om on 2014-11-27
adrigmaill Hi !

Here is the tell tale thing:
[quote]
E: /var/cache/apt/archives/linux-headers-3.2.0-72-generic_3.2.0-72.107_i386.deb: error creating directory `./usr/src/linux-headers-3.2.0-72-generic/include/config/input/gpio/rotary': [color=red]No space left on device[/color]
[quote]

Likely the root partition is full; checks:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes .

If it turns out that the /boot partition is full from old kernels, will require removing those old kernels. ( within the package management system we hope !).

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by adrigmail on 2014-11-28
Hej, thx for the reply!

You are a wonderful help!!

still some files in /usr/src had to be removed, and no not the clean way, it wasn't possible that way but a guy here
[http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition]("http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition")
wrote how to proceed if you can't use apt to clean up due to a 100% full /boot, he only didn't mention /usr/src.

---

### Post by ibjsb4 on 2014-11-28
That link looks good, but I prefer the official documentation.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users)

The last command (in Advanced users) has worked for me.  This will remove all but the latest kernel.

---

### Post by Bashing-om on 2014-11-28
adrigmail; Great !

As all is good, and the situation is under control;

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

