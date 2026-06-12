---
title: "Plymouth problem with NVIDIA driver"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-04-18
Okay so I was testing Ubuntu 10.04 and I updated my drivers and it told me to reboot, so I did. When I rebooted I got a black screen with a white underscore and I rebooted some more and sometimes I got a messed up screen with stripes and stuff like that. Sometimes I rebooted and I got that screen but it booted okay. So I tried to burn the 9.10 CD's and they didn't work so I installed Kubuntu 9.10 and upgraded it to 10.04 and I updated my drivers and the problem happened again!!

So then I burned a cd from my sister's laptop and it worked on my computer. I installed Ubuntu 9.10 then I updated my drivers first and upgraded, but the problem happened again!! Help!!

If anyone has the answer to my problem, it would really make my day. :(

And how can I report this problem to developers?

I'm just going to stop testing Lucid Lynx and upgrade when it officially comes out or when I get my CD's in the mail, just to be safe if the problem persists again. I'm still going to be testing other versions.

---

### Post by gastly on 2010-04-18
I believe it's a plymouth problem, you're upgrading your drivers to the proprietary ones (I'm assuming nVidia) and since they don't support kernel modesettings therefore this is happening.

I myself am fed up of having problems with plymouth, it....simple put....sucks.

Btw, if you don't use the proprietary drivers and just use the drivers provided by Ubuntu, then this problem won't occur. Though, I think 3D effects and such won't work with those drivers.

---

### Post by SpinningAround on 2010-04-18
Also experienced problems with the beta release, installed it yesterday and so far have it crashed 3 times. In all cases have the screen gone blank (no windows) in two of those did I end up with stripes going vertical over the screen. Is there a known problem regarding to ATI graphic cards in this release?

EDIT: There is one other wired thing, if I don't move the mouse during boot up will the screen go inactive as if the computer was turn off.

---

### Post by TheNerdAL on 2010-04-18
Is there an answer to this? Because I burned like 3 CD's and they don't work.

---

### Post by uRock on 2010-04-18
You tested and found a major bug, so now you are going to quit testing?

I thought that was the point of testing, to find problems, so that those problems aren't there on release date.

Regards,
Ronnie

---

### Post by Uncle Spellbinder on 2010-04-18
@ TheNerdAL

As has been stated, it sounds like a Plymouth issue. You still haven't stated your drivers. nVidia, ATI, Intel??

In any event, I hope this issue is fixed before release. Too many people are suffering this Plymouth problem.

---

### Post by TheNerdAL on 2010-04-18
> **uRock said:**
> You tested and found a major bug, so now you are going to quit testing?

I thought that was the point of testing, to find problems, so that those problems aren't there on release date.

Regards,
Ronnie

I'm just done testing Lucid Lynx. I will be testing Ubuntu 10.10 and other versions. It's just that this bug has been getting me mad. D:<

---

### Post by Uncle Spellbinder on 2010-04-18
> **TheNerdAL said:**
> I'm just done testing Lucid Lynx. I will be testing Ubuntu 10.10 and other versions. It's just that this bug has been getting me mad. D:<

All the more reason to *continue* testing. That's the whole point.

---

### Post by TheNerdAL on 2010-04-18
> **Uncle Spellbinder said:**
> @ TheNerdAL

As has been stated, it sounds like a Plymouth issue. You still haven't stated your drivers. nVidia, ATI, Intel??

In any event, I hope this issue is fixed before release. Too many people are suffering this Plymouth problem.

Nvidia, I installed the recommended drivers.

---

### Post by TheNerdAL on 2010-04-18
> **Uncle Spellbinder said:**
> All the more reason to *continue* testing. That's the whole point.

True, but if I do contine testing, I might get the same problem and have to reinstall Lucid Lynx.

---

### Post by Uncle Spellbinder on 2010-04-18
> **TheNerdAL said:**
> True, but if I do contine testing, I might get the same problem and have to reinstall Lucid Lynx.
I've re-installed at least a half a dozen times since Alpha 2. It's the nature of testing. And no big deal, really. From the time I insert the CD to a fully functional system is 20 minutes or less.

---

### Post by TheNerdAL on 2010-04-18
> **Uncle Spellbinder said:**
> I've re-installed at least a half a dozen times since Alpha 2. It's the nature of testing. And no big deal, really. From the time I insert the CD to a fully functional system is 20 minutes or less.

Yeah, well. My Burned CD's don't work and you don't wanna know how many reboots it takes me just to get to get to the logo and then it freezes. I think because my optical drive is bad, but that's another problem, it's on another thread.

I think I might have to get a new optical drive. 

How do I report this problem anyways?

---

### Post by cariboo on 2010-04-18
I would suggest checking out [this]("http://ubuntuforums.org/showthread.php?t=1416872&highlight=plymouth") thread, You'll probably find a solution for your problem. 

One of the prerequisites of running a testing version is that you should be able to solve most basic problems yourself, then if you run into something you can't fix yourself, do a search of this sub-forum, as several people have run into the same thing you have and have offered solutions. Also you should have a launchpad account, and search there before creating a new thread.

---

### Post by TheNerdAL on 2010-04-18
Eh, I'm having bad luck with my optical drive reading my burned cd's. I'm just going to try testing Lucid Lynx the week before it comes out, which is April 22.

---

### Post by flipper9 on 2010-04-18
This might be a dumb question, but...

Why is there no GUI safe mode for Ubuntu?  I don't mean running a Live CD, or command line, or whatever.  I mean a GUI mode that will work on ALL HARDWARE, will ALWAYS work, and will help the user to reconfigure their graphical and other hardware?  

There should be no reason that a newbie user shouldn't be able to at least boot into their system to fix problems, in a graphical and easy-to-do way.  The system should never dump a user to an xterm or require them to edit files or do complex commands just to get their system up and running in a basic, graphical state.  Otherwise, Ubuntu will never be user friendly.

---

### Post by flipper9 on 2010-04-18
> **cariboo907 said:**
> I would suggest checking out [this]("http://ubuntuforums.org/showthread.php?t=1416872&highlight=plymouth") thread, You'll probably find a solution for your problem. 

One of the prerequisites of running a testing version is that you should be able to solve most basic problems yourself, then if you run into something you can't fix yourself, do a search of this sub-forum, as several people have run into the same thing you have and have offered solutions. Also you should have a launchpad account, and search there before creating a new thread.

Well I'll have to disagree to a point with this.  Many people are brave enough to test out the system BEFORE it gets released.  We shouldn't just say "well it's a test version, suck it up".  Very soon this test release will be out in the wild as a release, and then we will start finding out problems. Better to get them fixed now with the brave testers before we release it to the world.  Othewise, you'll be having Linux newbies ranting and raving that Lucid is a piece of *$&#@$, buggy, etc.

---

### Post by uRock on 2010-04-18
> **flipper9 said:**
> Well I'll have to disagree to a point with this.  Many people are brave enough to test out the system BEFORE it gets released.  We shouldn't just say "well it's a test version, suck it up".  Very soon this test release will be out in the wild as a release, and then we will start finding out problems. Better to get them fixed now with the brave testers before we release it to the world.  Othewise, you'll be having Linux newbies ranting and raving that Lucid is a piece of *$&#@$, buggy, etc.

He is not saying suck it up. He is saying that when one is testing, he/she should exhaust the proper channels before creating threads. Mostly because this topic has already been covered.

---

### Post by TheNerdAL on 2010-04-18
> **uRock said:**
> He is not saying suck it up. He is saying that when one is testing, he/she should exhaust the proper channels before creating threads. Mostly because this topic has already been covered.

Lol, yeah. I  should've just partitioned it with a stable version just in case something goes wrong. :P

---

### Post by sparker256 on 2010-04-18
> **TheNerdAL said:**
> Eh, I'm having bad luck with my optical drive reading my burned cd's. I'm just going to try testing Lucid Lynx the week before it comes out, which is April 22.

I do my ISO testing with a USB thumb drive. Is that a possibility in your case? It would allow you to test even if your optical drive may be bad.

Bill

---

### Post by TheNerdAL on 2010-04-18
> **sparker256 said:**
> I do my ISO testing with a USB thumb drive. Is that a possibility in your case? It would allow you to test even if your optical drive may be bad.

Bill

I was thinking that too. I might do that. But I'm saving money for more ram.

---

### Post by utnubuuser on 2010-04-18
if you can use the 9.10 CD or your sister's, use that, and in your update-menu, before clicking "insall-updates" uncheck plymouth and any other nvidea related upgrade.

---

### Post by cariboo on 2010-04-18
I think you're still missing the point, the link in my post, linked to a large plymouth thread, where people had the same problem with a blank screen as you do, and there are solutions to the problem in that thread. In other words, by going through the thread, you could fix your problem and continue using Lucid without having to reinstall. Although it is a good idea to have a partition with an older version available, just in case you run into problems.

---

### Post by paxmark1 on 2010-04-19
First off, it probably would not hurt to also send plymouth bugs to 

[https://bugs.freedesktop.org/](https://bugs.freedesktop.org/)      they appear to be a bit more upstream.  They have only 9 open bugs listed for all of plymouth.  

Kudos to the original poster.

He is not missing the point.  I tried doing alpha and beta testing on Kubuntu when it was going from 3 to 4.  continuously kept seeing the same errors pop back up and the ever expanding requirements when kde 3.5.9 was really great for me.  I went to gnome, and ubuntu.  I did not look back.

Looking at Kubuntu forums, I can see that I was not the only one.  

Seeing all of the 70 plus pages of plymouth woes and the same problems popping up again and again: 10.04 ain't looking much like a LTS to me. 

Go onto the freedesktop.org web page and jump to downloads and look at the NEWS.bz on 0.10 versus 0.80 or 0.82.  There really are not that many developers working on this.  I would also suspect that many of them are more involved with Fedora and Red Hat (nothing wrong with that).  It is also very apparent that they are a very extremely competent and tight team.  They are doing very fantastic work.  6 months to a year down the road and I suspect they will have one fantastic cohesive structured piece of code that just works.

This is not like the Debian fork of cdrecord to wodim, which had not that many developers.  It shares that it is very (probably a better term) much more into machine language like the wodim fork.  It shares with the Halectomty that it is a strong effort to purge old and dated cruft for a faster, more orderly boot and operation.  

But that is not a whole lot of people developing  AND fielding bug reports for a brand spanking new splash.  And it has no business going into a LTS.   (BTW when was the last Kubuntu lts - it sure was not 8.04)

Squueze looks a whole lot more stable than 10.04 will be.  


But who needs Plymouth when there is openbox.   I think I will just swim a little further upstream and either put Crunchbang on my main computer (it is the bomb for netbooks) or Arch Linux.  No rush, 9.10 will remain supported and works well.  

Debian can wait a little bit long until it is "ready", but throwing this plymouth thing down peoples throats is not about choice, and linux is about choice.  


I fell in love with 4.10 and it has been a great ride.  I wish you well.  

peace,   mark

---

### Post by kansasnoob on 2010-04-19
> **flipper9 said:**
> This might be a dumb question, but...

Why is there no GUI safe mode for Ubuntu?  I don't mean running a Live CD, or command line, or whatever.  I mean a GUI mode that will work on ALL HARDWARE, will ALWAYS work, and will help the user to reconfigure their graphical and other hardware?  

There should be no reason that a newbie user shouldn't be able to at least boot into their system to fix problems, in a graphical and easy-to-do way.  The system should never dump a user to an xterm or require them to edit files or do complex commands just to get their system up and running in a basic, graphical state.  Otherwise, Ubuntu will never be user friendly.

If you boot into Recovery Mode there is now a "failsafeX" option :)

---

### Post by TheNerdAL on 2010-04-22
So I think today is when the Release Candidate is out and I was wondering if they resolved the Plymouth problem.

Go here if you don't know what I mean: [http://ubuntuforums.org/showthread.php?t=1457365](http://ubuntuforums.org/showthread.php?t=1457365)

---

### Post by 23meg on 2010-04-22
What has that thread got to do with Python? It would help us understand the problem better if you linked to a specific bug in the bug tracker.

---

### Post by TheNerdAL on 2010-04-22
> **23meg said:**
> What has that thread got to do with Python? It would help us understand the problem better if you linked to a specific bug in the bug tracker.

I mean Plymouth. :P

---

### Post by 23meg on 2010-04-22
> **TheNerdAL said:**
> I mean Plymouth. :P

OK, threads merged, and I've edited the title to reflect the content. Next time, please post to the thread you previously started rather than starting a new one.

---

### Post by TheNerdAL on 2010-04-23
*bump*

---

### Post by TheNerdAL on 2010-04-24
> **23meg said:**
> OK, threads merged, and I've edited the title to reflect the content. Next time, please post to the thread you previously started rather than starting a new one.

This isn't getting people to post replies do to is saying the thread is solved. :|

---

### Post by 23meg on 2010-04-24
> **TheNerdAL said:**
> This isn't getting people to post replies do to is saying the thread is solved. :|

You can mark threads as unsolved (check "Thread Tools" at the top). I've unmarked it for you.

---

### Post by TheNerdAL on 2010-04-24
> **23meg said:**
> You can mark threads as unsolved (check "Thread Tools" at the top). I've unmarked it for you.

Thanks.

---

### Post by TheNerdAL on 2010-04-25
*bump*

---

### Post by 4Orbs on 2010-04-25
This is only a suggestion, but it has worked for me with every release of Ubuntu and Xubuntu during the past three years... including Lucid. If you have the installation cd that you know works:
1. Install it again being sure to reformat the / partition, and reformat /home if there are no important settings or files you need to keep.
2. When you boot into the fresh installation, DON'T change the screen resolution from default, even if it's difficult to read.
3. Run the update manager and allow it to complete it's work. Reboot after updates if told to do so.
4. Activate your nVidia driver and reboot. Chances are good that the default resolution may have adjusted itself automatically to your desired resolution.
5. If, by some miracle, the resolution makes you happy and the boot screens show up correctly... be aware that changing the resolution now will probably screw things up again.. even if you use the proper method to change it (gksudo nvidia-settings then save the new settings to /etc/X11/xorg.conf by clicking the save button on nvidia settings mgr.)
6. If this doesn't work for you, then my apologies. Good luck.

---

### Post by RickyCodes on 2010-04-25
did you uninstall the old drivers first?? You should be able to rebuild xorg, reboot and should work

---

### Post by TheNerdAL on 2010-04-25
I'm just asking if the problem is resolved in Release Candidate.

---

### Post by TheNerdAL on 2010-04-28
Is the problem solved already in Ubuntu 10.04 Stable Release?

---

