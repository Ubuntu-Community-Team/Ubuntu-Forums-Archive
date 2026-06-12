---
title: "/var/lib/dpkg/available-old is corrupted"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by FreshP on 2009-11-27
Hi,
i am new to ubuntu forums and ubuntu in general.

Whenever i try to install a package i get the following error
```

dpkg: failed to link `/var/lib/dpkg/available' to `/var/lib/dpkg/available-old' for backup of available info: Input/output error

```I went to this directory did ls -la and i get
```

-rw-r--r--  1 root root       0 2009-11-27 14:42 available-new
-?????????  ? ?    ?          ?                ? available-old

```among other results.

I dont know what caused this problem, it happened about a week ago. Now whenver install something i get an error and the installation is not completed.
Any help?

---

### Post by sisco311 on 2009-11-27
Hi and welcome to the forums!

available-old is a backup file and it  seems that it's corrupted. Remane/Remove it an see if the error persists:
```
sudo mv  /var/lib/dpkg/available-old /var/lib/dpkg/available-old-bad
sudo apt-get update
```

---

### Post by FreshP on 2009-11-27
Thanks for answering.
I already tried to move it or delete it, i cant

```

mv: cannot stat `/var/lib/dpkg/available-old': Input/output error

```
Actually i cant do anything with this file, i tried cat, rm, mv, it doesnt even show using gnome, only from terminal it is shown.

---

### Post by sisco311 on 2009-11-27
> **FreshP said:**
> Thanks for answering.
I already tried to move it or delete it, i cant

```

mv: cannot stat `/var/lib/dpkg/available-old': Input/output error

```
Actually i cant do anything with this file, i tried cat, rm, mv, it doesnt even show using gnome, only from terminal it is shown.

Check the partition for errors:
```
sudo tune2fs -C 40 /dev/sdXY
```
and reboot. (NOTE: that's an uppercase c in the command option)

replace /dev/sdXY with the actual partition.

run 
```
mount
```in a  terminal to get a list of mounted devices.

i.e. my root ("/") partition is /dev/sda1:
```
mount
**/dev/sda1** on / type ext3 (rw,relatime,errors=remount-ro)
...
```

---

### Post by FreshP on 2009-11-27
I should mention that i am running ubuntu9.10 from a usb so when i do mount i get

```

aufs on / type aufs (rw)
.......

```

so i am not sure what to use to check for tune2fs

---

### Post by FreshP on 2009-11-28
I guess I will have to reinstall? No solution yet

---

### Post by FreshP on 2009-11-28
I did reinstall Ubuntu finally, i just hope it doesn't happen again. Thanks to everyone who answered.

---

