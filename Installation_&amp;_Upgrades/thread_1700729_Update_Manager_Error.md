---
title: "Update Manager Error"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by anton_s59 on 2011-03-05
Hi,
I am getting an error of "The Package System Is Broken" in the Package Manager. I started with one error and was able to overcome it by forcing the installation. But now I have another error that I am unable to force, or remove, or purge with dpkg commands. The error is:
~$ sudo apt-get remove xserver-xorg-video-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-all
0 upgraded, 0 newly installed, 1 to remove and 22 not upgraded.
30 not fully installed or removed.
After this operation, 24.6kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7984:
' not allowed (only letters, digits and characters `-+._'))
E: Sub-process /usr/bin/dpkg returned an error code (2)

I cannot overcome this error. Does anyone have a suggestion?
I am relatively new to Linux and Ubuntu. This is the first issue I have not been able to resolve.
Thanks

---

### Post by runeh76 on 2011-03-05
Hi

try: ```
sudo dpkg --configure -a
```

---

### Post by anton_s59 on 2011-03-06
Ok. I tried that, but got same message:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 7984:
' not allowed (only letters, digits and characters `-+._'))

---

### Post by Timmer1240 on 2011-03-06
You May have to go into that file as administrator and edit out that part of it.

---

