---
title: "Ubuntu Box Troubles: Update"
date: 2016-10-06
forum: Installation &amp; Upgrades
---

### Post by leebrent on 2016-10-06
Having some troubles updating a box I inherited, tried a few things on google with little success, so here I am: 

brent@eblend:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mdadm
0 upgraded, 0 newly installed, 1 to remove and 105 not upgraded.
1 not fully installed or removed.
After this operation, 1,201 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 153576 files and directories currently installed.)
Removing mdadm (3.3-2ubuntu7.1) ...
/var/lib/dpkg/info/mdadm.postrm: 10: /var/lib/dpkg/info/mdadm.postrm: update-initramfs: not found
dpkg: error processing package mdadm (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
mdadm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appreciated.

---

### Post by Impavidus on 2016-10-06
> **leebrent said:**
> 
/var/lib/dpkg/info/mdadm.postrm: 10: /var/lib/dpkg/info/mdadm.postrm: update-initramfs: not found
That doesn't sound right.

The problem with inherited boxes is that you never know what cruel creatures the previous proprietor left lurking under the shiny surface. So the question is whether you want a fresh install with pristine packages or want to fix this faulty stuff. Let's first learn what release you're running:```
lsb_release -a
uname -r
```

---

