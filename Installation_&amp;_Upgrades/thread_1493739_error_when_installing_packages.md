---
title: "error when installing packages"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by gorsebush on 2010-05-26
Am a recent convert from Microsoft so that makes me a Linux bunny.  Have just upgraded to lucid by downloading upgrade via Update Manager.
Found on first boot that I had lost windows manager resulting in loss of tool-bars in any application I opened.  Managed to fix that by copying files from administrator folder.
Now..when trying to install packages get the following error message:
Unpacking dvdauthor (from .../dvdauthor_0.6.14-3ubuntu4_i386.deb) ...

Processing triggers for man-db ...

Setting up festival (1.96~beta-10ubuntu1) ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /home/festival -g audio -s /bin/false -u 117 festival' returned error code 1. Exiting.

dpkg: error processing festival (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of festlex-cmu:

 festlex-cmu depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

dpkg: error processing festlex-cmu (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of festlex-poslex:

 festlex-poslex depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

dpkg: error processing festlex-poslex (--configure):

 dependency problems - leaving unconfigured

Setting up usbmuxd (1.0.2-1ubuntu2) ...

No apport report written because the error message indicates its a followup error from a previous failure.

No apport report written because the error message indicates its a followup error from a previous failure.

Adding system user `usbmux' (UID 117) ...

Adding new user `usbmux' (UID 117) with group `plugdev' ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /home/usbmux -g plugdev -s /bin/false -u 117 usbmux' returned error code 1. Exiting.

dpkg: error processing usbmuxd (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of libimobiledevice0:

 libimobiledevice0 depends on usbmuxd; however:

  Package usbmuxd is not configured yet.

dpkg: error processing libimobiledevice0 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of gvfs-backends:

 gvfs-backends depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: error processing gvfs-backends (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libgpod4:

 libgpod4 depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: errNo apport report written because MaxReports is reached already

No apport report written because MaxReports is reached already

No apport report written because MaxReports is reached already

No apport report written because MaxReports is reached already

No apport report written because MaxReports is reached already

or processing libgpod4 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libgpod-common:

 libgpod-common depends on libgpod4-nogtk (>= 0.7.90) | libgpod4 (>= 0.7.90); however:

  Package libgpod4-nogtk is not installed.

  Package libgpod4 is not configured yet.

 libgpod-common depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: error processing libgpod-common (--configure):

 dependency problems - leaving unconfigured

Setting up rtkit (0.6-0ubuntu1) ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /proc -g rtkit -s /bin/false -u 117 rtkit' returned error code 1. Exiting.

dpkg: error processing rtkit (--configure):

 subprocess installed post-installation script returned error exit status 1

No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of festvox-kallpc16k:

 festvox-kallpc16k depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

 festvox-kallpc16k depends on festlex-poslex (>= 1.3.0); however:

  Package festlex-poslex is not configured yet.

 festvox-kallpc16k depends on festlex-cmu (>= 1.3.0); however:

  Package festlex-cmu is not configured yet.

dpkg: error processing festvox-kallpc16k (--configure):

 dependency problems - leaving unconfigured

Setting up dvdauthor (0.6.14-3ubuntu4) ...

No apport report written because MaxReports is reached already

Errors were encountered while processing:

 festival

 festlex-cmu

 festlex-poslex

 usbmuxd

 libimobiledevice0

 gvfs-backends

 libgpod4

 libgpod-common

 rtkit

 festvox-kallpc16k

Setting up festival (1.96~beta-10ubuntu1) ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /home/festival -g audio -s /bin/false -u 117 festival' returned error code 1. Exiting.

dpkg: error processing festival (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of festlex-cmu:

 festlex-cmu depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

dpkg: error processing festlex-cmu (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of festvox-kallpc16k:

 festvox-kallpc16k depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

 festvox-kallpc16k depends on festlex-cmu (>= 1.3.0); however:

  Package festlex-cmu is not configured yet.

dpkg: error processing festvox-kallpc16k (--configure):

 dependency problems - leaving unconfigured

Setting up rtkit (0.6-0ubuntu1) ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /proc -g rtkit -s /bin/false -u 117 rtkit' returned error code 1. Exiting.

dpkg: error processing rtkit (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of festlex-poslex:

 festlex-poslex depends on festival (>= 1.4.3-9); however:

  Package festival is not configured yet.

dpkg: error processing festlex-poslex (--configure):

 dependency problems - leaving unconfigured

Setting up usbmuxd (1.0.2-1ubuntu2) ...

Adding system user `usbmux' (UID 117) ...

Adding new user `usbmux' (UID 117) with group `plugdev' ...

useradd: cannot lock /etc/passwd; try again later.

adduser: `/usr/sbin/useradd -d /home/usbmux -g plugdev -s /bin/false -u 117 usbmux' returned error code 1. Exiting.

dpkg: error processing usbmuxd (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of libimobiledevice0:

 libimobiledevice0 depends on usbmuxd; however:

  Package usbmuxd is not configured yet.

dpkg: error processing libimobiledevice0 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libgpod-common:

 libgpod-common depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: error processing libgpod-common (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of libgpod4:

 libgpod4 depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: error processing libgpod4 (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of gvfs-backends:

 gvfs-backends depends on libimobiledevice0 (>= 0.9.7); however:

  Package libimobiledevice0 is not configured yet.

dpkg: error processing gvfs-backends (--configure):

 dependency problems - leaving unconfigured

Is that enough info for someone to help me identify the problem??  Please
Further to all this, all those packages mentioned above are installed though I don't know if they are properly installed.  it would seem that the "dependency problems" would be at the heart of the issue.  When trying to deal with the problem through the terminal I get "Unable to lock the download directory".  I'm starting to think that I should just back up my files onto a separate hard drive, and reinstall from scratch.   ???

---

