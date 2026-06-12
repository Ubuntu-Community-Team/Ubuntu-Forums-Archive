---
title: "Can't install Feisty Server on Compaq Proliant"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2007-04-26
I could at least get through the install process with Edgy.  With Feisty, when it gets to the part about partitioning, it says it can't read the disk geometry or something like that.  It shows the Compaq Smart Array device, so it knows what it is.. it just can't access it to let me partition it for some reason.  In Edgy, this had no problems.

Any ideas??  Is there some boot option that will make this work?

---

### Post by jaydeel on 2007-06-01
Compaq Prolinea ML370 with Smart Array Controller

I am having this exact same issue, Unable to determine drive geometry/size. The raid disk shows up in the list, but the size shows 0G0.  

/dev/ida/c0d0 exists, but no partitions are visible. ie c0d0p1, etc. 

and fdisk /dev/ida/c0d0 isn't able to open the drive either.

Anyone else run up against this? is the option to downgrade to edgy?

I did a dmesg, and found errors identical to the post found below...

> For all 2.6 kernels before 2.6.18 (released Sep 20, 2006), there was a problem with the RAID driver in Linux. The error messages look like: "cpqarray: Finding drives on ida0", "cpqarray: ida0: idaSendPciCmd Timeout out, No command List address returned.", "cpqarray: error sending ID Controller", etc. It turns out that the RAID device would be taken by another driver (sym53c8xx) before the cpqarray driver could claim it.

What confuses me now is that the feisty server kernel is 2.6.20, shouldn't this be fixed?

---

### Post by jaydeel on 2007-06-07
I've gotten the install to work by making a custom cd... see my other post...

[http://ubuntuforums.org/showthread.php?t=384319&page=2]("http://ubuntuforums.org/showthread.php?t=384319&page=2")

---

