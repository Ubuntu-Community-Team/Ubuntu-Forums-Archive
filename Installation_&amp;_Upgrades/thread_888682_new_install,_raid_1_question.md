---
title: "new install, raid 1 question"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Moogard on 2008-08-13
Hello,
My set up will be, hopefully, ubuntu 8.04 on a 20g ide hd, with ubuntu booting from this 20g drive.[ I have
two 80g ide hd's that i would like to use for data storage. Is it
possible to set up the two 80g drives as a raid 1? Sorry if this sounds ignorant, but all the raid1 howto's discuss making the drives bootable, adding grub to 2nd drive etc. Can I just set up the 80g's as raid 1 w/o bootable partitions?
I believe I have a handle on partitioning/formating, just confused
about raid. Thanks in advance for any help!

---

### Post by theyranos on 2008-08-13
If it's software RAID you're looking for, make sure both your 80g drives are empty (by which I just mean they don't have useful data you can't lose) and unmounted, then do:
```

sudo apt-get install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/firstdrive /dev/seconddrive

```
replacing /dev/firstdrive and /dev/seconddrive with the device nodes of the partitions on your 80g data drives. (like, /dev/sdb1, for example)

If the apt-get install asks you whether you want MD arrays started automatically, choose "yes." Theoretically, after running those two commands you should see a message to the effect of "array started."

Then, all you need to do is make a filesystem on your new raid array,
[php]
sudo mkfs.ext3 /dev/md0
[/php]
and you should be all set to add /dev/md0 to your fstab and mount.

---

### Post by Moogard on 2008-08-13
Awesomeness! Thank you very much!

---

