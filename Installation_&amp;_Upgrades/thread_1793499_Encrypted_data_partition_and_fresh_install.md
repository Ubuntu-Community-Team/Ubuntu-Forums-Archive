---
title: "Encrypted data partition and fresh install"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by Djalmahal on 2011-06-29
Hi,

I'm having a data and an OS partition, currently running 10.10. I would want to do a fresh install of 11.04 on the OS partition and keep the data partition. The problem is I can't find the key I was given at my last install for the encrypted partition and I assume with a fresh install the data partition would become unreadable.

So what can I do, is there a way to retrieve the key through a terminal command or so?

Thanks for your help
Andreas

---

### Post by Djalmahal on 2011-06-29
I know recovered the encryption key through a command, how do I use it on a fresh install, i.e. tell the new install to use this to unlock the /home partition?

---

### Post by smurphy_it on 2011-06-29
something similar:

```
- First up - boot from desktop liveCD and make sure you have an internet connection.
- Now you have to install some stuff thats not there in the liveCD. Pull up a terminal (Applications>Accessories>Terminal)
- type "sudo su" 
- type "apt-get install lvm2 cryptsetup
- type "mkdir /media/test"
- type "modprobe dm-crypt"
- type "cryptsetup luksOpen /dev/sda5 test"
(enter password... are you set up on sda3 or sda5? change as needed)
(you should get a command successful message... continue:)
- type "vgchange -ay" 
(this will reveal your volume group name)
- type "mount /dev/("volume group name")/home /media/test
- type "nautilus /media/test"
(and now your encrypted /home should open in a window.)

If all that works... manually mounting the partition... then its not the encrypted header or partition thats got a problem. So close it all up...
- close nautilus
- type "umount /media/test"
- type "cryptsetup luksClose /dev/sda5

```

[http://ubuntuforums.org/archive/index.php/t-868681.html](http://ubuntuforums.org/archive/index.php/t-868681.html)

---

### Post by Elfy on 2011-06-29
Thread closed. Please do not post duplicates, it dilutes community effort.

---

