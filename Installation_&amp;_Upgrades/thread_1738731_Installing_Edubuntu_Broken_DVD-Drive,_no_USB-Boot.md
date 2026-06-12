---
title: "Installing Edubuntu: Broken DVD-Drive, no USB-Boot"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by JackAndBlues on 2011-04-25
Hey guys,

I would like to install Edubuntu 10.10 on this ancient Toshiba with Windows XP on it. The situation is a little complicated since I have no stable internet connection (I can not download Edubuntu once more). 

Now I realised that the DVD-Drive is broken and I can not boot from DVD to install Edubuntu. I have, however, an external USB-Drive, but there is no Boot-Option from USB (Phoenix Bios V. 1.3). So now I figured different options:


[LIST=1]
[*]I could update my PhoenixBios to have a USB-Boot-Support. But I don't know if that's possible, so I am asking for opinions.
[*]I sucessfully installed Ubuntu 10.10 with Wubi on the Laptop, but I wasn't able to install the packages for Edubuntu. Any time I put the DVD in my external USB-Drive and tried to mount with Synaptic I got the error message: "E: Could not mount CD-Rom". So I could install Ubuntu 10.10 with the CD, the Edubuntu-packages in addition with the DVD afterwards.
[*]Is there no way to install Edubuntu directly with Wubi?
[/LIST]

Would be great, if I could have help there.

JackAndBlues

---

### Post by JackAndBlues on 2011-04-26
bump

---

### Post by MundoMondo on 2011-04-26
Simplest would be to use unetbootin from sourceforge and extract the iso file of edubuntu to a USB stick. You could try to do it on an external HDD as well. If you don't have a working USB or CD / DVD drive, you're pretty much screwed i'm afraid.

---

### Post by adit on 2011-04-26
grub2 supports booting from iso files in hard drive. Put the edubuntu iso file in your hard disk and if you have grub2 installed you can boot from that iso file

---

### Post by JackAndBlues on 2011-04-26
> **adit said:**
> grub2 supports booting from iso files in hard drive. Put the edubuntu iso file in your hard disk and if you have grub2 installed you can boot from that iso file


Interesting, would this work with a Wubi-Installation of Ubuntu?

---

### Post by bcbc on 2011-04-26
You can't install Wubi from a DVD image - so that seems to rule out Edubuntu.

You should be able to mount the DVD from your hard drive and install packages from there... 
```
sudo mount -o loop /host/pathToIso/edubuntu.iso /mnt
``` 

But in order to get synaptic to recognize it, you might have to mount it to /dev/sr0 or something like that. Otherwise you'd be manually installing packages which would be a pain.

---

### Post by adit on 2011-04-27
> Interesting, would this work with a Wubi-Installation of Ubuntu?
From inside wubi it is impossible.  Grub2 should be in MBR for this to work.  First migrate your wubi installation to a dedicated partition by following these instructions.
_[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)_
Before migration your boot sequence is:
Windows Bootloader(from MBR) -> Boot Menu -> Select either windows or ubuntu
After migration your boot sequence is:
Grub2 (from MBR) -> Boot Menu -> Select either windows or ubuntu

Now grub2 is in MBR.  Copy your edubuntu iso file to your hard drive.  Then boot it from grub2.

---

