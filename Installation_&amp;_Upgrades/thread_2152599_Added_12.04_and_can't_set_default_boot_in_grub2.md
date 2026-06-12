---
title: "Added 12.04 and can't set default boot in grub2"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by JimLS on 2013-06-08
Have 11.10 with mythtv.  (HVR1600 tuner and FX5200 nvidia card).  System was working fine but thought I would move to newer.  Added 12.04.  12.04 has errors on boot so want to make 11.10 default boot until I figure that out.  Went into /etc/default/grub and changed GRUB_DEFAULT to 4 (the latest kernel for 11.10 - it boots fine if selected manually).  I got the number from counting the lines displayed by grub when booting starting at 0.  Then ran 
sudo update-grub
which seemed to complete normally.  But the system still hangs on booting unless I manually select 11.10.  When booting the highlighted line is the first one (not sure if it should highlight the 5th one as the one that should boot).  I still have to manually select 11.10.

I ran:
 grep menuentry /boot/grub/grub.cfg

and the 11.10 entry was the first item displayed.  Not sure how to interpret this but it seems that this would be the item used for boot?

---

### Post by oldfred on 2013-06-08
It depends on which grub is in MBR. Then that systems grub.cfg is the one used to boot. Usually the last system installed will be the one in the MBR. But if you boot 11.10 then that grub.cfg is not used except by sudo update-grub in 12.04 to add latest entries into the 12.04 grub.cfg.

Easiest way may be just to install 11.10's grub2 boot loader to the MBR. Boot into 11.10 and run sudo grub-install /dev/sda.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

