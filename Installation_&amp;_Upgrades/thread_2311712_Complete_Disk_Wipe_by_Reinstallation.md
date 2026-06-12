---
title: "Complete Disk Wipe by Reinstallation?"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by Jacob_Jones on 2016-01-29
Hello,

I messed up on downloading OpenCV and I've heard it takes long to make it working again. I would like to know if reinstalling Ubuntu would wipe all of the installed libraries so that I could just start over again.

---

### Post by sudodus on 2016-01-29
Welcome to the Ubuntu Forums :-)

Yes, a normal reinstallation will wipe all of the installed libraries (all files). But if you choose 'Something else' alias 'manual install', you can decide to format the partition(s) or not. Since you want to get rid of everything, you should format at least the root partition, which contains the libraries.

You need not bother about the swap partition. If you have a home partition, you might keep it (not format it). It contains settings that are specific for the user, and of course personal data files. These might or might not affect your program package with problems. (I don't know where OpenCV saves its settings.)

---

### Post by Jacob_Jones on 2016-01-29
I see. I have done the reinstallation but the errors persist. What would be the reason for this?

---

### Post by sudodus on 2016-01-29
***I don't know OpenCV. Let us hope someone who knows it will read this thread and can help you.*** :-) Until then, and to help us help you,

please describe you system, which version of Ubuntu?

How do you install OpenCV? Which version is it?

When do the errors appear (before or after installing OpenCV)?

Please describe what happens - how it goes wrong / how you see that there are errors!

---

### Post by Jacob_Jones on 2016-01-29
I'm running 14.04 but I think I'll switch over to 12.04 since the maker said he uses it on that OS. The version of OpenCV I used are 3.1.0 and 2.4.0. I only recently had to use ubuntu and I wasn't aware that installing both would cause so many problems. I'm using eclipse and I thought for sure that the errors would be erased but I don't understand why these errors would persist. The program worked fine until I installed 2.4.0. I am also curious but are there any side effects of installing an OS too many times?

---

### Post by ubfan1 on 2016-01-29
Multiple versions of a program can be installed, but 1)not in the same space, and 2)You might have configuration issues going back and forth between the two versions (particularly new to old).  The 2.4 version seems to be in the Ubuntu repositories, so that one should be easy to install.  Any other version should be able to be built and run from anywhere, like from your home directory.  It's up to you to figure out how to switch between the two.  I haven't looked at opencv since 2.2, the I still have the old directory, but it was from another machine, doesn't run because of old/missing libraries, and I can rebuilt it because I don't want to install all the missing packages on the new machine.  When it ran, I could just run it from my home directory.
  Multiple OS reinstalls should not hurt a hard disk, but an SSD does have a limited number of writes (newer ones are better) to be aware of.
The only reason to drop back to 12.04 would be if a needed package were not present in 14.04.  Otherwise, you face all the same problems, maybe even more if the 2.4 version is not offered in the 12.04 repositories.

---

