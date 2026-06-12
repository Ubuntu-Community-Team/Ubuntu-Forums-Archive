---
title: "Installing XP alongside Ubuntu"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by judith_sw on 2009-11-22
Hi,

Just curious ... I am happily running / exploring Ubuntu 9.10 as the sole OS on my HP 2133. My home PC runs XP, and I was wondering how easy it is to install XP alongside Ubuntu, given that instructions tend to refer to people installing Ubuntu in addition to pre-installed XP. Also, as this XP disk already has its product key linked to my PC, how easy / expensive is it to purchase another key to make this version legit?

I'm not determined to do this, but am interested in the possibility - how much disk space would I need. The 2133 has a 120GB HD.

Thanks!

---

### Post by darkod on 2009-11-22
You are already using Ubuntu so you know how much space it has used. For how much space you dedicate to XP it all depends what do you need it for, whether any space consuming software is gonna be installed, etc.

The procedure would be to use Ubuntu liveCD booted with the option Try Ubuntu, unmount all of the ubuntu partitions in case some are mount (swap seems to be mounted automatically), and shrink the partition to make unpartitioned space for XP. It's probably better to shrink it that way so the free space remains on the back of the drive.

Depending how many partitions you have for ubuntu, you need to make a PRIMARY partition for XP. Install it there, and restore grub2 on the MBR after that because it will get erased by the windows installation.

---

### Post by The Thug on 2009-11-22
You could also install XP within Virtual Box on your HP.

---

### Post by lmarmisa on 2009-11-22
If you want to explore and learn how to run other operating systems in your HP machine (XP or others), I would recommend you a virtualization type solution. I like [http://www.virtualbox.org](http://www.virtualbox.org)

If you use VirtualBox, you can define as many virtual machines as you want running inside your Ubuntu system. Each virtual machine simulates an independent computer (with disk, screen, network, etc), running the operating system that you want: XP, Ubuntu, etc. 

Virtual machines have virtual disks (standard files of Ubuntu). Therefore do not have to worry about defining new partitions on the physical disk of the host computer where the virtual machines run.

It works great.


Best regards,

Luis

---

### Post by judith_sw on 2009-11-22
I've downloaded and installed, but cannot find it. Do I need to go to the terminal?

---

### Post by judith_sw on 2009-11-22
Found it!

---

### Post by lmarmisa on 2009-11-22
These are my recommendations:


[LIST]
[*]You need a XP CD (or better an ISO image of this CD) and the serial key.
[/LIST]

[LIST]
[*]20 Gbytes could be a good size for a XP virtual hard disk.
[/LIST]

[LIST]
[*]Base memory: 250-350 Mbytes
[/LIST]

[LIST]
[*]Use dinamically expanded storage (this virtual disk  initially occupies  a very small amount of space in the physical hard disk).
[/LIST]

[LIST]
[*]Define a folder for virtual hard disks and another folder for ISO images. If you have several partitions, use home partition or that with a greatest free storage for those folders.
[/LIST]

[LIST]
[*]Select Bridged Adapter mode in the network interface.
[/LIST]

[LIST]
[*]Install GuestAdditions. This is a virtual iso cd. Install these drivers  that provide the perfect integration of the mouse and the screen with Gnome.
[/LIST]
Best regards,

Luis

---

