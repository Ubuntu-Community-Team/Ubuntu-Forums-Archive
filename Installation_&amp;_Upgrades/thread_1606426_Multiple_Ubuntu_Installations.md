---
title: "Multiple Ubuntu Installations"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by zahid990170 on 2010-10-26
Hi everyone, 

I installed Ubuntu 9.04 X86-64 as a dual OS on my system which already had Windows 7. I ran into some problems during installation of some packages in Ubuntu. Thereafter, my system would not boot into graphical mode, After going through some fruitless tries, I decided to install Ubuntu again. 

I had with me the CD, but it did not offer an option to install/repair my previous Ubuntu installation, and now I have two Ubuntu versions and a Windows 7 on my system. 

Is it possible that I could delete the partition of my previous Ubuntu OS (since it does not have any useful data as yet), and assign that space to new Ubuntu installation. I can use the gParted software. This is how the Partition Editor looks like (in textual):



/dev/sda3                           extended              24.99 GiB
           
              /dev/sda7             ext3                     2.33 GiB
              /dev/sda8             linux-swap            172.54 MiB
              /dev/sda5             ext3                     22.32 GiB
              /dev/sda6             linux-swap            172.54 GB

Here,   /dev/sda5 and  /dev/sda6  account for the old Ubuntu installation, whereas  /dev/sda7 and  /dev/sda8 account for the new one. 

What is the safe way to remove the old paritions and assign the space to the new partition. Would it create any problem for the dual boot up. 


Sincerely, 

Zahid Iqbal

---

### Post by drs305 on 2010-10-26
zahid990170,

Welcome to Ubuntu and the Ubuntu forums.

If you boot to your normal installation you can unmount and delete sda5 and sda6 with Gparted. You will not be able to move or expand your remaining (current) partitions. To do that, you would have to do so via the LiveCD since you cannot unmount a running partition.

For safety, I would probably delete the sda5 and sda6 from your running Ubuntu. Since you would not be able to unmount your current partition, it would be impossible (almost) to delete them via Gparted.

After deleting sda5 and sda6, and before rebooting, I would reinstall Grub just to make sure it still recognizes your current setup:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

At that point, I would reboot to make sure everything still boots correctly. Then I would boot the LiveCD and move your existing partitions to the start of the extended partition. Note that is going to take a long time (perhaps hours). Another option would be to use the space to the left as a large data partition, which would take very little time to set up.

When you are done with this, if you run "sudo fdisk -l" (lowercase L) it will say that your partitions are not in disk order. That is something we can fix after your partitions are where you want them to be.

---

### Post by oldfred on 2010-10-26
+1 on drs305's suggestions.

I prefer the use of the space as a data partition or as a /home. You can move your current home into a separate /home partition if you want.
I just do not like moving the start of a system partition left as it takes a long time and sometimes can cause issues.


Three version essentially the same, just using different commands to copy data.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
cp without -a and copying as sudo root takes ownership (not good)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by zahid990170 on 2010-10-27
thanks drs305, 

I seem unable to delete the partitions sda5 & sda6 from running ubuntu. It asks me to unmount sda7 & sda8 first. I cannot unmount sda7 as it is busy.

Can I do the same via live CD ? when using the live CD, if I delete the partitions, and then use the terminal to execute the following code

sudo grub-install --recheck /dev/sda
sudo update-grub
before restarting my system. Would the above commands have the desired effect. 

 thanks, 

Zahid

---

### Post by drs305 on 2010-10-27
> **zahid990170 said:**
> Can I do the same via live CD ? when using the live CD, if I delete the partitions, and then use the terminal to execute the following code

sudo grub-install --recheck /dev/sda
sudo update-grub
before restarting my system. Would the above commands have the desired effect. 


You can delete the partitions from the LiveCD. The grub install commands would be different (the commands assume your Ubuntu install is on sda7). I'd use the second command just to verify you see your Ubuntu folders before proceeding:
```

sudo mount /dev/sda7 /mnt
nautilus /mnt &
sudo grub-install --root-directory=/mnt /dev/sda
```

Note you do not include the partition number in the last command.

---

### Post by zahid990170 on 2010-10-27
thanks, now the old Ubuntu partitions are deleted, and I have the following situation:

/dev/sda5                   ext3                      2.33 GiB
/dev/sda6                   linux-swap          172.54 MiB
unallocated                unallocated          22.49 GiB

I want to resize sda5, the main ubuntu partition to contain the unallocated space. I can resize the sda6 to contain the unallocated space but can't do it for sda5 since it is not adjacent with unallocated space. 

How can I do that ?

I would like to have the bigger sda5 since currently its not enough for the regular system updates even. 

Thanks,

---

### Post by drs305 on 2010-10-27
The easiest way to do this will be to just delete the swap partition, then expand your Ubuntu partition to include as much space to the right as you wish, then recreate a new swap partition after that.

You will have to edit your fstab to note the new swap partition UUID or device after you have created it, since the device name (sda6) and/or UUID may change.

---

### Post by zahid990170 on 2010-10-29
thanks drs305,
the problem was successfully solved.

---

