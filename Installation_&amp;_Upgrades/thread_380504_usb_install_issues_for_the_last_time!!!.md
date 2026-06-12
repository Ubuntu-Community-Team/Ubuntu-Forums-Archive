---
title: "usb install issues for the last time!!!"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by papercuts on 2007-03-09
OK I have been searching and trying to install Linux from USB now for two days. I have a brand new computer and it frustrates me so much that I couldn't even get it to run. So before I sleep I want to post some issues so that ho&#305;pefully someone can shed some light.

I have no CDROM drive or floppy but a bootable USB stick. I installa syslinux now without problems and the boot is OK. Then I copy the files.  When I boot I am happy to see that actually the LiveCD menu appears. 

BUT!

The links don't work. When I try to install Ubuntu it said that it couldn't find the kernel. The guide ([https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")) told us to delete all references to casper in the paths of the syslinux.cfg but the program said can't find /casper/vmlinuz So I copied vmlinuz to root of the USB, then it couldn't find something else in /casper/ which wasn't even there on the CD!!  I can't explain this. Neither can I explain why we have to delete all reference to /casper. Because we move the contents of /install folder to root so it makes sense to delete the reference to install (and that part actually works) but why /casper?

In the folder "dists" there are symlinks. I can't copy them (it says error: operation not permitted) nor make new ones with the sudo command? Why is that? And do we really need these symbolic links?

Can anyone please help on this. I read the forums on USB installations but either finding correct info was hard (i.e. not intalling TO a USB, installing FROM a USB) or nothing really helped my situation. I searched the error text in google, and received four inconclusive results. 

So really I'm going crazy here. :(

---

### Post by zvacet on 2007-03-18
[http://ubuntuforums.org/showthread.php?t=308027&highlight=usb+install]("http://ubuntuforums.org/showthread.php?t=308027&highlight=usb+install")

---

