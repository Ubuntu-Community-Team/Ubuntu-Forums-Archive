---
title: "The creation of swap space in partition #5 of SCSO1 (0,0,0) (sda) failed."
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by fosbinder on 2013-04-03
So I messed up the installation of Ubuntu 12.10 and now am trying to reinstall.. have been for a few hours and no luck.. I tried the GParted Method and was unable to remove the partitions for reasons nobody could figure out and now i tried without doing that and am getting this error.. 
There is no data to be saved.. im just trying to install an OS on an empty laptop

---

### Post by fosbinder on 2013-04-04
i think im wearing out my browsers refresh button

---

### Post by fosbinder on 2013-04-04
I will be back in the morning and here posting as many threads as needed to get some help..I cant refresh my browser for more than 5 hours strait..

---

### Post by oldfred on 2013-04-04
Gparted can only work on unmounted partitions. So you have to use liveCD/DVD/Flash drive. Also most liveCD mount an existing swap which typically mounts the extended partition as swap is normally inside the extended. Then you cannot work on any logicals unless you click on swap and right click swap off.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

