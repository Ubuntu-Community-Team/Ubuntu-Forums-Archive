---
title: "install ubuntu alternate from usb drive /cdrom mount problem"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by bcn17 on 2008-06-16
I have been trying to install 8.04 alternate w/ a usb drive. 

I followed the instructions under the "manual" section here:
     [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This is what I did:

Use gparted to format 720 mb fat16 partition on usb thumb drive and set flags to boot

```
sudo aptitude install mtools syslinux
```

```
sudo fdisk -l
```
this tells me my usb thumb drive is /dev/sdb1

it is already automatically mounting to /media/disk-1

so I type:
[HTML]syslinux -s /dev/sdb1[/HTML]

the hidden file ldlinux.sys pops up on the usb drive just like its supposed to

I then right click the ubuntu 8.04 alternate .iso and extract contents to a folder on my harddrive. I then drag all contents (hidden also) to the thumb drive.

Next I rename the isolinux folder to syslinux and the isolinux.cfg file in the isolinux folder to syslinux.cfg

I am using syslinux Version: 2:3.53-1ubuntu2

I then take the usb drive and set the bios to boot to the usb drive on my moms computer. It boots up and I hit enter to install

Next after setting keyboard preference etc before it can load  information is says that the cdrom is not mounted (but it obviously can see it because I'm in the process of installing)

So I take note that on the tutorial page it had this:

> Mounting the USB stick as /cdrom

This step is only needed for the **Alternate install CD** and Ubuntu 6.10 or older.

Switch to the second virtual console during the first couple of dialogs (when asked about your preferred language for the installation etc.) by pressing the ""ALT-2"". Do the following:

    *

      mkdir /cdrom /dev/cdroms
    *

      cd /dev/cdroms
    *

      ln -s ../sda1 cdrom0 (where sda1 is your USB stick)
    *

      mount -t vfat /dev/cdroms/cdrom0 /cdrom

Then switch back to the first virtual console by pressing ""ALT-1"". Continue installing Ubuntu as if you were running from CD. 

On the first step it won't let me mkdir /cdrom /dev/cdroms because the directory /cdrom is already there. 

Furthermore If I just try and type: 
```
mount -t vfat /dev/sdb1 /cdrom
```

It gives an error. 

Keep in mind that the above steps after renaming the file/directory will make a usb drive that boots perfectly if I use the Live CD- I tested this on my computer, however on my mothers the alternate CD is going to be required. Any help  appreciated thanks!  

also, some thoughts- is there any command like sudo or way to force a mounting of a parition in the virtual console? I don't see why I can't just mount with ```
mount -t vfat /dev/sdb1 /cdrom
```

Thanks!

---

### Post by maybeway36 on 2008-06-17
For the mkdir line, try adding the -p option.
Also make sure that nothing is mounted on /cdrom.

---

### Post by bcn17 on 2008-06-17
Okay, I have managed to mount /dev/sdb1 to /cdrom in the console that you access via ALT + F2 during the alternate cd install. I can then type ```
cd /cdrom
ls -a
```

and see the entire contents of what was on my usb drive.

However, When I  hit ALT+F1 and and go back before I load preconfiguration files it says that the cdrom isn't there or that I should check the integrity of the cdrom. What should I do??? I'm thinking network install but I'm not sure it will boot to network. mini.iso doesnt work either...
Is there anyway to simply copy files to a partition and make it boot manually like I did with the usb drive?? Or does the install process examine hardware and in a way "customize" the install to a particular computer? Any help  or ideas appreciated!

---

### Post by jriggz on 2008-07-14
> **bcn17 said:**
> Is there anyway to simply copy files to a partition and make it boot manually like I did with the usb drive?? 

[http://ubuntuforums.org/showthread.php?t=766959]("http://ubuntuforums.org/showthread.php?t=766959")
[http://ubuntuforums.org/showthread.php?t=316093]("http://ubuntuforums.org/showthread.php?t=316093")

Those links might help you a bit with that.

---

### Post by jonijones on 2010-11-29
To finally give the right hint to any of you who get stranded in this thread, this worked for me:

First download the desired Ubuntu-alternate version from ubuntu.com

Use UNetbootin for either Linux or Windows:
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Select Ubuntu and the version you just downloaded but be sure to select the "...hd-media" part and start the UNetbootin installer.

Then copy the downloaded .iso file to the root-folder of the usb-stick and boot the desired device and voilà.

---

