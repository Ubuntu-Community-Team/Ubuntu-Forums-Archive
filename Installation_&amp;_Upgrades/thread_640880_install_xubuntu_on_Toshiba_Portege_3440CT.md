---
title: "install xubuntu on Toshiba Portege 3440CT"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by find_the_key on 2007-12-14
Hi guys,

I want to install Xubuntu on Toshiba Portege Laptop 3440CT (500MHz, 192MB RAM, 6GB HD) from an USB Flash drive (1GB).

Which version (of XUbuntu) is suitable for this laptop? If I download the .iso file, can I install it from an USB drive and how can I do this? Now, I have installed Win XP. Also, I have the US Robotics USR5421 Wireless MAXg USB adaptor to connect the laptop to the internet through the router. Will it work with Xubuntu, or I have to install drivers for this? 

Thanks in advance :)

---

### Post by eternal-one on 2008-02-27
not sure if you can even boot from usb on this notebook, i want to do the same thing. lemme know if you find a solution:)

---

### Post by charlie763 on 2008-03-05
I'm in the same situation. I'm going to try using a PCMCIA card to boot across the network and do an install that way. Has there been any success from anyone else? I'm also considering removing the hard drive, attaching the hard drive to another computer, doing an OEM install on the hard drive, and placing it back in the Portege. Hopefully, one of these options will work.

---

### Post by Rayalix on 2008-06-15
Yes I've just done this on a 3440CT. By far the easiest way is to use UNetbootin, a small app that installs GRUB then reboots the machine and connects to an FTP site to download and install a distro of your choice. You can choose to install to a partition or format the entire hard drive.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

I selected Xubuntu 7.10 but it's still really slow on this machine, I think I should have probably chosen 6.06.

---

### Post by charlie763 on 2008-06-15
> **charlie763 said:**
> I'm also considering removing the hard drive, attaching the hard drive to another computer, doing an OEM install on the hard drive, and placing it back in the Portege.

This is what I did and it worked. The computer is slow and the RAM cannot be upgrade beyond what is already in it (64 or 96 MiB). The screen is pretty nice and I used it to read a PDF of Freakonomics.

---

