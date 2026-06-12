---
title: "Will 32-bit run on 64-bit system?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Martyn Thompson on 2010-10-04
Hi guys and gals,

Quick question and I apologise in advance because I am quite sure this will have been answered a thousand times before... 

I am looking at buying a new laptop with a 64-bit processor but would like to run Ubuntu 9.10 32-bit on there.  I am sure there will be pro's and con's for doing it this way but will it at least work? 

Thanks for your input as always...

Martyn

---

### Post by sikander3786 on 2010-10-04
There are no problems running 32-bit OS on a 64-bit machine. On the contrary there are problems running 64-bit OS on a 32-bit machine. Actually it doesn't run :-)

---

### Post by Crazedpsyc on 2010-10-04
I actually had lots of problems with this. One. I used Linux Mint 8 (32 bit) (the equivalent of ubuntu 9.10) on my 64 bit laptop and the graphics didn't work at all. I had a black screen.
when I used 32 bit ubuntu 9.04 the graphics were terrible. Everything was stretched out and blurred, so to me unusable.

---

### Post by karthick87 on 2010-10-04
> **Martyn Thompson said:**
> Hi guys and gals,

Quick question and I apologise in advance because I am quite sure this will have been answered a thousand times before... 

I am looking at buying a new laptop with a 64-bit processor but would like to run Ubuntu 9.10 32-bit on there.  I am sure there will be pro's and con's for doing it this way but will it at least work? 

Thanks for your input as always...

Martyn

Yes sometimes it may cause driver issues..

---

### Post by Martyn Thompson on 2010-10-04
Cheers for fast replies fellas (or laydees!). 

Appreciate your answers. 


Martyn

---

### Post by mörgæs on 2010-10-04
> **Martyn Thompson said:**
> I am quite sure this will have been answered a thousand times before... 


Yes, you can find a lot of pro's and con's here:
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by SeijiSensei on 2010-10-04
A 32-bit OS can't address more than 3 GB of memory, so if your machine has 4 or more GB, that memory will be wasted unless you use a 64-bit OS.

---

### Post by sikander3786 on 2010-10-05
> **SeijiSensei said:**
> A 32-bit OS can't address more than 3 GB of memory, so if your machine has 4 or more GB, that memory will be wasted unless you use a 64-bit OS.
It actually can... PAE kernel is needed then.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by formaldehyde_spoon on 2010-10-10
You can usually do what you're suggesting without trouble, but if you have 64 bit hardware it's best to use 64 bit software - using 32 bit software is like putting a perfomance cap on your machine; you miss out on all the potential performance increases of 64 bit (more than just being able to address more RAM).

Here is the new 64 bit Flash for anyone looking: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by srs5694 on 2010-10-10
The graphics problems described by Crazedpsyc are almost certainly *not* related to running a 32-bit version of Ubuntu on a 64-bit CPU. Without more information, I can't be sure what happened, but my suspicion is that the same problems would have occurred with a 64-bit installation of the same version of the OS. (Crazedpsyc didn't say whether s/he tried such an installation.) Video issues like this are usually a result of a misconfigured X server, and that can happen on any platform. These problems can be overcome by reconfiguring X, which takes some experience and trial-and-error experimentation.

I'm not sure to what "driver issues" getyourkarthick is referring. I have yet to hear of any driver issues when running a 32-bit (x86) version of Linux on a 64-bit (x86-64) CPU. (I don't count Crazedpsyc's comments since they don't specify a direct comparison and the cause hasn't been adequately determined.) If you've got some specific issues in mind, getyourkarthick, I'd be interested in seeing references. (This said, in theory there *could* be issues, but this would be a matter of bugs that affect 32-bit code but not 64-bit code. Until recently, the opposite problem was more likely, since Linux originated on the x86 platform and x86-64 support was more recent and therefore more likely to exhibit bugs. Linux's kernel/driver x86-64 support is quite mature now, though.)

More broadly speaking, I do favor using 64-bit installations whenever possible, since they result in a modest performance boost. (About 10%, overall, although it varies a lot from program to program.) 64-bit also supports large amounts of RAM better -- although 32-bit *can* handle more than 4 GiB of memory, that support has some limitations that aren't present on a 64-bit system. Until recently, the [Ubuntu download page](http://www.ubuntu.com/desktop/get-ubuntu/download) labeled the 64-bit version "not recommended for daily use," or words to that effect, but most users of this forum, including myself, disagree with this assessment. The latest page now labels the 32-bit version as "recommended," with no such word applied to the 64-bit version. I'm not sure what the logic is behind this application of the word "recommended" (or "not recommended" on earlier versions of the Web page).

---

