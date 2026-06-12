---
title: "installing karmic to replace xp"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by amd-vagabond on 2010-05-06
any help would be highly appreciated!

trying to install ubuntu 9.10 ( just got it from the mail):

main harddrive is 160G with following configuration

partition 1 ( D ) : files
partition 2 ( C ) : windows xp
partition 3 ( E ) : files

how to install ubuntu at C, and replace os.

thanks

---

### Post by halj32 on 2010-05-06
boot from the live CD, use gpart to delete "C" leave it as unformated.
then install Ubuntu to the largest free space.
this is probably the easyest way to do it if your not used to using linux.
remember it wont be called "C" after youve installed linux
good luck

---

### Post by nitstorm on 2010-05-06
Or

Once you are in the installation process where you need to select the partitions for Ubuntu. 
Select Manually Specify Partitions
There delete c:\ and create a new partition for the Ubuntu install and swap(1 or 2 Gigs are enough for swap) 
(for the Ubuntu install - the mount point should be [B]/
[/B]and for the swap area - the mount point should be **swap**)
(or) Choose c:\ select the mount point as **/** and it make sure the format box is checked.

Personally I'd go with the first method where C:\  is deleted and new partitions for Ubuntu and Swap are created.

---

### Post by amd-vagabond on 2010-05-18
halj32 / nitstorm,

thanks for the response and help!!!
sorry for the late reply....

thanks again guys!

---

