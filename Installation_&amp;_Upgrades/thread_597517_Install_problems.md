---
title: "Install problems"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by lanamor on 2007-10-30
Hello and thanks in advance for any help.

I'm running into an odd problem that I hope someone could shed some light on. I'm attempting to install a distro of Linux on a Toshiba A135-S2276 laptop. The problem I'm having is that of the three distros I've tried so far (Fedora 7, Ubuntu, and OpenSUSE) won't boot from the install DVD unless I "mess" around with the partitions and/or MBR. I say "mess" because I can zero the MBR then use a linux boot disk to get to a command line and reset up partitions using fdisk. After I did this several times I did get OpenSUSE to come up once but I decided to run the firmware test from the install menu. Running the test locked up and then I was back to square one with not being able to boot the DVD again even after repeating my "messing" around steps. I'm wondering if the Linux kernels just don't like the laptop's firmware. I do know that these laptops are not supported by Toshiba unless they are running Vista and didn't even develop XP drivers.

I know it's not a hardware issue because my Ultimate Boot CD works just fine every thime. No matter how I set up my HD I just can't seem to get the Linux distro disks to boot into install mode. 

I'll admit I'm no Linux ninja but I have a very well rounded understanding of computer administration. Any ideas guys

---

### Post by Pumalite on 2007-10-30
Can you boot a Live CD?

---

### Post by lanamor on 2007-10-30
I did not try they live CD (correct me if I'm wrong) because the DVD come with many more packages installed. I tried a live cd of Ubuntu and it didn't even have the gcc or c++ libs installed. I know I could just install all of this but I'd rather the full DVD. Plus I'm the type that would rather work through the problem rather than around it.

---

### Post by Pumalite on 2007-10-30
Bad idea. Your best bet is install with Alternate CD while wired to the Internet.

---

