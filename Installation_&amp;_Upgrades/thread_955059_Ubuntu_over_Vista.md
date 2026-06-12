---
title: "Ubuntu over Vista"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by borncrusader on 2008-10-21
Hi Folks!

I have Vista Business on my PC on which I installed ubuntu 8.04 (from the alternate disk). The installation went smoothly but when I restarted my pc it goes straight to vista and grub doesn't show up. Any idea what's going on here?

Thanks in advance.

borncrusader

---

### Post by Bakon Jarser on 2008-10-21
Do you have multiple hard drives?  If you do try switching the boot order in your bios.  If that doesn't work then change the boot order back and try this page.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by haydnc on 2008-10-21
When it asked you where you wanted to install Ubuntu did you choose to resize the main partition and install in the spare space or use all of an existing partition?

Usually I've found Ubuntu to be pretty good at picking up the existence of other OS's. If it's not displaying options to load Vista it could possibly be that Vista isn't there anymore.

Open a terminal and type in:
```
fdisk -l
```

If you could post the results of that it would at least give some indication of whether you still had Vista lurking somewhere at all. It would probably show up as a NTFS partition.

---

