---
title: "Xubuntu 7.10 PXE install. help please."
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by alanmzifa on 2007-11-12
Hi, I need to install **Xubuntu Gutsy** over PXE as the laptop has no CD-ROM.

I've done a PXE install on Ubuntu Dapper 6.06 beforefrom a Windows machine  based on [this excellent tutorial]("http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows") so all I need to know is how do I do the same for** Xubuntu 7.10**.
I cannot download Ubuntu 7.10 as the laptop **only has 256MB RAM** and Ubuntu Gutsy needs 320MB. 

**Xubuntu** Gutsy only needs 128MB, hence my choice.

thanks

---

### Post by mikewhatever on 2007-11-12
It should work the same with Xubuntu, or any other version, just select correct mirrors. [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by alanmzifa on 2007-11-12
That's the bit I still can't work out. 

Don't I need to get to a mirror that's set out in [this format]("http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/20070308ubuntu18/images/") (with NETBOOT and PXE files) except for Xubuntu and not Ubuntu?

I need to know where to find that.

---

### Post by mikewhatever on 2007-11-12
Yes, there is no such format. Well, the only difference between Ubuntu and Xubuntu is the package ubuntu-desktop vs xubuntu desktop and all associated software. If I understand correctly, you first install the base system (which is the same for all *buntus) and then download and install the rest. Am I wrong?

---

### Post by alanmzifa on 2007-11-12
> **mikewhatever said:**
> Yes, there is no such format. Well, the only difference between Ubuntu and Xubuntu is the package ubuntu-desktop vs xubuntu desktop and all associated software. If I understand correctly, you first install the base system (which is the same for all *buntus) and then download and install the rest. Am I wrong?

I've only installed by PXE once. From memory it just chugged down Ubuntu which I'll have to later  change to Xubuntu. If it did that for Gutsy it won't work as the install needs 320MB RAM.

I was hoping I could just change what was originally downloaded in some way.

---

### Post by mikewhatever on 2007-11-13
OK, how about this guide [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by alanmzifa on 2007-11-15
> **mikewhatever said:**
> OK, how about this guide [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

Thanks mikewhatever. I'd already come across that link via a Google search.


I went through the the PXE install for 7.04 which only needs 256MB RAM. I used the Ubuntu version and found that it gave me the option late in the install process for Edubuntu/Xubuntu etc. I'll try and remember that for the next time!

Still having trouble getting wireless to work though.

---

