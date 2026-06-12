---
title: "windows 10 ubuntu 17.10 dual boot gparted need professional help"
date: 2017-11-15
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2017-11-15
windows 10 ubuntu 17.10 dual boot gparted need professional help 
i installed ubuntu 17.10 on a dual boot system with win 10
this is what i got now on my grub menue
see attached png [ATTACH=CONFIG]277534[/ATTACH]
any gparted help in totally removing and reinstalling ubuntu 17.10
would be great

[ATTACH=CONFIG]277535[/ATTACH]

---

### Post by oldfred on 2017-11-15
If you run this command and you should see results like this. Or do you now have multiple copies of 30_os-prober file?
Or did you install along side multiple times?

```
fred@Z170N:~$ ls -l /etc/grub.d/
total 80
-rwxr-xr-x 1 root root  9791 Jan 13  2017 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Mar  1  2017 10_linux
-rwxr-xr-x 1 root root 11082 Jan 13  2017 20_linux_xen
-rw-r--r-- 1 root root  3353 Mar  6  2017 25_custom
-rwxr-xr-x 1 root root 11692 Jan 13  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Jan 13  2017 30_uefi-firmware
-rwxr-xr-x 1 root root  1534 Nov  9 11:19 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2017 41_custom
-rw-r--r-- 1 root root   483 Jan 13  2017 README

Post this:
sudo parted -l

```

---

### Post by jimbean on 2017-11-16
yeah i need professional help but im not professional
thanks fred
can i just boot a gparted usb stick, format everything in the  linux partition  and then reboot and install 17.10 again without blowing up win 10
or do you need the {sudo parted -l} info from the terminal

---

### Post by oldfred on 2017-11-16
To even be able to suggest fixes, we need more info.
Please run the parted command.

---

### Post by jimbean on 2017-11-19
thank`s fred again
but i was looking to do more to both systems win 10 and ubuntu 17.10 and 
alls well that ends well
or if if i broke it which i didn`t this time
it would of been great also
keep going forward

---

