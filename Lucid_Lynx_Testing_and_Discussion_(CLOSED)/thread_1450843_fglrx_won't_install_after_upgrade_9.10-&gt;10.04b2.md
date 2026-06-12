---
title: "fglrx won't install after upgrade 9.10-&gt;10.04b2"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Eagleguy125 on 2010-04-09
Alright, so I upgraded one of my systems from 9.10 to 10.04 (beta 2). Most of the installation process went over without a problem with the exception of the fglrx package--my GPU drivers. I've got windows behaving erratically, the system doesn't really know what to do with a number of keyboard shortcuts (such as alt+tab) and compositing is completely out of the question, so I can really only work on one thing at a time. Running from the Update Manager, I get a handy error stating that:

"You have 3 broken packages on your system! Use the "Broken" filter to locate them."

Unfortunately, although I've been using Ubuntu for quite some time, I've never had to fix a problem like this, so I really don't know how to react.

I also get this fun little nugget of output immediately afterwards:
"E: /var/cache/apt/archives/fglrx_2%3a8.721-0ubuntu7_i386.deb: subprocess new pre-installation script returned error exit status 2"

I've tried what little terminal wizardry I know (sudo apt-get install fglrx -f, for example) but everything universally gives me the same error message. Any ideas?

---

### Post by Scibax on 2010-04-09
I am getting the same things from beta 1 to beta 2 upgrade.  I even attempted running a patch which was said to work and it still failed.

Here is the message I get when I attempt to remove fglrx:

> [PHP]graphicw@graphicw-desktop:~$ sudo apt-get remove fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx fglrx-amdcccle
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 109MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217341 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/PHP]

I have already ran the latest update, check the bug report and ran any fixes suggested there.  The bug reports say the fix is released as of a few hours ago, but the problem still persists.  Maybe someone can shed some light on what is going on or it is possible the fix is not yet in the repository as of yet.

Brion

---

### Post by Scibax on 2010-04-09
Here is what I get when I reinstall fglrx.  It actually appears to install normally, however, the driver never works.

[PHP]graphicw@graphicw-desktop:~$ sudo apt-get install fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fglrx-amdcccle
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/34.3MB of archives.
After this operation, 9,253kB of additional disk space will be used.
Selecting previously deselected package fglrx.
(Reading database ... 217152 files and directories currently installed.)
Preparing to replace fglrx 2:8.721-0ubuntu8 (using .../fglrx_2%3a8.721-0ubuntu8_amd64.deb) ...
Unpacking replacement fglrx ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.721-0ubuntu8_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.721-0ubuntu8) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.721 DKMS files...
Building only for 2.6.32-19-generic
Building for architecture x86_64
Building initial module for 2.6.32-19-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-19-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up fglrx-amdcccle (2:8.721-0ubuntu8) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
[/PHP]

---

### Post by Scibax on 2010-04-09
I think I found a solution after looking closer at the error messages when trying to remove fglrx.  The error had to do with diversions, so I decided to take a look at them.  I found references to fglrx and decided to delete them.  I then reinstalled fglrx and it worked for me.  

The solution is as follows:

sudo gedit /var/lib/dpkg/diversions

Delete any lines mentioning fglrx.  It is a short file, so it wont take you long.  Reinstall fglrx and you will be good to go.

---

### Post by Eagleguy125 on 2010-04-09
Thanks! That fix brought me from three to one broken package. Working to locate the last one.

---

### Post by Eagleguy125 on 2010-04-09
Alright, after booting in low-graphics mode, configuring a few things, restarting a few times, and fiddling with settings on the desktop, I've got my windows working, kinda. Compositing is still iffy, but I can move my windows around now, and that's a huge step. I'll keep posting here as I find fixes for these issues.

---

### Post by Scibax on 2010-04-09
Awesome, glad I was able to get you a little closer as well as finding the complete solution to my problem.

---

