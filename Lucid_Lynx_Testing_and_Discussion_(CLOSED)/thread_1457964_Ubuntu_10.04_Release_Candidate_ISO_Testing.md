---
title: "Ubuntu 10.04 Release Candidate ISO Testing"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-04-19
We are in [Final Freeze]("https://wiki.ubuntu.com/FinalFreeze"), and the [Release Candidate]("https://wiki.ubuntu.com/ReleaseCandidate") for Ubuntu 10.04 will be out this Thursday. It's thanks to those of you who volunteered to test the previous milestones that we got mostly showstopper-free alphas and betas along the development cycle, and it's now time to repeat that effort for the RC, which will be the last and most widespread milestone release before 10.04 goes final.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

[Final Freeze]("https://wiki.ubuntu.com/FinalFreeze") is now in effect, and candidate images for the RC are available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by ranch hand on 2010-04-19
Grabbing that bugger right now.

---

### Post by kansasnoob on 2010-04-19
I'd really like to get some confirmation on this bug if possible:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373)

I fear that could be a real show stopper if it's not fixed by final.

Edit: Colin Watson's on this now, changed to Fix Committed so I'm happy dancing.

---

### Post by ranch hand on 2010-04-19
How in flinderation do you get a menu on the LiveCD.  I see no option for this or instructions on this.

Must be handy for folks that are going to need options.

I was going to test the OEM install.

The thing has bugged me from the start of this new style, which is much slower to come up, but I have  never needed to change anything.  The default stuff that come s up was fine.

This is a pain.

---

### Post by kansasnoob on 2010-04-19
> **ranch hand said:**
> How in flinderation do you get a menu on the LiveCD.  I see no option for this or instructions on this.

Must be handy for folks that are going to need options.

I was going to test the OEM install.

The thing has bugged me from the start of this new style, which is much slower to come up, but I have  never needed to change anything.  The default stuff that come s up was fine.

This is a pain.

When you see the initial screen with two emblems (a human and a keyboard) you must press "any key" (I always hit either enter or the space bar), then you can select language and then you get the typical boot options screen.

NOTE: It passes quickly! You have maybe two or three seconds to press a key!

I always use it to check disc for errors and then to add persistent to the boot so I can test persistence of the Live CD. Then getting rid of the "casper-rw" partition is kind of a rascal!

---

### Post by ranch hand on 2010-04-19
Well I actually tried that and got no response at all the first time I was on here.  This is my 3rd try and I read somewhere that if you hit Esc at the logo you got something.

I did.  I got an error message saying that it couldn't open sdc.   I think sdc is one of my card readers.  Big surprise it couldn't open the sucker.

This is no way to enter into the CD.  Might as well be some MS product.  "Oh its easy, just do this or that".  Could put some kind of indication on the screen so users would know this.

This is as bad as folks that get on here and say "Oh help me my computer won't run" .  OK give us a clue.  This will not do.

EDIT
Thanks for the clue, I will try it again.

---

### Post by ranch hand on 2010-04-19
That worked.

Haven't booted to the OEM yet.  Thought I would chroot in and arrange things a little to see if I like the results.

I have some old boxes that I thought I would set up and use this install method to make folks more comfortable but have everything set up to run the way the install slide show says it does (ready to play music and video oh yes).

---

### Post by djchandler on 2010-04-20
> **kansasnoob said:**
> I'd really like to get some confirmation on this bug if possible:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373)

I fear that could be a real show stopper if it's not fixed by final.

And I got the same messages on the beta 2 trying manual partitioning and trying the "use largest free space on disk" option. Very disconcerting. But of course if you disregard and go ahead, it will still install, apart from my laptop overheating once and shutting down before finished with the install. I had to put a desk fan on the laptop so it would finish. But I was expecting that part still. There's an upstream bug in the xorg ATI driver causing heat issues.

One thing I would like to know though. Why is a separate account apart from my launchpad and OpenID login needed for ubuntu brainstorm? Just curious, not criticizing.

I'm going to try to get the i386 DVD overnight.

---

### Post by kansasnoob on 2010-04-20
> One thing I would like to know though. Why is a separate account apart from my launchpad and OpenID login needed for ubuntu brainstorm? Just curious, not criticizing.

So old fogies like me have to keep a password cheat-sheet :lolflag:

