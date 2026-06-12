---
title: "Why can't I find winnt.exe or winnt32.exe from my HDD using Ubuntu 9.10 live cd?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by lewisk on 2010-05-06
Hello,

First off, please excuse my newness to Ubuntu..
I am trying to install Ubuntu because I was unable to succeed in reinstalling my copy of Windows. My computer did not come with a Windows installation CD, so I used a program already on my HDD to do the job, winnt32.exe. When the installation failed due to a missing or corrupted file (hal.dll), I was unable to open Windows or retry installing it, so basically I could do nothing. I have no real preference for Windows over Ubuntu, but I am not crazy about erasing and using the entire disk for Ubuntu, since I would lose my copy of Windows which I paid for when I bought my computer. I thought if I could find the Windows installation files on my HDD and copy them to my external hard drive, I could feel free to reformat my HDD and use it just for Ubuntu, and I would be able to try installing Windows again sometime later if I felt like it. Running my computer on the Ubuntu live CD, I tried to find my Windows installation files, winnt.exe and winnt32.exe, from the I386 folder, but the files are now either invisible somehow or they've been erased. This is strange since everything else on my HDD seems to still be there. Then I thought I could leave windows be and use part of my HDD for Ubuntu, worry about it later. This too is proving difficult, since I am not getting the option to resize my HDD for Ubuntu when I select "specify partitions manually" (according to Ubuntu's official documentation [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html) this should be one of the given options when right-clicking on the HDD).
Thank you for following this, it's not a typical situation for someone to be in, though when a Windows installation has failed and you have no installation CD you don't have many options.
But I basically have just two questions: 1. Why am I unable to find my Windows installation files (winnt.exe and/or winnt32.exe) running my computer on the Ubuntu live CD if everything else on my HDD seems to be there? 2. Why am I not getting the option to resize my HDD for Ubuntu upon selecting "specify partitions manually" during the installation process? 
Overall I just want a running computer, so I'd be happy with Ubuntu only, but if it can be avoided I don't want to lose my copy of Windows.

Thanks! any suggestions would be appreciated!

Lewis

---

### Post by Mark Phelps on 2010-05-06
Can't answer the first question.

As to the second, you can't resize a partition that is in use.  You have to unmount that partition first.  Then, you can resize it.

Which means, that if you're running Ubuntu, you can't use it to resize its own partition.  You would have to boot from an Ubuntu LiveCD or boot from a GParted Live CD.

---

### Post by lewisk on 2010-05-06
OK, but I am trying to install Ubuntu from the Ubuntu live CD, I haven't yet installed any version of Ubuntu onto my HDD, so I still don't see why I don't get the option to resize.

Lewis

---

