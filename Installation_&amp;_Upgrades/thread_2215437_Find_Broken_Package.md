---
title: "Find Broken Package"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by borgward on 2014-04-06
How to I find Broken Package? I ran Update Manager. Got message 1 broken package - use broken filter to find it. 

Get same message from Synaptic Package Manager:

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

Settings > Filters > Broken - (Synaptic indicates 1 broken) "No Package selected" What package do I select?

---

### Post by ajgreeny on 2014-04-06
Try either using the **Edit ->Fix broken packages** from the menus of synaptic, or use the status button in left hand pane to see if broken packages are there; it is a long time since I've had a broken package and I can't remember.

---

### Post by gifford on 2014-04-06
Yes, use synaptic package manager. Select custom filters and it will bring up a choice for broken.

---

### Post by ibjsb4 on 2014-04-06
You need not specify the broken package.  "Edit ->Fix broken packages" will try to repair anything thats broke.

[COLOR=#ff0000]Edit[/COLOR]

[https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages](https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages)

---

### Post by borgward on 2014-04-10
Edit > Fix Broken Packages get "successfully Fixed Dependency Problems"

Status Button - 0 Broken 1 to install/upgrade 

Broken Dependencies:

chromium-browser-l10n
chromium-browser language packages

Installed version Chromium 32.0.1700

Latest vesion 33.0.1750

Bottom of window indicates 0 Broken 1 to install/upgrade 

Apply  

Downloading

An error occured. 

E: chromium-browser-l10n: dependency problems - leaving unconfigured

Changes applied Not all succeeded.

Details:

dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (<< 32.0.1700.107-0ubuntu0.12.04.1~20140204.866.1.1~); however:
  Version of chromium-browser on system is 33.0.1750.152-0ubuntu0.12.04.1~pkg879.1.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 chromium-browser-l10n
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (<< 32.0.1700.107-0ubuntu0.12.04.1~20140204.866.1.1~); however:
  Version of chromium-browser on system is 33.0.1750.152-0ubuntu0.12.04.1~pkg879.1.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 chromium-browser-l10n

Maybe I should remove Chromium and then do updates

Updates were current until right after I installed Chromium.

---

### Post by monkeybrain20122 on 2014-04-10
After you fixed broken you have to restart synaptic. If you just click "apply" they will be broken again. And yes, could also be a Chromium problem. Just don't upgrade it  (not check the box) and wait a few days.

---

