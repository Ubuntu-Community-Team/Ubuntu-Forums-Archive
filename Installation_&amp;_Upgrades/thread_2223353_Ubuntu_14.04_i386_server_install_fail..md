---
title: "Ubuntu 14.04 i386 server install fail."
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by Kevin_Ruhl on 2014-05-10
Hi all, when I want to install the Ubuntu 14.04 server version for i386. When I've set the keyboard layout, it's going to initialize the disk etc. But before the point that there should pop-up a network configuration window, the screen stays at an purple color..

The screen is not freezed, when I try to type something, there appear characters in a grey bar at the bottom. I can also open a command line with CTRL + ALT + F2.
The point is, after 2 hours or so, I get the following error message:
> [!!] Lead debconf preconfiguration fileFailed to retrieve the preconfiguration file
The file needed for preconfiguration could not be retrieved from file:///cdrom/preseed/ubuntu-server.seed. The installation will proceed in non-automated mode.

If I press continue, I can skip this step, but it won't make it any better, because I get a purple screen again..

How am I going to solve this?

Thanks in advance,
Kevin Ruhl.

---

### Post by ibjsb4 on 2014-05-12
It sounds like you need to comment (#) out CDRom in your sources.list

Take a look

```
cat /etc/apt/sources.list
```

---

