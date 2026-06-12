---
title: "LiveUSB"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-09-27
I have looked around, and noticed that you can make a LiveUSB with many distros. 
My question is can i make a LiveUSB that would allow me to update, and install some programs i use onto the LiveUSB which would keep all the programs and setting from boot to boot. The reason for this is to mostly show others what you can do, but to also have some of the common programs i use alot, and to make installing easier, i have looked at UNetBootin, but all it did was make it just like a liveCD so that it couldn't update, or install any programs that it would keep on the drive.

I know it shortens the life span of the USB.

---

### Post by Pumalite on 2008-09-27
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by Huss on 2008-09-27
Yep, I'm using a live USB. The new (hardy) Xorg makes it much easier to jump between monitors and graphics cards

---

### Post by melenor on 2008-09-27
does it have persistent storage?

---

### Post by snowpine on 2008-09-27
There are 2 types of USB drive install.

One is to install to the USB drive just like it is a normal hard drive. This is just like a normal installation; you can install applications, update packages, save your settings for next time you log in. Disadvantage is it occupies a lot of drive space (I want to say almost 4gb for Ubuntu), is slower than a hard drive install, and will reduce the lifespan of your flash device.

The other way is a LiveUSB install consisting of a compressed system ISO and a /home folder. The system is uncompressed at boot time, just like a Live CD. By default, you lose any downloaded packages/applications when you reboot, just like a Live CD. However, many distros have a "persistent" feature that writes downloaded packages  to the USB, effectively "remastering" your system. SliTaz is a good example (using the TazUSB utility). Advantage of Live USB over full USB install is LiveUSB uses much less drive space (700mb vs 4gb for Ubuntu, for example) and reduces wear and tear on your flash device. Disadvantage is that it can be slightly harder to set up and trouble shoot than a full install.

The thread Pumalite linked to is an excellent source of info.

---

### Post by melenor on 2008-09-27
I am looking to set up the thread one that you talked about, the one that has the LiveUSB with persistent storage

---

