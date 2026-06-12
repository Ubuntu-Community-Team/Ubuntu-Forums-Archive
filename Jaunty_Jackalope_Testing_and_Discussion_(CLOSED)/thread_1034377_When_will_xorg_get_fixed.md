---
title: "When will xorg get fixed?"
date: 2009-01-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-01-08
I've decided not to use any work arounds. Trying to install the nvidia driver from synaptic still wants to remove xorg. This has been going on for weeks now.

---

### Post by ShirishAg75 on 2009-01-08
with the latest driver which came up yesterday/today?

---

### Post by Archmage on 2009-01-08
> **philinux said:**
> I've decided not to use any work arounds. Trying to install the nvidia driver from synaptic still wants to remove xorg. This has been going on for weeks now.

I assume it will be fixed at the 23rd April. Before that priority drivers wont run that well.

---

### Post by philinux on 2009-01-08
> **ShirishAg75 said:**
> with the latest driver which came up yesterday/today?

Yep even the 180 driver. I'm not manually installing drivers. I'd rather wait for xorg to get fixed.

---

### Post by gnomeuser on 2009-01-08
> **philinux said:**
> I've decided not to use any work arounds. Trying to install the nvidia driver from synaptic still wants to remove xorg. This has been going on for weeks now.

It is not X that requires fixing, it is the nvidia driver. That however is entirely out of the communities hands as nvidia refuses to let us.. basically you have to wait till they get it done.

---

### Post by jerrylamos on 2009-01-08
> **gnomeuser said:**
> It is not X that requires fixing, it is the nvidia driver. That however is entirely out of the communities hands as nvidia refuses to let us.. basically you have to wait till they get it done.

What CHANGED in Ubuntu/Debian/X that needs an nvidia change?

UBUNTU/DEBIAN/LINUX/X     DON'T DO THAT!

If UBUNTU/DEBIAN/LINUX/X makes a change that requires everyone else to change in concert, DON'T DO THAT!

Us owners/users of Intel, nvidia, ATI, etc. get the shaft when someone in the "community" decides to make a unilateral change. 

Jerry

---

### Post by gnomeuser on 2009-01-08
> **jerrylamos said:**
> What CHANGED in Ubuntu/Debian/X that needs an nvidia change?

UBUNTU/DEBIAN/LINUX/X     DON'T DO THAT!

If UBUNTU/DEBIAN/LINUX/X makes a change that requires everyone else to change in concert, DON'T DO THAT!

Us owners/users of Intel, nvidia, ATI, etc. get the shaft when someone in the "community" decides to make a unilateral change. 

Jerry

First up, calm down. You need to realise how development is done. Upstream X.org has performed a routine API update. This happens when needed for progression of the X stack.

Nvidia needs to adapt their driver to follow suit. We can't do that for them as their driver is closed source. All the other drivers have been adapted as part of the upstream X.org update. The only affected drivers that remain are those for which we have no source code. It is up to the people with access to that source code to make the changes needed, namely nvidia and ati.

Jaunty is a development platform, you cannot expect to run a desktop on it. It will be broken, this isn't even a bug, this is intended as part for progress. 

I urge you to spend less time yelling and demanding we "fix" what we are not capable of and more time understanding the meaning of a development release. If you cannot live without a driver that is not supported on the current development platform then I kindly suggest to use the stable releases of Ubuntu.

---

### Post by LordVeovis on 2009-01-08
> **jerrylamos said:**
> What CHANGED in Ubuntu/Debian/X that needs an nvidia change?

UBUNTU/DEBIAN/LINUX/X     DON'T DO THAT!

If UBUNTU/DEBIAN/LINUX/X makes a change that requires everyone else to change in concert, DON'T DO THAT!

Us owners/users of Intel, nvidia, ATI, etc. get the shaft when someone in the "community" decides to make a unilateral change. 

Jerry

