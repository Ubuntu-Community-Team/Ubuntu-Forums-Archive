---
title: "LPIA abandoned"
date: 2009-11-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jbernardo on 2009-11-25
Just read a [ubuntu devel announce]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-November/000643.html") that LPIA builds are now discontinued. After the crappy GMA500 support (granted, that is Intel's fault), now the main advantage ubuntu had on the netbook market is dropped. Is it no longer a priority? And can't the LPIA builds be done more or less automatically, from the x86 ones, with minor patching? Or is the breakage that big that every LPIA build needs special tuning?

Maybe I'm being thick, but throwing away ~10% power savings seems to me a bad decision. Well, maybe I'm the only one using LPIA kubuntu...

---

### Post by gnomeuser on 2009-11-25
The performance enhancements are statistically insignificant when using the version of GCC in Karmic (and Lucid). As for the power savings I think we can gain more using other generic power saving tricks that are a better investment as they apply to all cases.

If you feel strongly about the LPIA arch then you can gather together supporters and do the builds yourself, like what is done with PPC today.

---

### Post by snowpine on 2009-11-25
> **gnomeuser said:**
> The performance enhancements are statistically insignificant when using the version of GCC in Karmic (and Lucid). As for the power savings I think we can gain more using other generic power saving tricks that are a better investment as they apply to all cases.

If you feel strongly about the LPIA arch then you can gather together supporters and do the builds yourself, like what is done with PPC today.

Hi Gnomeuser, I hope you don't mind my asking, but you seem knowledgeable about the project. Can you give a quick summary of what exactly lpia is, how it works? Is it a "Gentoo" sort of optimization?

I want to believe in lpia, but the fact that no other distro supports it leads me to believe there's no real benefit. It seems to me that recent kernel versions must have good Atom support, since it is such a common chip.

---

### Post by jbernardo on 2009-11-25
One of the benchmarks I've[ found ]("http://snowulf.com/archives/605-Benchmarking-Ubuntu-9.04-i386-vs-LPIA-on-Eee-PC-1000.html")(addmitedly, for 9.04) claims up to 21% improvement on more intensive tasks (kernel make). Another benchmark of 9.04 is the one done by [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_power_usage&num=1"), which gives the 10% less power spent by LPIA.

If the latest GCC blurs these differences, more power to it. If not, maybe you're right, time to try to rally up some LPIA supporters. Or join easypeasy or something like it, even though I prefer to run kubuntu on my netbooks.

---

### Post by snowpine on 2009-11-25
Thanks for the links, I appreciate it!

---

### Post by gnomeuser on 2009-11-25
> **snowpine said:**
> Hi Gnomeuser, I hope you don't mind my asking, but you seem knowledgeable about the project. Can you give a quick summary of what exactly lpia is, how it works? Is it a "Gentoo" sort of optimization?


Well, it is a known fact that if you set your compiler to optimize for your CPU you will generally get better performing code. LPIA is nothing more than this, in essence. You tell the compiler to output code that performs well on a subset of CPUs. This is a sane assumption to make since currently 99% of all netbooks (the intended platform for LPIA) are ATOM CPUs and the rest are probably VIA Nano CPUs which are already faster than the ATOM and will run ATOM optimized code as well.

The cost is that any package in your system will need to be compiled an additional time, you cover different optimization paths in the compiler (meaning if it produces wrong code you are more likely to be affected). The additional compiling means that for each package you as a maintainer send through the build system there is a longer wait till it hits your users (and for big projects like Openoffice this easily means compile times ranging in tens of hours or more). This naturally slows down development and reduces productivity, any measure taken to remove this problem either means making the arch a second class citizen compiled separately (which also slows down development since your users will be on different versions depending on the platform they install on) or removing it entirely.

By removing it entirely you'd have to ensure that the advantages you gained from the arch are reasonably covered by your generic build settings. With the new toolchain (gcc, binutils, glibc, etc.) we are very close to encompassing this goal and the regressions are deemed acceptable.

> 
I want to believe in lpia, but the fact that no other distro supports it leads me to believe there's no real benefit. It seems to me that recent kernel versions must have good Atom support, since it is such a common chip.

