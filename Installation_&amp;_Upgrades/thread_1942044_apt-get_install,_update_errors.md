---
title: "apt-get install, update errors"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by KernelKlink on 2012-03-16
I issued the commands you suggested/used, and received these errors:

```

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
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
(Reading database ... 245298 files and directories currently installed.)
Preparing to replace flashplugin-installer 11.1.102.55ubuntu0.11.10.1 (using .../flashplugin-installer_11.1.102.63ubuntu0.11.10.1_amd64.deb) ...
update-alternatives: error: cannot stat /usr/bin/firefox: Not a directory
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: cannot stat /usr/bin/firefox: Not a directory
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_11.1.102.63ubuntu0.11.10.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
nspluginwrapper: /usr/lib/flashplugin-installer/libflashplayer.so is not a valid NPAPI plugin
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_11.1.102.63ubuntu0.11.10.1_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not installed.
  Package flashplugin-downloader:i386 is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
Setting up chromium-browser (17.0.963.56~r121963-0ubuntu0.11.10.1) ...
update-alternatives: error: cannot stat /usr/bin/firefox: Not a directory
dpkg: error processing chromium-browser (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of chromium-browser-l10n:
 chromium-browser-l10n depends on chromium-browser (= 17.0.963.56~r121963-0ubuntu0.11.10.1); however:
  Package chromium-browser is not configured yet.
dpkg: error processing chromium-browser-l10n (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-installer

```

Seems like there's a bunch of issues, but I don't know how to solve them.  Your help is appreciated.

Note:  I removed firefox.

---

### Post by oldos2er on 2012-03-16
Post moved to its own thread.

---

### Post by jerrrys on 2012-03-16
Please post the commands you have already used.  And here's a guest.

Open a terminal and enter:

sudo apt-get clean

sudo apt-get update

get any errors?

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

and hay; welcome to the forums :D

---

### Post by raja.genupula on 2012-03-17
Hi Jerry.

@op what you're getting if you did like this ?

```
sudo dpkg-reconfigure flashplugin-installer
```

---

