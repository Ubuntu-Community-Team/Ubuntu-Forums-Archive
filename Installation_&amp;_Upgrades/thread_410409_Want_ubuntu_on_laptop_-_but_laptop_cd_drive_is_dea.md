---
title: "Want ubuntu on laptop - but laptop cd drive is dead."
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Cloop on 2007-04-15
Title explains a lot, I'm a noob and I dont know how to get it to install any other way... the only other medium apart from the internal harddrive that I can boot from is an sd card reader, and usb and flash drives arent listed in the boot menu apparently.  Is it possible to boot ubuntu from my windows hard drive? Or some other way I dont know...

Thanks in advance,

Cloop

---

### Post by Tsen on 2007-04-15
There's the Ubuntu Windows installer, which you can find [here.]("https://wiki.ubuntu.com/install.exe/Prototype")  That's still in testing, and I've never tried it so I can't vouch for its stability, but it WOULD work for your situation.

I'd recommend just getting the CD drive fixed, though, if possible.  It's a very, very nice thing to have in working condition. ;)

---

### Post by Cloop on 2007-04-15
I've installed with the method you said and everything seems to be working fine, apart from one thing,.

Its left me with windows XP also installed.
This means on boot I select between ubuntu and XP and when I go onto ubuntu there is a host thingy on the desktop, with all the XP and old crap.  How do I get rid of it?  Also Im on NTFS, I Dont know what that really means but I thought linux uses its own better thing..

Another Adittion: Why is the space in my Home limited to around 700mb? How do I Expand that? Im very confused - please help!

Thanks again,

Cloop

---

### Post by TheTinman on 2007-04-15
> **Cloop said:**
> 
Another Adittion: Why is the space in my Home limited to around 700mb? How do I Expand that? Im very confused - please help!


I'm not sure what you mean by this part.  Are you talking about your Ubuntu Home folder?

---

### Post by Cloop on 2007-04-15
Yes, I Was trying to copy some xp stuff over and it wouldnt fit, I think what it is is that xp has a huge partion and linux has a titchy one, I want to know how to get rid of xp so I Just have ubuntu

---

### Post by zvacet on 2007-04-15
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")
[https://wiki.ubuntu.com/InstallationUbuntuFromWindows?highlight=%28install%29]("https://wiki.ubuntu.com/InstallationUbuntuFromWindows?highlight=%28install%29")

---

### Post by Cloop on 2007-04-15
Sorry, I found neither of those wiki pages helpful in *removing* windows.  It just tells me how to install ubuntu and it would ask me to get rid of it, It didnt. At all. Nothing about partions even like in my desktop livecd install.

---

### Post by whfrazier on 2007-04-15
You can boot it with Grub, I have read it can boot windows too, but I havent used it for that myself. I did use XP to install grub and Ubuntu installer on a second hard drive then used the hard drive in a laptop with no CD.

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

WinGrub works good
[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

Hope that helps

---

### Post by Cloop on 2007-04-16
Grub is just a way of choosing between windows and ubuntu on boot isnt it?  I can already do that, what I want to do is get rid of all the windows crap and this "host" drive and just have ubuntu :(.

---

### Post by beniwtv on 2007-04-16
Firstly, we would need to know how you actual partitions are setup.

Open a terminal (Programs->Accessories->Terminal) and type in:


```
fdisk -l
```


Then, post the output here.

---

### Post by Cloop on 2007-04-16
root@ubuntu:/home/rob# fdisk -l

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4864    39070048+   7  HPFS/NTFS

---

### Post by beniwtv on 2007-04-16
Well, it *seems* like you only have one partition on that disk, which is 40GB big, and has the NTFS file system (Windows file system).

As it stands today, you can't easily install Linux on NTFS. So I would say this is your Windows partition (/dev/sdb1), and the HDD where Windows is installed is /dev/sdb.

This leads me to suspect another SATA device in your system (which should be /dev/sda), with perhaps Linux on it?

Now, go and install GParted (From Add/Remove programs or Synaptic). Open it, and you will see a list of HDD´s and their partitions.

We will need to find out where Linux is located, to don't delete it accidentally instead of Windows.

---

### Post by Cloop on 2007-04-16
i deleted everything in the host folder.. absent mindingly hoping that would make windows go away, instead after a restart the computer refused to boot.  Ive got no other means of getting anything to boot onto the comp, im going to have to buy a new cd drive.

Thanks to everyone who tryed to help,

Cloop

---

### Post by beniwtv on 2007-04-16
No problem, you're welcome.


When having a CD-Drive, installing Ubuntu is painlessly easy.

Have fun. :popcorn:

---

### Post by Cloop on 2007-04-16
Wait umm, I have an external HDD and a couple of external cd drives would any of that work?


Cloop

---

