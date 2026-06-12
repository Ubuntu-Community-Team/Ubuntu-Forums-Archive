---
title: "FULL instalation on partitioned USB HDD"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by groovy354 on 2010-08-04
How to install FULL (not liveCD-like) Ubuntu on one of usb hdd's partition (leaving other partitions as they are) and make it bootable?

---

### Post by oldfred on 2010-08-04
As long as your system lets you boot USB devices, it is just another install. Just be sure to use the advanced button on the last partition screen to install grub2 to the external drive's MBR. Because of USB speed limits it will not run quite as fast but it works well for most.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by cazo on 2010-08-04
> **oldfred said:**
> As long as your system lets you boot USB devices, it is just another install. Just be sure to use the advanced button on the last partition screen to install grub2 to the external drive's MBR. Because of USB speed limits it will not run quite as fast but it works well for most.

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

You'll need a bootable pen drive; make one from an ISO, or booting from CD-LIVE, go menu System->Administration->Create Bootable Disk.

---

### Post by -kg- on 2010-08-04
The [PenDriveLinux site]("http://www.pendrivelinux.com/") has a wealth of information (and tools) on the subject.

---

### Post by groovy354 on 2010-08-04
So it's better to use "Create bootable disc" or normal install? Note it's _partitioned_ usb HDD and I want to use it on multiple PCs

---

### Post by snowpine on 2010-08-04
> **groovy354 said:**
> So it's better to use "Create bootable disc" or normal install? Note it's _partitioned_ usb HDD and I want to use it on multiple PCs

OldFred's post #2 is correct if you want to do a full install. 

The USB method (usb-creator) with persistence is probably a better choice if you want Ubuntu to be fully portable from computer to computer, as it is basically the same as running a Live CD (plus persistence).

---

### Post by oldfred on 2010-08-04
Just as a test I did a full install to a 16GB flash with gpt. It booted just fine in my portable with intel & desktop with nvidia. Often the biggest issue is video drivers. Either set to use older configuration (X.org) for video or be ready to add parameters to grub's kernal line to get it to boot.

Someone knew what drivers and did this:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by groovy354 on 2010-08-06
I used the "Create Bootable Disk" method, now how to get rid of that "Install" screen on startup?

---

