---
title: "Help Mounting External Hard Drive."
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by thetmyster on 2012-04-11
Hi, 

I recently Bought a Hitachi Toro Pro Hard Drive. 

I am having trouble getting it to mount under Ubuntu (VM In Mac OSX).

I have re formatted it to XFS as my TV is a pain in the ***. :frown:

It is refusing to mount, or re format. Could this possibly be a driver issue? 

Sorry that I cant be of any further use, but I'm new to Linux :)

[img]http://cl.ly/3f0m1L3K3w0Q2m2l2Y13/Screen%20Shot%202012-04-11%20at%2018.51.46.png[/img]

[img]http://cl.ly/2X2r3b2W0U1c0r0k1u39/Screen%20Shot%202012-04-11%20at%2019.03.50.png[/img]

P.S:

I think somebody already found a fix for this, however it is in russian :)

[http://translate.google.com/translate?sl=ru&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntu.ru%2Findex.php%3Ftopic%3D183390.0](http://translate.google.com/translate?sl=ru&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntu.ru%2Findex.php%3Ftopic%3D183390.0)

Thanks,

Theo.

---

### Post by darkod on 2012-04-11
What did you use to format it as XFS, your Mac?

If you open it with Gparted, does it read it correctly?

Also, the XFS format might be not understandable to ubuntu, you could try format it as NTFS on your Mac, or simply delete the XFS partition, then open ubuntu and Gparted and try to create XFS partition on the disk.

---

### Post by thetmyster on 2012-04-11
> **darkod said:**
> What did you use to format it as XFS, your Mac?

If you open it with Gparted, does it read it correctly?

Also, the XFS format might be not understandable to ubuntu, you could try format it as NTFS on your Mac, or simply delete the XFS partition, then open ubuntu and Gparted and try to create XFS partition on the disk.


I used a Samsung Series D TV.

Gparted? (Sorry!)

I'm pretty sure that it works, as I have done the same on a WD Hard drive, that was recognised by ubuntu after the initial format by the TV.

I'm going to try formatting it to NTFS, and seeing if that works :)

[http://cl.ly/1D1z3D2W260d3V171s3r](http://cl.ly/1D1z3D2W260d3V171s3r)


I got it to mount after doing this (Formatted NTFS)

```
echo "blacklist uas" | sudo tee -a /etc/modprobe.d/blacklist.conf 
 sudo reboot
```

---

### Post by darkod on 2012-04-11
Gparted is one of the most commonly used partition editors in ubuntu. By default it is not installed, you need to search for it in Software Centre and install it.

I prefer it over Disk Utility for example.

So, the final verdict? Working with the TV as you need it, or not yet?

---

### Post by thetmyster on 2012-04-11
Yea, working. Now, to get my mac files on Ubuntu.
(parallels tools installer is deciding not to work :( )


Whats the quickest way to get a NFS Share running? :)

---

