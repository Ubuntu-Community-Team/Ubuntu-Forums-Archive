---
title: "Matrox P650 not working after upgrade to 10.04"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by 2pat on 2010-06-04
Hi, installed Kubuntu 9 and got my Matrox P650 to work with my dual monitors, using the latest driver from Matrox. But after upgrading to Kubuntu 10.04 the X fails to start. Is there a way to get a picture on two monitors without a Matrox driver?


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux hanstr1-desktop 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:17:36 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=a1de658d-c18e-44a1-966f-221df4c326ad ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 20:54:29 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
dlopen: /usr/lib/xorg/modules/extensions/libglx.so: undefined symbol: miInitVisualsProc
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) module ABI major version (1) doesn't match the server's version (2)
(EE) Failed to load module "mtxcfg" (module requirement mismatch, 0)
dlopen: /usr/lib/xorg/modules/drivers/mtx_drv.so: undefined symbol: resVgaShared
(EE) Failed to load /usr/lib/xorg/modules/drivers/mtx_drv.so
(EE) Failed to load module "mtx" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

---

