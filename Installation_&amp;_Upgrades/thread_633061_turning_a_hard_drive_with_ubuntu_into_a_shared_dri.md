---
title: "turning a hard drive with ubuntu into a shared drive while retaining files"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by swiftor on 2007-12-06
i have done a clean install of ubuntu 7.10 on my desktop. i have a hard drive with ubuntu 7.04 on it along with a ton of music and movie files. i want to turn the drive with 7.04 into just another storage drive for 7.10 but retain the files on it. is there a way to do this, besides buying a new hard drive to back everything up with? 

:)

---

### Post by logos34 on 2007-12-06
You could just delete all the system folders--everything, in fact, except /home/user (or whereever your multimedia files are saved)...then add it to your gutsy fstab:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

you can even wipe grub from the mbr:
[http://www.tuxation.com/mbr-tricks-with-linux.html](http://www.tuxation.com/mbr-tricks-with-linux.html)

---

### Post by swiftor on 2007-12-06
thanks! its working like a charm now!

---

