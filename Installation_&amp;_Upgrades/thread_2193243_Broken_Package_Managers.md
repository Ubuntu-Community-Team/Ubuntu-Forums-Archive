---
title: "Broken Package Managers"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by jordan.stanford on 2013-12-11
I'm running 12.04 on a Dell Latitude D820. For several months the wireless card (a Dell branded broadcom device) has not worked. I spent a few hours working on it at the time, and never got back to it.
Two weeks ago the real trouble began. A message popped up telling me that my package manager was broken and I should either use synaptic (which does not load for some reason) or run dpkg --config -a to fis the issue.
Unfortunately, dpkg --config -a hangs after it seems to either uninstall or reinstall the wireless drivers.
I have been unable to get any apt commands to run, and everything I can find seems to lead me right back to dpkg --config -a.

My Kernel is 3.2.0-54-generic and I don't know what other information to provide. I'm somewhere between newbie and end user so please be patient with me friends :)

---

### Post by ian-weisser on 2013-12-11
> **jordan.stanford said:**
> I have been unable to get any apt commands to run

If your package manager is broken, then that behavior is expected.

Please open a terminal, run the command **sudo --configure -a** again, and please show us the *complete* output of the command. Some of it may look like garbage to you, but it has important meaning to us.

---

### Post by jordan.stanford on 2013-12-11
sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-54-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-54-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic
Building for architecture i686
Building initial module for 3.2.0-54-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-54-generic/updates/dkms/

depmod....

DKMS: install completed.

---

### Post by jordan.stanford on 2013-12-11
So that is the output. I can see where it is removing the wireless package and reinstalling it. After it seems to succeede though it just hangs there. I'm a windows admin by trade so I understand a bit more of this than I am letting on, but I don't want to miss something based on an assumption I have made. I always feel in over my head when dealing with my ubuntu boxes off script... Thanks for your assistance.

---

### Post by jordan.stanford on 2013-12-13
I am now also recieving a message that my software indexes are corrrupt, but the solution provided uses apt to correct this, which obviously won't work, and I have not found an alternative in my searches these past couple of days.

---

### Post by ian-weisser on 2013-12-13
Please show us the command and complete output, including the exact error message.
Please use [code] tags to comtain output - it helps make the output much more readable.

---

