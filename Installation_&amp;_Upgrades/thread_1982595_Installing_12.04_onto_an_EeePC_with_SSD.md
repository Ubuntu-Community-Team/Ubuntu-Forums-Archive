---
title: "Installing 12.04 onto an EeePC with SSD"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by mheartwood on 2012-05-18
I ran into 2 problems trying to upgrade from 10.04 Netbook Remix to 12.04LTS. 

First, I got a warning telling me that I need at least 4.4GB of HD space to load Ubuntu 12.04 desktop. The SSD in the EeePC 701 is 4GB, so it's not big enough. Without cracking the case, no real way to fix that.

Second, the warning screen was taller than the 480 pixel height on the 701. So I had to quit without installing 12.04.

I guess I'm going to be sticking with 10.04 for awhile.

I know that netbooks are not as popular any more, but some of us still use them. The 701 is my back-up netbook in case my primary netbook falls down a set of stairs or something. But the largest SSD on any of my netbooks is 4GB. The 901 has 2 such drives, one for / and one for /var and /home and Ubuntu 12.04 refuses to install because the primary SSD isn't big enough.

---

### Post by Old_Grey_Wolf on 2012-05-19
On my 701, I put an 8 GB SD card in the card slot. I used the 4 GB SSD drive for other purposes.

---

### Post by JRV on 2012-05-19
This worked for 11.10. 

Get the netboot disk. Available here:

[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

Install a command line system.
Reboot and log in.

Run these commands:
```

sudo apt-get update
sudo apt-get install lightdm xorg xinit ubuntu-desktop

```

You will then have to go in and trim the fat.

---

### Post by gilgeg on 2012-05-22
> **mheartwood said:**
> I ran into 2 problems trying to upgrade from 10.04 Netbook Remix to 12.04LTS. 

First, I got a warning telling me that I need at least 4.4GB of HD space to load Ubuntu 12.04 desktop. The SSD in the EeePC 701 is 4GB, so it's not big enough. Without cracking the case, no real way to fix that.

Second, the warning screen was taller than the 480 pixel height on the 701. So I had to quit without installing 12.04.

I guess I'm going to be sticking with 10.04 for awhile.

I know that netbooks are not as popular any more, but some of us still use them. The 701 is my back-up netbook in case my primary netbook falls down a set of stairs or something. But the largest SSD on any of my netbooks is 4GB. The 901 has 2 such drives, one for / and one for /var and /home and Ubuntu 12.04 refuses to install because the primary SSD isn't big enough.

I have upgraded my EEEPC 701 4GB from UBUNTU 11.04-desktop-i386 to LUBUNTU 12.04 using an USB stick made from lubuntu-12.04-alternate-i386 by the Universal-USB-Installer-1.8.9.6.
I did this because that non-pae netbook is not supportet anymore in UBUNTU 12.04.

The installation was straigt forward, no problems with space, but I had a problem with the wifi access.
It was so slow that I couldn't get access with The Chronium browser supplied, so I changed it with the Firefox browser, but still it takes minutes to use Google.

When I use the wired LAN I get instant access to allmost all web-adresses,
so it must be the wifi driver or the setup of the wifi connection that is the problem.

Does anyone have the same problem or even better have a solution for the problem ?

---

### Post by maestrobwh1 on 2012-08-17
I just used the regular iso, put in an 8 GB SSD so the installer saw I had enough space, chose the internal ssd for my target drive, and chose no swap space.  It worked as well.  

I used a ppa for ramzswap to have compressed swap in memory.

[https://launchpad.net/~shnatsel/+archive/zram/](https://launchpad.net/~shnatsel/+archive/zram/)

I actually use this package on all my systems, even those with a regular HD, and I don't use physical swap.  I NEVER have run into a crash.  Memory is faster than a drive.

---

### Post by pearce_jj on 2013-02-20
Appreciate this is old, but for the benefit of the search perhaps, the actual disk space requirements are much less as the installer includes a 'fudge factor'.

Without swap and using btrfs transparent compression, 4GB SSD is fine for 12.04 or 12.10, for example with eeePC 701, 4G and others.

Google "eeepc 4g ubuntu 12.10" for more info :)

---