LPIA was a win when it was introduced but now it is less so and thus not worthwhile to keep up. The upgrade path naturally needs to be tested well but I think the decision will benefit Ubuntu overall.

Where it will hurt is that we get less coverage of the compiler optimization paths and generally the more architectures you compile a piece of software on the more genuine bugs you tend to uncover. We do get good coverage for ARM now which we didn't have before which is likely to matter more than LPIA for this specific case. Now if people are passionate about LPIA or any other arch and wish to support it because they see benefits from it then I would wholeheartedly applaud them for taking on the project and getting Ubuntu to help out in some unofficial capacity. It would make the code better for us all and it would help reach those few SPARC, IA64 and what not machines out there people might really want to use Ubuntu on.

---

### Post by gmc on 2009-11-25
This SUCK! ... I get regularly get 7-9 hours on my eeepc 1000he, depending on usage. With the lpia version 10% translate into 42-54 minutes more productive minutes. Of course it would help if Canonical didn't hide the lpia iso in it's ports directory!

I would consider switching to Gentoo but have no wish to burn out my SSD drive that I upgrading my machine with and spend 3 weeks compiling it on an Atom processor.

I certainly hope there's enough interest in continuing the lpia version alive.

G

---

### Post by gnomeuser on 2009-11-25
> **gmc said:**
> This SUCK! ... I get regularly get 7-9 hours on my eeepc 1000he, depending on usage. With the lpia version 10% translate into 42-54 minutes more productive minutes. Of course it would help if Canonical didn't hide the lpia iso in it's ports directory!


That is indeed a lot and I understand your concern. However please remember that the aim is always to improve power management for the entire distro. We have made great progress on this front in the past and will continue to do so. I would not be surprised if we managed to keep your excellent battery time with Lucid. Regardless this is a real concern and I would love it if you filed a bug so that we might track the exact loss and find ways to bring the overall stats back to an acceptable level in the Lucid timeframe (also please poke me via pm with the link I am interested in keeping up with this).

> 
I would consider switching to Gentoo but have no wish to burn out my SSD drive that I upgrading my machine with and spend 3 weeks compiling it on an Atom processor.


See above, it's not a disaster and we can gain you a lot back if you help us by getting data.

> 
I certainly hope there's enough interest in continuing the lpia version alive.


It would make for an interesting and fairly easy community project.

---

