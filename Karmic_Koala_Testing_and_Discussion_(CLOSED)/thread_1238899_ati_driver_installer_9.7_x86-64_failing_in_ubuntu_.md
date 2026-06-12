---
title: "ati driver installer 9.7 x86-64 failing in ubuntu 9.10"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by brianInNZ on 2009-08-12
Hi, I have a ATI HD4650 graphics board which is too new for the currently available fglrx driver (2.8.6) but is supported by the newest version on the ATI site (fglrx-8.632). 

The installation failed, and here are the messages and log: 

I executed the install script:

 sudo sh ./ati-driver-installer-9-7-x86.x86_64.run

shell output: 
------------------------

 Created directory fglrx-install.LXnMnZ
 Verifying archive integrity... All good.
 Uncompressing ATI Proprietary Linux Driver-8.632.

 ==================================================
  ATI Technologies Linux Driver Installer/Packager 
 ==================================================
 	 Detected configuration:
 Architecture: x86_64 (64-bit)
 X Server: X.Org 7.4 and later releases 64-bit
 loki_setup: directory: (null)
 DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
 Removing temporary directory: fglrx-install.LXnMnZ

log file contents:
-----------------------

 Creating symlink /var/lib/dkms/fglrx/8.632/source ->
		  /usr/src/fglrx-8.632

 DKMS: add Completed.

 Kernel preparation unnecessary for this kernel.  Skipping...

 Building module:
 cleaning build area...
 pushd /var/lib/dkms/fglrx/8.632/build; sh make.sh --nohints; popd.......
 [Error] Kernel Module : Failed to build fglrx-8.632 with DKMS
 [Error] Kernel Module : Removing fglrx-8.632 from DKMS

----------------------

after this I executed the /usr/share/ati/fglrx-uninstall.sh  to get back to a usable state.

What do you guys think ? 

Cheers,

---

### Post by QIII on 2009-08-12
I can't tell you for sure since my Karmic machine has an nVidia card, but I can say this:

Karmic is not yet in production.  It is still an Alpha and isn't even expected to be a Beta until October 1st.

The best place to address this is probably in Launchpad as a possible bug so it can be dealt with before Karmic is released.

---

### Post by hanbin973 on 2009-08-15
the latest catalyst right now dosn't support 2.6.31 in karmic.

My PPA's fglrx added a patch for 2.6.30 and higher.

[http://launchpad.net/~hanbin973/+archive](http://launchpad.net/~hanbin973/+archive).

Try mine. 

I am using 2.6.30 kernel and its perfect~

---

### Post by jiveaxe on 2009-08-18
Hi hanbin973,
I've added your ppa to apt and installed fglrx, then i run the two commands:

aticonfig --initial
aticonfig --overlay-type=Xv

then reboot; after rebooting I got a black screen while kde seems to load normally (I have auto-login, can hear the login jingle and my wireless network is working); so it is a simple black screen and not a more severe freeze. I'm using kubuntu karmic 64bit with kernel 2.6.31-6.

Can you help me?
Thanks

---

