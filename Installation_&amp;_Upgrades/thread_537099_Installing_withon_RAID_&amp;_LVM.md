---
title: "Installing with/on RAID &amp; LVM"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by SixedUp on 2007-08-28
I've searched through the forums, but advice on this subject is a bit thin on the ground, and it appears that software raid and LVM are both fast moving targets, so much of the advice on the internet is questionable, or just plain out of date.

So ... I currently have a small server with an 80GB "OS" drive, and 2 x 500GB "data" drives. I was planning to simply use the 2 x 500GB drives in a RAID 1 configuration to provide me with resilient data storage space. However, I am having problems with the 80GB drive, and am considering replacing it with another 500GB drive. In theory I believe that that would allow me to define a single partition on each drive, and combine them (using software raid) into a single RAID5 partition, which I can then use as a physical volume for a volume group under LVM.  I can then define logical volumes out of that volume group on which to create my filesystems.

Questions: 
Can I put /boot into that kind of setup? Ie, do Grub and/or LILO understand how to boot a kernel that is under LVM, on a software RAID5 partition?
Is the Ubuntu server installer smart enough to help me set that up, or do I need to do unnatural things? I'm thinking specifically here about how I get the boot manager (Grub or LILO) installed into all three MBR's, so no matter what drive dies, I still have a bootable system ...
Finally, is there anything else that I should be considering?

My backup plan is to have 2 partitions per disk, a small one (for /boot) and the rest. I'll then use either RAID 5 or RAID 1 on the 3 small partitions without LVM, and RAID 5 & LVM on the large ones (as before). Any suggestions on this approach also welcome.

Thanks for any and all recommendations, suggestions and comments.

---

### Post by david3d on 2007-08-29
Boot can not live on a software raid5 but it can live on a Raid1 as each drive is pretty much identical to a stand alone non-raided drive.  With the exception that there is the RAID metadata stored normally at the end of the drives.

The standard strategy for partitioning that I tend to use is this.

```
Disk         Partition        Size                     
 1               1            1GB
 1               2            Rest of Disk
 2               1            1GB
 2               2            Rest of Disk
 3               1            1GB
 3               2            Rest of Disk

```
The first partition on the first 2 drives become a RAID1 set for Boot.  The 1GB partition on the third drive becomes the swap.  Then Raid5 the 2nd partition on each drive and use that for LVM.  Then create your logical volumes for /, home, var, and tmp.

--
David

---

### Post by SixedUp on 2007-08-30
Thanks David, you've pretty much confirmed what I'd managed to glean from around the internet. 

Your recommended approach is close to my backup "plan B", apart from the swap space. It looks to me that you could end up with a broken system if you lost your third drive, and happened to be swapping at the time. Since I only have 1GB of memory, that could be an issue for me, so are there any disadvantages to putting /swap into the LVM, or into another small raid set, similar to the /boot - apart from the overhead of the raid slightly hitting performance of course?

I'm thinking something like:
```

Disk  Partition    Size      Raid?     Use
 1       1         1GB       Raid 1   /boot
 1       2         3GB       Raid 1   /swap
 1       3       The rest    Raid 5    LVM

 2       1         1GB       Raid 1   /boot
 2       2         3GB       Raid 1   /swap
 2       3       The rest    Raid 5    LVM

 3       1         1GB       Raid 1   /boot
 3       2         3GB       Raid 1   /swap
 3       3       The rest    Raid 5    LVM
```

Then (I assume) I could manually install Grub into the MBR of each drive ... so even if my normal boot drive fails, I ought to be able to replace the drive, fiddle with the BIOS, and boot from one of the remaining drives - allowing me to bring the system up and rebuild the raid sets?

---

### Post by proti on 2007-09-03
Hum, why are you putting the swap zone on Raid1 ?

You lose half of it, and it's by definition a scratch zone.
Try to put one partition of swap one each disk and enjoy the doubled swap size :-)

---

### Post by SixedUp on 2007-09-03
Because I want this server to be able to survive a disk failure. Swap space is only a "scratch zone" when you're not using it. I have limited memory, and may sometimes be swapping.

So, if I Raid 1 the swap space I get 3GB of resilient swap space for the cost of 9GB of real space (3 drives remember). Which I agree sounds like a bad idea.  However I'll get increased read performance (and I'm lead to believe that you read from swap more than you write to it) and the ability to keep on running if a drive totally fails, even if I happen to be swapping heavily at the time. 

Since I have 1.5TB of disk available, that 6GB is a relatively small price for me to pay  :)

---

### Post by SixedUp on 2007-09-03
Just to (hopefully) close off this thread:
I have now installed the 3rd 500GB drive, and partitioned the system up as per my second post, using the Ubuntu 7.04 Server CD.  Installation apparently proceeded correctly, but the system failed to reboot. I've spent some time fiddling with it via the rescue function of the CD, and have now finally got it all working.

To do so I applied the changes recommended by [Harald Rudell in bug 126934]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/126934"), and also reinstalled GRUB by hand, into all three disk MBR's, as per the information [on this website. ]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") Finally, I also made the partitions that go to make up the /boot partition bootable, though I'm still not sure if this was needed or not.

I seem to have a huge delay while starting up as the system executes swapon to the 3GB raid partition; over a minutes delay according to the logs, which I didn't expect.  Total startup time is around 2 minutes (on a very low-powered mini-ITX system), but once up and running its very responsive. As I expect to run the system 24x7 and rarely reboot it, I guess I can live with that.

---

