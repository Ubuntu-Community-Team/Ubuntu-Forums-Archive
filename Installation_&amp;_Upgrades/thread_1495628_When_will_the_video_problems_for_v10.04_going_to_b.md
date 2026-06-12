---
title: "When will the video problems for v10.04 going to be fixed?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by nowikn on 2010-05-28
I love my Ubuntu but this video issue for v10.04 needs to be fixed . . . soon.  It's very frustrating for the many users such as myself that are sold on this OS but when we upgrade to v10.04 it bombs because of a well publicized video issue.

I guess our only recourse is to stick with v9.10 . . . because it 'just works' . . .

:frown:

---

### Post by darkod on 2010-05-28
> **nowikn said:**
> I love my Ubuntu but this video issue for v10.04 needs to be fixed . . . soon.  It's very frustrating for the many users such as myself that are sold on this OS but when we upgrade to v10.04 it bombs because of a well publicized video issue.

I guess our only recourse is to stick with v9.10 . . . because it 'just works' . . .

:frown:

Will you make hardware manufacturers work faster to provide drivers also for linux not just for windows? The linux developers are left with designing drivers most of the time, and you still complain.

Not to mention that there are lots of guides already depending what your cad model is. Some of the things will not work "out of the box" as much as the developers try, and if you are not ready to "fix" them, I don't know what to say.

You didn't even specify your card model, I don't know if you are asking for help or just complaining...

---

### Post by nowikn on 2010-05-28
Will you make hardware manufacturers work faster to provide drivers also  for linux not just for windows? The linux developers are left with  designing drivers most of the time, and you still complain.

============

Are you saying that the vid drivers that the Linux developers built for my laptop that worked great with v8 and v9 somehow changed on v10?  If so, please explain to me how this got by the testers?

My point is this - yes, I am complaining - it's simple issues such as this that is preventing this great OS from going mainstream.  For those of you that think of this as a personal attack and say "hey, go out on the support site and sort through the 1000's of posts - you'll find your answer there . . . " just know that it's you that are holding us back.  Simply share your knowledge with us people who just aren't as smart as you are! :)

---

### Post by darkod on 2010-05-28
I'm not a developer myself, and I can't say with 100% certainty how the process goes, but I know this for sure: it's not as straight forward as it looks to the rest of us.
Just because something worked on previous version doesn't make it work on the next one. In fact, if the versions are so identical, there wouldn't be a new one released at all.

As for helping and sharing, I didn't see anyone refusing to help you here. But you have to provide information.

For example, to make sure it's video driver issue, did you try running the 10.04 cd in live mode with selecting Safe Graphics? Or by adding the nomodeset parameter?

Lots of people have reported nomodeset allowed them to boot the first time after install, and then install a driver. After that, it worked fine. Not sure if all of those issues were video related, but some were.

---

### Post by nowikn on 2010-05-28
No, I have not used the LiveCD yet - will do it this weekend and will report my results as well as the (2) laptops that I have the video / install issue with.

---

### Post by darkod on 2010-05-28
I installed my 10.04 another way, but from what I read on the forum, when the cd boots you get a purple splash screen. If you hit any key while it is still shown, you will get the main menu similar to 9.10, with Try Ubuntu, Install Ubuntu, etc.

At bottom of the screen, also as in 9.10, you will have option to press F6 for advanced options. Safe Graphics should be there.

Or if F6 just shows the boot command, go to the end with the cursor and delete quiet splash, and add nomodeset.

If that makes it boot properly in live mode, you could install with the Install icon on desktop, but on first boot again you need to press 'e' in the grub boot menu, and again add nomodeset at the end of the line starting with linux.

That should allow first successful boot from the hdd. Once inside, update the recommended video driver and see how it goes.

---

### Post by wkulecz on 2010-05-28
No issues for me using the Nvidia proprietary drivers, but I'm not using any cards newer than GeForce 210.  I had some issues on a couple of systems with the open source drivers that were quickly fixed by installing the restricted driver.

OTOH while shopping for Quad core components to build a new 10.04 system I eliminated MBs with built-in AMD video based on the problems with the beta.  I need top of the line 2D performance which is pretty trival these days, 3D not so much and after a brief period playing with compiz effects on the GeForce 210 I could see no use for any of them and most were just plain annoying to me.  YMMV.

Stability and the "leading edge" just don't go together.  But the bang/buck of the mid range systems is so good and prices so low these days compared to the extreame that its way less hassle to buy a new mid range system every 18 months or so than to fight with the bleading edge for 20% better performance at 2X+ the cost today.

---

### Post by darkod on 2010-05-28
> **wkulecz said:**
> 
OTOH while shopping for Quad core components to build a new 10.04 system I eliminated MBs with built-in AMD video based on the problems with the beta. 

Now that you mentioned built-in AMD. I have a mobo with Radeon HD3200 (which is now AMD I guess, since ATI got purchased).

True, Karmic was not able to run live mode (it was restarting the PC just when it should show the live desktop loaded). Also after install, it didn't want to load, it was doing the same, restarting before showing the login screen.

However, even though Karmic was my first touch with Ubuntu, I didn't mind learning new things, so I learned how to log in with the recovery mode entry, with command prompt how to add the EnvyNG package which helped me install ATI driver, and Karmic worked great ever since.

Also, I can report that this 'problem' was solved with Lucid. Lucid was able to load live mode, without any specific steps, just 'out of the box'. Also, after install it was loading and working fine without needing to add driver, or EnvyNG, or what ever...

So, for my chipset at least, there was progress.

---

### Post by nowikn on 2010-06-07
I did all the things suggested in this thread to fix the issue with no luck:

* Or if F6 just shows the boot command, go to the end with the cursor and  delete quiet splash, and add nomodeset.

-> Did that and during the 'load' I was able to see a lot of system messages then the screen blanked again and the system 'hung'

================

I am attempting the install on the following laptop: IBM ThinkPad R50e

---

### Post by nowikn on 2010-06-07
[CENTER][SIZE=5][U][B][COLOR=SeaGreen]RESOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR]
[/B][/U][/SIZE][/CENTER]

Here's what I did to finally resolve this issue:

* Or if F6 just shows the boot command, go to the end with the cursor  and  delete quiet splash, and add nomodeset.

[COLOR=Red]**-> (my solution) removed quiet splash and add, without quotes: nomodeset xforcevesa**[/COLOR]

After the edit was applied, I booted to the "LiveCD" (aka "Try Ubuntu without any changes) and about fell out of my chair when I heard the familiar Ubuntu music upon boot!

I am in the process of installing the full version onto my local hard drive but don't expect any issues

---

