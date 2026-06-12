---
title: "Switch from WUBI to Dedicated drive/partition"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by stewbaby on 2010-03-26
Hi there. I have Jaunty installed as a WUBI install, and I now wish to give it space of its own. Can someone confirm that what I need to do is:

* backup/gzip from / down to an external location
* uninstall WUBI
* install the same Ubuntu version to its own partitions
* boot to and unzip backup to root
* reboot and be happy ;)

If not, would it be better to wait for 10.04 to do all this?

---

### Post by oldfred on 2010-03-27
You do not need to backup root (/). All you settings and files are in /home. 
If you have installed a lot of applications you can from synaptic or the command line export a list and reinstall that list. But you may install some older version when newer versions  have replaced them. (I did this a version or two ago and reinstalled python 2.4 & 2.5 when only the newer 2.6 was needed, for example)

If you have space you can install the new version and mount the wubi root file and copy files directly over.

---

### Post by stewbaby on 2010-04-02
> **oldfred said:**
> You do not need to backup root (/). All you settings and files are in /home. 
If you have installed a lot of applications you can from synaptic or the command line export a list and reinstall that list. But you may install some older version when newer versions  have replaced them. (I did this a version or two ago and reinstalled python 2.4 & 2.5 when only the newer 2.6 was needed, for example)

If you have space you can install the new version and mount the wubi root file and copy files directly over.

Thanks, but as I have a fully working WUBI install, and I pay arms legs and other limbs for my 'net connection , I didn't want to have to re-download everything. Can I simply move my WUBI install?

Stewbaby

---

### Post by bumanie on 2010-04-02
This may help [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

