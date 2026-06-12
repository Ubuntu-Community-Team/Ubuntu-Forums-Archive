---
title: "ThinkPad X23 + Xubuntu USB Installation"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by knightrous on 2007-11-04
Hi all,

I'm having a little trouble with getting Xubuntu put onto my X23 laptop. The X23 use to run windows xp until a nasty virus (first one I've had in close to 5 years, being use to Ubuntu for nearly 18months, I was a little lax on my AV) and I've had to format the hdd. I'd like to ditch windows and put Xubuntu 7.10 onto it. The problem lies in the fact that the X23 doesn't have a CD Rom. I have looked into some guides on doing an installation from my 2GB USB drive, but I've had no success.

First off, I tried the simple zcat method [HERE](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)
The files were loaded onto the usb drive, but it wouldn't boot off the USB drive, even after I forced it via bios, just gave me a plain jane "No Operation System" message...

Next I tried this one [HERE](https://help.ubuntu.com/community/Installation/FromUSBStick)
It says to use the alternate install image, the problem is that it asks to copy files from the 'casper' folder, but the alternate install doesn't have this folder, but the normal desktop installation does.... This confused me... I tried both images and failed. I did get it to boot with the desktop image, but it crashed saying that the ramdisk wasn't big enough. I found a line from  [HERE](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)
that said to modify the syslinux.cfg to have this in it: 
```
default vmlinuz
append initrd=initrd.gz ramdisk_size=12000 root=/dev/ram rw
```
But I don't know where to insert it, as there is a good 30-40 lines in the config file.

I also tried PXEboot, but the only network I have setup at the moment is at work and I can't just knock up a DHCP server with the 8 servers here at work plus 80+ desktop pc's running from the domain controllers DHCP...

If anyone could give a few more points or things to try, it would be appreciated

---

### Post by knightrous on 2007-11-06
I hate to bump this thread up, but I know there have been some similar threads with people posting with experience, unfortunately those threads didn't contain enough information for my situation, if anyone from those threads happen to read this, please post something to push me into the right way of fixing this issue.

Thanks in advance!

---

### Post by knightrous on 2008-01-25
Alright, since no one was able to provide me with an answer, I'll provide one back :-)

I eventually found that someone had update the USB install guide on the Community Docs.
```

wget http://www.startx.ro/sugar/isotostick.sh
chmod 755 isotostick.sh
sudo ./isotostick.sh ubuntu-7.10-desktop-i386.iso  /dev/sdb4

```

That helped me, you can find the rest of the guide here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

