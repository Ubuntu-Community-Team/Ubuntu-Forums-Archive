---
title: "Dual Boot Ubuntu/Desktop 10.10 &amp; Windows7, wanted example of good /etc/fstab file"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Hakunka-Matata on 2011-03-21
Can you post an example of a good Ubuntu/Window7 dual boot single drive /etc/fstab file.  Thanks in advance
HK

---

### Post by oldfred on 2011-03-21
What is the real question? The fstab is not different for Ubuntu, or are you looking at how to mount the windows partition in fstab. I suggest read only with a separate NTFS shared partition set read/write.

I have XP on a different drive so my fstab is not exactly what you want. But, I have seen many posted from boot scripts that get posted.

---

### Post by Hakunka-Matata on 2011-03-21
[http://ubuntuforums.org/showthread.php?t=1711323](http://ubuntuforums.org/showthread.php?t=1711323)

relevant post is post #17 

I don't know how to answer him on that one.  And don't want to steer him wrong either.

Thanks for looking in

---

### Post by oldfred on 2011-03-21
I just ran across that thread. I think you were side tracked with minor issues on fstab. OP did mention that the issue was he only booted  Xubuntu. I do not know all the differences with Xubuntu over Ubuntu, but if he is booting then fstab must be ok or at least functional.

One of the issues of the boot script is that it gives so much info. I still miss things and like others to also review a post. One of the more difficult things is to know that something is missing out of all the info posted.

---

### Post by Hakunka-Matata on 2011-03-21
The OP made several changes in his partitioning scheme, and he removed/deleted a partition also.  That's the main reason I went to examine the fstab file and compare with the UUIDs.  There were discrepancies which he has fixed.  
He also confused me by saying it booted straight into xubuntu.  Think I'll install an Xubuntu system right now just to see what it looks like.  

Thanks

---

