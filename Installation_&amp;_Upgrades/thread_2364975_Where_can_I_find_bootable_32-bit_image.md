---
title: "Where can I find bootable 32-bit image"
date: 2017-06-30
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2017-06-30
Hello,

Trying to create bootable USB with 32bit Ubuntu (using Rufus tool), I get the following message:

[IMG]https://s10.postimg.org/7ovd8onbt/bootable_ubuntu_error.jpg[/IMG]

The 32-bit image I've downloaded from here:
[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

BTW, with the 64-bit images bootable USB is created successfully ... but USB isn't seen in my 32-bit notebook
Where is a problem ?

Thanks in advance.

Pavel.

---

### Post by Michael_McKenney on 2017-06-30
[http://cdimage.ubuntu.com/netboot/16.04/?_ga=2.193435693.1452294873.1498741196-1508202544.1498741196](http://cdimage.ubuntu.com/netboot/16.04/?_ga=2.193435693.1452294873.1498741196-1508202544.1498741196)

[i386]("http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/installer-i386/current/images/netboot/") - For 32-bit Intel/AMD (x86)

---

### Post by py-ohayo on 2017-06-30
Thanks,

I've just tried with this one (43Mb).
[IMG]https://s11.postimg.org/x1spt08pv/bootable_ubuntu_image.jpg[/IMG]
The USB bootable is created successfully in Rufus tool, but when I try to boot from this bootable USB on my targret PC, the USB isn't seen.

---

### Post by py-ohayo on 2017-06-30
I've changed Partition Scheme in Rufus and then could use 32-bit .iso file

---

### Post by oldos2er on 2017-06-30
What is the make and model of your notebook? 

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555)

---

### Post by py-ohayo on 2017-06-30
HP mini. There is another issue that appeared while I've tried to install Ubuntu.
After launching installation ... it starts and fails at certain point with the following error:
The installer encountered an error copying files to the hard disk:
[Errno 30] Read-only system: '/target/usr/share/keyutils/request-key-debug.sh'

Here I should mention that before this attempt of installing Ubuntu this PC had Windows 7 with 2 logical disks: System about 60Gb and Data about 2 times bigger.
This PC fell down 3 days ago and System disk with Windows became corrupted.
I succeed to recover data from Data logical drive, hoping the during installing Ubuntu corrupted sectors will be managed and system will be installed correctly.
Apparently, this HDD drive should be processed with some special tool before installing Ubuntu ?

Thanks in advance for any suggestions.

---

### Post by oldos2er on 2017-06-30
Found [this]("http://blog.room34.com/archives/5260"), can't attest to whether it works or not as I've never owned or used an HP computer.

You will need the 64 bit version of Ubuntu.

---

### Post by johndough2 on 2017-07-03
> **py-ohayo said:**
> HP mini. There is another issue that appeared while I've tried to install Ubuntu.
After launching installation ... it starts and fails at certain point with the following error:
The installer encountered an error copying files to the hard disk:
[Errno 30] Read-only system: '/target/usr/share/keyutils/request-key-debug.sh'

Here I should mention that before this attempt of installing Ubuntu this PC had Windows 7 with 2 logical disks: System about 60Gb and Data about 2 times bigger.
This PC fell down 3 days ago and System disk with Windows became corrupted.
I succeed to recover data from Data logical drive, hoping the during installing Ubuntu corrupted sectors will be managed and system will be installed correctly.
Apparently, this HDD drive should be processed with some special tool before installing Ubuntu ?

Thanks in advance for any suggestions.


Hi

I would look to a LIVE version of something from the Debian stable, Ubuntu, Mint or KNOPPIX.

Check thru your partitions with Gparted to see that all are healthy.  Move / Backup sensitive data and consider a new partition layout to accommodate Ubuntu.

The disk layout might be helpful, along with details of as make/model of hardware.

The 32 bit issue is secondary to your HDD partition concerns.

If in doubt please ask.

---

### Post by johndough2 on 2017-07-03
> **oldos2er said:**
> 

 as I've never owned or used an HP computer.



[FONT=Comic Sans MS]It's an experience I can assure you.[/FONT]

But HP has a lot of compatible kit for Linux usage, and I expect that factor to be useful in this case.

---

