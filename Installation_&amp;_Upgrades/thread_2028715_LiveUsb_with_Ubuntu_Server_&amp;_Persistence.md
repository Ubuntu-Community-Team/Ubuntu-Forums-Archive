---
title: "LiveUsb with Ubuntu Server &amp; Persistence"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by Jahragon on 2012-07-18
Is there any way to get ubuntu 12.04 server or even any server edition of ubuntu to run from usb with persistence. 

My objective to is to create a bunch of these usblive usb's with ubuntu server and run them from numerous pcs which dont have hardrives, with persistence, but i have tried everything and can not find a solution, any help or guidance is greatly appreciated.

---

### Post by Paddy Landau on 2012-07-19
What an unusual request. I'd love to know why you need this.

You have not specified what problem you are getting. Have you tried using Startup Disk Creator with the ISO? If so, what happened? What else did you attempt and what were the results?

The only solution I can think of (without knowing any more) is to create a normal Live USB with persistence. Uninstall what you don't need. Install LAMP and anything else you need for a server.

---

### Post by efflandt on 2012-07-19
I haven't used the server install, but if it is for installing only like the alternate iso, your best bet would be to have large enough USB to do a regular server installation to it, probably using ext2 and some other tricks like tmpfs for /tmp and noatime option for mounting flash partitions to minimize write cycles.

One issue with a live/install iso is that anyone who boots it can do most anything without any login, so it is not very secure.  Another issue is that you cannot change certain things that happen during boot, like kernel version and video drivers that are loaded from a fixed squashfs file system before persistent data is mounted.  If you wanted to change things like that, you would need to remaster the iso yourself before using it to make bootable iso on USB.

---

