---
title: "Extracted apps not replacing previous versions"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by northie1 on 2011-11-11
As a newby, I'm pretty happy with Ubuntu 11.10 just installed.  However, I observed that there were updates of Firefox, Thunderbird as well as clamtk available, so I downloaded these and extracted them.  I expected them each to over-write the previous versions, but that hasn't happened.  Have I missed something here?:)

---

### Post by lisati on 2011-11-11
What sometimes happens is that the versions of apps shipped with Ubuntu have had some customizations done, including installing components to different folders, that the downloads from the "official" site don't take into account. Most of the time I'm happy to update using the update manager, which takes the differences into account. Failing that, you can uninstall the default versions first using the software center or synaptic.

---

### Post by ottosykora on 2011-11-11
not sure where and how you did download those files.

In general, updates are done by the update manager , or in terminal with command 

sudo apt-get update 

and this will check for new versions in the repository.

One can download for example the latest version of clamtk some days before it arrives in the repository. This needs to be the .deb file and you can install it either with the software center or gdebi installer for example. (not unpack it, it works on its own)

With Firefox and Thunderbird, you have to update them via the repository the best. The deb files floating around in the net may  not be always suitable for ubuntu and mozilla has AFAIK only targz pack at their download.

---

### Post by northie1 on 2011-11-12
Thks, will do

---

### Post by lovinglinux on 2011-11-12
Firefox will be available in the repositories once they fix some issues.

Check [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

