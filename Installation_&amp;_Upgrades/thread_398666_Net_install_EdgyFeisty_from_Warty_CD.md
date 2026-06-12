---
title: "Net install Edgy/Feisty from Warty CD?"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by ortazel on 2007-04-01
I have an old laptop I'm trying to install Ubuntu on, and I have one of the official Ubuntu Warty installation CDs that were sent out ages ago. However, I don't have a CD burner so I can't just download the Edgy or Feisty isos and burn them to install from. Is there a way that I can do a net install from the Warty install CD? I already tried just installing Warty and upgrading it, but I ran into so many problems it wasn't worth it- dependency nightmares and loops all over the place :(

---

### Post by tkjacobsen on 2007-04-01
I dont know if you can use the warty cd's.

But if you have an >8.3mb usb stick you can try with this netboot image: (link for feisty)
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/boot.img.gz)

First you gunzip it
```
gunzip boot.img.gz
```

Then insert usb stick (you will use all data).. Make sure it is not mounted, and find the device name (e.g. /dev/sda, you can use dmesg for that)
then just
```
sudo dd if=boot.img of=/dev/sda
```
assuming the device is /dev/sda.

NOTE: You will have to reformat your usb stick afterwards in order to use it as usual.. Usually usb sticks use the fat32 filesystem.

If that is not a possibility I would try to install only the minimal server / command line version from the warty cd's, then update (change in sources.list and dist-upgrade) and finally install ubuntu-desktop..

---

### Post by thelinuxguy on 2007-04-01
> **ortazel said:**
> I have an old laptop I'm trying to install Ubuntu on, and I have one of the official Ubuntu Warty installation CDs that were sent out ages ago. However, I don't have a CD burner so I can't just download the Edgy or Feisty isos and burn them to install from. Is there a way that I can do a net install from the Warty install CD? I already tried just installing Warty and upgrading it, but I ran into so many problems it wasn't worth it- dependency nightmares and loops all over the place :(

Here is another way:

I had a Dapper system and installed Edgy from the desktop ISO using a USB pen drive. Something similar could be done for Feisty though I do not have any personal experience with that.
My system, for some reason, wouldn't boot from USB. So the tutorials on making a bootable USB and installing from there didn't prove useful in my case. If you don't have such problems, you may try out one of those tutorials. An example for Breezy can be found at [http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html](http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html)

This is what I did:
[LIST]
[*]Copied the contents of the ISO to my pen drive
[*]Copied vmlinuz and initrd.gz from the casper folder in ISO to one of my ext3 partitions and made grub entries to boot from there
[*]Had my computer boot from this kernel and made sure that the cd-rom tray was empty and the USB stick containing Edgy ISO's contents was plugged in.
[*]The installation kernel detected the filesystem on my USB drive and I had Edgy Live-USB on my desktop. Rest of the installation is same as that from Live-CD.
[/LIST]
After installation, Edgy wrongly labeled my USB as cdrom. I just had to edit my fstab to correct this.

---

### Post by ortazel on 2007-04-01
This laptop is old enough that it won't boot from USB, and my pen drive isn't big enough to hold a whole ISO as thelinuxguy suggested (plus that sounds a little over my head) so I'm going to try upgrading from a server install. Thanks for the quick help.

---

### Post by ortazel on 2007-04-01
> **ortazel said:**
> This laptop is old enough that it won't boot from USB, and my pen drive isn't big enough to hold a whole ISO as thelinuxguy suggested (plus that sounds a little over my head) so I'm going to try upgrading from a server install. Thanks for the quick help.

Hm, I'm updating through all the versions, as instructed by the Ubuntu help pages, and for the upgrade from Breezy to Dapper it's saying that I *must* have ubuntu-desktop installed. I want to go up the upgrade tree all the way to Feisty, and it seems like the simplest way to do that would be to go as far as possible without the desktop installed.

edit- and now I'm trying to install ubuntu-desktop with the sources.list given here ([https://help.ubuntu.com/community/BreezyUpgradeNotes](https://help.ubuntu.com/community/BreezyUpgradeNotes)) and it can't find the package :confused:

---

### Post by thelinuxguy on 2007-04-01
> **ortazel said:**
> This laptop is old enough that it won't boot from USB, and my pen drive isn't big enough to hold a whole ISO as thelinuxguy suggested (plus that sounds a little over my head) so I'm going to try upgrading from a server install. Thanks for the quick help.

Oh! I realise that my description was very abstract and unclear. Some more detail could have helped. Anyways, do make a post about how you got it running.

---

### Post by ortazel on 2007-04-01
> **thelinuxguy said:**
> Oh! I realise that my description was very abstract and unclear. Some more detail could have helped. Anyways, do make a post about how you got it running.

I got Hoary up and running, went through the steps to upgrade to Breezy (but it still listed it as Hoary in the startup prompt :confused: ), was forced to install gnome-desktop for the upgrade to Dapper and that's where it all went pear shaped. X wasn't recognizing my monitor's h-sync/v-refresh properties right, so the desktop was unusable, and after editing xorg.conf to the settings that worked before on a Warty install that broke X completely, to the point where every time I rebooted it was spitting out tons of errors and package dependency loops. 
Then I found the WinXP CD that I had thought I'd lost and gave up completely- XP installed with no problems whatsoever
It shouldn't be this hard :(

---

### Post by thelinuxguy on 2007-04-01
What about the netboot image for Feisty that tkjacobsen has provided a link to? Is that not an option in this case?

---

### Post by ortazel on 2007-04-01
> **thelinuxguy said:**
> What about the netboot image for Feisty that tkjacobsen has provided a link to? Is that not an option in this case?

I saw that, but the laptop is old enough that it won't boot from a USB pen drive... unless I'm mistaken then that method requires it (?)

---

### Post by tkjacobsen on 2007-04-02
> **ortazel said:**
> I saw that, but the laptop is old enough that it won't boot from a USB pen drive... unless I'm mistaken then that method requires it (?)

Unfurtunately you have to boot from the usb drive...

An alternate way could be to try the install.exe from windows.. Allthough this will not give a true installation.
[https://wiki.ubuntu.com/install.exe/](https://wiki.ubuntu.com/install.exe/)

---

### Post by MadMan2k on 2007-04-02
exactly your use-case:
[http://www.madman2k.net/article/1](http://www.madman2k.net/article/1)

you probably should not directly upgrade to feisty, but  go throught the previous versions first. (its just the base system, so it will be faster)

---

### Post by ortazel on 2007-04-03
> **MadMan2k said:**
> exactly your use-case:
[http://www.madman2k.net/article/1](http://www.madman2k.net/article/1)

you probably should not directly upgrade to feisty, but  go throught the previous versions first. (its just the base system, so it will be faster)

Thanks a lot- going through the key upgrade versions (warty -> breezy -> dapper -> edgy) worked perfectly. Edgy is a hell of a lot nicer than Warty too, this distro has made a lot of progress since I last played around with it :)

---