This is why there is a release cycle.  Jaunty is not a release.  By release this /should/ be fixed.  This is not something Ubuntu did wrong as this is how development works when you have access to only 1 side of code.  If they want to add something they have to wait for NVIDA to add something too.  You should be yelling at NVIDIA (if anyone) for being so closed minded/sourced.

EDIT: I was a little unhappy too when mine broke. Just feel lucky there is a community her that is willing to help for free!!  The first time mine broke I didn't know why, I reinstalled and updated and it broke again.  I have several posts in the other thread because I too need the fix.  It is easy to apply, there is nothing wrong with applying it.  I still play games and notice no slowdown.  In fact they seem to run a little faster than the old driver.

If you require a system with no downtime stick to releases as developments, ESPECIALLY Alpha, **/WILL/** have problems.  Aplha and Beta does not mean bleeding edge new features.  It is made so that a core group of knowledgeable people who want too see the OS progress can work to find where any issues lie.  Even if the devs knew that their updates would break the NVIDIA driver, I would glady ask them to lay it on us as it is FAR more important to find other bugs than to cae about NVIDA being slow.  When they first updated x-org it was still not even a release itself.

Give NVIDIA time to fix their driver and all will be good.  NVIDIA wont waste the time to build a new driver while it is still in development as it may still be in flux (though it likely has allready been "freeze" NVIDIA wont release a driver for a non release version - at least I dont think so, they will consider it a waset of valuable resources and time)

---

### Post by ronacc on 2009-01-08
this happens every dev cycle , and not just to nvidia but to ati and intel also , atleast with nvidia I usualy have the ability to fall back to a hand installed driver . Looking around the forum I see just as many posts about intel and ati getting blanksceern/low graphics/console as I do about nvidia .

---

### Post by castrojo on 2009-01-08
> EDIT: I was a little unhappy too when mine broke. Just feel lucky there is a community her that is willing to help for free!!  The first time mine broke I didn't know why, I reinstalled and updated and it broke again.

You're not just blindly dist-upgrading are you? FYI a normal upgrade will just hold those packages back so it won't break.

---

### Post by LordVeovis on 2009-01-08
> **whiprush said:**
> You're not just blindly dist-upgrading are you? FYI a normal upgrade will just hold those packages back so it won't break.

Not normally.  But the first day the update went through if you used the Update Manager it would not prompt on removing packages but didnt say that any were going to be removed (there was a bug put in about it)

---

### Post by ShirishAg75 on 2009-01-09
Btw there is another nvidia update . 

> 

nvidia-graphics-drivers-180 (180.22-0ubuntu1) jaunty; urgency=low

  * New upstream version.  First "stable" driver in 180 series. (LP: #315169)
    *  Added support for the following GPUs:
          o Quadro FX 2700M
          o GeForce 9400M G
          o GeForce 9400M
          o GeForce 9800 GT
          o GeForce 8200M G
          o GeForce Go 7700
          o GeForce 9800M GTX
          o GeForce 9800M GT
          o GeForce 9800M GS
          o GeForce 9500 GT
          o GeForce 9700M GT
          o GeForce 9650M GT
          o GeForce 9500 GT
    * Added initial support for PureVideo-like features via the new VDPAU API (see the vdpau.h header file installed with the driver).
    * Added support for CUDA 2.1.
    * Added preliminary support for OpenGL 3.0.
    * Added new OpenGL workstation performance optimizations.
    * Enabled the glyph cache by default and extended its support to all supported GPUs.
    * Disabled shared memory X pixmaps by default; see the "AllowSHMPixmaps" option.
    * Improved X pixmap placement on GeForce 8 series and later GPUs.
    * Improved stability on some GeForce 8 series and newer GPUs.
    * Fixed a regression that could result in window decoration corruption when running Compiz using Geforce 6 and 7 series GPUs. (LP: #306605)
    * Fixed an nvidia-settings crash when xorg.conf contains Device and Screen sections but no ServerLayout section.
    * Fixed a problem parsing the monitor sync range X config file options.
    * Fixed a problem with the SDI sync skew controls in nvidia-settings.
    * Fixed a problem that caused some SDI applications to hang or crash.
    * Added support for SDI full-range color. (LP: #218736)
    * Improved compatibility with recent Linux kernels.
  * debian/rules:
    - Create patches directory in case it wasn't present in orig.tar.gz


[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html)

---

### Post by gnomeuser on 2009-01-09
> **ShirishAg75 said:**
> Btw there is another nvidia update . 



[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002757.html)

I have to admit, Ubuntu's build system seems extremely closed to me. It's very hard to figure out, coming from Fedora with a fully open system I would just go to [Koji](http://koji.fedoraproject.org/koji/builds) and there everything that flows through the build system is listed. I can download packages, see build logs, errors. Hell I can even add the build system as a repo.

Ubuntu in contrast seems to have nothing like that, there is a nifty little list to notify with regards to updates but despite the updates appearing to happen there are no packages in my cache. I tried going to what I assume is the main [repo](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-180/).

It would be really nice if we eventually could get something going that works like koji. As a maintainer Koji is great, it is one of the things I miss the most when using Ubuntu. Secondly I miss the per package bug thing Fedora has - basically bugz.fedoraproject.org/packagename will give me a list of every bug filed against that package which makes it very easy to get an overview so to avoid duplicate bugs and as a maintainer I have a quick list of everything that is filed.

---

### Post by kaboca on 2009-01-09
I believe something got fixed with xserver-xorg 1:7.4~5ubuntu10 

I had nvidia 180.22 stable from nvidia. I had problems with the driver to start, playing fullscreen video and compiz. 
I have a Ge7600GT videocard.
Today i did upgrade xorg and everything works fine so far.

Even compiz works. It was a problem since 180.16. 

be sure to remove any old nvidia before install 180.22 .

---

### Post by dinxter on 2009-01-09
apologies if this isnt what you were looking for [gnomeuser]("http://ubuntuforums.org/member.php?u=142879") but i tend to look at builds states and so on on launchpad such as
_[https://launchpad.net/ubuntu/+builds?build_text=nvidia&build_state=built](https://launchpad.net/ubuntu/+builds?build_text=nvidia&build_state=built)_
you can see the various states of various builds, logs and so on. links to the respective launchpad pages where you can get the built deb and various logs and suchlike. don't know much about koji but it might at least be helpful to you

[EDIT] just to add, per package bug reports are on the same package launchpad pages such as 
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180)
you can choose the version and see the bugs relating to that already filed to avoid duplicates, best place to search for these package pages is at 
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by DougieFresh4U on 2009-01-09
> **kaboca said:**
> I believe something got fixed with xserver-xorg 1:7.4~5ubuntu10 


I have to agree with you on that one. My desktop is a little more stable this morning. Also, my desktop theme was giving me problems, where the color all 'disappeared' a few days ago
but it reappeared after updating this morning. Of course I use the 'Intel865G' for graphics and it seems to be holding it's own. I was using Google Earth yesterday and it was giving messege about graphics not 'up to par' but it worked with out giving 'fit'.

---

### Post by plun on 2009-01-09
> **DougieFresh4U said:**
> I have to agree with you on that one. My desktop is a little more stable this morning. Also, my desktop theme was giving me problems, where the color all 'disappeared' a few days ago
but it reappeared after updating this morning. Of course I use the 'Intel865G' for graphics and it seems to be holding it's own. I was using Google Earth yesterday and it was giving messege about graphics not 'up to par' but it worked with out giving 'fit'.

Intel-RC2 was also released yesterday

[http://www.phoronix.com/scan.php?page=news_item&px=Njk3Nw](http://www.phoronix.com/scan.php?page=news_item&px=Njk3Nw)

I dont know if Ubuntu uses all code, maybe its coming  ?

We must take this as a challenge...:popcorn:

---

### Post by gnomeuser on 2009-01-09
> **dinxter said:**
> apologies if this isnt what you were looking for [gnomeuser]("http://ubuntuforums.org/member.php?u=142879") but i tend to look at builds states and so on on launchpad such as
_[https://launchpad.net/ubuntu/+builds?build_text=nvidia&build_state=built](https://launchpad.net/ubuntu/+builds?build_text=nvidia&build_state=built)_
you can see the various states of various builds, logs and so on. links to the respective launchpad pages where you can get the built deb and various logs and suchlike. don't know much about koji but it might at least be helpful to you

[EDIT] just to add, per package bug reports are on the same package launchpad pages such as 
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180)
you can choose the version and see the bugs relating to that already filed to avoid duplicates, best place to search for these package pages is at 
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

Wow that is incredibly horrible.. compared to the workflow and discovery presented by Koji and bugz this comes up short in every way. 

One example: clicking launchpads million links gives me:

[https://launchpad.net/ubuntu/jaunty/amd64/nvidia-180-kernel-source/180.22-0ubuntu1](https://launchpad.net/ubuntu/jaunty/amd64/nvidia-180-kernel-source/180.22-0ubuntu1)

Error page not found for the amd64 binary it said was succesfully built. How is that logical? 

This is in dire need of an injection of transparency

I think Ubuntu has a profound lack of openness, the public devel lists are near silent and yet work is being done, decisions are being made, seemingly all behind closed doors. The tools used are both proprietary and impossible to figure out even for a simple overview. It really shouldn't be this hard to dip ones feet or for users to dig out rational, debate and resulting work. There are many things about Ubuntu that impresses me, this however is not one of them.

---

### Post by philinux on 2009-01-09
> **gnomeuser said:**
> It is not X that requires fixing, it is the nvidia driver. That however is entirely out of the communities hands as nvidia refuses to let us.. basically you have to wait till they get it done.

Thanks for the clarification.

---

### Post by plun on 2009-01-09
> **philinux said:**
> Thanks for the clarification.

No... gnomeuser is badly wrong and for the moment its nothing to do about it.  nVidia is doing a lot for Linux.

Gnomeuser can choose his Fedora/Debian Duke Nukem Forever doctrine and 
keep it there...  

Just sad and stupid, IMHO....:(:(:(


I am testing Windows 7 on my portable PC and its even more stupid to choose this Duke Nukem Forever road..  :( 

[B]
This IS Bug No 1[/B]

[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)


But if this IS Ubuntu for the moment I can format and just quit.......:(

---

### Post by gnomeuser on 2009-01-09
> **plun said:**
> No... gnomeuser is badly wrong and for the moment its nothing to do about it.  nVidia is doing a lot for Linux.


How exactly am I wrong when the problem clearly is nvidia not adapting their driver to the upstream X API.

Would you claim that all APIs should remain frozen and supported for all time.. in which case I strongly encourage you to try, just for one small project, let alone something big like the kernel or X. In fact you can start by reading [this](http://www.mjmwired.net/kernel/Documentation/stable_api_nonsense.txt).

Nowhere did I say it was immoral or illegal for them to have closed kernel modules (though it is my belief that it would ruled as such in most court rooms). It is a purely techical matter, if the code was available the API changes could have been made and rolled out along with the X update. Nvidia are actively working against such development by the model they picked. This means their users have to wait. That is not X's fault, nor is it Ubuntu's fault. We break APIs when we need to, not because we think it's fun to mess with nvidia or their userbase.

My prediction though, Red Hat just hired one of the nouveau developers and with the other general developments in X and the kernel (GEM is in the kernel now e.g., drivers are getting massively better, Gallium3D is coming along). A year from now the nvidia module as we know it will not be the problem it is today for users (it will still be around, doubt we can get to 100% coverage in a year even at this pace but we will do the most used cards to an acceptable degree). This work will be no thanks to nvidia.

---

### Post by jerrylamos on 2009-01-09
> **gnomeuser said:**
> How exactly am I wrong when the problem clearly is nvidia not adapting their driver to the upstream X API.

 This means their users have to wait. .... We break APIs when we need to, not because we think it's fun to mess with nvidia or their userbase.

When you make a habit of breaking API's, in particular without telling any of us users why, you certainly are likely to lose linux users.

Why do you feel confident in breaking the codes that us users have to live with for no stated reason to us?  This pc uses Intel i845 video, and as stated in the Ubuntu Jaunty Alpha 2 release, it won't work unless I by hand enter Driver "Intel" Option "NoAccel" "true".  

O.K., jaunty isn't released code, and intrepid doesn't need that workaround.  It's a few months until release so it may/may not get fixed.  For example, launchpad had the intrepid won't boot intel problem two months before release, which was a problem running compiz which was not fixed at release time.  The current workaround is to block running compiz on the affected pc's.

Jerry

---

### Post by plun on 2009-01-09
> **gnomeuser said:**
> How exactly am I wrong when the problem clearly is nvidia not adapting their driver to the upstream X API.

Would you claim that all APIs should remain frozen and supported for all time.. in which case I strongly encourage you to try, just for one small project, let alone something big like the kernel or X. In fact you can start by reading [this](http://www.mjmwired.net/kernel/Documentation/stable_api_nonsense.txt).

Nowhere did I say it was immoral or illegal for them to have closed kernel modules (though it is my belief that it would ruled as such in most court rooms). It is a purely techical matter, if the code was available the API changes could have been made and rolled out along with the X update. Nvidia are actively working against such development by the model they picked. This means their users have to wait. That is not X's fault, nor is it Ubuntu's fault. We break APIs when we need to, not because we think it's fun to mess with nvidia or their userbase.

My prediction though, Red Hat just hired one of the nouveau developers and with the other general developments in X and the kernel (GEM is in the kernel now e.g., drivers are getting massively better, Gallium3D is coming along). A year from now the nvidia module as we know it will not be the problem it is today for users (it will still be around, doubt we can get to 100% coverage in a year even at this pace but we will do the most used cards to an acceptable degree). This work will be no thanks to nvidia.

Well ... it can just be a big disaster such as Fedora 10.

Stop this "b---****" and be happy.... 

Or download Omega 10.


Do you support this company ?

[http://cbs5.com/technology/intel.antitrust.amd.2.773809.html](http://cbs5.com/technology/intel.antitrust.amd.2.773809.html)

---

### Post by ShirishAg75 on 2009-01-09
stop fighting children.

AFAIK the following things are true. 

1. Nvidia does it own thing. 
2. AMD/ATI had two sets of drivers but both open source. I dunno about RH but AMD/ATI did get one of the developers on its roll because the community drivers were much better. 

The last it seems that both the efforts are being merged to radeonhd 

3. Intel the other big boy has been releasing open source drivers since 3 years now. Keith Packard the Intel maintainer and now X.org maintainer did the work alone for quite some time. Now there are 2 more developers from Intel. 

AFA the Intel/AMD litigation is concerned, have to say there were few bad business decisions on AMD part 
n the past.

In the big picture Intel wouldn't want AMD not to survive. VIA is way way behind atm. The good thing is they also seem to be serious about supporting FLOSS.

---

### Post by plun on 2009-01-09
> **ShirishAg75 said:**
> stop fighting children.

No I will not and I take consequenses for it....  "RMS-nonsense !

This is just outrageous when this is also out.

[http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx](http://technet.microsoft.com/en-us/evalcenter/dd353205.aspx)


Makes me damned angry and just furios...  "nuts"](*,)](*,)](*,)

---

### Post by ronacc on 2009-01-09
> **ShirishAg75 said:**
> stop fighting children.

.
 sometimes you either fight or get sh*t on.

---

### Post by Rocket2DMn on 2009-01-09
Thread closed for bashing.

---

