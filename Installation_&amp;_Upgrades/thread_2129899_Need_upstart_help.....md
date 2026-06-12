---
title: "Need upstart help...."
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by ghat on 2013-03-27
hi
SO I am using ZFS on Linux through the zol stable ppa, and my newly built system has a LSI MPT2SAS based card. 

There is a ongoing bug, with mpt2sas, in which the ZFS modules get loaded before (or there is some race condition) the mpt2sas has finished. 
We sort of are working around this by adding a "sleep 60" in the mountall.conf (upstart) script so that the zfs is mounted after the mpt2sas 
I believe that I it should be possible to setup some "emit" which can check for the mpt2sas devices instead and then run the mountall functionality. 

Similarly for /etc/init/libvirt-bin.conf I want it to load after /etc/init/mountall.conf has completed... as my VM images are on the zfs pool. 
SO I need to put some 'emit' there too..

However I am not clear of how this emit business works, can someone point to some good understandable documentation ?
emit is very confusing literally,it there also an inject ?

G

---

