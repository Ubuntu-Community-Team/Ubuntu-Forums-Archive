---
title: "Cannot activate proprietary driver - ATi 6850"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by sunil237 on 2011-05-21
Upgraded to Natty,just after I got this new GPU - ATi Radeon HD 6850.

I cannot activate the driver for it, I have also tried to download and install from AMD but it didn't work. I cannot open the catalyst control centre that is already installed.

When I try I get this.

"system error: Install archives() failed"

When I open the software update application I get this

"Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?"

So click yes. The process is:
"Repairing broken deps and states "Finished"

error message appears with
"package operation failed"
Details:
"installArchives() failed: (Reading database ... 
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
(Reading database ... 193535 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.840-0ubuntu4_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.840-0ubuntu4_amd64.deb
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured"


I have tried to use this guide [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
to remove the files but it won't let me remove.

Any ideas?

---

### Post by sunil237 on 2011-05-21
anyone?

If there is no known solution, I'd appreciate a reply too.

---

