---
title: "[HELP]Can I upgrade to Breezy using ISO file without burning?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by james4e on 2005-10-14
I have download Breezy Install CD. I don't have CDROM driver. I want to know whether I can use this ISO file to upgrade my Ubuntu.

I have make some experiments. But I don't get what I want. I mount the ISO file into /media/iso. Then I used apt-cdrom to add it as a source. But I failed.

My question can also be how can I add a ISO file as a upgrade source?

Thanks in advance.

---

### Post by giopas on 2005-10-14
I think you can't, 'couse the system has to install and configure all the packages and not only to copy them.

enjoy, ;)
giopas

---

### Post by deBaas on 2005-10-14
I am sure you can, I did it once, I used a guide in the wiki, which i unfortunaly cant find right now

edit: it was on the forums:
[http://ubuntuforums.org/showthread.php?t=35807](http://ubuntuforums.org/showthread.php?t=35807)

---

### Post by james4e on 2005-10-15
Thanks all very much. I made it.

What I have done is:

> sudo mount -t iso9660 -o loop ubuntu_install.iso /cdrom
           sudo apt-cdrom -m -d /cdrom add


---

### Post by solusrex on 2006-02-13
thank you ever so much for this. I can't believe us 2 are the only people who didn't know how to do this!

---