### Post by jbernardo on 2009-11-25
Seems like a good idea to me - if we can get enough people with free time to spend on this project. A kernel with only intel/atom support (no need for AMD if you're targetting LPIA), and LPIA optimized packages might mean a lot for our netbooks. As I wrote above, easypeasy and other ubuntu derivatives are options, but they tend to have "non-standard" interfaces. On bigger screen netbooks (10" or more) I see no reason not to run one of the three bigger DEs (KDE, Gnome, XFCE), so why not the whole (K)(X)ubuntu?

---

### Post by snowpine on 2009-11-25
Thanks, Gnomeuser... that is the clearest explanation I've ever heard of the lpia project. :)

I wonder if it is possible to compile specific applications optimized for lpia, within an i386 or amd64 system? In other words, for example if VirtualBox is faster in lpia, would there be any benefit to recompiling it with similar optimizations on a "regular" Ubuntu system?

---

### Post by jbernardo on 2009-11-26
You can mingle i386 and LPIA optimized code without problem. After all, I am running skype and picasa on my LPIA netbook, and those are only available in binary, for the i386.

---

### Post by gmc on 2009-11-26
I'd love to post a bug report about the demise of our beloved LPIA optimized version but have no idea under what I would post it on launchpad. After all it's not really a bug.

---

### Post by jbernardo on 2009-11-26
What we need isn't a bug  - its a fork, community project, or whatever you want to call it. I really don't have the time, but what I see as the path towards a "full ubuntu for atom netbooks" is:
First, as a precondition, benchmarking of both versions, LPIA and 386, with a "decent" test suite, to make sure there are really advantages for our netbooks. We need to watch out if the code available is really LPIA optimized, as the atom patches were removed from GCC in May, due to bug [#376499]("https://bugs.launchpad.net/ubuntu/+source/gcc-4.4/+bug/376499"). I am assuming they were put back later, for karmic.

If there are measurable advantages on using LPIA:

[LIST=1]
[*]Get in place build system and scripts to be able to build ubuntu's packages;
[*]"Clean" kernel options, to build a Atom/LPIA kernel; no need to carry all AMD, VIA, etc. stuff.
[*]Check package building, start tunning up more those that can give greater improvement - kernel, xorg, qt, plasma-*, etc.
[*]Mantain package parity with Lucid, and after launch aim for the next release, keeping the same maintenance as "main" ubuntu, supporting LRE for three years.
[/LIST]
What do you think?

---

### Post by gnomeuser on 2009-11-26
> **snowpine said:**
> Thanks, Gnomeuser... that is the clearest explanation I've ever heard of the lpia project. :)


you are welcome, please note it is not an explanation that covers everything, consider it the start of a conversation.

> 
I wonder if it is possible to compile specific applications optimized for lpia, within an i386 or amd64 system? In other words, for example if VirtualBox is faster in lpia, would there be any benefit to recompiling it with similar optimizations on a "regular" Ubuntu system?

Well.. recompiling VB might not give you what you seek, the specific performance increases might be more akin to a bit from glibc using optimized string operations, a bit from the kernel defaulting to other settings that are more suitable for ATOM type deployments and so on. VB itself isn't likely to gain that much as opposed to higher system impact packages. 

This also means that one might be able to get 80% or so of the benefits of LPIA by making builds of specific packages such as the kernel and glibc in LPIA configuration. At a much lower impact to your development process this might be the way to go.

It is worth further investigation at least. I would start by identifying hotspots and converting those packages to LPIA on an opt-in basis. My guess would be that we'd maybe need to convert less than 10 packages on a default system to get within that 80% range.

---

### Post by snowpine on 2009-11-26
> **gnomeuser said:**
> you are welcome, please note it is not an explanation that covers everything, consider it the start of a conversation.


Yes indeed, thanks again!

I agree with Jbernardo this is all idle speculation until someone comes up with a compelling set of benchmarks of Ubuntu 9.10 lpia vs. Ubuntu 9.10 i386 (and possibly amd64, for the Atom 330). 

My purely unscientific anecdotal evidence is that there is no advantage. I have not personally experienced increased battery life or tangible performance benefits. (Virtualbox did seem a little faster in 9.04 lpia, but I'm not feeling it with 9.10 so far).

---

### Post by Regenweald on 2009-11-26
This article may be of use, it would seem that the devs intend to include the lPIA extensions in the existing i386 platform.

[http://www.phoronix.com/scan.php?page=news_item&px=NzczOA](http://www.phoronix.com/scan.php?page=news_item&px=NzczOA)

---

### Post by SKLP on 2009-11-26
I do hope they include the Atom optimizations in the x86 version of Ubuntu (like they did in the latest Fedora). I think it gains more performance to Atoms, than the performance lost (compared to normal x86 build) when running on other x86 CPUs. And besides, a) Atoms are slow, thus it is important to get optimum performance  b) Most non-netbook people will be using x86_64 anyway

---

### Post by snowpine on 2009-11-26
> **SKLP said:**
> I do hope they include the Atom optimizations in the x86 version of Ubuntu (like they did in the latest Fedora). I think it gains more performance to Atoms, than the performance lost (compared to normal x86 build) when running on other x86 CPUs. And besides, a) Atoms are slow, thus it is important to get optimum performance  b) Most non-netbook people will be using x86_64 anyway

I agree; I've been running Fedora 12 on my eee since release day last week. Very happy with it so far!

---

### Post by michael37 on 2009-12-28
@jbernando, sign me up on whatever you come up with.  

I am running both Ubuntu 9.10 i386 and Ubuntu 9.10 lpia on my netbook.  I can probably do head to head benchmarks, but then again, it may not be the best comparison since lpia kernel in 9.10 is genericized.  jolicloud came up with Atom kernel, so I am sure there can be optimizations for this architecture.  Overall, I just don't get why my Atom netbook should run the same binary code as some Semptron based desktop.  Just because developers think that are better off spending time on IA-64 desktop and server ports (Itanium workstations were discontinued in 2004) than on zillions of netbooks in user hands??

---

