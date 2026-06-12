---
title: "nvidia error during upgrade"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Jeffa on 2007-06-29
hello all, 

I was attempting to upgrade to fiesty when i encountered an error. the upgrade stopped and it ran a repair utility. When I rebooted, i had over 400 updates to install. When I tried installing them, all but two installed and i get this error:

```
E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev
```

any idea what caused this? I used the envy script for installing the nvidia drivers. Is this causing a problem? 

any help would be much appreciated. 


Thanks.

Update. I uninstalled Automatix, and everything seemed ok. Then i uninstalled Envy and it broke xorg. soooooooo, now i'm just trying to fix xorg. :-) 

anyone know how to recover xorg?

Update 2. 

I tried doing [this]("http://ubuntuforums.org/showthread.php?t=484989") but it didn't help. I tried booting into recovery mode, but i get the same error. *gulp*

I think i'm sinking fast!

Update 3. 

and now, i can't even get a command prompt. Looks like i'll be reformatting!

---

### Post by confused57 on 2007-06-29
You could try mounting your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

then you can edit your /etc/X11/xorg.conf...change the video driver to "vesa", with quotes...what sort of errors are you getting when you attempt to boot?

---

### Post by Jeffa on 2007-06-30
> **confused57 said:**
> You could try mounting your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

then you can edit your /etc/X11/xorg.conf...change the video driver to "vesa", with quotes...what sort of errors are you getting when you attempt to boot?

all of them. 

ok seriously. when i look at the details of the failure, it says:

(==)"/var/log/xorg.o.log", time sat jun blah blah blah
(==)using config file: "/etc/x11/xorg.conf"
(EE)failed to initialize glx extension compatible nvidia x driver not
(EE)xf860openserial: cannot open device /dev/gpmdata
no such file or directory


I tried what you mentioned above. I mounted the partition and took a look at the xorg.conf file. the vesa driver was listed. (but without quotes)

---

### Post by confused57 on 2007-06-30
> **Jeffa said:**
> all of them. 

ok seriously. when i look at the details of the failure, it says:

(==)"/var/log/xorg.o.log", time sat jun blah blah blah
(==)using config file: "/etc/x11/xorg.conf"
(EE)failed to initialize glx extension compatible nvidia x driver not
(EE)xf860openserial: cannot open device /dev/gpmdata
no such file or directory


I tried what you mentioned above. I mounted the partition and took a look at the xorg.conf file. the vesa driver was listed. (but without quotes)

Open your xorg.conf file again, scroll to the video device section...if  the driver is listed as "nvidia", change it to "nv" or "vesa"..."nv" would result in a better display on most Nvidia cards..."vesa" will not display as well, but definitely should work.

---

### Post by Jeffa on 2007-06-30
I tried "Vesa", "NV" and "Nvidia" to no avail. 

I decided to just reformat. I needed to upgrade anyway.

Thanks for the help though.

---

