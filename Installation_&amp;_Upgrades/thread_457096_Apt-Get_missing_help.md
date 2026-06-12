---
title: "Apt-Get missing help"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Borg on 2007-05-28
when I boot up I get a repair console saying apt-get is missing and I should run  

sudo apt-get install apt-get

but thats like asking a snake to eat itself. 

How can I get apt-get to reinstall ?

Thanks

---

### Post by taurus on 2007-05-28
Does these commands work from a terminal?

```
sudo aptitude update
sudo aptitude install apt-get
```

---

### Post by Borg on 2007-05-28
OK bigger problems now

I installed some upgrades that the system said where out, after the re start I can't get any desktop.

It says there are no NVidia driers there. It was working fine before these 'upgrades/updates'

I have ran sudo apt-get nvidia-glx and kernel-common and it says they are installed and up to date but nothing.

---

### Post by taurus on 2007-05-28
So you got apt-get back now.

Sounds like the latest updates screw up your X which means you need to reconfigure it again.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Borg on 2007-05-28
> **taurus said:**
> Does these commands work from a terminal?

```
sudo aptitude update
sudo aptitude install apt-get
```

returns

> Couldn't find any package matching "apt-get".  However, the following
packages contain "apt-get" in their description:
  newbiedoc gnome-apt xen-headers-2.6.19-4-generic 
  xen-headers-2.6.19-4-server adept-updater libcmdparse2-ruby1.8 aptitude 
  xen-headers-2.6.19-4 cron-apt debarchiver apt jablicator libcmdparse-ruby 
  posixtestsuite r-base libcmdparse2-ruby apt-build debdelta grep-dctrl 
  aptoncd auto-apt apt-move 
No packages will be installed, upgraded, or removed.


---

### Post by Borg on 2007-05-28
[QUOTE=taurus;2736244]So you got apt-get back now.

nope

---

