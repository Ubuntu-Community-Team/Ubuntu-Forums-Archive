---
title: "Installation on Server w/o physical access"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by fbreuer on 2006-06-01
Hello!

I would like to install Ubuntu 6.06 (Server) on a rented server I do not have physical access to. That means I cannot insert floppys, cds, usbsticks, etc. and I cannot set up a DHCP server to do net-boot. Moreover I can only communicate with the server via SSH.

What I can do is boot into a minimal Linux rescue system (SuSE), SSH into that one and download/partition/install stuff on the harddisk from there.

What is the best way to install Ubuntu 6.06 (Server) in this case?

Thanks,
Felix

---

### Post by ubuntu_demon on 2006-06-01
So the server runs SuSe ? It would have been easier if it ran debian or Ubuntu :).

I hope this helps :
[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

---

### Post by fbreuer on 2006-06-22
I have checked all the Installation Guides on the wiki and none seems to be suitable. All require me to have a special DHCP server running on the network or to insert a CD/Floppy/etc.

The rescue system installed on the server is Debian, though, albeit a minimal one! How would a minimal Debian help?

The most natural solution IMO would be to simply extract an image of an Ubuntu-installation onto the harddisk using the rescue system and then configure it via SSH. 
[LIST]
[*] In this scenario, are there any pitfalls I should be aware of? 
[*] Is there some way to configure Ubuntu elegantly from the shell? 
[*] Is there some curses-version of the installer?
[/LIST]

---