---

### Post by ranch hand on 2010-04-20
Is there any indication as to the status of the ISO?  Did it pass or do we have another coming?

---

### Post by ToxicBurn on 2010-04-20
this i would like to know also i want to download the iso and test myself but dont want to have to re-download later tonight ?

---

### Post by kansasnoob on 2010-04-20
> **ranch hand said:**
> Is there any indication as to the status of the ISO?  Did it pass or do we have another coming?

Your guess is as good as mine.

---

### Post by kansasnoob on 2010-04-20
> **ToxicBurn said:**
> this i would like to know also i want to download the iso and test myself but dont want to have to re-download later tonight ?

No guarantees! I remember once having four builds in one day :guitar:

My best guess, based on the bug reports I've seen, is there may be one more build prior to the RC.

But your guess is as good as mine.

---

### Post by ranch hand on 2010-04-20
I was just looking at the results.  The i386 desktop does not look to good there.

I am betting on another on of those anyway.  Two critical bugs.

---

### Post by kansasnoob on 2010-04-20
> **ranch hand said:**
> I was just looking at the results.  The i386 desktop does not look to good there.

I am betting on another on of those anyway.  Two critical bugs.

Then again I remember a release being held back 24 hours and seeing no change :rolleyes:

---

### Post by ranch hand on 2010-04-20
Yup, and one of those bugs goes back to 9.10.

---

### Post by jerrylamos on 2010-04-21
> **ToxicBurn said:**
> this i would like to know also i want to download the iso and test myself but dont want to have to re-download later tonight ?
Not that we can "drive by looking in the rear view mirror" but many times close to release the change rate is very slow.  When CD live stops changing, I take an .iso and try an install.  If there's a late change "most of the time" I can just do sudo aptitude update && sudo aptitude safe-upgrade to pick it up.

Updating frequently for me does not get the same Ubuntu as a late install since there seem to be gdm and boot changes that do not get picked up with update.

Having said that, note this is April 21 and the daily build is still dated April 19.  No changes in the last couple days.

There have been ongoing bugs example intel video graphics driver is broken for i830 and i845 so there are workarounds see launchpad bug #541492 and some other long lasting problems see the Linux forum so I don't expect magic fixes....

Now I do multi-boot so I still have a running Ubuntu while I install another one on another partition.  Mostly 10G partition is fine, even 5G on my old 1 gHz laptop which is still comfortably responsive on Ubuntu Lucid but was real slug on XP.

Jerry

---

### Post by djchandler on 2010-04-21
I finally got a download yesterday only to find that it seems I cannot log-in to report. I'm not sure why as I have launchpad and brainstorm accounts.

At least the problem I encountered was reported by someone else. I did a manual partitioning and got the "no partitions defined" message still. Not a real problem as Ubiquity installed correctly anyway.

---

### Post by RickyCodes on 2010-04-21
just installed 

[[IMG]http://iso.qa.ubuntu.com/modules/qatracker/images/icon/info.png[/IMG]]("http://iso.qa.ubuntu.com/qatracker/info/3985") [Ubuntu Alternate  amd64 (20100419.1)]("http://iso.qa.ubuntu.com/qatracker/test/3985")                     7/9                      0 bugs reported so far. 

Smooth install on a Acer AMD 3800+ 3gb memory.

manual partition dual boot over an old beta 1 install.l

---

### Post by ranch hand on 2010-04-22
That is the same install I did with the Live CD.  When very slick on this box.

---

### Post by mk04 on 2010-04-22
Where can i download the .iso for Ubuntu 10.04 RC?

---

### Post by ranch hand on 2010-04-22
There will be an announcement, when it is released, in the stickies.  don't get your knickers in a knot just yet.

It seems that it is usually later in the day so this is way early.  If you are up to date with the updates you are already using the RC.

My great grand father was on the first boat of settlers to Holland, nice area.

---

### Post by The Seeker on 2010-04-22
[Ubuntu 10.04 LTS (Lucid Lynx) Release Candidate](http://releases.ubuntu.com/releases/10.04/)

---

### Post by 23meg on 2010-04-22
[RC is now out]("http://ubuntuforums.org/showthread.php?t=1460131"). Thanks to everyone who contributed to ISO testing.

---

