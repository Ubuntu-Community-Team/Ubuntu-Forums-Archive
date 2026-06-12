---
title: "Preseed value for installing Grub on Ubuntu 14.04 unattended"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by phikapjames on 2014-04-29
I had posted this in ask ubuntu with no luck, so I'm going to try here (sorry about two mediums).  I'm running into issues installing grub using the preseed on an unattended installation. This has worked for us on 12.04 and 13.10 though. We currently have the two lines in the preseed file in regards to grub:

```
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
```

The problem is, while watching the failed installs through the serial console, we are hitting a section in the grub installation portion that shows:

```

  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; [!!] Install the GRUB boot loader on a hard disk &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474;                                                                         
  &#9474; You need to make the newly installed system bootable, by installing     
  &#9474; the GRUB boot loader on a bootable device. The usual way to do this     
  &#9474; is to install GRUB on the master boot record of your first hard         
  &#9474; drive. If you prefer, you can install GRUB elsewhere on the drive, or   
  &#9474; to another drive, or even to a floppy.                                  
  &#9474;                                                                         
  &#9474; The device should be specified as a device in /dev. Below are some      
  &#9474; examples:                                                               
  &#9474;  - "/dev/sda" will install GRUB to the master boot record of your       
  &#9474; first                                                                   
  &#9474;    hard drive;                                                          
  &#9474;  - "/dev/sda2" will use the second partition of your first hard         
  &#9474; drive;                                                                  
  &#9474;                                                                         
  &#9474; _____________________________________________________________________   
  &#9474;                                                                         
  &#9474;     <Go Back>                                            <Continue>     
  &#9474;                                                                         
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

Notice that this screen came up and that it doesn't even have a device path specified yet. In our case we can type in /dev/sda and it will work. If we don't type it in and just hit continue, the installation will proceed just fine, but after the reboot it does not have the correct grub2 bootloader installed.

I tried doing d-i grub-installer/bootdev  string (hd0,0) with no luck already.

So, any idea what we should put into the preseed to tell it to install grub on the first MBR?

---

### Post by sire1 on 2014-06-04
This helped me: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1012629/comments/5](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1012629/comments/5)

---

