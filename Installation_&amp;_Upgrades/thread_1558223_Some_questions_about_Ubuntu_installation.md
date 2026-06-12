---
title: "Some questions about Ubuntu installation"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by Captain_Falafel on 2010-08-21
When I partition my hard drive during installation, I will give the ubuntu system a partition (~ 30 GB) and the "Data" (2nd bigger partition) files a partition as well. (and a swap)

1) What will giving a mount point to the "Data" partition do? Will it be mounted during startup? And can if so, can I make up my own mount point, such as /mnt/Data/? If it doesn't get mounted during startup, is there a way to get it mounted like that during installation?
2) Will this allow me to do a fresh install of Ubuntu without wiping over the "Data" partition and keeping everything stored on "Data" untouched?

I've always installed Ubuntu over the entire disk with no partitions and got tired after fresh installs and having to wipe everything, especially every 6 months :P

Thanks in advance

---

### Post by dagdeniz on 2010-08-22
Normally, you can install Ubuntu to any part of the harddrive. However, by default, it either resizes an NTFS part or uses the entire disk. 
It seems that you choose to use the entire disk every time. It At the phase of preparing the partitions, you'll have to choose to "Specify Partitions Manually". There you'll choose a root (system) partition, a /home partition if desired (home keeps your configuration and private files, that's actually what you want) and a swap area. If you assign the same /home partition after a re-install (again, of course, by specifyin partitions manually), all of your configuration and data will of course be kept. 
The link below shows it with pictures if you want: 
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Captain_Falafel on 2010-08-22
Thanks! that did it :)

---

