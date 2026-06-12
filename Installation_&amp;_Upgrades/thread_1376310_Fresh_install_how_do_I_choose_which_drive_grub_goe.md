---
title: "Fresh install: how do I choose which drive grub goes on?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by McQuaid on 2010-01-09
I've used ubuntu for many years, sometimes upgrades or fresh installs, but always could get through installing it.

With the new simplified partitioner during install, I'm a little iffy on things.

The main thing is, I want to choose where grub goes.  Will it default to sda?  I want it on sdb.  On sdb is an existing ntfs filessystem.  The slider will let me set a specific amount for ubuntu, but I don't like it's not clear that the existing used space is an ntfs part.

I would prefer using gparted, I assume there is no way to launch that instead during install.

btw, is there an installation guide for intrepid that doesn't gloss over the partition part of the install?

---

### Post by mikewhatever on 2010-01-09
1. You can choose where to install GRUB by pressing the 'Advanced' button in the bottom-right corner of the window that appears right after all the changes are made and before the file copying begins. The default selection is hd0, which is the mbr of the first hdd. In your case, hd1 is the way to go.
[http://farm3.static.flickr.com/2494/4082797551_bbef800cf8.jpg](http://farm3.static.flickr.com/2494/4082797551_bbef800cf8.jpg)

2. You can use gparted before beginning the installation, in fact, gparted is included with the Karmic live cd. That implies using Karmic, which I'd suggest over intrepid.

---

### Post by McQuaid on 2010-01-09
Also, I read that if there is an existing swap part it will use it by default.  There is an existing swap on sda which I don't want it to use, as this drive will be removed after some backups.

At what point can I manually create a new swap part to be used?

---

### Post by darkod on 2010-01-09
Well if you are creating partitions manually (root, home, etc) it would allow you to create swap the way and where you want it too. Later even if it also uses your other swap, you will just unmount (swapoff) and remove that drive.

---

### Post by McQuaid on 2010-01-09
well, this first drive is dying, so it would be nice to know it's not using the existing swap from the start.

Most install guides gloss over the partition part or go under the assumption it's a blank drive.  The more typical scenario would be someone with an existing OS.  Guides should cover this a little better.

I've done this stuff numerous times in the past with gparted.  Is there a guide for the new 'simplified' partitioner during install?

---

### Post by oldfred on 2010-01-09
I am not sure what is simplified, it is still gparted. I prefer manual partitioning if you understand a little about partitions. Then in the install you choose manual install and tell it each partition to use for what, root, home, swap etc.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

