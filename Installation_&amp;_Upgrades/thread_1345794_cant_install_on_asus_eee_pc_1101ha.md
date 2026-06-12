---
title: "cant install on asus eee pc 1101ha"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by fotisp88 on 2009-12-04
Hello,

I am trying to install ubuntu on my asus eee pc 1101HA with no success at all.
I tried both ubuntu netbook remix and the normal version and both normal installation and windows installation. 
When I try with the normal procedure I go upto the partitioning part and it fails to partition the hard drive with an error like gparted cannot resize windows dynamic disk or something similar. When I try with the windows installation it downloads everything and restarts and then gives a "no root file system is defined. Please correct this from the partitioning menu".

Does anybody know what to do?

Thank you in advance!

Fotis

---

### Post by darkod on 2009-12-04
The message about dynamic disk might mean that your disk is in dynamic mode rather then basic. Open Disk Management in windows and see if it says basic or dynamic. I don't think you can install on dynamic, like the message said it can't resize it to make space for ubuntu.

---

### Post by fotisp88 on 2009-12-05
yes it says dynamic. how can I change it to basic?

---

### Post by darkod on 2009-12-05
I have not worked much with dynamic disks but unfortunately I think there is no way to change to basic without losing all data and the OS. Try googling more on the subject.
You can go from basic to dynamic without reformatting and losing the data but not the other way.
One option would be to move all data you need to external usb hdd for example, then reformat the whole hdd and make it basic. But you would need to reinstall windows and all your software back, and then ubuntu, and put the data back from the external drive.

---

### Post by darkod on 2009-12-05
There is some procedure here and they claim you will not lose the data but use it on your own RISK!!! I haven't tried it and can't recommend it.
[http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)
 Google will give you other tutorials too.

---

### Post by fotisp88 on 2009-12-05
thank you very much mate! I hope I dont need do a reformat as it is a netbook and I dont want to get into the procedure of installing windows 7 from a usb (as i dont know how to do it but if I need to I will do it) and having ubuntu is a must cz I study computer science. 

Thx again for your help!

---

### Post by fotisp88 on 2009-12-05
I have found a software that coverts to basic without any data loss (dynamic disk converter) but you have to buy it. does anyone knows if there is any similar program on ubuntu? I mean I can boot my netbook in ubuntu from the usb without installing them. so if there is any similar program I can boot into ubuntu and change from dynamic to basic from ubuntu.

---

