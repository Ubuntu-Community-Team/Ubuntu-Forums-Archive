---
title: "Installed ubuntu but used wubi and have few questions about changing the install"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by AbbyRose on 2010-04-29
From what I have read and understood wubi makes it so that ubuntu is installed inside of windows. (I noticed that when I went to my add/remove programs and ubuntu was listed.)
My questions are:
1) Installing without using wubi; the files can be found on the ubuntu website?
2) I have all my files moved to the ubuntu I currently have and I was wondering if I could keep the files there when installing ubuntu outside of windows? I do not have a large external hard drive about 10GB with the majority of them photos. I would move them all to the external if needed but I'd prefer to not have to re-download all my music. 
Let me know if this makes no sense?
I have a tendency to confuse things very easy.

---

### Post by oldfred on 2010-04-29
Yes wubi is inside the NTFS partition your windows on on. It is a full install and intended for extended testing by windows users who may want to uninstall it easily. 

You can get the newest version here:
[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

You can install it to a CD or USB key (not copy) as bootable disks to install. The liveCD will let you run it also so you can see that it works with your system.

I do not know how space restricted you are but part of the advantage of Ubuntu is that your data is not in your windows partition. If windows crashes your data may not be accessible. You can mount the root.disk in the full install to copy data (or use it if you really want). IF you copy data over, you can then delete the install in windows and shrink the windows partition.

---

