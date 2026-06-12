---
title: "Ubuntu 10.10 crashes"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by LabRatNo9 on 2011-04-06
Hi All,

it all started a few days ago... the update wouldn't initiate downloading.

I had to force close the update.

And it has gone from bad to worse...

i decided to do the latest version of ubuntu 10.10 and that took more then 3 hours.

ever since it crashes occasionally.

when i want to update manually i got this message :

All help is welcome.

LabRatNo9

installArchives() failed: (Database inlezen ... 
(Database inlezen ... 5%
(Database inlezen ... 10%
(Database inlezen ... 15%
(Database inlezen ... 20%
(Database inlezen ... 25%
(Database inlezen ... 30%
(Database inlezen ... 35%
(Database inlezen ... 40%
(Database inlezen ... 45%
(Database inlezen ... 50%
(Database inlezen ... 55%
(Database inlezen ... 60%
(Database inlezen ... 65%
(Database inlezen ... 70%
(Database inlezen ... 75%
(Database inlezen ... 80%
(Database inlezen ... 85%
(Database inlezen ... 90%
(Database inlezen ... 95%
(Database inlezen ... 100%
(Database inlezen ... 509818 bestanden en mappen geïnstalleerd.)
Voorbereiden om virtualbox-ose-dkms 3.1.6-dfsg-2ubuntu2 te vervangen (door .../virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb) ...
Removing all DKMS Modules
Done.
Removing obsolete module vboxnetflt version  3.1.8

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.32-28-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.32-30-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-30-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.32-29-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-29-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.32-26-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.35-28-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.35-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod........

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  vboxnetflt
Version: 3.1.8
Kernel:  2.6.32-27-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-27-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall Completed.

------------------------------
Deleting module version: 3.1.8
completely from the DKMS tree.
------------------------------
Done.
Removing obsolete module vboxnetflt version  3.1.8

Error! There are no instances of module: vboxnetflt
3.1.8 located in the DKMS tree.
dpkg: fout bij afhandelen van /var/cache/apt/archives/virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb (--unpack):
 subproces nieuw pre-installation script gaf een foutwaarde 3 terug
No apport report written because MaxReports is reached already
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/virtualbox-ose-dkms_3.2.8-dfsg-2ubuntu1_all.deb

---

### Post by LabRatNo9 on 2011-04-07
I know have completed all updates but Ubuntu keeps crashing...

---

### Post by Hedgehog1 on 2011-04-08
> **LabRatNo9 said:**
> I know have completed all updates but Ubuntu keeps crashing...

Hi LabRatNo9! ( great user name :D )

I think things started to go wrong because you were running Virtual Box during an attempt by the Update manager to update Virtual Box.

I think that your best hope of resolving this is to uninstall your current Vbox.  If you still use Vbox, please re-install the most recent version from the Virtual Box web site: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")  This new 4.0.4 version supports USB devices and even has some 3d support for the guest OS.

I cannot say for sure this will resolve your issue, but it seems a reasonable first step.


***The Hedge*** *(Der Igel)*

:KS

---

