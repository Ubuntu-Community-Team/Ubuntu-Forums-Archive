---
title: "Linux dead end?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by Radly on 2010-05-06
I have been running 8.04 LTS for almost as long as it's been available and recently decided it was time to rejuvenate my Linux box.  I installed a new graphics card (GeForce instead of the on-board chipset) and a new disk drive (320 GB instead of the 30 GB it had).  I've ordered 1 GB of RAM to upgrade from 384 MB.  But I'm stuck with the P4 Celeron processor, which "should" be good enough for me at 1.8 GHz.  I downloaded the 10.04 ISO image, checksummed it, burned it onto a CD, and tried to install it.  (Twice, the second of which was at the slowest burn speed I had, 1x).  The installer crashes almost immediately.  I tried the "check disk" option to make sure the CD was okay, and THAT crashed.  So I installed 8.04 (that went just fine) and tried the online upgrade to 10.04.  That, too, went just fine until I tried to boot into my spiffy new OS.  That crashed, too.  So I got a tad frustrated, downloaded Fedora 12, and THAT installer crashed.  All the evidence says I'd better get comfortable with 8.04, but that's kinda sucky.

Does anyone have a good idea what's going on and what I can do about it to get more up to date?

---

### Post by alphacrucis2 on 2010-05-06
> **Radly said:**
> I have been running 8.04 LTS for almost as long as it's been available and recently decided it was time to rejuvenate my Linux box.  I installed a new graphics card (GeForce instead of the on-board chipset) and a new disk drive (320 GB instead of the 30 GB it had).  I've ordered 1 GB of RAM to upgrade from 384 MB.  But I'm stuck with the P4 Celeron processor, which "should" be good enough for me at 1.8 GHz.  I downloaded the 10.04 ISO image, checksummed it, burned it onto a CD, and tried to install it.  (Twice, the second of which was at the slowest burn speed I had, 1x).  The installer crashes almost immediately.  I tried the "check disk" option to make sure the CD was okay, and THAT crashed.  So I installed 8.04 (that went just fine) and tried the online upgrade to 10.04.  That, too, went just fine until I tried to boot into my spiffy new OS.  That crashed, too.  So I got a tad frustrated, downloaded Fedora 12, and THAT installer crashed.  All the evidence says I'd better get comfortable with 8.04, but that's kinda sucky.

Does anyone have a good idea what's going on and what I can do about it to get more up to date?

What software did you use to burn the disks?

---

### Post by kaldor on 2010-05-06
Fedora has a reputation to mess up on my laptop. Check another distro instead.

It could be that the newer kernels dislike your current hardware, but don't take my word on it.

---

### Post by matchett808 on 2010-05-06
try switching back to onboard graphics and doing the install.....

---

### Post by matchett808 on 2010-05-06
try switching back to onboard graphics and doing the install.....

---

### Post by fedexnman on 2010-05-06
i bet ubuntu 9.10 would work.

---

### Post by iponeverything on 2010-05-06
A few people have had luck by adding adding grub boot options. 

google around a bit.

---

### Post by oldsoundguy on 2010-05-06
Check that new memory.  It sounds like a memory issue.

Or try a different CD/DVD player .. run it from the burner?

---

### Post by QIII on 2010-05-06
Odd.

Have you tried using the alternate install disk?

---

### Post by Radly on 2010-05-06
Well, that's certainly several things to try.  Let me answer a few of them here.

I used Active(c) ISO Burner (on my Windows box, since it actually works), the same burner I used to burn my 8.04 installer, which works perfectly.

The new memory hasn't arrived yet--I'm still using the same memory that runs 8.04 perfectly.  It also passes the memory test on the install CD.

I thought about the 9.10 idea, but couldn't find the install image anywhere.  I'll look again.

Where should I add grub boot options?  The installer never got to the point of installing anything, let alone grub.

Maybe a good night's sleep for me AND my machine will do us both good. :)

---

