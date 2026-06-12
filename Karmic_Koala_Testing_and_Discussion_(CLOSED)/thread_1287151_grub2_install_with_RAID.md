---
title: "grub2 install with RAID"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iandotcom on 2009-10-09
Hey,

Finally managed to get an install going of karmic on my computer. I get the error which I expected which shows grub2 unable to be installed, from the RAID configuration that I use. Any idea on how to complete the installation and install grub2?

Thanks, Ian.

---

### Post by ranch hand on 2009-10-09
I don't but there may be something in the links on this post;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by ranch hand on 2009-10-09
I, personally, can't stand raid.  That said, I hope you get this figured out.

A search for grub2 and raid may turn something up besides what is in those links.

Please post the buggers so that those of us that put up links can do that.

Please mark this thread as "Solved" when you get it done.

Thanks

---

### Post by 0xff on 2009-10-21
ave

I installed grub2 on usbdrive on other computer, and cerate grub.cfg like that by hand:

```

timeout=3

menuitem "U" {
root (hd0,5)
linux /vmlinuz root=/dev/mapper/myraid_VOL05 ro 
initrd /initrd.img
}

```

where hd0,5 is my /boot partition on raid volume in grub.
You can check your drive configuration in grub command line by **ls**.
In bios set first boot form usb storage. This is temporary solution but working fine.
I partly based on [this how to](http://www.panticz.de/MultiBootUSB).

---

### Post by psyke83 on 2009-10-21
Issues with GRUB2 and RAID configurations are mentioned [Known Issues]("http://www.ubuntu.com/testing/karmic/beta#Known%20issues") of the release notes.
> 
If a RAID partitioning scheme is used during installation the grub boot loader will only be installed on the first hard drive instead of all the drives. Booting the system if the first drive has failed will not work. As a workaround users can manually install grub to each disk in the array using the grub-install command ([427048]("https://bugs.launchpad.net/bugs/427048")). 

---

### Post by 0xff on 2009-10-21
> **psyke83 said:**
> Issues with GRUB2 and RAID configurations are mentioned [Known Issues]("http://www.ubuntu.com/testing/karmic/beta#Known%20issues") of the release notes.

With this issuse in one small problem - it,s not for raid0.

---

