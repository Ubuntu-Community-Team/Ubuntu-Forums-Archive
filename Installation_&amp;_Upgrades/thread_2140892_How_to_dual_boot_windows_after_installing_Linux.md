---
title: "How to dual boot windows after installing Linux??"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Ragi1992 on 2013-05-01
I have Ubuntu 12.04, and I was hoping to completely wipe my hard drive of Ubuntu.

Well, seeing as how it seems like thats practically impossible without a live cd/dvd (Which I no longer i have) I was curious to know if I can dual boot instead.

Note:Using GParted the permissions keep me from formatting my hard drive or altering it in anyway at all. If there is a way around this please help me with that.

I really need windows on my computer (Virtual Machine will not work for what I want at all)

If the only way is to remove linux and only have windows I don't mind at all, just please help :(

---

### Post by claracc on 2013-05-01
If you have the installation windows disk and a license key for it, removing ubuntu and installing windows is easy, there is a lot of links addressing it in the web: [http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

---

### Post by Bucky Ball on 2013-05-01
Gparted will erase all partitions that you can unmount. You can't, of course, unmount the partition which is running Ubuntu because that's also running Gparted, if that makes sense. Why not just burn another LiveCD or just download and burn the Gparted ISO. Boot from either and all disks will be unmounted and you can kill the lot. 

Or ... just free up some space at the beginning of the disk, install Windows and dual-boot.

---

