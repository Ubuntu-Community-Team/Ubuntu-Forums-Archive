---
title: "grub timeout not working on 10.10"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by p4trykx on 2011-02-16
I have a very strange problem with Grub. After installation of 10.10 on my laptop grub immediately boots the default kernel on it's list, despite that I have 10s delay defined in config files. Of course I did 
```
sudo upgrade-grub
```
after modifications. Grub just flashes for a moment and starts to boot the first kernel on the list. 
However if I boot from Ubuntu DVD and choose "boot from hard disk" grub shows the list and waits those 10s. The same is with Windows boot cd. So I'm sure that modifications of config file affect grub.

So it seems that maybe grub thinks that there is some keypressed?

My laptop is a Compal dl70. It's about 5 years old Pentium M. Previously to 10.10 grub was working fine. 
Grub version is 
```
grub-mkconfig (GRUB) 1.98+20100804-5ubuntu3.1
```

This is my /etc/default/grub
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="

```

---

