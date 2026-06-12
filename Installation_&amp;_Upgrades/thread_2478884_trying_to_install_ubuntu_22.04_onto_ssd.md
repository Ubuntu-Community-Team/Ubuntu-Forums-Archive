---
title: "trying to install ubuntu 22.04 onto ssd"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-09-07
trying to install a copy of ubuntu 22.04 onto a new 1tb ssd.  I put in a new ssd and a ubuntu boot stick.  Started the boot disk (took a lot of time) and then told me "ubi-partman failed with exit code 10.  It gave me the option of going ahead or trying again.  I tried again and got the same thing and am stopped.  

thoughts?

---

### Post by ajgreeny on 2022-09-07
What is on the new 1T ssd?  Does it have any partitions or is it completely unformatted and without even a partition table?

How did you create the Ubuntu boot USB?

EDIT:
Have read through this thread which may be some help to you.
[https://askubuntu.com/questions/1032905/ubi-partman-failed-with-exit-code-10-ubuntu-18-04](https://askubuntu.com/questions/1032905/ubi-partman-failed-with-exit-code-10-ubuntu-18-04)

---

### Post by oldfred on 2022-09-07
SATA or NVMe SSD?
Some now are pre-formatted for Windows and may also have encryption?
Some need firmware update.

You can get firmware revision and then go to vendor's site to see if update is available.
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ udisksctl status [/COLOR]
MODEL                     REVISION  SERIAL               DEVICE 
-------------------------------------------------------------------------- 
Samsung SSD 980 PRO 1TB   5B2QGXA7  S5P2NS0T335627H      nvme0n1  
Samsung SSD 840 PRO Series DXM06B0Q  S1ANNSAF511092D      sda      
ASUS SDRW-08U9M-U         A112      K0QLB375428          sr0     


[/FONT]
```

---

