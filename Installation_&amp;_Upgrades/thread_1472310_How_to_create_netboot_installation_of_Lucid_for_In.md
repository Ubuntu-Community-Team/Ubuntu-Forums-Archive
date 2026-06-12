---
title: "How to create netboot installation of Lucid for Inspiron 11z"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2010-05-04
I have a Dell Inspiron 11z that I want to install Lucid on. As can be seen here [http://ubuntuforums.org/showthread.php?p=9233518](http://ubuntuforums.org/showthread.php?p=9233518), a netboot installation of Lucid does not work out of the box on this machine; it fails to find both network cards. I'm using the kernel and initrd files from install/netboot/ubuntu-installer/amd64/ from the alternate-amd64 iso.

Now I've tried to install from a USB stick instead (using Unetbootin) and the desktop-amd64 iso. This works fine, and to my surprise, the wired network works out of the box. However, the desktop iso does not have the netboot directory.

For deployment reasons, I need to be able to install this machine via netboot.

Thus, I wonder what I need to do to modify my netboot installation (from the alternate iso) with files from the desktop iso to create an installation image that works. Apparently, all drivers that are needed are present in the Ubuntu dist as such, only not in the right iso. How do I fix this?

---

