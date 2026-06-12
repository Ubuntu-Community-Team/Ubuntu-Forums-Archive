---
title: "GRUB noapic argument HELP! :D"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by Acer8888 on 2013-01-05
Hello i am having a problem getting the noapic argument to work automatically on each boot. 

I have a virtual ubuntu 12.04 server running on Server 2012 Hyper-V. When i attempt to shutdown the server i get a black screen and hyper-v says the guest is still running. 

I was troubleshooting the issue and i tried adding noapic to the linux line in grub, and it WORKS!! yay!

So i tried to edit /etc/default/grub; i added noapic to GRUB_CMDLINE_LINUX="noapic" ; This caused ubuntu to no longer boot it comes up with and says something like it cannot find the /dev/mapper or something of that sort (im trying to remember from memory, the server cannot be shutdown right now)

I next removed noapic from 
GRUB_CMDLINE_LINUX="" and added it to 
GRUB_CMDLINE_LINUX_DEFAULT="noapic" ; but same results, ubuntu fails to boot.


So to recap when i manually enter noapic each time the server boots the server will shutdown correctly. When i attempt to add the noapic command to the grub.cfg it fails.

What am i doing wrong? Thank you in advanced for the help!

---

### Post by dino99 on 2013-01-05
enter like this (remove quiet splash)

```
GRUB_CMDLINE_LINUX_DEFAULT= noapic
```

then to make it permanent:

```
sudo update-grub
```

---

### Post by Acer8888 on 2013-01-05
when I put noapic without quotes, like so 
 
GRUB_CMDLINE_LINUX_DEFAULT= noapic
 
I get the following error when I try to do sudo update-grub
 
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: noapic: not found

---

