---
title: "need to find out what partition(s) I'm installed on"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by mkramer on 2007-07-03
Hi hi, linux newb here.  I've just set up and actually got working a LAMP + DNS configuration that I'm using for a web development testbed.  Getting this installation to work took several days, and I'd  I'd like to keep this installation, but move it to another drive.   Is this possible?  How would I do this from the command line? 

If that isn't feasible, I could make do by having this installation load by default in GRUB; currently, another ubu installation is the default loader, and I don't want that.   To boil it down:


0) I need to find out what partition this installation is on, as I can't remember.  All I can remember is that it is somewhere on sdf. 

1)  Is there a way to move an installation wholesale to another drive, and make it bootable? (i.e. from sdf to hda)

2) If not, what file do I need to edit, and what do I need to change, to ensure that GRUB defaults to loading some particular OS installation?  (Currently it is defaulting to an installation on sda, which I don't want it to.  That installation is ubuntu-desktop which I play around with occasionally to learn GNOME.  However I think I'm starting to appreciate/prefer the command line and I don't think I'll be using that install much anymore; besides I need it to default to this installation because when I restart from a remote shell I need it to boot back into the server).
 

thanks for your help

---

### Post by louieb on 2007-07-03
Its doable but it is also time consuming. 
To find what partitions you are using **df -h** or **mount** will list them.
Programs such as **parted** or the **dd** command  or the **tar** command can copy the installation over.
GRUB's /boot/grug/menu.lst will have change. Maybe GRUB will have to be reinstalled. [Grub From the Ground Up]("http://www.troubleshooters.com/linux/grub/grub.htm") [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")
/etc/fstab will have to change to reflect you new location.

---

### Post by mkramer on 2007-07-06
thanks, I ended up just doing a clean install.    But the df command is new to me and useful so thanks for reply.

---

