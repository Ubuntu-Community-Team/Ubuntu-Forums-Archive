---
title: "Help on apt-get error"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by cripperz on 2010-04-11
Hi All,

i am having this problem constantly ... cant seem to get it off even after doing apt-get upgrade and so on. I am using ubuntu 8.04 LTS. please help. i even did a dpkg-reconfigure and apt-get install -f ...doesnt work

> Errors were encountered while processing:
 samba-common
 smbfs
 freenx-media
 freenx
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by mac9416 on 2010-04-11
Hi there,

Could you post everything, including the command? Also, you might want to try an apt-get update (which updates lists of available packages) rather than apt-get upgrade (which upgrades actual packages).

---

### Post by cripperz on 2010-04-11
dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.


i have been getting this as well ...there is whole list of it...

---

### Post by cripperz on 2010-04-11
it starts to happen when i accidentally delete off the whole list of package in /var/cache/apt/archives or something. is there anyways i can reverse this or fix it ?

---

### Post by mac9416 on 2010-04-11
Well, /var/cache/apt/archives is where downloaded package files are kept. It shouldn't matter if you clean that out. As a matter of fact, some folks periodically do that with 'apt-get clean' to save disk space.

Perhaps you deleted the files in /var/lib/apt/lists? In that case, a simple 'apt-get update' should solve it.

---

### Post by cripperz on 2010-04-11
did some search, i am having the similar problem that is in the last post of this topic [http://ubuntuforums.org/archive/index.php/t-922764.html](http://ubuntuforums.org/archive/index.php/t-922764.html)

---

