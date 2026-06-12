---
title: "Ubuntu 12.04.1 LTS kernel 3.2.0-35 + AMD procs/Nvidia graphics"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by NM5TF on 2012-12-21
Since installing kernel 3.2.0-34 caused my PC to become unusable, yes I have filed a bug on Launchpad,and only able to use it by regressing back to kernel 3.2.0-33, I am reluctant to install kernel 3.2.0-35...

Has anyone running 12.04.1 LTS with AMD processors + Nvidia graphics had 
any problems so far???

TIA,

Tommy

---

### Post by NM5TF on 2012-12-23
bump

NO ONE has seen this problem???

hard to believe...:o

---

### Post by bogan on 2012-12-24
Hi!, **NMSTF,**

You would probably get more responses if you describe just what it is that you call: "unusable"; is it graphics? or internet?  or system?,  failure to boot?  does it freeze?, or what ???

Also give a link to your Bug report and details of your set up, especially video card and any non-default drivers you have installed.

Read: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
**Re: Suggestions on how to get your support questions answered as quickly as possible.**
Chao!, **bogan.**

---

### Post by darkod on 2012-12-24
Well, I have AMD CPU but not Nvidia. You might have issue with the nvidia drivers, I doubt it's related to the cpu.

In fact, two days ago I upgraded my 12.04.1 running the 3.2.0-34 with a new board and AMD A8-5600K APU which has included HD 7560D graphics.

So, I went from a combination of AMD Athlon 4850e + integrated HD 3200 on the board, to the A8-5600K with integrated 7560D in the APU. I just plugged in the same SSD and it worked right away.

After that I activated the fglrx driver, because earlier I was using the radeon driver, never really tried to activate fglrx. Went without any issues.

Then I updated the kernel to 3.2.0-35 and it continues to work fine.

From what I can say with my 3 years of using ubuntu, ATI seems to be much better supported and I like it more too. Make sure that the kernel update is not leaving you without the nvidia driver, so you might need to use nomodeset after every update to boot once and activate the nvidia driver. Or something like that.

I don't think the CPU has anything to do with it, unless you have some rare combination of hardware that it doesn't like.

---

### Post by NM5TF on 2012-12-24
thanks for the replies Bogan & Darkod...

here is a link to my original thread describing my problems:

[http://ubuntuforums.org/showthread.php?t=2089885](http://ubuntuforums.org/showthread.php?t=2089885)

here is a link to my bug report on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1085548)

there is also an on-going thread about AMD procs & the newer kernels here:

[http://ubuntuforums.org/showthread.php?t=2085789](http://ubuntuforums.org/showthread.php?t=2085789)

I have not been able to get past the "puple screen of death" since
the 3.2.0-33 kernel as it will NOT go any further no matter what suggetions I try

system is AMD Athlon 64 X 2 4000+ procs with Nvidia GeForce 6150SE nForce 430 bought in 2007
running Nvidia kernel 173.14.35

Tommy

---

### Post by NM5TF on 2012-12-24
OK...so I got brave & went ahead and installed the 3.2.0-35 kernel today

and it WORKS with no problems...guess the kernel devs found/fixed whatever
3.2.0-34 bug was keeping my sys from booting...:guitar:

marking this thread solved now....:P

will also go to Launchpad & annotate my bug report on 3.2.0-34 kernel

thanx for the replies...

Tommy

---

