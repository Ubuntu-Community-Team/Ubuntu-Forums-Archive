---
title: "Transfering an inatalation to another, smaller hard disk (not an issue, a question)"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by cm0n3y34 on 2011-06-17
I have a question. This is not an issue anymore, but I am curious to see if anyone can tell me a better solution to this problem, in case I ener have to do this again.

I just finished setting up my computer with ubuntu 10.10(downgrade because compiz in 11.04 hated my computer)
I  then needed the hard disk I had just gotten everything set up on for  another PC. I have 2 other hard disks, a 1TB for data (with 1ooGB free space), with a 6gb swap,  and a 500GB, with 400gb for an ntfs vista partition (for games), a 30gb  recovery partition, and the last 70 I made an ext4 partiton for ubuntu.  The one I was removing was a 500gb disk with ~200GB for the root folder,  and ~300GB for the home folder.( so a straight clone into a 70gb partition  was not going to work) Before wiping the hard disk with my then current  copy of ubuntu, I tried to make a tar.gz file of my home folder with all permissions  intact, but it failed. So I kept the disk I was removing plugged in, and  booted it one last time, did gksu nautilus, renamed the hidden config  folders in the new home folder, and pasted my whole home folder over the  new one. I booted the new one, to find lots of sanity check errors (I  forgot to chown the files from root to my name) 
I started changing  permissions for the folders and files in nautilus ONE AT A TIME, then I  realized this will take forever with 16,000+ files...
So I did sudo chown -R cm0n3y34:cm0n3y34 ~/ (or something like that)
it now seems stable, and kept all of my settings, except compiz and emerald, which didn't take long at all. 
Sorry for the drawn out explanation...

My  question is, is there an easier way to transfer everything to another  hard disk, possibly including possibly everything I installed, even on a smaller hard disk, assuming the data fits? I did  this going off the theory that if most, if not all, of the settings are  in the dot folders in the home folder, copying those will make my life a  lot easier.

---

### Post by Bobhuber on 2011-06-17
> **cm0n3y34 said:**
> I have a question. This is not an issue anymore, but I am curious to see if anyone can tell me a better solution to this problem, in case I ener have to do this again.

I just finished setting up my computer with ubuntu 10.10(downgrade because compiz in 11.04 hated my computer)
I  then needed the hard disk I had just gotten everything set up on for  another PC. I have 2 other hard disks, a 1TB for data (with 1ooGB free space), with a 6gb swap,  and a 500GB, with 400gb for an ntfs vista partition (for games), a 30gb  recovery partition, and the last 70 I made an ext4 partiton for ubuntu.  The one I was removing was a 500gb disk with ~200GB for the root folder,  and ~300GB for the home folder.( so a straight clone into a 70gb partition  was not going to work) Before wiping the hard disk with my then current  copy of ubuntu, I tried to make a tar.gz file of my home folder with all permissions  intact, but it failed. So I kept the disk I was removing plugged in, and  booted it one last time, did gksu nautilus, renamed the hidden config  folders in the new home folder, and pasted my whole home folder over the  new one. I booted the new one, to find lots of sanity check errors (I  forgot to chown the files from root to my name) 
I started changing  permissions for the folders and files in nautilus ONE AT A TIME, then I  realized this will take forever with 16,000+ files...
So I did sudo chown -R cm0n3y34:cm0n3y34 ~/ (or something like that)
it now seems stable, and kept all of my settings, except compiz and emerald, which didn't take long at all. 
Sorry for the drawn out explanation...

My  question is, is there an easier way to transfer everything to another  hard disk, possibly including possibly everything I installed, even on a smaller hard disk, assuming the data fits? I did  this going off the theory that if most, if not all, of the settings are  in the dot folders in the home folder, copying those will make my life a  lot easier.
fsarchiver

---

### Post by cm0n3y34 on 2011-06-17
> **Bobhuber said:**
> fsarchiver

I figured there would be some program for just that. Oh well, I guess you learn something new everyday.
Thanks!

---

