---
title: "server 7.04 disk partioning"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by jdereku on 2007-10-05
I am fairly new to Linux so have patience.  I setup the desktop version and refreshed my memory of commands etc (My old Unix days are pretty far behind me)

I am now trying to setup a server, I have a box with 2 250 sata drives in it.  I would like to setup one drive as my working drive with a /vmfs partition for running vmware images in.  I have gone through the guided setup to see the default and would like to now do it manually.  I am not sure of what partitions need to be there (/, swap, etc) and how to set them up.  Once the first drive is up and running, my next project will be software raid 1 with the second drive but I will worry about that later.

Any help or pointers to tutorials for the manual partitioning step would be appreciated.

Derek

---

### Post by Pumalite on 2007-10-05
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by lennartack on 2007-10-05
> **jdereku said:**
> I am fairly new to Linux so have patience.  I setup the desktop version and refreshed my memory of commands etc (My old Unix days are pretty far behind me)

I am now trying to setup a server, I have a box with 2 250 sata drives in it.  I would like to setup one drive as my working drive with a /vmfs partition for running vmware images in.  I have gone through the guided setup to see the default and would like to now do it manually.  I am not sure of what partitions need to be there (/, swap, etc) and how to set them up.  Once the first drive is up and running, my next project will be software raid 1 with the second drive but I will worry about that later.

Any help or pointers to tutorials for the manual partitioning step would be appreciated.

Derek
Gparted is a program that can do everything with a user friendly interface, and it's in the live cd. Just run "gparted" at the command line.

I recommend using ext3 for all your partitions, and make one little swap partition(just swap, +-500MB, no mount point, linux detects is automatically).

If you want to install the latest ubuntu every time a new one comes out, you might want to keep your old data. In that case it's usefull to have a "separate home partition". Create an extra ext3 partition to store all your personal files in and at the installation choose to mount this partition at /home(at the manual disk configuration).

---

