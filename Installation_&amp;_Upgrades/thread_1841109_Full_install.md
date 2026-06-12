---
title: "Full install"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by Brizlitman on 2011-09-08
I used a bootable cd to begin the installation process(the one where you wipe your HD) and i got to the bit where you pretty much have to chose which drive you have to format as well as the 'mount point'. Where do I go from there?

---

### Post by haqking on 2011-09-08
> **Brizlitman said:**
> I used a bootable cd to begin the installation process(the one where you wipe your HD) and i got to the bit where you pretty much have to chose which drive you have to format as well as the 'mount point'. Where do I go from there?


Follow the instructions given ;-)

what point are you at ?

you mean the mount point ?

have you cerated one partition, manual or automatic ?

if its manual and created only one then you mount it as /

what version of Ubuntu  ?

need more information ?

---

### Post by Brizlitman on 2011-09-08
Version 11.04. HD(C) has 2 partitions, one containing windows and the other is just 1.31GB of space. the 2nd HD contains what appear to be system files.

---

### Post by Hakunka-Matata on 2011-09-08
1.3 GB space is not enough to get started.
Can you boot the Ubuntu install disk and choose "Try ubuntu without installig"
then come back here and post the output of 
```
sudo sfdisk -luM
```

---

### Post by mastablasta on 2011-09-09
> **Brizlitman said:**
> Version 11.04. HD(C) has 2 partitions, one containing windows and the other is just 1.31GB of space. the 2nd HD contains what appear to be system files.
 
 
wiping HD will also erase windows.
 
it you can install it alongside (if you wish) the partitioning should be done automaticly in this case. also use whole disk (means delete windows) it will also repartition it automaticly unless you select the advanced options.
 
to install it next to windows see how to here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

