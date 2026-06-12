---
title: "Problem to install ATI driver in Ubuntu 10.04"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by figo2476 on 2010-04-16
Hi all,

I installed the proprietary ATI driver previously. After I upgrade to Ubuntu 10.04 beta 2, my laptop (with ATI radeon HD 4xxx) is not able to boot into graphic mode (false safe mode works)

I did sudo apt-get install fglrx && sudo aticonfig --initial


It gives me error:

-------------------------------------------------------------------------
[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
-------------------------------------------------------------------------


Any help will be appreciated.

---

### Post by hawthornso23 on 2010-04-17
Try installing the latest version of the ATI drivers. I don't think just installing fglrx is enough. You have to uninstall the ATI drivers. There is a kernel module and other stuff involved. The ATI installation instructions tell you how to uninstall older versions, so following those should clear the problem.

---

### Post by clhsharky on 2010-04-17
HI


Lucid requires special fglrx driver

[http://ubuntuforums.org/showpost.php?p=9062521&postcount=158](http://ubuntuforums.org/showpost.php?p=9062521&postcount=158)

>  Originally Posted by jngrim  View Post
i couldn't get it to work either for HD3200 so did the following:

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics, ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

This section is for Lucid
Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Ubuntu Gets Another ATI Catalyst Driver Handout
[http://ubuntuforums.org/showthread.php?t=1434064](http://ubuntuforums.org/showthread.php?t=1434064)


Sharky

---

### Post by arloth on 2010-04-28
hmm, that seems to have done it for me as well.  however, i also had to rm -rf /usr/share/ati before it would work (for better or worse). There wasn't an /etc/ati on my install at all, no directory or file there.


 it looks like ALOT of people are getting this error..  A search for inst_path_default and inst_path_override shows quite a few results with people having trouble updating to 10.04. 

```
Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).
```


Now the moment of truth, to see if Stream still works. ;)

---

