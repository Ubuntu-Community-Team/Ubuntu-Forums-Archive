---
title: "Problems Installing Hardy on P5W DH Intel RAID 0"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by UberBock on 2008-06-24
So thanks in advance to all who can help on this...

I am trying get Hardy installed on a ASUS P5w DH via the Intel RAID.  So I have read a few forums about how to proceed and I am using the Live CD and getting dmraid installed first and then using fdisk to partion the RAID 0 array such that I have a /boot, /, and Swap partions.  I can format the partions and then change the swap to type 82 and turn it on.  SO then per some forum posts one should be able to install everything via the normal way except that in the manual partion section one has to select the 2nd set of partions that is displayed and change the mount points.  I do that but when things are being formated it halts with an error about not being able to mount the Swap.
ok
so I thought about when I was trying Suse11 and it seemed to indicate that the Swap had to be on a mirror array and not a stripped.  So I connected another drive to the system and put the swap on that drive.  This time all went well; up to the point that the LiveCD install complained about not installing GRUB (but the is something that I expected).

SO the question is do I have to use the other drive for the swap or am I doing something wrong here.  

I guess I would comment to those who can influence the next release of Ubuntu that they should really consider expanding the support of RAID.  It would seem that since alot of the MB that are available today have some sort of RAID (ok its not true hardware RAID) options that making it a tad easier to install Ubuntu on a RAID array would be nice.

---

