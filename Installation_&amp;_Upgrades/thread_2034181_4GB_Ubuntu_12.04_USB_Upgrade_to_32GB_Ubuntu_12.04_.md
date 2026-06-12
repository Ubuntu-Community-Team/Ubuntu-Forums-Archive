---
title: "4GB Ubuntu 12.04 USB Upgrade to 32GB Ubuntu 12.04 USB"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by RaveJ on 2012-07-28
So I have a 4GB Ubuntu 12.04 USB. Works great, but I want to install it onto a 32gb USB Flash Drive, to increase the memory space I have to save things to. How can I do this? 

I tried making an .img from the 4gb USB, on a 8GB USB, but it installed the .img and only left 414mb disk space to use, and left 3.9GB UNALLOCATED to use and dont know how to get it recovered to use again.

Any help is appreciated.

---I dont want to install to my Hard Drive, just USB to USB.

---

### Post by oldfred on 2012-07-28
How do you have 12.04 installed to a 4GB flash? It says full installs need 4.5GB so is this the installer with persistence?

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With a 32GB flash you can do a full install. I have a full install in a 8GB partition on my 16GB flash, mostly for testing. A little slow loading and writing, but once applications are loaded runs just fine with a fair amount of RAM.

---

### Post by RaveJ on 2012-07-30
I did not put it on the USB. I got it from a friend.
I would assume from my research that it is the persistance once you speak of.

My problem is when I install it to the 32GB USB, it leaves unallocated space that I cant use. Think maybe I need to partition the 32GB over and start over.

Memory is not a problem. 16GB of RAM i think is good enough for it :)

---

### Post by C.S.Cameron on 2012-07-30
If you wish to stay with persistent install, you can create ext2 partitions on the drive and name them casper-rw and home-rw.
Casper-rw will save programs etc and home-rw will save settings etc. 
Home-rw is optional and stuff will be saved to casper-rw if it does not exist. Home-rw can be reused with future releases.
If you need to copy your existing casper-rw file to the casper-rw partition let me know.

Size of these partitions is only limited by the size of the disk.

The FAT32 partition Ubuntu is on can also be used for storing and transporting files.
It can be accessed, (when booting the usb), by going to filesystem/cdrom.

---

