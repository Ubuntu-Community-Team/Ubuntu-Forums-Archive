---
title: "Dependency Hell..."
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by sean.travis.taylor on 2009-12-28
Hello everyone recently upgraded a desktop from 9.04 to 9.10. This machine does not currently have internet access. I installed APTonCD on a wireless netbook running 9.10 and copied all the packages on the netbook to an ISO. I burned the iso image to a CDrom using desktop's burner. After burning the disc and re-inserting it into the desktop's CDrom the desktop immediately detected an APTonCD restore disc. I then selected "restore" from the APTonCD program to restore the packages from the CD onto the desktop. APTonCD looked as though it did this. When I opened Synaptic the packages on the disc I burned were categorized under the Not Installed section. When I tried to mark them for installation individually I get a dependency hell situation in which no package can be installed because it depends on other packages which are either available but not being installed or not installable because they are not available. I assumed using APTonCD would restore not only the packages but also their dependencies as well. What am I doing wrong?

I simply want to copy the packages from my netbook to my unconnected desktop.  

Opinions? 

Thanks for any assistance anyone can provide in advance.

Sean.

---

### Post by avtolle on 2009-12-28
[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html) It appears from the on-line manual that one must do more than just copy the cache. Did you use the "Auto Select Dependencies" option as mentioned?

---

