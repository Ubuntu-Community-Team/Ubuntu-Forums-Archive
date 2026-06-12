---
title: "Is it the instillation?"
date: 2012-12-18
forum: Installation &amp; Upgrades
---

### Post by qojont on 2012-12-18
Several weeks ago I decided to try Linux , so I downloaded Ubuntu. It was working fine at first, I was downloading some editors, compilers, etc. Nothing was wrong with the instillation (I downloaded it dual boot), out of nowhere after booting up Ubuntu it took me to some GRUB thing and everything was ****** up so I tried typing in several commands to get the GUI started up but nothing worked, so I just uninstalled it. Now, 2 days ago I decided to try it once more and like last time it was all fine until I tried to start it up and it takes me to some purple screen and it says something like "error hard drive loop0" and my caps button light keeps switching on and off, when this happened I cant turn my computer off and I have to wait for the battery to die while it stayed in this loop( my laptop doesn't have an external battery). I can't think of any reason why it keeps crashing, maybe its because I switch from windows to Ubuntu so much because I have to program for robotics through windows.
Someone pleas help me.

---

### Post by qojont on 2012-12-18
bump?

---

### Post by offgridguy on 2012-12-18
Can you force shutdown by holding the power button?
Some more info about you computer, how you have it setup regarding 
installation would be helpful.:)

---

### Post by churchy d on 2012-12-18
The cycling caps lock light sounds like a kernel panic to me.  My first thought would be that maybe you moved hardware around, but unlikely since its a laptop.  

You might want to try booting off a livecd and running fsck on the linux partitions on your hard drive, but there isnt much we can suggest without knowing more about your setup.

---

### Post by qojont on 2012-12-18
No, I can't force shutdown. I set it up normally I guess, went to the site, downloaded for windows the dual boot option and that was it. I think it keeps getting screwed because i switch from windows to ubuntu so often but that's just my guess.

---

### Post by oldfred on 2012-12-18
So this is probably a wubi install, which is not a true dual boot a way to test drive Ubuntu using the Windows boot loader and  a file inside the NTFS partition.

You will need to create a liveCD/DVD/flash version that boots Ubuntu so you can make repairs.

You may need to run chkdsk on your Windows partition first.

       [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by Bucky Ball on 2012-12-18
*Thread moved to **Installation & Upgrades***

If you have a Wubi install, it is not a dual-boot. It is Ubuntu installed inside Windows, both on one partition, as oldfred suggests. Dual-boot = Ubuntu and Windows side-by-side on separate partitions.

---

### Post by qojont on 2012-12-18
Oh, ok, well how can I get a legit dual boot? Will it fit in a 16GB usb flash drive?
Never mind, just noticed the second half of your post lol.

---

### Post by qojont on 2012-12-18
I'm doing the dual boot thing with Unebootin and there's something im not quite sure about it lets me select space used to preserve files across reboots (Ubuntu only) I have 1TB btw

---

### Post by oldfred on 2012-12-18
Unetbootin is for installing to the flash drive, usually 2GB but your can use larger. This is a live installer, so you can boot and test that it works with your system and if everything seems ok then you click on install. 

Make sure you have backed up all your data before installing any new system.

Then you use flash drive to install to your hard drive.

What are current partitions on hard drive. If you have Windows use Windows to shrink the Windows partition, but not to create any partitions as it may convert to dynamic which does not work with Linux.

       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

