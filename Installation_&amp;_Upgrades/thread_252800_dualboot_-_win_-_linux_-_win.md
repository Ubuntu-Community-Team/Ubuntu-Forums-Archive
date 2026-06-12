---
title: "dualboot - win - linux - win"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by carlossousa on 2006-09-07
Hi there,

I normally install ubuntu on a machine *after* I install windows because if I do it the other way round, I dont know how to instruct the grub boot manager to rebuild the menu so grub takes control of the MBR.
Any ideas?

Thanks

---

### Post by publicv on 2006-09-07
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstalling+grub")

---

### Post by nothingworks on 2006-09-07
I had the same issue.
/dev/hd0 had windows98
I created /dev/hd1 as the root partition for ubuntu, and installed it there

Issue: after installing ubuntu (no choice offered in the live cd install as to where to put grub ](*,) , otherwise I always choose to install it on the root partition) the windows 98 option of the grub menu would just hang. :confused: 

Solution::) 
- make sure grubs menu.lst has root=/dev/hd0 and chainloader for the windows section. (savedefault is not needed)
- boot off a win98 startup/boot disk and transfer system files to c: I think it updates the windows partition as well.
i.e boot from floppy "without cdrom support"
run "sys c:"
note: you may need to extract sys.com from ebd.cab using the extract command first.

Windows boots from grub normally after that

---

