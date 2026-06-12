---
title: "After upgrade to 2016.04, cannot access USB fat32 storage devices (permission)"
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by lngndvs on 2016-05-02
Recently I upgraded to the new 16.04 Ubuntu on my dual boot iMac.  

Now, when a USB device (fat32) is plugged in, a message is displayed indicating that the permissions are undiscoverable. I cannot access the device or files.

I found a potential one-off solution for one devic, using a label.  In /etcfstab I entered the following:

     LABEL=STICK     /media/lexar    vfat   rw,uid=1004,gid=users       0

I seek a more general solution, since I suspect that this is a bug; Ubuntu has always made light work of mounting USB drives of any nature.

Can someone indicate whether this is a problem due to incomplete updating or a bug?

THank you

Alan Davis

---

