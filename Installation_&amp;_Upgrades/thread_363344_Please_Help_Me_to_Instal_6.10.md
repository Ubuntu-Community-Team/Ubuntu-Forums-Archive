---
title: "Please Help Me to Instal 6.10"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by insyted on 2007-02-16
Hello. I am brand new. Never used Ubuntu before or Linux for that matter.
I just have a few questions about my installation.

1. I am using Intel Core 2 Duo E6400 64-bit Processor.
Is that compatible with the 64-bit version of Ubuntu?


2. Will the 64 bit version of Ubuntu be able to run all the apps that run on the 32-bit version?


3. Is there a format feature on the Ubuntu CD that will allow me to format my hard drive whether I install Ubuntu on it or not? I'm looking to do a clean format without regard to installing any OS. I just want it to be completely empty. I can use it for storage or install any OS on it.


4. Any examples on how Ubuntu-64 takes advantage of 64-bit technology?


5. Thank you.

---

### Post by Kateikyoushi on 2007-02-16
1. Yes you can run the 64bit version of ubuntu on it.
2. It can run the same apps at least most of them.
3. You can use gparted from live cd to partition and format the drive.
4. I do not consider 64 bit a significant advantage so far on desktop the benefits do not worth the possible problems.

I would rather pick the 32bit version if bandwidth is not an issue try both and decide for yourself.

---

### Post by Cobikegeek on 2007-02-16
The recommendation for Edgy is to use the default "generic" kernel, which should work fine on your machine (I'm using it with an AMD 64 bit processor).  

There is a partitioner called gparted on the 6.10 live cd/install disk that works very well.  The installation process will ask if you want to partition/resize you drive.  If you are planning to dual boot with windows - be sure windows is installed first and run the windows defrag program before resizing any windows partitions to make room for Ubuntu.

Some problems reported running 32 bit apps in 64 bit mode, but this is a non-issue if you just use the default generic kernel.  

There are some good instructions/resources at [www.psychocats.net/ubuntu/index](www.psychocats.net/ubuntu/index) and [www.help.ubuntu.com](www.help.ubuntu.com)

Good luck and welcome to Ubuntu.

---

### Post by insyted on 2007-02-17
Thanks! Will proceed to install Ubuntu 6.10 64-bit version today.

I'm using Intel G965 chipset. I saw a review about it, and somebody was complaining about incompatability with Linux. Is there any way I can get info about any possible compatablity issues with this board and Ubuntu?

---

### Post by insyted on 2007-02-18
I created an Ubuntu installation CD. Full 64bit version.

1. Thanks for letting me know it worked on my hardware. The only reason I asked is that the 64 version is called 64-bit PC (AMD64) desktop CD. I wasn't sure if it worked because it is called AMD64, and I use Intel. If they had not called it AMD, I would not have asked. But why do they call it AMD?

2. I created the installation CD, for full version of Ubuntu. I cannot seem to figure out how to format my computer as I mentioned above. I'd like to format my backup drive only with no OS files or any kind of files intalled in it. I have searched for instructions, but could not find any. Would anybody happen to know how to do this or provide me with a link?

Thank you.


I also have a question about Xubuntu. Is it made specifically for old computers? How does it run on modern fast computers? Do they have a 64bit version?

---

