---
title: "errors after today's upgrade 18.04"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by stevelcb on 2018-07-18
Hi everyone
I get the following errors. Any ideas?
TIA,
Steve

```
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of netplan.io:
 netplan.io depends on python3; however:
  Package python3 is not configured yet.


dpkg: error processing package netplan.io (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of nplan:
 nplan depends on netplan.io; however:
  Package netplan.io is not configured yet.


dpkg: error processing package nplan (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.


dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent processing triggers for gnome-menus:
 gnome-menus depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.


dpkg: error processing package gnome-menus (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:18.04.11.3); however:
  Package python3-update-manager is not configured yet.


dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 python3
 python3-update-manager
 netplan.io
 nplan
 update-manager
 gnome-menus
 update-manager-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by cigtoxdoc on 2018-07-24
I am getting the same or nearly the same error.  Will this problem be corrected?

John

---

### Post by cigtoxdoc on 2018-07-26
This is a major problem for me.  It may be related to the fact that I have hplip softrware installed for my hp 6700 printer installed on this pc.

I have attached a copy of the terminal text for the following command sudo apt-get update && sudo apt-get upgrade.

I ran that command because software update failed.  It won't update the programs it says needed to be updated and/or removed.

Please note that I use lightdm for my display manager and not gdm.

Thank you and please send help.

John

---

### Post by stevelcb on 2018-07-26
> **cigtoxdoc said:**
> This is a major problem for me.  It may be related to the fact that I have hplip softrware installed for my hp 6700 printer installed on this pc.

I have attached a copy of the terminal text for the following command sudo apt-get update && sudo apt-get upgrade.

I ran that command because software update failed.  It won't update the programs it says needed to be updated and/or removed.

Please note that I use lightdm for my display manager and not gdm.

Thank you and please send help.

John

Hi
The error I had was produced by installing hplip from the HP site. Have you removed hplip and hplip-data using apt?
HTH,
Steve

---

### Post by cigtoxdoc on 2018-07-26
Thank you, Steve.  Problem came after I upgraded from 16.04 to 18.04.  Are you suggesting removal of hplip.  Letting 18.04 update itself and then seeing if I can print w/o hplip installed?

John

---

### Post by cigtoxdoc on 2018-07-26
Thank you, Steve. Uninstalling hplip solved the problem.
John

---

### Post by stevelcb on 2018-07-26
Good to know:)
I left my envy 4500 powered on before logging into 18.04 and it was recognised as 'HP driverless' with all bells and whistles. Even the scanner worked.
HTH,
Steve

---

