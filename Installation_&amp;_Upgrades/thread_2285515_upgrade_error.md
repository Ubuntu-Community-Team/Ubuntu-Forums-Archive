---
title: "upgrade error"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by huff2 on 2015-07-06
Hi all,

I recently used sudo apt-get update && sudo apt-get upgrade to upgrade. I found this error message:        

 [FONT=monospace][COLOR=#000000]Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/kubunt](http://download.virtualbox.org/virtualbox/debian/dists/kubunt)[/COLOR]
u/contrib/binary-i386/Packages  404  Not Found [IP: 216.68.10.177 80]

Does anyone know how to fix this?

Thanks
[/FONT]

---

### Post by v3.xx on 2015-07-06
Thats a bad address, need to remove it.  Are you running virtualbox?  Did you install from the vBox site?

---

### Post by huff2 on 2015-07-06
Fixed it. I just removed the broken address from /etc/apt/sources.list

---

### Post by v3.xx on 2015-07-06
ok :)

---

