---
title: "Can't upgrade to a newer kernel"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by Groggster on 2011-07-22
It seems that i am stuck using the 2.6.38-9 kernel, since no matter what i try, i can't update. I have had this problem since 2.6.38-10, but figured that the problem probably would solve itself after the next kernel update, sadly that was not the case.

I have had some worrying error-massages from dpkg about broken packages, which i believe might be the source of this problem, as it reported that the package "linux-image-generic" was broken. I removed the postinstall script from /var/lib/dpkg/info and updated both dpkg and aptitude. 

I am not getting any more error messages, and if i look in the synaptic package manager, i can see that kernel 2.6.38-11 is indeed installed, yet i can't select it at bootup, even though i have tried to manually update grub.

Any ideas anyone?

---

### Post by dino99 on 2011-07-22
close all opened apps and into a terminal, run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Groggster on 2011-07-22
Yes, i have done that already, and since i removed the postinstall script it does not give me any error messages either, however the kernel is not updated/changed/used.

---

### Post by dino99 on 2011-07-22
linux-generic:

This package will always depend on the latest complete generic Linux kernel
available.


linux-image:

This package will always depend on the latest generic Linux kernel image
available.

are they installed ?

---

### Post by Groggster on 2011-07-22
Hmm, the linux-image package was not installed, however installing it does not seem to make any difference. And why was the package missing?

---

### Post by Groggster on 2011-07-22
Also the package named "linux" was not installed. I installed it, but it didn't wort either, tough it says that the package is version 2.6.38-11.

---

### Post by Groggster on 2011-07-23
Bump for glory!

---

### Post by Groggster on 2011-08-07
Sorry for multiposting, but I have got an update!

I was playing around with this issue, and tried to reinstall all kernel related packages i could think of. And what I noticed that since I removed all of the related .postinst scripts in /var/lib/dpkg/info i no longer received any error messages while reinstalling the packages. I ran the update-grub command, but it still did not include the newer kernel image.

So i thought that i would try to manually enter it in grub.cfg (yes, I know i am not supposed to do that... I was merely trying for the hell of it), and i worked! I am now running version 2.6.38-11 according to uname.

However, I do realize that as soon as the kernel gets updated again, I will have to repeat this task. Also this post in grub.cfg disappears if I update grub manually with update-grub.

Any thought on how to permanently solve this issue given these new facts?

---

