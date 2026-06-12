---
title: "Dual Booting Vista and Ubuntu - getting errors"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by kylecchh on 2007-10-14
Hello everyone, 

(I'm a little new at Ubuntu so bear with me)

I've been planning to dual boot Ubuntu and Windows Vista for a while now, and I'm now doing it. I'm installing Ubuntu 7.04, and I am having some problems. I have all of my partitions created for the install, then, got to where it was preforming the partition actions. I get the following error: 

[I]Failed to unmount partitions

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points cannot be unmounted:

/media/Windows\040Vista

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions 
again?[/I]

I get the following options: Go Back and Continue, both which lead me back to the partitioner.

Is Windows Vista declining the install? Wouldn't be amazed if it is.

Thanks for any replies in advance,

Kyle

---

### Post by kylecchh on 2007-10-15
Sorry for double posting - but I really need help on this error. :(

---

### Post by arashiko28 on 2007-10-15
How did you created the partitions? Did you formatted the new partition after creating it? As I've heard vista is a major headache for double booters. And need to create the partition with vista, check around there are tons of post telling how to do it.

---

### Post by kylecchh on 2007-10-15
> **arashiko28 said:**
> How did you created the partitions? Did you formatted the new partition after creating it? As I've heard vista is a major headache for double booters. And need to create the partition with vista, check around there are tons of post telling how to do it.


I created it with gparted in the Ubuntu 7.04 installer live cd, and yes, I did format it.

Could I get a link to one of the posts on how to create the partitions in vista? :)

---

### Post by arashiko28 on 2007-10-16
Something that might be a problem:_ you created the new partition from a live CD of Ubuntu, I have been told a thousand times that it has to be created from Windows, in your case, Vista._ Now I must remark that this was given to me while compiling enough information to do it, but i have not had the time to sit and do it. So, under your own risk...

You have to install vista first, then create the partition and then install Ubuntu.

Here are some links you might be interested in:

[http://ungeeking.net/2007/04/09/dual...ta-and-ubuntu/](http://ungeeking.net/2007/04/09/dual...ta-and-ubuntu/)
(on HP dv600t)
[http://www.linuxdevcenter.com/pub/a/...ot-laptop.html](http://www.linuxdevcenter.com/pub/a/...ot-laptop.html)
(ubuntu + XP on laptop)
[http://apcmag.com/5046/how_to_dual_b...nstalled_first](http://apcmag.com/5046/how_to_dual_b...nstalled_first)
[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

Since I won't be able to do it until november, when my midterms ends, please let me know how did it turned out.
Best of lucks

---

