---
title: "Intalling Ubuntu from within Windows 7"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by PayPaul on 2011-09-14
Is it possible to install Ubuntu from within Windows? I seem to recall reading somewhere that it was possible. I have a partition on my 1st boot drive that also contains the Windows 7 64 bit installation that has enough space for Ubuntu. I'm looking for the easiest way to to do this and hope that an installation like that is still possible and that it will also be recognized in a dual boot situation. I'm trying to avoid possible pitfalls in creating a live CD. I'm not sure if a CD-R would be sufficient for that, if I'd need a DVD or whether if it would be successful. I'd like to do the installation in one step rather than the 2 or 3 required with an installation from a LiveCD.

---

### Post by oldfred on 2011-09-14
Welcome to the forums.

I have not installed wubi, but that sounds like what you want.

Wubi's advantage is that it installs to a file inside the Windows NTFS partition and uses the Windows boot loader in the MBR. You then have not changed Windows except to add the option to also boot into Wubi. It does avoid the issue of creating new partitions and therefore is easy to uninstall if you find you do not like Ubuntu.

That also is part of the disadvantage of wubi. It uses the Windows boot loader and is inside the NTFS partition. If you have problems with the NTFS partition or cannot boot Windows you cannot (easily) boot into wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Another alternative to wubi is to just install and run from a flash drive.
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by PayPaul on 2011-09-15
Oh yes! Wubi worked great. Now I do have the dual boot option. Aside from that I do get some kind error when I load Ubuntu but I'm able to input the EXIT command and the OS loads. So far it is a much better system than Windoze. It's a learning curve but that was expected. I just discovered where the System Settings was this evening. LOL!

---

