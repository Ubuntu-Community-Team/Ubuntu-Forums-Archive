---
title: "problems with uninstalling web content control"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by anatampalli on 2010-01-04
Hi,

I get an error when i try to uninstall a parental control software which i just installed a week ago. It does not uninstall the package...

anand@anand-desktop:~$ **sudo apt-get remove --purge webcontentcontrol**
[sudo] password for anand: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl gambas2-gb-form kdelibs4c2a linux-headers-2.6.31-14 libgtk1.2
  clamav clamav-freshclam kdelibs-data libdns50 aggregate liblualib50
  clamav-base gambas2-gb-form-dialog libclamav6 gambas2-runtime firehol
  gambas2-gb-qt libavahi-qt3-1 libmikmod2 tinyproxy dansguardian
  gambas2-gb-qt-kde-html libgtk1.2-common gambas2-gb-qt-kde libtommath0
  libqt3-mt liblua50 linux-headers-2.6.31-14-generic gambas2-gb-gtk
  gambas2-gb-gui gambas2-gb-settings
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  webcontentcontrol*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,004kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 185252 files and directories currently installed.)
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is running
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is running
TinyProxy is stopped
DansGuardian is stopped
There was an error
dpkg: error processing webcontentcontrol (--purge):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 webcontentcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MelDJ on 2010-01-04
first, kill the app. in terminal type sudo pkill webcontentcontrol
then try uninstalling

---

### Post by anatampalli on 2010-01-04
I continue to get the same error message...

---

### Post by MelDJ on 2010-01-04
try the steps from [http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)
then do the steps from my other post

---

