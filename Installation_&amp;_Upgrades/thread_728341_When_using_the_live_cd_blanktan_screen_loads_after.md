---
title: "When using the live cd blank/tan screen loads after starting"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by miketowninc on 2008-03-18
Hello,

When I try the ubuntu live cd 6.10 and I select try and install ubuntu. It loads the ubuntu bar. Then it just shows the mouse and blank tan screen. I let it go for 15 mins and nothing happen. The cd is working very hard. 

My specs

Intel intergrated graphics
256 ram
Windows xp home


I think thats all you need.


Thanks!

---

### Post by bescritt on 2008-03-18
It seems like you don't have enough memory for Ubuntu to load properly.  There is a workaround, however. Format a flash drive as swap (or, if you don't already have a working GNU/Linux computer, have a friend do it), the leave the flash drive plugged in while the LiveCD loads.  It should be automatically mounted and used, givving Ubuntu a little more room to load itself into.
Alternatively, you could use a lighter distro like Xubuntu.

---

### Post by miketowninc on 2008-03-18
I quote from Ubuntu's website:

System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space. 


I have 256 of RAM. How can I install without having to go into the live session? Is the safemode option supposed to run in the terminal instead of a gui?

---

### Post by Pumalite on 2008-03-18
With your RAM, I recommend Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by bescritt on 2008-03-19
You could try the Ubuntu-7.10-alternate disk image as well.  From there, use the text-based installer.
If a disk with lower requirements still doesn't work, then we know for sure it's some other sort of problem, such as a BIOS bug

---

### Post by Pumalite on 2008-03-19
If you are determined to use Ubuntu 7.10, you could even boot a Live CD making a 500 MB /swap partition ahead of time. The reason I recommended Xubuntu is that it is a lighter Desktop and therefore faster in your system. Ubuntu would run like a turtle if you managed to install it.

---

### Post by miketowninc on 2008-04-20
> **Pumalite said:**
> If you are determined to use Ubuntu 7.10, you could even boot a Live CD making a 500 MB /swap partition ahead of time. The reason I recommended Xubuntu is that it is a lighter Desktop and therefore faster in your system. Ubuntu would run like a turtle if you managed to install it.

Thanks. I just decided to take my brothers RAM out and put  it in mine. After I installed it I removed it.The installed version of ubuntu works fine with the little RAM I have. 

Thanks Because I'm sure the Xubuntu Alternative would have worked!

---

### Post by Pumalite on 2008-04-20
Good for you!

---

