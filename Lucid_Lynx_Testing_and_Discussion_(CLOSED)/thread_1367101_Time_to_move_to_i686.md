---
title: "Time to move to i686?"
date: 2009-12-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2009-12-29
Hi,
i686 was introduced in 1995.
Fedora already switched to i686.
**Who are the people** who use pre 1995 hardware that we're trying to stay compatible with by still using i386 builds?
Anyone (at Canonical or elsewhere) got any stats?
I think their "market share" is less than 1 in ten thousand.
We'd get a few % performance for free, which is what Ubuntu is focusing on lately.

---

### Post by farrell on 2009-12-29
That is so true...

I, for one, have switched to AMD64 to overcome this issue.

But I've also heard that x86-64 consumes more power than x86-32 (64bit pointers you may not need, ...). OTOH, you get more work done with large registers.

---

### Post by MacUntu on 2009-12-29
There's no such thing as i686. Do you mean the Intel P6 family or maybe AMD64?

---

### Post by sisco311 on 2009-12-29
Ubuntu's generic kernel detects the architecture of the processor at boot time and uses optimization for it.


[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html")
>  A lot has happened to the kernel since
the early days, though, and for some time, it has been capable of loading
these optimizations at runtime.  Even when you use the -386 kernel, you get
the benefit of many CPU-specific optimizations automatically.  This is great
news for integrators, like Ubuntu, because we want to provide everyone with
the best experience out of the box, and as you know, there isn't room for so
many redundant kernels on the CD (only one).  Many users spend time and
bandwidth quotas downloading these optimized kernel in hopes of squeezing
the most performance out of their hardware.

This begged the question: do we still need these old-fashioned builds?

---

### Post by fromthehill on 2009-12-29
> **kahumba said:**
> Hi,
i686 was introduced in 1995.
Fedora already switched to i686.
**Who are the people** who use pre 1995 hardware that we're trying to stay compatible with by still using i386 builds?
Anyone (at Canonical or elsewhere) got any stats?
I think their "market share" is less than 1 in ten thousand.
We'd get a few % performance for free, which is what Ubuntu is focusing on lately.

I don't think i368-only processors can even run ubuntu :P

---

### Post by Bachstelze on 2009-12-29
> **kahumba said:**
> We'd get a few % performance for free, which is what Ubuntu is focusing on lately.

Make that a few tenths of a percent.

---

### Post by sisco311 on 2009-12-29
> **Bachstelze said:**
> Make that a few tenths of a percent.

> == Conclusion ==

Having read over it, I think the numbers are fairly compelling.  The
difference in performance between -386 and -686 is **insignificant**; the
measurements are all within a reasonable error range, and within that range,
**-686 was slower as often **as it was faster.
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html")

---

### Post by kahumba on 2009-12-29
> **Bachstelze said:**
> Make that a few tenths of a percent.

> 
**[B]For Fedora 12, we are switching to i686 as the base architecture (including CMOV), and improving support for Atom processors.         **[/B]

Benefits:              
1. Faster binaries on mainstream architectures (Pentium M, Via C7, all 64-bit arches, Atom)                     

Next 2 reasons might not apply to Ubuntu:
2. Realistically, support for i586 in Fedora 11 was quite limited. This change makes that lack of support a little more clear.
3. Fewer kernel builds                     
[http://docs.fedoraproject.org/release-notes/f12/en-US/html/sect-Release_Notes-Architecture_Specific_Notes.html#sect-Release_Notes-Architecture_Specific_Notes_686](http://docs.fedoraproject.org/release-notes/f12/en-US/html/sect-Release_Notes-Architecture_Specific_Notes.html#sect-Release_Notes-Architecture_Specific_Notes_686)

---

### Post by cascade9 on 2009-12-29
> **kahumba said:**
> **Who are the people** who use pre 1995 hardware that we're trying to stay compatible with by still using i386 builds?
 
 Pre-1995? i386 was 1985-1989, i486 came out in 1989. 

> **MacUntu said:**
> There's no such thing as i686. Do you mean the Intel P6 family or maybe AMD64?

Technically, you can go round and round about if there is a 'i686'. I personally think its a valid term. Its used to mean 'P6 microarchitecture' (P6 being pentuim pro, so all intels from there onward, and AD from athlon onward).

> **fromthehill said:**
> I don't think i368-only processors can even run ubuntu :P

Nope, they cant. 486/32MB 'absolute minimum' (and thats CLI only, and very limited packages)

I'm pretty sure that ubuntu keeps the i386 name because debian (which, lets face it, ubuntu is just a fairly modded version of) does. 

IMO, they shouldnt move to i686, as while there is no way to get an 386 running on ubuntu, and a 486 would be painful, theres still quite a few people with AMD K6-2 and K6-3 (which is faster than the pentium 2's) around and they wont support i686.

---

### Post by kahumba on 2009-12-29
> **cascade9 said:**
> 
...
 theres still quite a few people with AMD K6-2 and K6-3 (which is faster than the pentium 2's) around and they wont support i686.
Bingo!
The question is, how many run Ubuntu for serious on AMD K6-2/3 in terms of %?
I'd bet that much (much!) less than 1%.
Imo Canonical should rather do like Fedora, use i686 builds optimized for Atom processors - now that's what I'd call a fully justified change.

---

### Post by caryb on 2009-12-29
Perhaps a poll is in order? 


Cary

---

### Post by kahumba on 2009-12-29
Good idea, just added the poll.

---

### Post by phillw on 2009-12-29
I voted no - however, there is a proviso in my "No" vote. **IF** xubuntu still supported said aged processors, then I'd give it a resounding **yes** for the main-stream Ubuntu -- But, then we'd be relegating xubuntu as second best & how long would the devs spend on it if it were untied and cast alone upon the open ocean ?
As computers for all - some people & countries DO have such aged processors, and I personally think that side-lining them would be totally against the Ubuntu ethos & a bad day for all.

Just my $0.02

Phill.

---

### Post by knarf on 2009-12-29
The gain is not worth the pain. The actual gains are negligible and processors which would benefit from i686 optimizations are already plenty fast. Those processors which would be shut out by these optimizations are on the slower side *but* they can still be useful in one way or another [1].

Another option is to offer an additional i686/Atom optimized kernel. There are already several kernels for different architectures so one more should not be a problem. The gains will still be small though so it might not be worth it.

[SIZE="1"][1] I have some 32MB Winchip and Geode machines which make useful X terminals with some local processing capability. Using NX and a working X server these do fine in the barn and the workshop as well as in the kitchen. [/SIZE]

---

### Post by cascade9 on 2009-12-29
> **kahumba said:**
> Bingo!
The question is, how many run Ubuntu for serious on AMD K6-2/3 in terms of %?
I'd bet that much (much!) less than 1%.
Imo Canonical should rather do like Fedora, use i686 builds optimized for Atom processors - now that's what I'd call a fully justified change.
 
 I actually think the moving to i686 is totally wrong. It would lose support for some newish CPUs (Geode GX, Via C3). Not that many of those CPUs, but it would be a right pain, and could cause a lot of user annoyance. I can already see cries of 'why isnt my CPU supported?', and confusion over exactly what is, and what is not supported. i586 might be OK. That way people would know that any pentuim class CPU, and pretty much anything after it, would work. 

As for optimizing i686 for Atom- stupid, very stupid. Only 1 series of 'standard' Atom is 32 bit only (Diamondville, or N270/280). The UMPC versions are 32 bit as well, but building a what is a desktop OS and optimizing for ultra-portables is silly. But I'm all for running 64bit if your CPU supports it in 90%+ of cases. 

IMO, there not much chance of even moving to i686 happening, it would just add extra work when making x.xx versions of ubuntu from the debian base. 

> **phillw said:**
> I voted no - however, there is a proviso in my "No" vote. **IF** xubuntu still supported said aged processors, then I'd give it a resounding **yes** for the main-stream Ubuntu -- But, then we'd be relegating xubuntu as second best & how long would the devs spend on it if it were untied and cast alone upon the open ocean ?
As computers for all - some people & countries DO have such aged processors, and I personally think that side-lining them would be totally against the Ubuntu ethos & a bad day for all.

Just my $0.02

Phill.

+1 on 'some countries do have older processors'. 

Xubuntu is 2nd best already IMO. I really wish that it was more Xfce-centric, as opposed to just moving all the gnome programs, standard setup, etc from ubuntu.

---

### Post by ronacc on 2009-12-29
I've been 64 bit exclusively for years but I still voted no . I386 and for that mater 32bit in general will die a natural death but the time is not yet . The I386 arch has a wider compatibility range than later archs and should be kept at least for the present .

---

### Post by edujose on 2009-12-29
> **kahumba said:**
> Bingo!
The question is, how many run Ubuntu for serious on AMD K6-2/3 in terms of %?
I'd bet that much (much!) less than 1%.
Imo Canonical should rather do like Fedora, use i686 builds optimized for Atom processors - now that's what I'd call a fully justified change.

I agree with phillw and cascade9. Not all countries are like the more advanced ones in Occident. Even in Europe, the poorer countries still have uses for PIII and AMD K2/K3 onward. Mine uses them in the more unthinkable of places, like in schools/highschools, where money for education is (strangely) scarce.

Such old computers are used by teachers in their departments (computer classrooms usually employ the newer ones sent to centers while departments employ PCs retired from such classrooms). And many regions in the country are using some Ubuntu variant for their PCs in schools, so with Ubuntu using the i386 instruction set these old machines can still be put to good use.

We would like having all our computers upgraded to the latest and greatest every 3 years, but those who decide seem to think money is better spent elsewhere (sigh).

---

### Post by dino99 on 2009-12-29
yeah,

as Linus have said some time ago, actual kernels are too fat. Linux is everywhere and run on not so strong cpu (embebded hardware).

Community still need to find a linux distro able to work on such hardware.

---

### Post by benjamimgois on 2009-12-29
> **ronacc said:**
> I've been 64 bit exclusively for years but I still voted no . I386 and for that mater 32bit in general will die a natural death but the time is not yet . The I386 arch has a wider compatibility range than later archs and should be kept at least for the present .

+1 , agreed. i386 will die naturally, 64bit architectures should be the main preocupation, even the new Intel ATOM processor are 64bit enable.

---

### Post by gnomeuser on 2009-12-29
Moving directly to i686 would mean that a number of the Via CPUs would stop working as they do not have CMOV support. These chips are widely and are still available in products on the shelves.

Also we would need some data to show what the impact across a multitude of chips, some would likely perform better, some worse - we need to know what the outliers are and determine if the trade-off is worth it. Another concern is that the i386 optimization in GCC is well tested, switching might uncover subtle bugs which we must be ready to deal with. 

However switching half way through an LTS cycle is not a good idea. I believe we should wait till Lucid+1 and perhaps then announce that for the next LTS anything below i686 isn't officially supported (people could still maintain unofficial versions for i386). Lucid+1 could then move to i585 plus a subset of optimizations for more recent cpus, for lucid+2 o +3 we can default to i686. That gives vendors time to anticipate such a major move, it gives the compiler maintainers time to prepare for a potential influx of new optimization bugs. It also lets us use the same path as Fedora has been taking meaning hopefully more cooperation on bugs and fewer problems.

---

### Post by Starks on 2009-12-29
Doesn't Fedora also have i486/i586/i686 optimized packages?

---

### Post by Gina on 2009-12-30
I voted no because as has already been said, we should not base Ubuntu on the more affluent Western countries.  And if fact, I still run a K6-2 machine.  I've only taken it off the list in my sig due to space and wanting to add more info on my other machines.  I am currently developing automatic weather station software and hope to run that on the K6-2, freeing up my other machines for other uses and testing.  Though I might test Xubuntu Lucid on it.  I think there might be more machines of this vintage around than many people think.  The alternative to Linux is Win98 <aarrgghh>

---

### Post by ranch hand on 2009-12-30
Our other box, running 8.10, is a HP pavilion xt 993.  I think it is going to have some problems with 64bit.

---

### Post by lykwydchykyn on 2009-12-30
> **knarf said:**
> 
[SIZE="1"][1] I have some 32MB Winchip and Geode machines which make useful X terminals with some local processing capability. Using NX and a working X server these do fine in the barn and the workshop as well as in the kitchen. [/SIZE]

+1 

I'm willing to bet a good chunk of the larger (and commercial-support-buying) Ubuntu deployments are thinclient related.  I don't know if i386 support is required for Geode processors, but if it is I know I'd have to look elsewhere for my thin client setup.

---

### Post by andrewabc on 2009-12-30
Not sure about this. Does i686 mean x64 only (not sure how possible with atom processors)? If so this is a bad idea.
I run ubuntu on pentium 4 computer that is not x64 processor.

Maybe after 10.04 make the decision, but for obvious reasons 10.04 would need x32 and old computer support. After that then get rid of it if needed and people can run 10.04 for 3 years.

---

### Post by lykwydchykyn on 2009-12-30
> **andrewabc said:**
> Not sure about this. Does i686 mean x64 only (not sure how possible with atom processors)? If so this is a bad idea.
I run ubuntu on pentium 4 computer that is not x64 processor.

Maybe after 10.04 make the decision, but for obvious reasons 10.04 would need x32 and old computer support. After that then get rid of it if needed and people can run 10.04 for 3 years.

i686 != x64

i686 refers to processor optimizations present in Pentium Pro processors or later.  So, speaking strictly of Intel CPUs, this would mean anything post 1995.  But as others have mentioned, non-intel CPUs (AMD, Via, etc) have much newer processors which don't support i686 apparently.

---

### Post by glasen on 2009-12-30
For clarification :

i686-optimization means, that only the Pentium Pro (predecessor to the Pentium 2) and newer and the AMD Athlon (aka K7) and newer will be supported. That means roughly for Intel-CPUs that they must not be older than 1997 and for AMD, not older than 1999.

i586-optimization supports all CPUs since the Pentium 1 and AMD K5. In years this means 1993 and 1996.

There are not many people out there who still use a Pentium 1. And when they do, it will be highly unlikely that they will use Ubuntu on this machine. For most P1/AMD-K5/AMD-K6-boards it was not possible to use more than 64MB of RAM.

---

### Post by Gina on 2009-12-30
> **glasen said:**
> 
There are not many people out there who still use a Pentium 1. And when they do, it will be highly unlikely that they will use Ubuntu on this machine. For most P1/AMD-K5/AMD-K6-boards it was not possible to use more than 64MB of RAM.Wanna bet?! :lolflag:

My K6-2 is running with 384MB of RAM quite happily and will support more though I'm not sure of the actual limit.  It is currently running Ubuntu.

If these are no longer supported by Ubuntu it will simply mean many will switch to another distro.  Ubuntu will lose out!

---

### Post by glasen on 2009-12-30
> My K6-2 is running with 384MB of RAM quite happily and will support more though I'm not sure of the actual limit.  It is currently running Ubuntu

Okay, i forgot that there were plenty of Socket-7-Boards, after the release of the Pentium-II, which were build for the K6, K6-2 and 3 and could support more than 64MB of RAM.


> 
If these are no longer supported by Ubuntu it will simply mean many will switch to another distro.  Ubuntu will lose out!

Why should Ubuntu "lose out"? If they use another Linux-distribution, they will still use Linux.

---

### Post by 6205 on 2009-12-30
My first question is, what do you mean by 686? 

First 686 CPU was Intel Pentium Pro 150Mhz in 1995 and has IMO very different architecture from any current Core2Duo CPU which is i think IA32/64 architecture. 

Second question, asuming that current CPU's are fully backward compatible with old pentium pro, question is what improvements it can bring to us, optimizing ubuntu on 686.

Is it even worth the bother? Can we notice the difference?

---

### Post by cascade9 on 2009-12-31
> **glasen said:**
> Okay, i forgot that there were plenty of Socket-7-Boards, after the release of the Pentium-II, which were build for the K6, K6-2 and 3 and could support more than 64MB of RAM.

Plenty of 486 chipsets took up to 128MB, and _all_ the intel 586 chipsets took 128MB RAM or over. 

I think you have confused 'max RAM' with 'max cacheable RAM'. Which was limited to 64MB on all the 'desktop' level intel pentuim chipsets (the server level chipsets, like NX and HX, went to 512MB)  

The non-intel chipsets were less limited- the VIA socket 7 chipsets normally went to 512MB, and later super socket 7 (MVP3, MVP4) to 768MB (with Intel didn't support on desktop til the rare 815EP). By the time of the Intel 815, VIA was going out to minimum 1GB, and up to 4GB!- 

[http://en.wikipedia.org/wiki/List_of_Intel_chipsets](http://en.wikipedia.org/wiki/List_of_Intel_chipsets)
[http://en.wikipedia.org/wiki/VIA_chipsets](http://en.wikipedia.org/wiki/VIA_chipsets)

> **6205 said:**
> First 686 CPU was Intel Pentium Pro 150Mhz in 1995 and has IMO very different architecture from any current Core2Duo CPU which is i think IA32/64 architecture. 

Yes, very different architecture, but they will run on P6 (pentium pro) instruction sets. 

Pentium Pro was the 1st intel CPU optimised for 32bit. Which made it slower the a normal pentuim for desktop use at the time. You needed a 32bit OS (unix, OS/2, NT)to even get close to getting max performance out of them, and it would really help if you were running a 32 bit application (which was rare). For a win95/dos user, the p-pro was a huge waste of time and money...but it was ahead of its time in a lot of ways. 

While intel lated added instruction sets for newer processors (MMX, SSE, etc) the 32 bit optimisation on the p-pro made it the 'base' for all later CPUs made for 32 bit.

---

### Post by Robin Nixon on 2009-12-31
I have used Ubuntu to revive several very old PCs that had become unusable for running Windows. For me that is probably the *biggest* benefit Ubuntu has going for it, and it should remain that way.

---

### Post by andrewabc on 2009-12-31
Sort of relevant to discussion:

[Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
64 bit wins almost every benchmark.

---

### Post by glasen on 2009-12-31
> **cascade9 said:**
> I think you have confused 'max RAM' with 'max cacheable RAM'. Which was limited to 64MB on all the 'desktop' level intel pentuim chipsets (the server level chipsets, like NX and HX, went to 512MB)

You are right.

But nevertheless, here is a interesting bit of read (Sorry it's in german only :

[Linux und Open-Source in Afrika]("http://www.be-jo.net/de/2009/12/linux-und-open-source-in-afrika/")

[Google Translation]("http://translate.google.de/translate?js=y&prev=_t&hl=de&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.be-jo.net%2Fde%2F2009%2F12%2Flinux-und-open-source-in-afrika%2F&sl=de&tl=en")

This means, even in one of the poorest countries in the world most PCs have at least a i686-compatible CPU (P2 or higher).

---

### Post by phillw on 2009-12-31
> **Robin Nixon said:**
> I have used Ubuntu to revive several very old PCs that had become unusable for running Windows. For me that is probably the *biggest* benefit Ubuntu has going for it, and it should remain that way.

Indeed, as already mentioned, the other option would be, gulp, 98SE. In fairness to 98SE it was the best, IMHO, of Win until XP got settled - and that a couple of years & a 'few' broken computers !!

We seem to over-look what we have, an upto date OS that supports older architecture - For this we should, and others are, very grateful. There's always those wishing to be at the bleeding edge - once they've cut their teeth with ubuntu - let them learn to optimise the core for themselves - the instructions are out there in the Wiki's. I was looking in on a thread where they were putting the entire OS into RAM, they were having gr8 fun learning stuff & learning even more when they broke it & then worked out to fix it.

We are a many coloured animal, different people want different things - But one thing that we should all be able to agree on is allowing as many people as possible to have the ability to use Ubuntu. Anything that cuts down on that, is IMHO, a retrograde step.

As for RAM -- I had 256K of ram strapped to an 8 Bit Atari, a very, very early case of 'expanded' or 'extended' (Too long ago to remember which) that would 'page' up & down - It was incredible !!! (Programming in HEX wasn't so much fun - lol) - People are incredibly resourceful & inquisitive, look at how Linux 1st started.

And on that missive, a very Happy New Year to All Ubuntu'ers (And everyone in the Linux Community) - May you all have a great 2010 - and may the march of Ubuntu continue !!!


Phill

---

### Post by ronacc on 2009-12-31
While I agree with your sentiment and that we should not reduce our user base by dumping i386 , win98 isn't the only option ,there are other linux distros that specialize in "challenged" hardware  .

---

### Post by phillw on 2009-12-31
> **ronacc said:**
> there are other linux distros that specialize in "challenged" hardware  .

I'd miss the smell of freshly brewed coffee.

:popcorn:

Phill.

---

### Post by ssam on 2009-12-31
I had a via epia that could not run i686, but it died this year. it was handy to run ubuntu on it, but debian would have been fine.

we really need a simple tool for rebuilding packages with different compile options. we can already do
```

apt-get source --build firefox

```
but it would be nice to do
```

apt-get source --build --cflags "-O3 -march=native" firefox

```
then if people could easily see the benefits.

whether to keep i386 also depends on what ubuntu aims to be. is it a universal OS that runs anywhere, and can be customised to do anything? is it the fastest desktop OS? is it best on new hardware, or netbooks, or old computers?

also maybe CPU optimisation is not where to look for speed ups. boot time has got dramatically faster but optimising disk access, parallelizing, and removing unnecessary things.

---

### Post by ronacc on 2009-12-31
no need to "puppy" will run on  your mr.coffe and still brew a cup :lolflag:

---

### Post by VMC on 2009-12-31
> **ronacc said:**
> While I agree with your sentiment and that we should not reduce our user base by dumping i386 , win98 isn't the only option ,there are other linux distros that specialize in "challenged" hardware  .

[TinyCore]("http://www.tinycorelinux.com/") anyone?

---

### Post by cascade9 on 2009-12-31
> **glasen said:**
> You are right.

But nevertheless, here is a interesting bit of read (Sorry it's in german only :

[Linux und Open-Source in Afrika]("http://www.be-jo.net/de/2009/12/linux-und-open-source-in-afrika/")

[Google Translation]("http://translate.google.de/translate?js=y&prev=_t&hl=de&ie=UTF-8&layout=1&eotf=1&u=http%3A%2F%2Fwww.be-jo.net%2Fde%2F2009%2F12%2Flinux-und-open-source-in-afrika%2F&sl=de&tl=en")

This means, even in one of the poorest countries in the world most PCs have at least a i686-compatible CPU (P2 or higher).

I wouldnt say that article, interesting as it is, says that most people in Tanzania have access to P2s or higher. Aside from any hard data, a computer lab and an internet cafe is where I would expect to find newer computers than a lot of people would own. BTW, from living in a hot country myself, I had to giggle at the 'side panel removed cases'. I would bet that are nice hot Intel chips in there (p3-600, p4s). 

There are still CPUs on the shelf here, now, in the west that are not i686- 

> **gnomeuser said:**
> Moving directly to i686 would mean that a number of the Via CPUs would stop working as they do not have CMOV support. These chips are widely and are still available in products on the shelves.

Going i686 would be a bad IMO. But, like I said before, I really doubt that its going to happen as long as ubuntu continues to be built of a debain base. 

Anyway, if you do have access to modern chips, the majority of them are AMD64 anyway. Why bother with all the extra work involved in i686 work (over i386 from the debian base) when almost everyone can run 64bit? Leave 32 bit to 'legacy', and support the greatest number of CPUs you can with it is my opinion.

---

### Post by Merk42 on 2009-12-31
> **cascade9 said:**
> Anyway, if you do have access to modern chips, the majority of them are AMD64 anyway. Why bother with all the extra work involved in i686 work (over i386 from the debian base) when almost everyone can run 64bit? Leave 32 bit to 'legacy', and support the greatest number of CPUs you can with it is my opinion.

+1

Is that market "between" i386 and AMD64 really that large that Ubuntu should go from i386 to i686?

---

### Post by phillw on 2009-12-31
> **ssam said:**
> 
whether to keep i386 also depends on what ubuntu aims to be. is it a universal OS that runs anywhere, and can be customised to do anything? is it the fastest desktop OS? is it best on new hardware, or netbooks, or old computers?


A good point. 
Should Ubuntu aim to be a universal OS, or should there be another flavour - optimised for i686 ?

I am in the process of putting xubuntu 9.04 onto an aged G3 Mac, that support is being carried by a group determined to keep xubuntu & older hardware all working (ppc, in my case). Is the Mac dead ? Nope. Is it well beyond the M$ "3 years old & replace it"? Certainly. Has it failed ? - Nope. Why should we, in this consumer society, throw away perfectly good computers ? - I've been involved in breathing new life into computers that have been thrown into municipal skips for electrical goods, so, maybe I am a bit biased.

If a flavour of Ubuntu can support, via xubuntu, such aged kit - surely those who want 'beeding-edge' stuff can do the same ?  It will gradually filter down - In 5 years, the computer I'm running on may only be capable of xubuntu ? - It's a bog standard Intel M Processor with 1GB RAM and a 80 GB Hard Disk. Hardly 'State of the art' when people are using quad core processors. But, compared to it running Vista - which it was designed for, and running Ubuntu ... Slug, crawling over a mountain of salt compared to a fighter jet with the afterburners on.  

I know that someone on this forum is involved with lubuntu --> [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

I, for one, would be more than happy to go get an aged piece of kit for them to use as a crash-dummy. 

Maybe, sometimes, we forget to be thankful of what we have & how far it has come. 

Push forwards, please do - only by doing that will we make progress, but please - do not forget those not as fortunate as yourselves.

Sorry to go back to our ethos, but, as you seek to cut off older equipment, please take the time to read this --> [http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

Or, for a more personal view of what we are, what we seek to be - I found this to be an excellent personal view.

[http://www.jonobacon.org/2008/12/19/the-ubuntu-ethos/](http://www.jonobacon.org/2008/12/19/the-ubuntu-ethos/)

This short extract from it, can still bring me to tears ...

> Shortly after I joined Canonical as the Ubuntu Community Manager I received an email from a contributor in Africa. The sender informed me that where he lived there was sparse Internet access and little access to computers. He told me that he had seen Ubuntu demonstrated in a local town and our ethos inspired him to join the community and participate. To do this he walked two hours to the local town to an Internet cafe, used his own money to buy an hours worth of Internet access to contribute to Ubuntu, and then walked two hours home afterwards.
  That email has always stayed with me. Firstly, it is a reminder that we need to make every second in his and everyone else’s hour count. We need to smooth every interaction. We need to optimize every process. We need everyone to not only feel that their hour was productive and satisfying, but it was fun and rewarding.
  But possibly the most salient of lessons in that email was just how much commitment people can have to an ethos they share and want to be a part of. When we *feel* the ethos and the mission, we are ready to take on the world.
  So, please, please do not turn your back on those people.

Phill.

---

### Post by ronacc on 2009-12-31
we need to keep i386 to maintain compatibility for ALL users , adding a separate version for the few who would benefit and then only marginally from i686 would add workload and complexity that I don't feel we need . For those of us in "advanced" countries who have access to relatively cheap hardware and want more performance , come on bite the bullet and go 64bit , I did years ago and it didn't hurt a bit .

---

### Post by reub2000 on 2010-01-01
> Should Ubuntu aim to be a universal OS, or should there be another flavour - optimised for i686 ?Well I don't think that Ubuntu itself targets such old hardware. But I think there are a few derived distros that do. In any case, even if Ubuntu dropped support for older CPUs, these machines wouldn't automatically turn into bricks as many other distros would support them. About a month ago that there was [an article]("http://distrowatch.com/weekly.php?issue=20091026#qa") and discussion on distrowatch about distros specifically tailored to older hardware. Even though I doubt many people are running Ubuntu on an 80386, I say keep it the same simply because the gains are too insignificant to warrant any change.

---

### Post by insane_alien on 2010-01-01
how about we just start leaning to x86_64. 32-bit is on the decline anyway and the kernel does have some dynamic optimisations that allow it to use i686 instructions if they are available anyway.

---

### Post by TrueTom on 2010-01-01
It still would be nice to have optimized packages for software that would noticeably benefit like *libjpeg* where the optimized version is two times faster.

---

### Post by edujose on 2010-01-01
> **phillw said:**
> 
Maybe, sometimes, we forget to be thankful of what we have & how far it has come.

Push forwards, please do - only by doing that will we make progress, but please - do not forget those not as fortunate as yourselves.

Sorry to go back to our ethos, but, as you seek to cut off older equipment, please take the time to read this --> [http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

Or, for a more personal view of what we are, what we seek to be - I found this to be an excellent personal view.

[http://www.jonobacon.org/2008/12/19/the-ubuntu-ethos/](http://www.jonobacon.org/2008/12/19/the-ubuntu-ethos/)

Have to agree with phillw, same sentiments here.

Perfectly valid PIII/P4 hardware must not be thrown away. Fitted with any Linux distro, they work great for everyday uses (even programming). And they are used extensively for giving computing access to schools, homes, shops, community centers, etc.

Also, the ethos or philosphy in Ubuntu is equally valid not just for Africa's poor countries but also for our richer countries. Just take a walk outside the city center with open eyes and see what kind of computers people use. Not a lot of quad cores nor i7s outside the wealthier places.

> **cascade9 said:**
> 
Anyway, if you do have access to modern chips, the majority of them are AMD64 anyway. Why bother with all the extra work involved in i686 work (over i386 from the debian base) when almost everyone can run 64bit? Leave 32 bit to 'legacy', and support the greatest number of CPUs you can with it is my opinion.

Also agreed with cascade9 and Merk42.

Would be reasonable to stay with i386 for older machines (and current ones with <= 4 GB RAM), and go to 64 bits in newer machines (and those with > 4 GB).

---

### Post by markp1989 on 2010-01-01
> **fromthehill said:**
> I don't think i368-only processors can even run ubuntu :P

agreed, any systems using i368 only cpus should run somthing lighter (even arch a light distro is compiled or i686)

---

