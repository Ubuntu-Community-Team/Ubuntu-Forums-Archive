---
title: "KUBUNTU won't mount CD-RW"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by adampyre on 2007-06-01
Hello,

I have decided to pull a "Mark Shuttleworth" after using Ubuntu on my laptop, I wanted to try Kubuntu on my desktop. (Apparently Mr. Shuttleworth uses Ubuntu on his laptop and Kubuntu on his desktop too)...

anyway, I have a problem that a few hours of scouring the forums has not solved. 

I installed Kubuntu using the live cd. I rebooted, everything is fine, but when I load a CD-Rom, my CD-RW does not mount. I checked the fstab and it shows:

/dev/scd0          /media/cdrom0     udf,iso9660 user,noauto     0     0

I attempted to mount /dev/scd0 and /media/cdrom0 and I get the same message each time: special device does not exist.

any suggestions?

Thanks,

Adam

---

### Post by adampyre on 2007-06-01
Ok, so I rebooted and now it mounted... ? The only thing I did differently is that right after I loaded grub, I inserted the cd... hmm.....

---

