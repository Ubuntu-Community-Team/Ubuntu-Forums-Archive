---
title: "Server cannot discover wireless networks"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by j.e.s.s.e on 2011-05-26
I installed Ubuntu 11.04 Desktop and can access the internet through a linksys router with WPA2. I then installed Ubuntu server in the free space left on the disk, but the installation network autoconfiguration failed. I can boot either OS, but the server's DHCP client cannot discover any networks (there are several in the area).

Any ideas why, or any idea's on how to fix this? Thanks.

PS... I'm new with linux.

---

### Post by Joe of loath on 2011-05-26
To connect to a WPA accesss point in a CLI distro, you'll need to use wpa_supplicant.

Check man wpa_supplicant, and man wpa_supplicant.conf for more info on how to do it with your setup.

Also, you are aware that Ubuntu server and Ubuntu desktop are virtually identical? Server just doesn't have a GUI, and has some extra packages included on the CD.

---

### Post by deconstrained on 2011-05-26
Have a Droid phone? Android uses WPA supplicant and you can use it to generate a configuration file for you.

Set it up with the wifi and password, and the conf file will be at /data/misc/wifi/wpa_supplicant.conf, which you can copy out using adb.

---

### Post by j.e.s.s.e on 2011-05-26
Thanks, Joe.

I installed wpasupplicant_0.6.10-2_i386.deb by downloading it on another pc and mounting a usb in the server. Running

```
sudo /etc/inti.d/networking restart
```
gives me errors like
```
failed to stat component /etc/network/if-post-down.d/wpasupplicant: No such file or directory
```
/etc/network/if-post-down.d/wpasupplicant is a broken symbolic link. Do you know why? Do I need to install more than the deb file above?

---

