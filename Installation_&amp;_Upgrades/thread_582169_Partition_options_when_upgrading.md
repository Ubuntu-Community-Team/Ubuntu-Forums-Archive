---
title: "Partition options when upgrading"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by schauerlich on 2007-10-19
I'm upgrading to Gutsy from Feisty using the alternate CD on a 2nd gen Macbook dual-booting Ubuntu and OS X , and I'm not sure what to do with partitioning. I want to replace my Feisty install with Gutsy without affecting the OSX install. My options are:

Guided - resize SCSI3 (0,1,0), partition #3 (sda) and use freed s
Guided - use the entire disk
Guided - use the largest continuous free space
Guided - Use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

My first guess was the first option, but I'm pretty new and I don't feel like accidentally erasing my hard drive from a wrong guess... Thanks in advance.

---

### Post by tamman2000 on 2007-10-19
It looks like you are trying to do an installation rather than an upgrade...

You should be able to boot feisty, and run the update manager to take care of everything...

see this page:  [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

that would install everything for gutsy in your existing feisty partition(s)

---

### Post by schauerlich on 2007-10-19
I can't get into GNOME from a botched attempt at Beryl, so that's why I'm installing via the alternate CD.

---

### Post by tamman2000 on 2007-10-19
I think you might be able to try this

gksu "sh /cdrom/cdromupgrade"

?

---

### Post by timotter9 on 2007-10-23
> **tamman2000 said:**
> It looks like you are trying to do an installation rather than an upgrade...

You should be able to boot feisty, and run the update manager to take care of everything...

see this page:  [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

that would install everything for gutsy in your existing feisty partition(s)

The answer I was looking for ... Thanks! :KS

---

