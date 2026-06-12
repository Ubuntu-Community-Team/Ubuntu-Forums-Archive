---
title: "apt-get ACPI problem?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by dogeatery on 2008-03-25
When I try to install programs through apt-get/aptitude, I get these error messages telling me the acpid processing failed.  Part of my printout is below.  Sometimes this doesn't cause a problem but this time I'm trying to download greenos-desktop and it appears to be blocking my progress.  Any help would be appreciated, but please explain in simple steps.  Thanks! ------------------------------------------------------------------------------  Writing extended state information... Done Setting up acpid (1.0.4-5ubuntu8) ...  * Loading ACPI modules...                                               [ OK ]   * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed. dpkg: error processing acpid (--configure):  subprocess post-installation script returned error exit status 1 Errors were encountered while processing:  acpid E: Sub-process /usr/bin/dpkg returned an error code (1) A package failed to install.  Trying to recover: Setting up acpid (1.0.4-5ubuntu8) ...  * Loading ACPI modules...                                               [ OK ]   * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed. dpkg: error processing acpid (--configure):  subprocess post-installation script returned error exit status 1 Errors were encountered while processing:  acpid Reading package lists... Done              Building dependency tree        Reading state information... Done Reading extended state information        Initializing package states... Done Building tag database... Done       dogeatery@dogeatery:~$

---

### Post by dogeatery on 2008-03-25
ah sheet, someone needs to teach me how to put my terminal printouts in that little box so it looks clear and readable

---

