---
title: "Cannot get X to start, driver errors?"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by mrwooster on 2011-05-07
I have quite an old desktop (5 years) with an integrated nvidia Geforce4MX graphics card.  Following the instructions here [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074) I installed the Nvidia drivers.  However, when I do sudo startx I get the following error... any ideas?

Thanks




X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux optimusprime 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=8e9ac526-0b02-41eb-9b6e-2c66912d0188 ro quiet splash vt.handoff=7
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.20.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May  7 09:04:37 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) NVIDIA: This server has an unsupported input driver ABI version (have 12.3, need < 12.0).  The driver will continue to load, but may behave strangely.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by danteuk on 2011-06-18
Extactly the same error.
Anyone have any ideas?

This is Kubuntu 11.04 on an old dell laptop.
Trying to use Legacy nvidia driver 96.43.19 because
nouveau doesn't work - screen corruption etc.

---

### Post by leaph on 2011-07-06
I also have the same problem after installing nvidia driver on my desktop.

---

