---
title: "basic installation messed up by me"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by 558 jakobsson on 2006-04-01
Sorry for this newbie q. I did install 5.10 as a dual together with Win 2K. Then I messed it up trying to get rid of both with the purpose of reinstalling 5.10

It won´t install completely. Complains about existing remains of the old first installation.

I have formatted, I have deleted the partions and even ran a wipe desk which claimed it could erase everything on the desk. It ran for 5 hrs. Still there is data left obviously. The wipedesk was a DOS floppy.

I should like to try 5.10 more. It seemed to be OK but now I am stucked. Reinstalling Win is no prob. I think it has nothing to do with the MBR as I have reinstalled Windows, I have run fdisk /MBR but still I does not succed to install 5.10 again.

The installation screen says debootstrap closes with error (1)
see   /target/var/log/bootstrap.log. for details

How kan I read that file? Through some other linux based distro in a live CD? 

Any hints??
Leif E "558" Jakobsson

---

### Post by SkimWear on 2006-04-01
you can use partition-magic to reformat the partition you are going to use as ext3. then shoot for another ubuntu install. thats the only thing i can think off this late night :\

---

### Post by Sef on 2006-04-01
> you can use partition-magic to reformat the partition 

Do not use partition magic.  There are known issues with it.   Use the partitioner that comes with Breezy's install disk.  You can delete all the partitions and reset them up.

---

