---
title: "Copying a Ubuntu installation to a new disk"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Eidar on 2006-06-20
Hey everyone,

I have a minor problem, my disk which I used to install Ubuntu on is becoming rather full lately, so I was wondering if it would have been possible to copy over all contents on a new fresh disk and disconnect the old one - and thus use the new disk with the copied contents on?

What is the smoothest and safest way to go about with this?

Thanks in advance.

---

### Post by pellgarlic on 2006-06-20
yes - you should be able to just copy the contents of the disk onto another disk with no problem. you should be able to use gparted (which is in the repos, and on the dapper "live/install" cd). first, copy the partitions as they are, then resize them to your desire. now disconnect the original hard drive, and connect the new hard drive as master, and check that it boots ok. i'm not sure if you'll need to reinstall grub or not - if you installed it on the mbr, you may have to.

---

### Post by rcarring on 2006-06-20
I would have thought that you would need to reinstall grub as the new hard disk would not have a bootloader installed on its mbr and therefore no way to load the boot image.

With Macs you used to have the bless the hard disk (to make it bootable) by moving Finder out and into the system folder.

---

### Post by pellgarlic on 2006-06-20
[QUOTE=rcarring]bless the hard disk[/QUOTE]

cool terminology :)

---

### Post by aysiu on 2006-06-20
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Eidar on 2006-06-21
Thanks guys for the quick replies. I will try this soon :)

---

