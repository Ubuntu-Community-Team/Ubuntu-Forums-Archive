---
title: "Re-installl with a previous raid"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by neuman1812 on 2012-12-24
Just reinstalled ubuntu 12.04 64bit.   Also installed mdadm.

Ran apt-get upgrade   to be sure system is uptodate.

Trying to get a previous raid array to be recognized.

In disk manager  The 2 drives are recognized as being part of the raid.  When I click on "Start Array"  I get the error 

```
Not enough components available to start the RAID Array
```

Command line gives me 
```

$ mdadm --assemble --scan
mdadm: only give one device per ARRAY line: /dev/md/New and RAID
mdadm: only give one device per ARRAY line: /dev/md/New and Array
mdadm: only give one device per ARRAY line: /dev/md/New and RAID
mdadm: only give one device per ARRAY line: /dev/md/New and Array

```

mdadm.conf is
```


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/New RAID Array metadata=1.2 UUID=114c06b7:daf49114:8ec76317:7758d346 name=New RAID Array

# This file was auto-generated on Mon, 24 Dec 2012 13:19:24 -0500
# by mkconf $Id$

```

Im guessing I have to modify the line 
```
# definitions of existing MD arrays
```
But I cant find what it should be.

---

### Post by steeldriver on 2012-12-24
it looks like you are trying to use a RAID array name with spaces in it

```
/dev/md/New RAID Array
```I believe it's more usual just to use a numeric identifier - for example mine is

```
ARRAY /dev/**md0** metadata=1.2 name=htpc-01:0 UUID=XXX...
```If you don't have any other arrays then I would think it's OK to use /dev/md/md0

However it may be better to comment out that line altogether, assemble the array by mdadm --assemble --scan, and then auto-generate an up-to-date entry using mdadm --detail --scan  

**I'm not 100% sure of the syntax for that so you should check it** - something like

```

sudo mdadm --assemble --scan
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf
```That should take care of the UUIDs as well in case they are out of date

See 

[http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

---

### Post by neuman1812 on 2012-12-26
This line here
```
# definitions of existing MD arrays
ARRAY /dev/md/New RAID Array metadata=1.2 uUID=114c06b7:daf49114:8ec76317:7758d346 name=New RAID Array
```

is the default line that was in the config file.  For testing I just commented it out.  I was then able to rebuild the array with disk manager.

---

