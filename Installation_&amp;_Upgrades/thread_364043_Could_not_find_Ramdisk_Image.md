---
title: "Could not find Ramdisk Image"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by ncinto on 2007-02-17
Hi!

I have been trying to install Ubuntu 6.10 on a Compaq Deskpro EN. The Deskpro has a P3 and 512Mb of Ram and a 40gb Hard drive. The Ubuntu CD works fine on my other PC (a P4 with 1 gb of RAm) but when I try to run it on this unit I get an error message that reads "Could not find Ramdisk Image: /casper/initrd.gz"

I am at a loss as to what the problem is an would appreciate it someone would help me out. I have been able to successfully install an older copy of Redhat on the same PC so I know that everything works ok. Would really like to get this going as I want to play with ubuntu without having to mess with my primary machine (too many family members use that one to risk any incident).

Thanks

Nc

---

### Post by eapache on 2007-02-17
Very bizarre. It sounds like a corrupt installer cd, but you said it runs fine on your other pc. Do you get into the boot menu, or does it crash even before that? If you can get there, try running the disc verification...

---

### Post by ncinto on 2007-02-17
i do get to the ubuntu boot menu and tried the option to verify the disk. It seems to take a long time to load the linux Kernel but does so successfully and then gives me the same error as before. Strangely enough the same CD works on my other PC and brings up the Ubuntu desktop with no problem.

---

### Post by eapache on 2007-02-18
In the CD boot menu, press F6 (I think) to edit boot options. Remove splash=quiet and add break=bottom

This will hopefully give you a more detailed error message. If it doesn't is there an way to test the cd drive itself? Also, how is your hdd currently partitioned?

---

### Post by ncinto on 2007-02-18
Hey eApache, you were right. After reading your post I decided to swap drives with my other Pc and the CD works fine now. I guess there is a problem with the CD drive on the Deskpro. (gotta go hunting for a replacement). Ubuntu is installing now and the installation seems to be coming along nicely. Thanks a million for your help. I am sure it will be fine now.

Nc

---

