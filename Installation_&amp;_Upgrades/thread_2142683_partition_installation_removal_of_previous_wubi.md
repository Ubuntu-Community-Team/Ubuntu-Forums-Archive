---
title: "partition installation removal of previous wubi"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by kyloth on 2013-05-06
my friend asked me to put linux on her windows 7 asus. i proceeded to download and install with the wubi.exe installer from the website. i allocated her 26.5 gb of space for it and let it run. after using it for a week, we received a gpu internal error dealing with xorg-xserver-video-intel . so in return i ran apt-get to update and install the new version of xserver-xorg-core. the 26gb wubi.exe installed partition refused to boot after this happened.we would choose it on the boot list, it would start to load then the screen would go black, we would press the power button and it would shut down.not a hard shutdown, it showed the ubuntu logo and loading screen on shutdown.  could not even access the terminals or a login page of any kind. on a seperate computer i downloaded a 12.4 amd64 bit iso and created a usb bootable disk. the disk did not recognize the existence of the wubi partition already existing. i allocated her a 92.5 gb partition leaving windows 7 almost 180gb of space to work in. she asked for a bigger linux partition. now that we have decided to take this route, how would i go about removing the wubi partition previously created, because i can access the windows partition and a different linux partition for the removal process. i have never had to remove a partition of an os that did not come from a boot disk, so i have never removed a partition without a boot disk before. please halp!

---

### Post by bcbc on 2013-05-06
Wubi uses a virtual partition (a file). To remove a Wubi install, boot Windows, go to the *Control Panel*, *Add or remove a  program* and look for the *Ubuntu* entry (double click to remove)

---

### Post by kyloth on 2013-05-06
thank you very much, i was also wondering now that i know i can simply do it this way. is there any way to obtain the files from my wubi partition and move them via flash drive to my new 92gb installation

---

### Post by fantab on 2013-05-06
You can infact migrate your WUBI install to a separate partition, follow the links:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

However, I suggest you do a fresh install. 
What files exactly do you want to move? Or were you thinking on the lines of migration?

---

### Post by bcbc on 2013-05-06
Yes. You just mount the partition that houses the root.disk. Then loop mount the root.disk. 

e.g. if the root.disk is on /dev/sda3
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

Then you can run nautilus to get at your data:
```
nautilus /mnt/home
```

When you're done:
```
sudo umount /mnt
sudo umount /media/win
sudo rmdir /media/win
```

---

### Post by bcbc on 2013-05-06
You can also get readonly access to a root.disk from windows using [ext2read]("http://sourceforge.net/projects/ext2read/files/")

---

