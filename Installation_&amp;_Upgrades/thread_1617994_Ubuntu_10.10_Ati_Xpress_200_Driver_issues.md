---
title: "Ubuntu 10.10 Ati Xpress 200 Driver issues"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by MrSpace on 2010-11-10
Ok before anyone tells me to use the open source drivers.  Did that and the 3d was messed up.  Wine + eve online = fail.  This is where this adventure begain. :P Be nice I am semi noobish in ubuntu.  Openbsd background so a total X noob.

lspci | grep VGA

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) 

System:
HP Dv5130ca AMD Turion 64

Glxgears:
Segment fault

ATI Proprietary Linux Driver-8.30.3 from the documentation seems to support this card. but no make install package for 10.10

ATI Proprietary Linux Driver-10.9-x86_64 fails on sudo ./

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

ok so sudo ./ati-driver-installer-10-9-x86.x86_64.run --buildandinstallpkg Ubuntu/maverick

pump out this

update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.771 DKMS files...
Building only for 2.6.35-22-generic
Building for architecture x86_64
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/fglrx.0.crash'
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.771-0ubuntu1) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
fglrx_8.771-0ubuntu1_amd64.deb fglrx-amdcccle_8.771-0ubuntu1_amd64.deb fglrx-modaliases_8.771-0ubuntu1_amd64.deb
Cleaning up removed packages
aticonfig: No supported adapters detected

Ok so any advice or help would be seriously appreciated. Share the love.

---

### Post by MrSpace on 2010-11-10
Linux bsd-Tiger 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

---

### Post by efflandt on 2010-11-10
Try **nomodeset** kernel boot parameter with default video modules.  Since 10.04 the default is to use kernel mode setting (kms) video, but older ATI devices often work better with the user space video modules instead.

To try that you can press e during grub menu and add it after (or instead of) **quiet splash**.  And if that helps (which I bet it will), you can include that in following line of /etc/default/grub to apply to all boot modes including (recovery), use sudo to run your editor as root:

GRUB_CMDLINE_LINUX="nomodeset"

Then do: **sudo update-grub**

I believe I have 200M on an old laptop and have not tired 10.10 on it yet.  But it actually ran better with 10.04 than it did with 9.10.  9.10 keyboard and mouse would glitch (dropped keys and delayed/jumpy mouse) and would not suspend/hibernate properly.  10.04 (using nomodeset) had much better keyboard/mouse response and suspend/hibernate worked.  Although, when I borrowed some RAM from it and only had 512 MB shared as video RAM games like supertuxkart had video tearing.  That was not a problem for normal system video.

I have not tried 10.10 on it yet because that laptop cannot boot from USB.

---

### Post by Mark Phelps on 2010-11-10
> **MrSpace said:**
> Ok so any advice or help would be seriously appreciated.

OK -- so, either learn to live with the shortcomings of the open-source drivers, or buy a new card that will work with the fglrx drivers.

Seriously -- these are the only alternatives available unless you want to take on really MAJOR work by backporting your X-server and all its related packages back to the Ubuntu 8.04 X-server days, and then LOCKING those packages so that they don't get updated in the future.

For someone who is "semi-noobish in ubuntu", this is NOT something you want to take on.

---

