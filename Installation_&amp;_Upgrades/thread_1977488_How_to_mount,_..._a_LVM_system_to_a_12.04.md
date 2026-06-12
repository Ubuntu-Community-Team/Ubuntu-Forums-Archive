---
title: "How to mount, ... a LVM system to a 12.04?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-10
I had used in the past from 7.04 till 11.10 a LVM system.

Now I installed a new system 12.04 on a new hard disk. 
How can I get access to the old LVM drive?
I can now only see the boot partition.

---

### Post by darkod on 2012-05-10
This link talks about activating LVM from live mode, to copy data:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

But the same would apply if you do it from your regular installation. Install the lvm2 package, activate the LVM and then simply create an entry in /etc/fstab to mount it on every boot. Something like:

/dev/VolGroup-LogVol   /moint-point   ext4   defaults   0   0

Note that if you used a filesystem other than ext4 on the LVM, you will need to use the correct one in the fstab entry. Also, create the mount point you plan to use first, if it doesn't exist.

That should do it. Even before restarting, after you edit fstab, you can check if it will work with:
sudo mount -a

If it reports errors, something is wrong with the entry.

---

### Post by ELMIT on 2012-05-10
(why is it so, that after you post a question, you find all the answers???)

Thanks for your help.

I solved it in this way:

1. fdisk -lu  
2. pvscan
3. vgscan
4. vgchange -a y  
5. lvscan
6. sudo mount /dev/lvmvolume/root /mnt/LVM/root  (all we got in 5.)

Thanks!

---

