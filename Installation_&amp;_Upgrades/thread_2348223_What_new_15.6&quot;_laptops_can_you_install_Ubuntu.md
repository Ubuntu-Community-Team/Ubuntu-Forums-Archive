---
title: "What new 15.6&quot; laptops can you install Ubuntu 16.04 in a dual boot configuration"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by wiz68 on 2017-01-01
I have spent numerous hours and called several Laptop manufactures trying to identify what new 15.6" laptops can be configured into a dual boot system that supports Win and Ubuntu 16.04.  I need a laptop that will take the install and have NO problems running 16.04 or Win.  This information is not available from my searches in Ubuntu documentation.  

So, would really appreciate some guidance.  Thx

---

### Post by TheFu on 2017-01-02
I'd start with Linux-specific laptop makers and ask them about Windows support.  System76 is one. There are others.  Dell sells some laptops with Ubuntu pre-installed. I'd look for those and see if they also sell it with Windows.

*_No problems_* is asking a lot.  I don't know of any laptop that doesn't have some issues. If not today, when microsoft patches their boot loader, they will break something.  I vaguely remember that happening about once a year.

OTOH, I don't dual boot anymore. Find virtualization much easier for my needs; less risky for screwing around with partitions and booting too.

---

### Post by mörgæs on 2017-01-02
'New' does not rhyme well with 16.04. If you decide upon new gear (could used stuff also be an option?) then you should focus on 16.10 at least, maybe 17.04 when it gets closer to release.

---

### Post by TheFu on 2017-01-02
I disagree concerning running anything newer than 16.04.  6 months of support is not sufficient for many people.  If you don't eat, drink, live Linux, installing a new OS is a big deal and something to be avoided.

Of course, this is just 1 opinion and doesn't mean that people choosing to run newer releases are wrong.  There are some very good reasons why running a newer release might be required - brand new hardware. Support for the newest chips and CPUs sometimes requires using the newest kernels.  My current chromebook required 15.10 to work, which made me unhappy. I wanted 14.04, which wouldn't boot. Fortunately, 16.04 was released just a few months later including the kernel HW support required.

I've made a conscious decision to NEVER run a non-LTS release. That leaves me with much more time to actually use my systems. I would not suggest that someone with limited Linux/Ubuntu experience get pushed into doing a major install every 6 months, which is what happens if any non-LTS release newer than 16.04 is used. 16.04 is the most current LTS.  Most of my systems still run 14.04 LTS, happily. We are making plans to move to 16.04 now, which we should finish by the end of 2017. ;)  I think we have 1 system still running 12.04 LTS as well. Upgrading that system to anything newer will be difficult, but it must be done soon.

Of course, the people who do run the latest and greatest non-LTS releases and constantly upgrade do the rest of us a huge service.  Just know what you are getting into if that is your choice or if the new hardware demands the newest kernel.

Carefully review the release and support dates here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) Be certain to scroll to the bottom and notice the specific kernel versions that have support AND just as importantly which versions do not have support. Not all LTS are really LTS. Basically, get onto the xx.04.1 release and stay patched on that to get the most stable system for the longest period of time.

---

### Post by mörgæs on 2017-01-02
> **TheFu said:**
> 
I've made a conscious decision to NEVER run a non-LTS release.

So have I. My various hardware is around 8-12 years old so it's well supported by the semi-old 16.04. 

For new stuff I recommend the newest software. Long term support is nice to have, hardware support is need to have.

---

### Post by Impavidus on 2017-01-02
16.04.2 LTS (with enablement stack) should support the same hardware as 16.10, so using the interim releases makes the latest hardware work only 4 months sooner than using the LTS releases.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by mörgæs on 2017-01-03
Four months is a long time waiting for a guy who has just bought a new computer. 

Anyway, is original poster still here?

---

### Post by wiz68 on 2017-01-03
Yup, still here.   Sounds like the best way to create a dual boot system with 16.04 is to use old laptops....   Unfortunately, that doesn't utilize latest hardware improvements....

---

### Post by TheFu on 2017-01-03
"old" doesn't mean 5 yrs.  Broadwell is well supported and has the power-management gains for a laptop. I remember skylake CPUs causing issues with suspend last year; could be fixed now. I dunno.  Routinely get 8+ hrs of battery on my broadwell system. Haven't had it a year yet.  Plus, being 1-2 yrs behind usually means not paying the "really-new" tax.

If this is for work and you need extremely powerful stuff - the Dell XPS line (I prefer the [XPS 13]("http://www.dell.com/en-us/shop/productdetails/xps-13-linux")), has i7, 16G of RAM, 1800p display, under 3lbs, and ships with Ubuntu pre-installed. Buddy of mine got one. He's a RHEL admin, so wiped Ubuntu and put Fedora on immediately. Prior to that, he used Apple laptops.  [Ars article on Linux laptops]("http://arstechnica.com/gadgets/2016/06/the-xps-13-de-dell-continues-to-build-a-reliable-linux-lineage/").

If you don't have that sort of money (I don't) and Windows inside a VM is acceptable, there are many lower-cost laptops.  I'm using an i3 chromebook. Basically, it is an ultrabook with limitations.  The only thing that doesn't work reliably is sound.  Pulse keeps dying, but I'm not running a standard Ubuntu distro and have created a tiny script to fix it. When I first got this machine, I had to use a non-LTS for a few months to get support for the new hardware. 4 months later, 16.04 was released and the new hardware was supported. As pointed out above - Ubuntu's Hardware Enablement releases solves this. 16.04.1 has some.  16.04.2 will have some more.

---

### Post by mörgæs on 2017-01-05
> **wiz68 said:**
> Yup, still here.   Sounds like the best way to create a dual boot system with 16.04 is to use old laptops....   Unfortunately, that doesn't utilize latest hardware improvements....

If you cling to 16.04 you will receive all improvements in the Buntu world with delay. Not a serious problem for people like me using old gear but a major problem for people using new.  

The short term support versions are made for a reason and that reason is for example your situation. Best you can do is abandon the LTS mindset and appreciate the luxury that someone provides you with a new operative system every half year. 

Some years into the future when your hardware is old news you will probably do fine with LTS.

---

### Post by wiz68 on 2017-01-15
My search will continue..   It is a sad situation where Micro Soft is so embedded with PC manufacturers.   I wonder, if Linux was a salable item, would manufacturers of new generation PCs, be in violation of the US Federal Fare Trade Act. 

Considered this subject closed.....

---

