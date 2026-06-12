---
title: "Help with my GRUB and kernel-img.conf"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by scottpledger on 2007-08-09
My computer has the following hard drive setup:
```

hd(0,0) -> Windows XP
hd(1,0) -> Windows Vista
hd(2,0) -> /boot (Originally from a Fedora Core 6 install).
hd(2,1) -> / for my old Fedora Install, which is broken.
hd(2,2) -> SWAP for old Fedora install.
hd(2,3) -> LVM for Ubuntu.
hd(2,4) -> / for Ubuntu.
hd(2,5) -> SWAP space for Ubuntu.

```
My computer boots into hd(2,0).  This is where all of my GRUB info is located.  Unfortunately, Ubuntu thinks that it is located under /boot in hd(2,4) and it also thinks that my Ubuntu install is located on hd(0,0).  Because of this, when I upgrade my linux-image package, it puts all of the boot information in the wrong menu.lst file and with the wrong hd() information.  So, I need to find a way so that it will update the proper menu.lst file in hd(2,0) and I need to force it to think that it boots into hd(2,4) not hd(0,0).  Is this possible??  I've found out about the kernel-img.conf file under /etc, but I don't know if I have the savvy to create a postinst script that it can run that will make the changes necessary to the proper menu.lst file.  Am I on the right track, or should I be looking elsewhere?  If I am on the right track, what should I include in the script file?  If not, where should I be looking?

---

