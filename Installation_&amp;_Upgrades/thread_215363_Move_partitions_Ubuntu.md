---
title: "Move partitions Ubuntu"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by caryb on 2006-07-13
Hi, I tried to install Dapper to my AMI 466 raid but unfortunatly it wasn't recognised during the setup, so I installed it to a single 18gb scsi with the  other raids in place. After install & upgrades the raids are now seen in qtparted. My disk arrangement is sda 18gb disk with Dapper on it & sdb 1 x 146Gb raid 5 & sdc 36gb raid 5. 

What I want to do is copy the whole sda -> sdc & create a single partition for sdb for some forum software (local Aquarium club)

Can anyone help a poor comming up to speed Linux noobie?


Cary

---

### Post by caryb on 2006-07-14
Ok have dd'd the partition! now how do i mount it to edit /etc/fstab & grub so I can boot it?



Cary

---

### Post by koshari on 2006-07-14
use gparted.

---

