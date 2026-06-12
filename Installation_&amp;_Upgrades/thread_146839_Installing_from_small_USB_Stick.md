---
title: "Installing from small USB Stick"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by mgc on 2006-03-19
Hi everyone! :)

I've been a user of Ubuntu for a while, and wanted to get it on my laptop to replace Slackware.  However, the problem with my laptop is that its CD drive is broken.

Right now, I have access to a 32MB and a 256MB usb stick.  

Based on this page: [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s03.html)
(section 4.3.1, not 4.3.2, as I don't have enough room to copy the ISO)
I think I can write a bootable ubuntu installer image, minus the packages, to my USB stick.

Now, I have a couple of questions about how exactly the installer files that are in that image work:

1) If there are no packages on the installation media (eg. my usb key), does the installer possess the ability to download the packages from the internet?

2) If I switch virtual terminals, am I able to get a command prompt?  My internet connection where I plan to install this is configured such that I need to ssh to a server and port forward outside in order to access the outside internet.

3) Can I configure the installer to use either a SOCKS proxy or an HTTP proxy of the form [http://username:password@localhost:port?](http://username:password@localhost:port?)  If neither is possible,
are all the packages located on a single server? (eg. [http://archive.ubuntu.com](http://archive.ubuntu.com), in which case I can just forward to archive.ubuntu.com and use [http://localhost](http://localhost) as my package repository :))

Thanks in advance for any help! :D

---

### Post by chuckyp on 2006-03-19
Here are directions for doing a net install from one of your other machines may be a faster option.

[https://wiki.ubuntu.com/Installation/Netboot?action=show&redirect=NetbootInstall](https://wiki.ubuntu.com/Installation/Netboot?action=show&redirect=NetbootInstall)

---

### Post by mgc on 2006-03-19
Thanks :)

However, doing a netboot and doing an install from a USB stick as described above in my post end up with, as far as I can tell, the exact same situation -- where an installer is present but none of the packages are.

Therefore, my original 3 questions still stand. EDIT: I guess the first one is answered since it seems that with a netboot install, packages *are* downloaded and installed over the internet.

Cheers!

---

### Post by mgc on 2006-03-20
For anyone that is reading this in the future:

1) Yes
2) Yes
3) Yes

<- impressed with Ubuntu installer :)

Cheers

---

