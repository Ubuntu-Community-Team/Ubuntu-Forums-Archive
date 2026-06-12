---
title: "Ubuntu as independent Operating System"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by Mazraq on 2012-10-23
Hi there,

I'm formatting my computer and I really don't want to download Windows again! Can I just install Ubuntu 12.10 independently or do I need to have Windows installed first? 

If I can download Ubuntu independently, how I can create a bootable USB stick to load it from?

Thanks a lot for your help.

Best,
Moe

---

### Post by darkod on 2012-10-23
Ubuntu has nothing to do with windows or any other OS. It's not a requirement to have a dual boot, most people still have windows because they need it for some programs, etc.

If you have ubuntu right now, it's best to prepare the usb stick now, before you format the hdd. First format the stick as FAT32.
Then download the ISO of the ubuntu version you want to use, if you don't have one already.

After that, in ubuntu open Start Up Disk Creator, select the ISO you want to use and the usb stick destination. That will create a bootable usb stick that you can use to run live mode or install.

---

### Post by Mazraq on 2012-10-23
Thanks Darkod so much! Really appreciate it!

---

### Post by Mark Phelps on 2012-10-23
If you go to pendrivelinux.com, they have a Universal USB Installer that you can use to create the USB stick.  I've used this multiple times, in fact, I used it yesterday to create an install USB stick for 12.10, and it works great.

---

### Post by Mazraq on 2012-10-24
Thanks a lot Mark, I downloaded the USB installer from this site, but then it asked me to browse my Ubuntu image "desktop*.iso file, which I downloaded from here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) it's the amd64 one. The USB installer however could not find it however, even though it is in my document! Any help?

---

### Post by Mark Phelps on 2012-10-24
When presented with the first choice of distros, go to the bottom of the list and choose that one -- as 12.10 is not actually in the list yet.

You can then browse to the folder containing the ISO file and select that. All you do is select the file, you don't actually open it.

If that doesn't work, I don't know what to tell you because I did the same thing and it worked for me.

---

### Post by darkod on 2012-10-24
You can also try creating the usb with unetbootin (you can download it for free, search on google).

Or, if you do have ubuntu right now (any version), as I said earlier, best to use Start Up Disk Creator.

And make sure the stick is fat32 formatted in any case, regardless if you are creating it on windows or ubuntu.

In unetbootin select the option to create it from ISO (not to select the distro in the drop down menu at the top), and at the bottom of the window make sure the correct letter for the stick is selected in windows.

---

