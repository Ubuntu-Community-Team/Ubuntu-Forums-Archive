---
title: "WHY is this still a problem????"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by isecore on 2008-10-24
Yeah, I know. I'm posting this in the general section even though I'm running Intrepid. It's less than a week left until Intrepid officially gets released, so I doubt much will change until then.

The story is this:

I have a quad-core with 4 gigs of RAM. When I ran Hardy any intense disk-activity (such as unpacking a DVD-R or Tracker indexing a fresh drive) would lock my desktop. The CPU usage would go through the roof and multi-tasking would become a distant memory. Edgy, Feisty and Gutsy all ran like a champ on much lesser hardware.

I have posted about this previously, with more detailed reports. I refer to that thread, which received bupkus responses: [http://ubuntuforums.org/showthread.php?t=873650](http://ubuntuforums.org/showthread.php?t=873650)

So, fast forward to earlier today. I just couldn't take it any more and upgraded to Intrepid. I hoped that this issue had been resolved, since I wasn't alone in experiencing this and no one had any seemingly reasonable theory to why it happened.

BUT NO! System still crawls to a effing halt as soon as any serious disk-activity happens.

THIS IS DRIVING ME NUTS! 

Why is this happening? I'm losing faith in Linux since as far as I can tell not a single person can answer why this is and how to solve it.

---

### Post by cariboo on 2008-10-24
I would suggest try a clean intallation there seems to be something strange with your installaion, especially if the problem carried over from a previous version. Also have you tried any other Linux distributions to see if the problem still exists?

Jim

---

### Post by estyles on 2008-10-24
I had a similar problem that was eventually cleared up by reinstalling fglrx.  Regardless of whether or not that's your problem...  is it any faster if you use metacity instead of compiz?
```
metacity --replace
```

Because that *temporarily* solved my problem until I figured out the problem and reinstalled my video drivers.

---

### Post by volanin on 2008-10-24
I read many reports that it's because of the IO Scheduler.
By default Ubuntu uses the CFQ scheduler, which is optimized for multi-user environments.

Try to add this to your kernel boot parameters:
elevator=deadline

Or even:
elevator=as

And check if you get a better desktop response!
:)

---

### Post by isecore on 2008-10-24
> **cariboo907 said:**
> I would suggest try a clean intallation there seems to be something strange with your installaion, especially if the problem carried over from a previous version. Also have you tried any other Linux distributions to see if the problem still exists?

Jim

I'm not going to reinstall. Simply because that isn't the problem. I reinstalled Hardy twice without the problem going away. Reinstalling because of this is the Windows style of problem solving.

Neither am I going to start experimenting with other distros. I want to run Ubuntu, if Ubuntu and it's community cannot find a solution for this problem... well, then I guess Linux is a dead end.

As for the other suggestions... reinstalling fglrx is not going to help me as I don't have an ATI graphics card.

Setting the IO scheduler to deadline rather than CFQ made it so that I at least can use my computer while the disk is being intensely used - however, everything takes two-three times as long now. Coyping a large file now takes 15 minutes rather than five, and the computer still feels sluggish. Also, even when not doing anything the computer feels much more sluggish - windows open slower, windows close slower, etc etc.

This is incredibly frustrating.

EDIT: Changing to the Anticipatory Scheduler (elevator=as) made the system even slower. Logging in takes ages, applications take literally minutes to start. So forth and so on.

EDIT2: Running with or without Compiz Fusion (aka "visual effects") made nada difference. All four cores still go 100% busy whenever disk-intensive applications are running, applications become unresponsive.

---

### Post by FuturePilot on 2008-10-24
This bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094")

---

