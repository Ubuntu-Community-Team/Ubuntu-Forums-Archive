---
title: "Raid 0+1.. an Act of God?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Eric the Red on 2007-10-21
I'm thinking about creating a fileserver with 4x1TB drives and I'd be configuring raid 0+1. However, before I went out and bought the drives for my (yet to be created server), I did a quick google search. Apparently, on the installation of Ubuntu - the kernel can't be configured to stripping and mirroring at the same time (i.e - raid 0+1).

 Has anyone accomplished this feat of raid 0+1? If so, what should I be using (software or hardware raid)?? OMG, I'm so lost.

Any help would be greatly appreciated.

---

### Post by Eric the Red on 2007-10-21
Nobody has setup raid 0+1 and is willing to talk about it??

---

### Post by Eric the Red on 2007-10-21
It's been almost 12 hours so, I'm bumping.

---

### Post by jaygo on 2007-10-22
I'm currently migrating my system from 2 drives in raid 1 to 4 drives in raid 10 (a stripe of mirrors). Since I'm migrating instead of reinstalling, I can't tell you what options the installer gives *for sure* but I believe it offers 0,1,5, and 10. Download the 'alternate' cd for ubuntu or kubuntu and go through a trial run. If you only have one or two drives to test with, just make four even-sized partitions during the install, then it will give you the option to setup RAID and you can see just what it will do.

I would recommend real hardware raid over software raid any day, but real HW controllers are about $360 & up (quality 3ware). So at the moment, I'm content with the free raid :).

BTW, raid 10 > 0+1
> RAID-10 and RAID-01 are not the same thing and it does matter. RAID-01 is a mirrored configuration of two striped sets. RAID-10 is a stripe across a number of mirrored sets.
RAID-10 provides better fault resilience and "rebuild" performance than RAID-01.
from [http://www.easeus.com/resource/raid10.htm]("http://www.easeus.com/resource/raid10.htm")

Let us know how it goes.

---

### Post by Eric the Red on 2007-10-22
To Be honest, I wasn't expecting a reply.. after bumping the thread a few times - I gave up. So, thanks a lot for a reply!! I'll look into raid 10 instead of raid 0+1. Nice to know I can still stick with Ubuntu.

---

### Post by jaygo on 2007-10-23
all's well that ends well, I guess. I ran the 7.04 alternate installer last night and found that it only offers raid 0,1, and 5. You can use LVM to create another layer on top of your raid arrays, and LVM lets you choose striping or mirroring, so in effect, that can give you nested raid levels (0+1, 10, etc.). However, my best googling shows that there might be a performance drop when using LVM instead of true software raid (mdadm), so I'm not using it. That would probably be a fine choice for your file server tho. Ask around for more intel on LVM.

So what your googling showed seems correct: you cannot use the installer to setup software raid 10 in debian / ubuntu ... it has to be done manually, and then an existing install can be copied / migrated over to it.

That said,I'm experiencing problems getting grub to recognize my raid 10 setup. It seems to simply load all of the simple raid 1 arrays, then think that it's done. Since it can't assemble a raid 10 array until the two raid 1 arrays are first assembled, then it just skips it.

Sooo, for now, I'm having no luck with software raid 10. Will be back once I come to a conclusion tho.

---

### Post by jaygo on 2007-10-25
giving up. See my post:
[http://ubuntuforums.org/showthread.php?p=3629417#post3629417]("http://ubuntuforums.org/showthread.php?p=3629417#post3629417")

raid 0 & raid 1 work fairly easily if you use the alternate installer. Just remember that grub & boot need to be installed onto a non-raid partition.

GLHF

---

### Post by Eric the Red on 2007-10-25
Thanks a lot for the time that you put into this.

---