### Post by iponeverything on 2010-05-07
> **Radly said:**
> 
I thought about the 9.10 idea, but couldn't find the install image anywhere.  I'll look again.

See:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
> 

Where should I add grub boot options?  The installer never got to the point of installing anything, let alone grub.

see:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also consider the Alternate install CD as suggested by @QIII

---

### Post by Radly on 2010-05-07
My good night's sleep did me good but not my Linux world.  I found a 9.10 "Alternate Installer" that allegedly is satisfied with less than 256MB RAM.  So I burned it, ran another memory test, ran the disk validator, and tried to install.  At least this installer didn't crash.  It just failed to recognize my ethernet card.  So the heck with it.  I'm reinstalling 8.04 and waiting for my new memory to arrive.  Maybe the newer installers require more memory than they like to publicize.

---

### Post by QIII on 2010-05-07
Could you leave just a bit of room for an attempt to install a newer version?

You may have hit on something here that may be a big problem that really should be solved.

A bit of altruism on your part might help the community.  If it wouldn't be too much trouble, of course.

---

### Post by Radly on 2010-05-07
I'm nothing if not altruistic!  This is not a mission-critical machine, so if there's something specific you want me to try and report on, let me know.  As I speak, 8.04 has just finished installing and I've not yet run the 250 updates, so I can redo that easily.

---

### Post by gnwiii on 2010-05-07
I just gave up on my P4 machine -- some applications (sagemath) are build for a new instruction set and won't run at all.   I could recompile, but sagemath takes a day to rebuild on P4 while downloading binaries and installing takes under an hour.   With free software you have to rely on the developers -- I'd prefer that they work on fast machines so they can make improvements without spending time waiting for compiles.   The money I saved by not buying M$ software has just been sitting around making some banker richer, so I don't mind spending it on new kit.

There have been some unexpected benefits -- a longstanding problem with a package I used was preventing my colleagues from updating their software.   The problem was one of those "my library doesn't have any bugs, so your program is at fault" vs 'my program doesn't have any bugs, so your library is a fault" stalemates.  Ubuntu 10.4 gave me the current version, and installing an older version in a VM allowed me to do some side-by-side comparisons in under an hour.  These revealed a change (new feature?!) affecting the conditions under which a file buffer was flushed.  Understanding this change means we now know how to make things work with the new version, and lets the library developer off the hook.    My P4 was often running 7x24 doing software test builds -- now the same builds can be done while walking the dog, so the new machine does not need to run those long hours.

---

### Post by Radly on 2010-05-07
You mean I should retire a computer that's only 7 1/2 years old? :lolflag:

---

### Post by nanohead on 2010-05-07
Sounds suspiciously like a pretty bad disagreement with the some hardware component and a base Ubuntu driver....   I've been through this before for sure.  Its frustrating, as the linux piecemeal method of installing is pretty crude (although you can get it to run on an old sneaker if you are determined!)

I would suggest shutting off as many onboard hardware components as possible in BIOS.  If possible, just leave disk and video, nothing else.  Shut off USB, network, serial, parallel, etc.  Whatever you can.

Also, pull any cards you can too, reduce it down to just muscle and bone.   Then try running the installer.  If it crashes still, it may be your video card or memory.   I guess it could be the CPU, but thats somewhat less likely (unless you are trying to accidentally install a 64 bit, or AMD specific image)

---

### Post by tgalati4 on 2010-05-07
With your large disk, you should set up dual boot.  8.04 on one partition that you know works and lucid/fedora/whatever on a second partition.  Installation will go faster with new RAM.  Be sure to run memtest for several cycles to validate your RAM before you get too invested in new distros.

---

### Post by pieguy on 2010-05-07
> **Radly said:**
> You mean I should retire a computer that's only 7 1/2 years old? :lolflag:

Man, I got a sony viao from 2001.  Running 8.10.  Had problems with wireless on the 9's, not even bothering with 10 because I'm happy with the way its customized by me.

---

### Post by Radly on 2010-05-12
Well, the older I get the less I understand...

