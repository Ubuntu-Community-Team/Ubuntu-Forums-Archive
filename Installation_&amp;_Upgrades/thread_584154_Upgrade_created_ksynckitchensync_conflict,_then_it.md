---
title: "Upgrade created ksync/kitchensync conflict, then it got worse"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by plm99 on 2007-10-20
When I finally got the upgrade to go, after several hiccups, I finally got down to just a conflict between ksync and kitchensync, so since kitchen sync looked more recent, I deleted ksync, then the wheels fell off.

Now I can check email.

I can't find ksync to re-install it, and apparently several programs depend on it. It must be bundled in something else? what then?

Now the following shows broken dependencies or incomplete installation. Here's what I get back from "dpkg --configure -a"

Setting up acpid (1.0.4-5ubuntu8) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Loading ACPI modules...                                               [ OK ]
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ivman (0.6.14-2ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Starting ivman: invoke-rc.d: initscript ivman, action "start" failed.
dpkg: error processing ivman (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 ivman
 acpi-support
 powermanagement-interface
 kubuntu-desktop

but none of these say anything about ksync, but this all happened when ksync was removed.

I've already tried reinstalling all of the afflicted packages, but to no avail. What's missing?

Thanks,

---

### Post by plm99 on 2007-10-21
I've solved my own problem. I uninstalled acpi, acpi-support, ivman, and powermanagement interface, then reinstalled them, and everything quit complaining. The email problem was unrelated.

---

