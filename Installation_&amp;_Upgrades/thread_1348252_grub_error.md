---
title: "grub error"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by knit.manish on 2009-12-07
hiiii
  can anyone tell me that is there any change in ubuntu karmic to recover ubuntu after installing windows. I was trying to recover karmic after installing window 7. but after booting ubuntu form live cd when i used the command ***sudo grub ***terminal it returned error ***sudo: grub: command not found. ***
Am i using the wrong command or my method is wrong?? and then what is the correct procedure to recover it then??
  Thanks in advance.:p

---

### Post by ubhi on 2009-12-07
first boot from ubuntu live cd then mount your existing ubuntu partition in ubuntu live cd then recover your grub according the steps give in that web page.. i am 100% sure this works for you.


just follow the mentioned document step by step,


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Castrato on 2009-12-07
> **knit.manish said:**
> hiiii
  can anyone tell me that is there any change in ubuntu karmic to recover ubuntu after installing windows. I was trying to recover karmic after installing window 7. but after booting ubuntu form live cd when i used the command ***sudo grub ***terminal it returned error ***sudo: grub: command not found. ***
Am i using the wrong command or my method is wrong?? and then what is the correct procedure to recover it then??
  Thanks in advance.:p


You can install grub from the LiveCD by:
sudo apt-get install grub

But you may want to read through here first:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And here:
[http://ubuntuforums.org/showthread.php?t=1329887](http://ubuntuforums.org/showthread.php?t=1329887)

---

### Post by Herman on 2009-12-07
> can anyone tell me that is there any change in ubuntu karmic to recover ubuntu after installing windows. I was trying to recover karmic after installing window 7. but after booting ubuntu form live cd when i used the command ***sudo grub ***terminal it returned error ***sudo: grub: command not found. ***Am i using the wrong command or my method is wrong?? You are trying to use the old traditional method for restoring the older version of GRUB, (GRUB 'Legacy'), but it won't work now because Karmic Koala has a completely new version of GRUB, called GRUB 1.97. Not all of the same commands will work anymore. There are new ways to do most things now.
> and then what is the correct procedure to recover it then??Try again to install GRUB 2 to MBR using your Ubuntu Karmic Koala 'Desktop' Live/Install CD using the following procedure.

**1. Boot with your Karmic Koala Live CD** and then [mount]("http://members.iinet.net.au/%7Eherman546/p10.html#Click-Icon_Mounting") your hard disk installed Ubuntu operating system. 

**2. Determine the name of the mount point**
Take a look around in /media to see what the name of the mount point is or use a terminal command to find out,
```
ls /media 
```

**3. Set a file system label (optional)**
 If all you can see is a big long file system UUID number, you should unmount it.
Open GParted, right-click on the partition and choose 'label', and set a nice user friendly name for the file system which you will find easier to type and remember. For example I simply call mine KARMIC. T
Mount it again so your mount point name will now be changed to your new user friendly file system label.

**4. Re-install GRUB to MBR**,
```
 sudo grub-setup -d /media/KARMIC/boot/grub /dev/sda 
```Where /media/KARMIC is the mount point for your Ubuntu file system, otherwise it could be some other name of your own choice (whatever you set as a LABEL), or a UUID number. Be sure to replace this with whatever is appropriate for your computer.
[COLOR=Red]**CAUTION:**[/COLOR] Do not make a mistake and install GRUB to any Windows boot sector, which will be a partition number, commonly /dev/sda1. If you want to install GRUB to a partition (boot sector) instead of to a hard disk, (MBR) you need to check which partitions are which first ! It's your own resposibility.

**If things go wrong**
If it complains about not being able to open /boot/grub/device.map, you might need to specify the path to the device.map file with the -m option, as follows,```
sudo grub-setup -d /media/KARMIC/boot/grub -m /media/KARMIC/boot/grub/device.map /dev/sda 
```If your computer has more than one disk you might need to change the '/dev/sda' part of the command to /dev/sdb or something else, but most often /dev/sda will be the first hard disk.

---