Since my last post I reinstalled 8.04 LTS on one of two 160 GB partitions and all has been back to normal.  Then yesterday my memory upgrade arrived: two each 512 MB sticks.  So I shut down my nicely running Ubuntu desktop, popped the 128 MB and 256 MB out and loaded up the new ones.  Nothing worked.  Ubuntu wouldn't boot, none of the installers ran.  The only thing that looked proper was the memory test.  Failing to think of anything better to do, I popped one of the two sticks out, reasoning that just maybe there was some kind of funky thing going on there.  Voila!  8.04 booted nicely.  10.04 and 9.10 still won't install and for the same reasons (10.04 crashes and 9.10 won't recognize my ethernet card), so my original conjecture seems confirmed.  This machine will not go beyond 8.04.  Thanks for all the fish--er, I mean, for all the help.

---

### Post by uRock on 2010-05-12
> **Radly said:**
> I have been running 8.04 LTS for almost as long as it's been available and recently decided it was time to rejuvenate my Linux box.  I installed a new graphics card (GeForce instead of the on-board chipset) and a new disk drive (320 GB instead of the 30 GB it had).  I've ordered 1 GB of RAM to upgrade from 384 MB.  But I'm stuck with the P4 Celeron processor, which "should" be good enough for me at 1.8 GHz.  I downloaded the 10.04 ISO image, checksummed it, burned it onto a CD, and tried to install it.  (Twice, the second of which was at the slowest burn speed I had, 1x).  The installer crashes almost immediately.  I tried the "check disk" option to make sure the CD was okay, and THAT crashed.  So I installed 8.04 (that went just fine) and tried the online upgrade to 10.04.  That, too, went just fine until I tried to boot into my spiffy new OS.  That crashed, too.  So I got a tad frustrated, downloaded Fedora 12, and THAT installer crashed.  All the evidence says I'd better get comfortable with 8.04, but that's kinda sucky.

Does anyone have a good idea what's going on and what I can do about it to get more up to date?
I'd recommend trying 9.10. It works great with nVidia and it is very stable and decent to look at.

---

### Post by PhilGil on 2010-05-12
Another alternative might be to try Debian Squeeze.  It should be fairly stable at this point as it's nearing release freeze.  You get the benefits of application upgrades, but Debian is more conservative than Ubuntu when incorporating new packages into their releases.

I have a 4-year-old computer that refuses to play nice with Lucid (X freezes, glacially-slow file reads and writes).  Karmic was usable but a bit temperamental.  I installed Squeeze a few days ago and (so far) it seems to be running great.

---

### Post by uRock on 2010-05-12
After my fight with Debian last night, I'll never go that route again. Spent six hours trying to get it to work. Even with the help of the guys on the Debian IRC it just wouldn't work for me.

I did find that Lucid works much better on my system after formatting the /home and starting it anew. I think a lot of the old settings were messing things up. Ask me again in a few days.

---

### Post by Radly on 2010-05-14
Well, my search is over, and I have resigned myself to being stuck on 8.04 until some new hardware comes my way.  I tried Fedora, Debian, and later versions of Ubuntu, all to no avail.  But with a new graphics card and decent amounts of memory and storage, this should last me a while.

What annoys me with the various distro providers is an ISO image with *i386* in the name and *i686* in the actual installed code.  I think my P4 Celeron predates i686.

---

### Post by uRock on 2010-05-14
There is a P4 in my daughter's old Dell and it is super fast with Ubuntu Karmic on it.

---

### Post by cascade9 on 2010-05-14
> **Radly said:**
> Well, the older I get the less I understand...
 
 Since my last post I reinstalled 8.04 LTS on one of two 160 GB partitions and all has been back to normal. Then yesterday my memory upgrade arrived: two each 512 MB sticks. So I shut down my nicely running Ubuntu desktop, popped the 128 MB and 256 MB out and loaded up the new ones. Nothing worked. Ubuntu wouldn't boot, none of the installers ran. The only thing that looked proper was the memory test. Failing to think of anything better to do, I popped one of the two sticks out, reasoning that just maybe there was some kind of funky thing going on there. Voila! 8.04 booted nicely. 10.04 and 9.10 still won't install and for the same reasons (10.04 crashes and 9.10 won't recognize my ethernet card), so my original conjecture seems confirmed. This machine will not go beyond 8.04. Thanks for all the fish--er, I mean, for all the help.
 
 That sounds like aging hardware...it ran with 128MB + 256MB sticks, but it doesnt like 2 x 512MB sticks. 
 
Could be the old single/double sided issue, but I'm not sure of that. As far as I know, I havent had that issue on the p4/celerons systems I've played with.

You could always get a cheap network card (hey go for about 5$ 2nd hand here) and run 9.10. 

> **uRock said:**
> After my fight with Debian last night, I'll never go that route again. Spent six hours trying to get it to work. Even with the help of the guys on the Debian IRC it just wouldn't work for me.

From what I saw you post on a different thread, that could be because you've started doing things from the debain wiki, then when its gone wrong you've tired IRC. Sometimes if you start doing things one way, then change course, it can stuff things up. Or it could just be that you have an nvidia card that doesnt have the a current nvidia-kernal, etc (which I hit with a GF4-MX440 a few days ago). 

> **Radly said:**
> Well, my search is over, and I have resigned myself to being stuck on 8.04 until some new hardware comes my way.  I tried Fedora, Debian, and later versions of Ubuntu, all to no avail.  But with a new graphics card and decent amounts of memory and storage, this should last me a while.

What annoys me with the various distro providers is an ISO image with *i386* in the name and *i686* in the actual installed code.  I think my P4 Celeron predates i686.

i386 is the base, but if you have newer hardware it installs newer code. Dont worry, your celeron is i686. The 1st i686 CPU was the pentium pro, the celeron p4s are much later CPUs than that.

---

### Post by uRock on 2010-05-14
> **cascade9 said:**
> From what I saw you post on a different thread, that could be because you've started doing things from the debain wiki, then when its gone wrong you've tired IRC. Sometimes if you start doing things one way, then change course, it can stuff things up. Or it could just be that you have an nvidia card that doesnt have the a current nvidia-kernal, etc (which I hit with a GF4-MX440 a few days ago). 
Mine is an old 6150. Yeah, Their wiki is way out dated. If they were to incorporate ubuntu's Hardware Drivers app, I would try again, but I am happy with Lucid. They seem to have worked out the bugs that were bothering me before.

---

### Post by cascade9 on 2010-05-14
> **uRock said:**
> Mine is an old 6150. Yeah, Their wiki is way out dated. If they were to incorporate ubuntu's Hardware Drivers app, I would try again, but I am happy with Lucid. They seem to have worked out the bugs that were bothering me before.

AFAIK, jockey-gtk uses the restricted-modules package- and there is no version of that for debian. I could well be wrong....

If it makes you feel any better, I had absolute tons of fun when I last tried to get the nvidia drivers installed on squeeze- IIRC it was because the kernel I was using had no nvidia-kernel-common. Took me a while to realise that I wasnt going to get it working without doing something not in the wiki (in the end, I got it going). 

I'm not sure about how current the nvidia drivers debain wiki is, to be honest. Apart from that one time with squeeze, its worked for me. The only issues I really seem to get is that the nvidia-kernel-common or nvidia-kernel-source wont work with some cards (like my old GF4 MX and GF4 Ti). 

BTW, if not that this matter that much, but I've found the nvidia install porcess is easier on sidux than with debian. Not that it helps with outdated cards with no nvidia-kernel-common or nvidia-kernel-source. 

[http://manual.sidux.com/en/hw-dev-hw-dri-en.htm](http://manual.sidux.com/en/hw-dev-hw-dri-en.htm)

One of these days, I should try the sidux method with debian. Just for fun. :)

---

