---
title: "Windows boot.ini file"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by cubnextdoor on 2012-06-10
I have Windows XP Professional SP3 installed on my main C: drive and have a newer secondary internal drive that I would like to have partitioned, half for Ubuntu Studio 12.04 and the other half as a logical drive for backup storage.

I seemed to have installed Ubuntu 12.04 just fine on the secondary drive, but the boot.ini is not allow me to load up Ubuntu properly.

I want there to be the Windows-based OS choice menu with Windows XP Pro and Xubuntu/Studio as a second choice.  This is what my boot.ini file looks like and it is clearly wrong:


[boot loader]
timeout=5
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr="Xubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


Also, it lists Windows XP Professional twice in the OS choice menu, one opens the C: drive and goes into Windows and the other Win XP choice does nothing.  I'd like to make sure I delete the enter that doesn't boot Windows XP.  Thanks for anyone's help!

---

### Post by wilee-nilee on 2012-06-10
> **cubnextdoor said:**
> I have Windows XP Professional SP3 installed on my main C: drive and have a newer secondary internal drive that I would like to have partitioned, half for Ubuntu Studio 12.04 and the other half as a logical drive for backup storage.

I seemed to have installed Ubuntu 12.04 just fine on the secondary drive, but the boot.ini is not allow me to load up Ubuntu properly.

I want there to be the Windows-based OS choice menu with Windows XP Pro and Xubuntu/Studio as a second choice.  This is what my boot.ini file looks like and it is clearly wrong:


[boot loader]
timeout=5
default=C:\wubildr.mbr
[operating systems]
C:\wubildr.mbr="Xubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


Also, it lists Windows XP Professional twice in the OS choice menu, one opens the C: drive and goes into Windows and the other Win XP choice does nothing.  I'd like to make sure I delete the enter that doesn't boot Windows XP.  Thanks for anyone's help!

So you have a wubi install, that should be in your thread header.

So I started this thread earlier today for just this sort of situation, you might post a link to this from there if you don't want to report yourself to get wubi added to the header.
[http://ubuntuforums.org/showthread.php?t=2000572](http://ubuntuforums.org/showthread.php?t=2000572)

---

### Post by Mark Phelps on 2012-06-11
You've inadvertantly made this a LOT harder than it needs to be -- by choosing Wubi.

When you have a second drive, one on which you want Ubuntu to be the ONLY OS, the easiest way to do this is to have ONLY that drive connected, boot from the installer CD/USB and install Ubuntu to that drive.  That will also install GRUB on that drive.

Then, reconnect the first drive, but continue to boot from the Ubuntu drive, and when Ubuntu gets to the desktop, open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB config file, and when you reboot, you will see a GRUB menu with entries for Ubuntu and Windows.

IF I was you, I'd go into Windows, remove Ubuntu -- and reinstall this way.

---

### Post by oldfred on 2012-06-11
+1 on Mark Phelps comments.

Wubi is for those who want an extended test of Ubuntu over a liveCD and do not want to partition. It installs inside your existing Windows, so it is easy to uninstall.
But if you have a second drive you are partitioning and then can easily use grub2 to boot both systems.

Even the creator of Wubi assumes you will change to a partitioned install.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Some guides on installing to a second drive:

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

