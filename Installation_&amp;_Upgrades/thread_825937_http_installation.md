---
title: "http installation"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by white8 on 2008-06-11
Is it possible to do an HTTP installation for 8.04 server?  I am trying to install 8.04 server on a Proliant 5500 and once it reaches gets 10-20% into copying files to the hard drive it complains that it can't read the cd.  I've tested the cd in another computer and it shows no errors.  I've also used the same cd to install on another Proliant 5500 with nearly identical specs with no problems.

---

### Post by logos34 on 2008-06-11
How about the minimal cd?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by dstew on 2008-06-11
If your server already has an OS on it, you can use [unetbootin]("http://unetbootin.sourceforge.net/") to install the server over the internet. If the server is blank, you can install over the network if it has a PXE BIOS. See [Installing Ubuntu]("https://help.ubuntu.com/community/Installation"), look for the Network Install section. There are some other schemes to install to a blank server over the net listed there as well. I have used the PXE method, using another local Linux box as the DHCP-netboot server, and it works well.

---

### Post by avtolle on 2008-06-11
[http://ubuntuforums.org/showthread.php?t=824576](http://ubuntuforums.org/showthread.php?t=824576) may or may not apply if the OP decides to try a network install.

---

### Post by logos34 on 2008-06-11
> **dstew said:**
> If your server already has an OS on it, you can use [unetbootin]("http://unetbootin.sourceforge.net/") to install the server over the internet.

if is has OS, then yes, UNetbootin would probably be the better way.  But if no OS, minimal cd route is a lot easier than PXE network install.  Don't you think so?

---

### Post by white8 on 2008-06-11
The minimal CD is working great!

Thanks

---

### Post by dstew on 2008-06-11
Logos, I agree the Minimal CD is better, but I had understood he was having trouble with the CD-ROM drive. But, seems it works ok, so all is good...

---

