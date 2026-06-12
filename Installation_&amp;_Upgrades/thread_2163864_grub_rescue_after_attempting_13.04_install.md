---
title: "grub rescue after attempting 13.04 install"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by Zeophlite on 2013-07-19
I have a machine that triple boots Windows, Snow Leopard and Ubuntu.  I recently tried to upgrade Ubuntu from 12.04 to 12.10, but that ended up breaking my Ubuntu installation.  I have a backup of the data from the Ubuntu partition that I wanted to keep, and I decided I wanted to install a fresh 13.04 into the Ubuntu partition.  I downloaded the 13.04 ISO (md5 was correct), and created a live USB with LiLi, but when I went to install 13.04, I got this error:


```

[Errno 5] Input/output error


This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may 
help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD 
drive lens (cleaning kits are often available from electronics suppliers), to check 
whether the hard disk is old and in need of replacement, or to move the system to a 
cooler environment.

```


Now when I reboot, I get the grub rescue prompt.


I have downloaded the boot-repair-disk ISO, and created a boot-info here [http://paste.ubuntu.com/5892726/](http://paste.ubuntu.com/5892726/)
When I try to run boot-repair, I get this error:

```

Please enable a repository containing the [linux] packages in the software sources of Ubuntu 13.04 (sda6). Then try again.
Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 13.04 (sda6). Then try again.

```


I just want to wipe sda6, install 13.04 to it correctly, and have the GRUB2 menu show all my OSs.

---

### Post by sudodus on 2013-07-20
Why did you start upgrading to new versions? Was something broken, or is there some new feature, that you really want? Or was it simply that you are eager to get a new version of Ubuntu?

1. If Ubuntu 12.04 was actually working well enough, I suggest that you reinstall that version. There might be compatibility issues between the hardware of your computer and the newer versions of Ubuntu.

2. But if you really need a new version, I suggest that you try some other tool to make the USB install drive. See this link.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

