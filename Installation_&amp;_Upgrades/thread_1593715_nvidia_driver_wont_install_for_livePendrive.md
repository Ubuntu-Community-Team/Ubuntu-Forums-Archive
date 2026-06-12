---
title: "nvidia driver wont install for livePendrive"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by kraylus on 2010-10-11
i recently got the netbook edition of 10.10 loaded on a usb drive so i could test drive the unity interface, but on boot its telling me i dont have 3d acceleration and that unity requires that to run. im running this on an asus g51 (totally not a netbook) just to see what its like while i wait for my netbook in the mail.

in any case, i was trying to install the nvidia drivers so i could mess around with unity and perhaps some of the sweet desktop effects but it tells me that theres an error when it tries to install the package. doesnt say what exactly, just that it wont work. tried different versions of the nvidia driver but to no avail.

i recall doing this when ubuntu 8 came out back in the day and installing the nvidia drivers on a livependrive and everything working just fine (even got compiz-fusion working with all the bells and whistles). is this problem going to persist when i try to install ubuntu on my laptop too? my netbook thats comin wont have an nvidia card in it so it wont be an issue but id still like to put it on my laptop at some point.

i updated the synaptic repos or whatever you call em, so its got all the latest stuff in it (sorry, forgot the lingo. its been awhile). as a side note, it also says it couldnt install initramfs or some such dependency.

help please?

***UPDATE***

i tried installing a newer version over 173 and got this log:

> installArchives() failed: Selecting previously deselected package nvidia-current.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 123713 files and directories currently installed.)

Unpacking nvidia-current (from .../nvidia-current_260.19.06-0ubuntu1_i386.deb) ...

Selecting previously deselected package nvidia-glx-185.

Unpacking nvidia-glx-185 (from .../nvidia-glx-185_260.19.06-0ubuntu1_i386.deb) ...

Processing triggers for man-db ...

Setting up initramfs-tools (0.98.1ubuntu6) ...

update-initramfs: deferring update (trigger activated)

cp: cannot stat `/vmlinuz': No such file or directory

dpkg: error processing initramfs-tools (--configure):

 subprocess installed post-installation script returned error exit status 1

Setting up nvidia-173 (173.14.28-0ubuntu1) ...

update-initramfs: deferring update (trigger activated)

cp: cannot stat `/vmlinuz': No such file or directory

dpkg: error processing nvidia-173 (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of nvidia-glx-173:

 nvidia-glx-173 depends on nvidia-173; however:

  Package nvidia-173 is not configured yet.

dpkg: error processing nvidia-glx-173 (--configure):

 dependency problems - leaving unconfigured

Setting up nvidia-current (260.19.06-0ubuntu1) ...

No apport report written because the error message indicates its a followup error from a previous failure.
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.

update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.

update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.

update-initramfs: deferring update (trigger activated)

cp: cannot stat `/vmlinuz': No such file or directory

dpkg: error processing nvidia-current (--configure):

 subprocess installed post-installation script returned error exit status 1

No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of nvidia-glx-185:

 nvidia-glx-185 depends on nvidia-current; however:

  Package nvidia-current is not configured yet.

dpkg: error processing nvidia-glx-185 (--configure):

 dependency problems - leaving unconfigured

No apport report written because MaxReports is reached already
Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...

Processing triggers for bamfdaemon ...

Rebuilding /usr/share/applications/bamf.index...

Processing triggers for python-support ...

Errors were encountered while processing:

 initramfs-tools

 nvidia-173

 nvidia-glx-173

 nvidia-current

 nvidia-glx-185

Setting up initramfs-tools (0.98.1ubuntu6) ...

update-initramfs: deferring update (trigger activated)

cp: cannot stat `/vmlinuz': No such file or directory

dpkg: error processing initramfs-tools (--configure):

 subprocess installed post-installation script returned error exit status 1

Setting up nvidia-173 (173.14.28-0ubuntu1) ...

Loading new nvidia-173-173.14.28 DKMS files...

First Installation: checking all kernels...

Building only for 2.6.35-22-generic

Building for architecture i686

Building initial module for 2.6.35-22-generic



Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)

Consult the make.log in the build directory

/var/lib/dkms/nvidia-173/173.14.28/build/ for more information.

dpkg: error processing nvidia-173 (--configure):

 subprocess installed post-installation script returned error exit status 10

Setting up nvidia-current (260.19.06-0ubuntu1) ...

update-initramfs: deferring update (trigger activated)

cp: cannot stat `/vmlinuz': No such file or directory

dpkg: error processing nvidia-current (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of nvidia-glx-173:

 nvidia-glx-173 depends on nvidia-173; however:

  Package nvidia-173 is not configured yet.

dpkg: error processing nvidia-glx-173 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of nvidia-glx-185:

 nvidia-glx-185 depends on nvidia-current; however:

  Package nvidia-current is not configured yet.

dpkg: error processing nvidia-glx-185 (--configure):

 dependency problems - leaving unconfigured

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...

Processing triggers for bamfdaemon ...

Rebuilding /usr/share/applications/bamf.index...

Processing triggers for python-support ...

when i go to check the addtl drivers under system>admin it says the driver is activated but not in use. when i follow the instructions under nvidia config it says to run nvidia-xconfig as root. i do so, then it tells me it repaced my config file and i go to restart X and boom... its dead. no more worky.

and since its a persistent livependrive, its perma broke and im not savvy enough these days to fix that. so i went and remade the bootable livecd on the usb drive.

whaaaat do i do?

thanks,

ryan

---

