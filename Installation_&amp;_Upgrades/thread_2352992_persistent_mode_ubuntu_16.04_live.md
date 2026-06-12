---
title: "persistent mode ubuntu 16.04 live"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by miro.ilia on 2017-02-17
Hi all, I unpack ubuntu 16.04 iso on my external HDD with GPT (made in Gparted - because of asus UEFI:() - everything is fine, but I can't create working persistent storage... I've tried to create the second partition (at the same external HDD in addition to ubuntu partition) with Ext2 (labeled casper-rw) and type "persistent" after "quiet splash" in grub menu before booting, then tried to change grub by using "sudo gedit /etc/default/grub" and "sudo update-grub" with needed parameters, but nothing help - after restarting my data and options become default. What I do wrong? 
I can't use any automatical programs, because they don't create live iso  in GPT, any others partition tables are not workong with my asus UEFI  (and I can't find "legacy bios" mode).
Can someone explain how to mount casper-rw or whatever i should do to solve my problem - I want to have live OS on my external HDD with persistent mode permanently and without typing every time "persistent" parameter while loading.

I'm beginner, please be patient =)

---

### Post by ubfan1 on 2017-02-18
Are you sure you don't want to do a regular full install to your USB disk?  That would be the normal way to install Ubuntu.  The ISO should be burnt as an image to a DVD or USB, no presistence needed, and then used to boot, to try Ubuntu and/or to install to the USB disk.

---

### Post by miro.ilia on 2017-02-18
> **ubfan1 said:**
> Are you sure you don't want to do a regular full install to your USB disk?  That would be the normal way to install Ubuntu.  The ISO should be burnt as an image to a DVD or USB, no presistence needed, and then used to boot, to try Ubuntu and/or to install to the USB disk.

no way, I've installed Ubuntu on my external HHD - everything was fine till I unplug my HDD... after that when I again plug HDD and click on ubuntu loader in UEFI menu my windows 10 loader has crashed, so I reinstalled windows 10... I find that there are no problems between win 10 and Ubuntu (when you use it on external HDD) if you use live ubuntu, but it has some inconveniences (that I've mentioned)

---

### Post by sudodus on 2017-02-18
I would recommend that you use the tool ***mkusb*** to create a persistent live drive with Ubuntu in your external USB HDD. When I had a new 4 TB HDD, I tested installing Ubuntu into that drive with mkusb, and it could use the whole drive because it uses GPT (by default).

You get the option to select how much of the drive to use for persistence (in percent), a linux ext file sysem with the label 'casper-rw'. The rest of the drive will be used as an NTFS partition with the label 'usb-data'. There will also be scripts for easy backup and restore of the casper-rw partition.

See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[mkUSB-quick-start-manual.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

---

### Post by C.S.Cameron on 2017-02-18
+1 for mkusb.
For your method try editing /boot/grub.cfg while booted from another medium, not the boot USB.

---

### Post by miro.ilia on 2017-02-23
> **C.S.Cameron said:**
> +1 for mkusb.
For your method try editing /boot/grub.cfg while booted from another medium, not the boot USB.

Tried a few days to install ubuntu on external HDD with mkusb - failed, when starting it shows: failed to load hd 0,4, error 0x410f4cc0: 4101a420, I've scanned HDD with gparted and it shows smth like this: [https://i.stack.imgur.com/aioNY.png](https://i.stack.imgur.com/aioNY.png) - I suppose I better use your advice =)
Please, can you describe what should I change in grub.cfg - I've read that it enought to add Ext4 partition with label casper-rw and install live-usb OS on the same HDD, then type "persistent" after "quite splash" in grub.cfg, am I right?

---

### Post by sudodus on 2017-02-23
***mkusb*** should work directly. You should not [have to] change anything in grub.cfg. See this link

[mkUSB-quick-start-manual.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

Creating a system in an internal drive is illustrated with the two screenshots of this post. The internal drive is a Kingston SSD with 60 GB. The first screenshot shows the output when mkusb has finished creating a persistent live drive, and the second screenhot was made, when booted into the new persistent live system in the internal drive. Some commands were run to illustrate, that it is really running in this Kingston SSD with 60 GB.

The same thing will happen if the SSD or a HDD is connected internally or externally via USB2, USB3 or eSATA.

[hr][/hr]
Your screenshot shows a 4 GB drive. The size makes me think that it is a USB pendrive. But it looks correct in principle.

There might be a problem, if you boot with two persistent live drives by mkusb connected, because the bootloader uses the same partition numbers, and the order that the drives are found cannot be controlled. So for example hd(0,4) can be in the internal or external drive, and hd(1,4) will be the other one. This causes confusion, and the system will not boot correctly.

- Did you try to boot from the internal drive, after removing the USB boot drive?

***Please post a screenshot of the partitions in your internal drive***, or if you find it easier, post the output of the following command lines.

```
df
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by ubfan1 on 2017-02-23
If you can accept the 4G limit of a persistent file, you can specify a "persistent-path=/X" to identify a directory containing the persistent file.  This works fine for running multiple disk-based live systems with different persistent files, but as mentioned, I have never found any way to specify the disk, the directory "/X" will be found on some FAT partition automatically.

---

### Post by miro.ilia on 2017-02-23
> **sudodus said:**
> There might be a problem, if you boot with two persistent live drives by mkusb connected, because the bootloader uses the same partition numbers, and the order that the drives are found cannot be controlled. So for example hd(0,4) can be in the internal or external drive, and hd(1,4) will be the other one. This causes confusion, and the system will not boot correctly.

Genius! Seriously! I ejected the second live-usb and my external HDD start working immediately, thanks a lot! Everything work correctly (include persistent mode). 
solved =)

One more question: did my settings and programs save when I create new user (with administrator permissions) on my live-usb OS?

---

### Post by sudodus on 2017-02-23
I *think* 'everything' is saved, including settings and programs, also the settings that define a new user. But there might be some limits to what you can do with such a user in a persistent live system.

I suggest that you try, and let us know how it works :-)

---

### Post by C.S.Cameron on 2017-02-23
> **miro.ilia said:**
> I've read that it enought to add Ext4 partition with label casper-rw and install live-usb OS on the same HDD, then type "persistent" after "quite splash" in grub.cfg, am I right?

Correct, however persistent partitions do not seem to be working on the same drive with installs made using SDC, UNetbootin, Rufus, Universal, etc. They do work with grub2 type installs such as made with mkusb.

My experience with creating a new user in a persistent install is that it becomes difficult to shutdown Ubuntu. 

[http://askubuntu.com/questions/582675/shutdown-persistent-usb-install](http://askubuntu.com/questions/582675/shutdown-persistent-usb-install)

---