### Post by cl333r on 2008-10-24
I can understand your frustration, I would still try out Mandriva and see whether it works fine. If it does, tell the ubuntu devs "hey guys, look over there that distro works fine and it's open source - grab it's code!". The last thing I'd try is OpenSolaris, I heard it's more responsive when the system does heavy I/O or has lots of processes running simultaneously (can't remember the scenario).
I mean the developers have tons of bugs to fix and enhancements to develop, if we can point them to the working chunks of code we would ease their life and ours in the long run.
Compared to what you've gone through - checking 2 other distros wouldn't be a lot of hard work I hope.

---

### Post by isecore on 2008-10-24
> **FuturePilot said:**
> This bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094")

Yeah, I've read that lots of times. Found it through googling. Have tried all kinds of suggestions found there. No real difference.

Whatever is causing this is in my opinion EXTREMELY serious. I ran Edgy, Feisty and Gutsy on my previous machine which had much, much humbler specifications (Athlon XP2200+, single core, a gig of RAM, no SATA-drives) and those were like having a jetfighter for an OS. Never ran Hardy on this machine though.

Buy my new machine with vastly superior specs, install Hardy and it runs like molasses on a really cold day.

---

### Post by isecore on 2008-10-24
> **cl333r said:**
> I can understand your frustration, I would still try out Mandriva and see whether it works fine. If it does, tell the ubuntu devs "hey guys, look over there that distro works fine and it's open source - grab it's code!". The last thing I'd try is OpenSolaris, I heard it's more responsive when the system does heavy I/O or has lots of processes running simultaneously (can't remember the scenario).
I mean the developers have tons of bugs to fix and enhancements to develop, if we can point them to the working chunks of code we would ease their life and ours in the long run.
Compared to what you've gone through - checking 2 other distros wouldn't be a lot of hard work I hope.

Like I said before, trying another distro just isn't an option. Sure, maybe some other distro has this problem solved, but then there's all the other problems, such as learning a new distro. I don't want to do that. 

I want to run a Debian-derivative, I want to run Ubuntu, and I want it to not take f***ing ages doing anything with the disk. This is the ONLY thing that annoys me with ubuntu, and it annoys me to no end. I am more than happy with Ubuntu in every other respect, except that it has really crappy disk-IO (for whatever reason) and no one seems to know why, or how to fix it, or even where to look.

(and running OpenSolaris is definitely more pain than gain no matter how one looks at it)

---

### Post by cl333r on 2008-10-24
OpenSolaris has changed a lot to the better this year, the new release will be somewhen this November.
I didn't suggest using them, but cheching if they have this issue. I wouldn't move to them either, cause I'm used to Ubuntu.
I would test myself, but I don't got that hardware.

---

### Post by MaxIBoy on 2008-10-24
Fact is, if one distro doesn't work out, you should just roll with it and get another distro (which isn't as far of a leap as you'd expect.)

Linux Mint is VERY similar to Ubuntu (being based on Ubuntu,) but some problems are fixed in it that aren't in Ubuntu.

---

### Post by isecore on 2008-10-24
> **MaxIBoy said:**
> Fact is, if one distro doesn't work out, you should just roll with it and get another distro (which isn't as far of a leap as you'd expect.)

Linux Mint is VERY similar to Ubuntu (being based on Ubuntu,) but some problems are fixed in it that aren't in Ubuntu.

I know it isn't a huge leap. But like I said, jumping from a distro I feel perfectly at home with just because of one thing isn't really worth it for me. Sure, Linux Mint is probably nice in whatever way it aims to be nice, and maybe it has this problem solved. But maybe it has lots of other issues or inconveniences that annoy me?

I'm not interested in spending my free time jumping from one distro to another. I like Ubuntu, I like how well updated it is, I like how large the community is, I like that it's backed by a solid company, I like using it, I want this problem to be solved in THIS distro, not just say "oh well" and keep moving on. That's not how I work, that's not how I think things should work.

So let me say it again - suggesting I try a new distro just isn't going to work. I might try Mandriva on a secondary harddrive this weekend, but it'll simply be to confirm if it behaves the same way or not.

---

### Post by Asraniel on 2008-10-24
Dumb suggestion perhaps, but can you install the version before hardy on your computer and see if the problem is the same?

Because between your two computers, there could be some hardware changes, that would also have affected Gutsy etc, not only hardy+

---

### Post by heavensblade23 on 2008-10-24
> **Asraniel said:**
> Dumb suggestion perhaps, but can you install the version before hardy on your computer and see if the problem is the same?

Because between your two computers, there could be some hardware changes, that would also have affected Gutsy etc, not only hardy+

I can tell you that it will be the same.  I've had this problem for the last several releases of Ubuntu.  The first release that had this problem was the first one that had CFQ as the default scheduler.  Fedora has the same problem and it also has CFQ as the scheduler.

The only working fix I've found is elevator=deadline which switches to a different scheduler.

Essentially the problem with CFQ is this...when you copy a bunch of files, it sounds out a large number of I/O requests.  If firefox needs to access the disk, even for a split second, that request ends up at the end of a long queue that may take a minute or two to clear.  In some cases this means Firefox will be frozen the entire time.  The deadline scheduler sets a deadline by which all I/O requests must be serviced, so the freezes either don't happen, or only happen 10% of the time they do when you're using CFQ.

Why this is seemingly not a priority to fix is beyond me.  Log into bugzilla and confirm it's happening on Intrepid and that switching to deadline alleviates it.  That's all we can do other than wait until someone decides to make CFQ less crappy.

---

### Post by caryb on 2008-10-24
2 things in response to this post, running to another distro wont fix the *buntu problem. If heavensblade23 is having this problem then maybe Fred the guy doing a appraisal for some tech magazine will have the same problem & he is right it should be fixed. I personally don't have his problem so I cant help but we should be able to see if there is a driver compatibility problem:confused: I give him full marks for trying to get to the bottom of the problem.

2nd > Reinstalling because of this is the Windows style of problem solving. I wholeheartedly agree with this, as in my previous paragraph it does not get to the root cause. If there is a problem in the upgrade process this also should be found & fixed, why should we expect multiple folks to reinstall to fix some deficiency in "our" distro:confused:

Cary

---

### Post by heavensblade23 on 2008-10-24
> **caryb said:**
> 
2nd  I wholeheartedly agree with this, as in my previous paragraph it does not get to the root cause. If there is a problem in the upgrade process this also should be found & fixed, why should we expect multiple folks to reinstall to fix some deficiency in "our" distro:confused:


Things I can reasonably confirm are not the cause:
-Hardware drivers (I've had this problem across several different machines)
-Versions of Ubuntu (I've been having this bug at least since Hardy and I believe before that)
-Different distros (I found a forum thread where people were having the same issue on Fedora)
-Dist-upgrade (I always install fresh)
-Search Indexing (Problem occurs even with indexing completely disabled...if there is an issue, it's a symptom and not a cause)
-Firefox versions (Fsync bug was fixed a long time ago, and people have tried reverting to Firefox 2 without success)
-Filesystem in use (People have reported the problem on ReiserFS as well as ext3)

Reasons I think it's the scheduler:
-It was reported switching schedulers helped this problem on Fedora which also uses CFQ.
-I've tried both deadline and anticipatory schedulers and then copied large numbers of files and the system was 95% more responsive.
-People first started reporting this problem on the Ubuntu forums around the time CFQ was switched to the default scheduler, which I believe was around the Edgy/Feisty timeframe.
-People have reported the problem doesn't exist on the 'server' version of Ubuntu, which uses the deadline scheduler instead of CFQ.

I don't even program, this is just a week's worth of detective work and some personal experience.

---

### Post by b0b138 on 2008-10-24
If you ran gutsy on an older computer with no problems, try it out on your quad core. If this is a new box, you might have some bad hardware.

---

### Post by cicatrix1 on 2008-10-24
Yeah, I really don't think the OP has a very good attitude about this problem.  I understand it's frustrating, but refusing to take basic troubleshooting steps isn't going to help.  If you tried another distro just for a little bit, you could help determine if it happened ALL the time (i.e. in other distros, too) or if it is in fact, a bug limited to Ubuntu.

It's possible you have bad hardware, or some bad driver.  But you wouldn't know, would you?

---

### Post by isecore on 2008-10-24
> **cicatrix1 said:**
> Yeah, I really don't think the OP has a very good attitude about this problem.  I understand it's frustrating, but refusing to take basic troubleshooting steps isn't going to help.  If you tried another distro just for a little bit, you could help determine if it happened ALL the time (i.e. in other distros, too) or if it is in fact, a bug limited to Ubuntu.

It's possible you have bad hardware, or some bad driver.  But you wouldn't know, would you?

Excuse me, but what "basic troubleshooting" has been suggested? The only suggestions that get regurgitated is either "reinstall" (which I'm not going to do since it's A) Stupid B) Stupid C) I've already done it with Hardy) or trying another distro (which I'll probably be doing this weekend)

I think it's an Ubuntu problem. Maybe it's fixed in $SOMEDISTRO and maybe it's not. I doubt it's a hardware thing though, because ironically enough Windows has no issues on this machine (except from, well, being crap in most every way possible but you know what I mean). But sure, I'll take the time this weekend and slap in another drive and install whatever distro on it.

I tried changing the scheduler. It did alleviate the issue to some extent but I felt it did so at the expense of other things.

If you have anything else that you feel I should try, then lay it on me! I bet you dollars to donuts though I've already tried it or know from experience that it won't have any effect. I don't like pulling rank, but just because I've only used Ubuntu for 1½+ years means I'm some kind of newbie. I started on Linux in 1995 and effective time I've used it probably amounts to a decade or so.

If I come across as arrogant or whatever then fine. Maybe I am. But I'm also frustrated beyond description by this issue, and maybe that frustration shines through and colors what I ask here.

---

### Post by nanog on 2008-10-24
> but some problems are fixed in it that aren't in Ubuntu
*blink*

To the OP: How do you expect to have *your* problem fixed if you do not report a bug and submit information to developers? Are they supposed to read your mind?

---

### Post by nanog on 2008-10-24
> Hardware drivers (I've had this problem across several different machines)

I own or administer dozens of ubuntu boxes and do not see this problem.

---

### Post by heavensblade23 on 2008-10-24
> **nanog said:**
> I own or administer dozens of ubuntu boxes and do not see this problem.

Do you regularly copy 100+ gigs worth of files while using the desktop at the same time?  Server variants seem to be unaffected because they use deadline by default.

I've experienced the problem on 4 different machines with different specs and different hardware, 2 laptops and 2 desktops, under that usage scenario.  All of them had both Windows and Ubuntu installed, and the problem did not exhibit itself in Windows.

---

### Post by Ocxic on 2008-10-24
Test your memory, I had the same problem for 8 months with my system randomly locking up and cpu go sky high only to find out that one of my RAM sticks was bad.

---

### Post by isecore on 2008-10-25
> **nanog said:**
> *blink*

To the OP: How do you expect to have *your* problem fixed if you do not report a bug and submit information to developers? Are they supposed to read your mind?

There already is a bugreport on it: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)

---

### Post by isecore on 2008-10-25
> **Ocxic said:**
> Test your memory, I had the same problem for 8 months with my system randomly locking up and cpu go sky high only to find out that one of my RAM sticks was bad.

I've tested my memory. There's nothing wrong with it. Memtest ran for two days straight without a single error. My system doesn't lock up randomly. What happens is that it becomes unresponsive when there's heavy disk-IO.

---

