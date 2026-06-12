---
title: "HD crash.. load files from previous installation?"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by jd342 on 2010-06-03
Hi everyone,

My HD with the Windows and Ubuntu (10.04 64-bit) partitions crashed.  I do have a backup HD, and I got Ubuntu installed and running on that.  I can also see the files, both Windows and Ubuntu from the crashed drive, so I was wondering if there's a way to migrate settings and preferences from the previous installation to this one.

Thanks

---

### Post by dino99 on 2010-06-03
maybe your "crashed" partition can be repaired: man fsck

[http://manpages.ubuntu.com/manpages/lucid/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/fsck.8.html)

[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

---

### Post by jd342 on 2010-06-03
I'm pretty sure the HD is physically gone at this point.  I've been having problems with both partitions for a while, and Western Digital's diagnostic software gave me an error code that indicates the drive needs to be replaced.

---

### Post by dino99 on 2010-06-03
in case try booting with [http://partedmagic.com/](http://partedmagic.com/) and check the hdd

or test with [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by varunendra on 2010-06-03
> **jd342 said:**
> Hi everyone,

My HD with the Windows and Ubuntu (10.04 64-bit) partitions crashed.  I do have a backup HD, and I got Ubuntu installed and running on that.  I can also see the files, both Windows and Ubuntu from the crashed drive, so I was wondering if there's a way to migrate settings and preferences from the previous installation to this one.

Thanks

If you can safely recover all the files then maybe you can also successfully clone the partitions ignoring some non-significant errors.
Apart from MBR & Boot-Sector, I think everything else depends upon system files. So if you partition a new HDD identical as the damaged one, put relevant boot-sectors on partitions, restore recovered system files on relevant partitions, then I hope reinstalling only Grub (or Grub2- as the case maybe) on MBR should do the job.
Be cautioned though - it's just a theoretical assumption of mine which is not properly backed up with experience.

---

### Post by jd342 on 2010-06-04
Did some more diagnostic stuff, and the HD is on it's death bed.  I can still access all of the files, but I'm not going to push it and try to boot from it.  

I do have Ubuntu installed on another drive that I'm using now, but there are a few things that I changed in the previous installation, and I forget what I did.

I've been looking into cloning software to copy everything over when I get the new HD, but if there's an easier transfer possible, like transferring settings after a clean install, I'd rather do that

---

### Post by varunendra on 2010-06-05
Whatever I suggested in my earlier post is only my assumption based on very little experience. Hence too little a chance to succeed! It may or may not work.

If you are not concerned about your data but only about settings, then I don't think wasting a lot of time going that way would be a good idea. I mean if it was my case, I'd have had definitely tried it but only because I love experimenting. I can't expect same way about others.

So if you like experiments or if you've got some tool that can easily & safely copy the files, go ahead. But if you are concerned about convenience, I'd suggest to rebuild the settings on your other installation.

As for cloning, I used a combination of 'R-Tools Agent' & 'R-Tools Emergency disk' some time ago to successfully image a dead HDD. But none of R-Tools packages are free.

You may try Clonezilla or PartImage for cloning/imaging purpose.
For straightforward file-recovery, testdisk may serve you best. But integrity of recovered files is guaranteed by no recovery software I'm afraid.

Do post whatever you try. Best of luck!

---

