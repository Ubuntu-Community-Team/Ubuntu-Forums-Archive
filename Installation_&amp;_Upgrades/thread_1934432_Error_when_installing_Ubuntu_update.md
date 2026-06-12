---
title: "Error when installing Ubuntu update"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by khosro on 2012-03-02
Hello,
Yesterday i decided to update my Ubuntu 11.10.
Progress bar of update completed 90% but suddenly my network cable disconnected and an error occurred and installation of updates stopped.
An error is as following :
> 
Downloading...
--2012-03-01 19:48:55--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.1.102.62.orig.tar.gz)
Resolving archive.canonical.com... failed: Name or service not known.
wget: unable to resolve host address `archive.canonical.com'
download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-downloader:i386:
 flashplugin-downloader:i386 depends on flashplugin-installer (>= 11.1.102.62ubuntu0.11.10.1); however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-downloader:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:



I think update manager wanted to download flash player but because my network cable disconnected it failed.After that, again open Update Manager but it said that all of updated installed,but as i said an error occurred during update installation.Why Update Manager did not continue update installation?After that i uninstalled and then installed flash player by Synaptic Package Manager manually.Did i do right thing(manually installing flash player)?
How can i ensure myslef that all of updates installed correctly?

Khosro.

---

### Post by Paddy Landau on 2012-03-02
Open a terminal and enter the following four commands (one at a time).
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```

---

