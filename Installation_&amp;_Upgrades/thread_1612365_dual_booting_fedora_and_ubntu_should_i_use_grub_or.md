---
title: "dual booting fedora and ubntu should i use grub or grub2?"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by sreek_arc on 2010-11-03
Hi,
I am using my computer with fedora 12 installed. Now i want to dual boot his computer with ubuntu 10.04. Now my idea is that i will install grub2 of ubuntu into its own boot menu and use the fedora legacy grub by chainloading ubuntu. Now my question is that is this the best option?
Or i install grub2 of ubuntu into MBR and do osprobe and find fedora 12?
I am familiar with grub legacy. But i never tried grub2. So i want to get some suggestions regardng this.
:)
Thank You

---

### Post by Rubi1200 on 2010-11-04
Hi and welcome to the forums :)

In my opinion, GRUB2 is the way of the future. Although it may seem complicated at first, I find it to be very flexible and customizable.

If Fedora is already installed, go ahead and install Ubuntu and allow it to install its bootloader to the MBR. Then, run ```
sudo update-grub 
```in Ubuntu to pick up the Fedora install.

There is a wealth of information available, much of it written by members of the Ubuntu community.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by wilee-nilee on 2010-11-04
Personally I always upgrade to grub2 on any platform that will allow it. I suspect that fedora will upgrade to it, if it was me I would do this then install Ubuntu.

Upgrading grub is not tricky but you have to do all the correct commands in the correct order at the correct time, which includes rebooting and running a final command.

Rubi1200 is correct though and your own contention that theoretically grub-legacy should chainload, personally I wouldn't risk it though when grub2 is a far better bootloader at least for my use. I think it is a matter of personal preference here.

---

### Post by stlsaint on 2010-11-04
I agree with Rubi about letting ubuntu install grub2 to the MBR. IF for some strange reason after you run ```
sudo update-grub
``` that grub does not see fedora than you can then run:
```
sudo os-prober
``` to find the fedora install.

---

