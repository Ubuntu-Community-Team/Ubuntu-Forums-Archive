---
title: "Why is 7.10 so unstable?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by pyrosama on 2007-12-15
I recently updated to 7.10 from 7.04 and I'm amazed at the massive back step this new version has taken.

I've been running it for about 2 weeks now and needless to say I'm very disappointed.

Issues:
Synaptic Touch Pad [1] randomly looses sync and will freeze my cursor in place or randomly shoot it across the screen and from time to time auto click for me.

Keyboard about every 30 seconds or so when typing a key will not respond or a key which has not even been touched will act as though it is being held down and its random every time no one key suffers from this problem.

Firefox and flash when I'm on a page containing flash every now and then it will screw up the way it handles focus so the flash will be in focus and I can click on it etc but nothing else outside of the flash can be interacted with ie if I go to click on the applications menu on my main panel it will not respond and if I right click it will pop up the standard flash righclick menu then if I right click again it will bring up what should normally be displayed for the righclick and will give focus back to the rest of the os. Also during this period short cuts including ctrl alt backspace do not respond.

Applications act as though I issued a kill. Randomly an applications just kills its self no warning nothing will slow down or act buggy before hand it just disappears from view suddenly and has to be relaunched.

Applications freezing at random times. If I just boot my computer it takes about 3.5 minutes before the thing get to where I can even type in the keyring password field for wifi then another ~ 2 minutes after launching firefox before I can do any thing with it. Then applications randomly freeze without warning or any thing to cause the freeze (reading an article on wikipedia and half way through the article every program will freeze and I will be unable to scroll on the page much less alt tap into any other program this freeze lasts any where from 30 seconds to 2 minutes)

Login password about every third time will tell me I entered the wrong password and its not very easy to mistype 'asdf' esp when it takes about 5 seconds to type in each letter (delay/freeze between leters)

Wifi randomly connects / disconnects

Screen randomly flashes black and then back again

Any config made to my synaptic touchpad is ignored after a reboot and has to be reconfigured

Volume up key on my keyboard must be held to increase the volume other wise a single press turns the volume down


Running the xubuntu release on a compaq presario v5201us laptop upgraded to 2 gig ram and a 64bit turion cpu (running 32 bit os)








[1]
> 
[ 5353.628000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5353.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5353.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5353.632000] psmouse.c: issuing reconnect request
[ 5483.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5483.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5483.624000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5483.624000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5483.624000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 5483.624000] psmouse.c: issuing reconnect request


---

### Post by Sef on 2007-12-15
Sorry that you are having problems with 7.10, Gusty Gibbon Xubuntu.  There is so much hardware out there that is impossible to check all the hardware with all the configurations.  Sometimes, you have to use a different distro.   I have had mouse problems with Xubuntu on my old laptop (700 Mhz, 128 mb ran, Dell), so I have ended up with Mempis on it.   It works fine.   I would prefer to have Xubuntu, and might check out Hardy Heron, 4.08when it comes out.

---

### Post by DizzyTech on 2007-12-15
Here's an answer to your question.  Two words:  **Bad kernel**.

---

### Post by pyrosama on 2007-12-15
> **DizzyTech said:**
> Here's an answer to your question.  Two words:  **Bad kernel**.

What must I do to fix the problem?

---

### Post by tbook on 2007-12-17
If anyone has an answer to this, I would love to hear it!  I am thinking about wiping out my hard drive and starting over, but that would be a big pain.  I wish Ubuntu were more "Dapper" and less "Edgy," "Feisty" or "Gutsy."  In other words, I probably need to switch to a version of linux that "just works," rather than one that tries to incorporate all the latest software.

---

### Post by kdarkentity on 2007-12-17
I have actually experienced similar problems, especially with the wireless internet connectivity issue, in addition to what you've said i have also had problems praying login in window sounds, logoff sounds and also firefox tends to freeze my machine frequently. But 7.10 still is a new release and im sure all of the bugs will be worked out soon.

---

### Post by orzechowskid on 2007-12-26
I'm having many instability issues with Gutsy as well.  Applications will randomly quit, firefox will freeze (and sometimes quit too), I'll get up from my desk and come back ten minutes later and see that my X session has ended and I've been dumped back to the user login screen.

Update-manager says my system is up to date, and I know this has included at least one kernel upgrade, so I'm not sure a crappy kernel version is the (sole) source of the problem.

Any hints on where to look?  Are there configuration files I can edit or values in /proc I can tinker with?

Thanks in advance for any information

---

### Post by atomkarinca on 2007-12-26
To my experience it's the opposite. Feisty never felt as stable as Dapper for me. Now with Gutsy, I feel like I have a brand new Dapper.

@DizzyTech: I'm not so sure it's a kernel issue. Although I'm using Ubuntu Studio now, I never had any stability issues with Ubuntu, either (AFAIK they use different kernels).

@OP: Maybe with a clean installation you can have a better performance out of your machine. Clean install is usually better than an upgrade.

---

### Post by LaRoza on 2007-12-26
I have found the Ubuntu 7.10 version to work perfectly with all of my hardware on my desktop and laptop (including wireless) with no tweaking.

---

### Post by Edho on 2007-12-26
Installed Gutsy on my Desktop 2 weeks ago. (Dapper before)
Seems very good, but slower, to me.

Installed Gutsy on my new Asus notebook, 5 weeks ago.
All main things are working and stable.

---

### Post by kelvin spratt on 2007-12-26
I just started using Xubuntu with E17 and find it really stable Gutsy with E17 or not is now very stable. Most problems being blamed on Ubuntu are not the distro fault, Flash, and Mplayer, have got problems. but can be cured by downloading off there sites.compix uses vast amounts of resources and makes Firefox unstable.and every thing else can become sluggish and unstable, using E17 I do not have these problems every thing is fast and stable.I use animated backgrounds and icons with E17. Tip always use the alternative install disc to install.

---

### Post by Pumalite on 2007-12-26
I've had Gutsy in three different computer since Tribe 3 and I've been updating them, so now I have Final Release in all three . Never a problem. I'm very happy with 7.10

---

### Post by information_entropy on 2007-12-26
I have been running 7.10 since it was available and have never had a problem.

I even swapped the video card in my main system.

(after emotionally and psychologically preparing myself for the expected trauma)

The system started up, identified the card, prompted me to install the restricted drivers,
and went happily on its way.

I have been very impressed with the stability of Ubuntu 7.10.

I have it installed on several computers and have not had a problem with any of them.

---

### Post by Casual Fan on 2007-12-26
O.P.--that's not unstable. That's haunted! You need a good priest!:)

---

### Post by PARO on 2007-12-27
For me most of gutsy's instability was display oriented.  If I changed the screen resolution the screen would go black except for the mouse, but work after a hard reboot, Ctrl+Alt+BKSPS wouldn't work for me.  Dual-screen mode didn't display properly either, the resolution would say one thing, but look another, and my gdm login screen, was always changing everytime I'd switch the screen setup to something unpredictable.  I lost my window borders when switching from dual-screens to single, and had a fair bit of crashing when doing any of the above mentioned things.  I have a compaq presario with an nvidia card, which worked beautifully in feisty, but for some reason is a real mess in gutsy.  That was my biggest problem, but performance in general was poorer than in feisty for me also, video was choppier switching viewports in compiz fusion was too, and less responsive.

---

### Post by cbsim on 2007-12-27
> **pyrosama said:**
> 

Keyboard about every 30 seconds or so when typing a key will not respond or a key which has not even been touched will act as though it is being held down and its random every time no one key suffers from this problem.

Login password about every third time will tell me I entered the wrong password and its not very easy to mistype 'asdf' esp when it takes about 5 seconds to type in each letter (delay/freeze between leters)



I am having the same problem with my keyboard too! :mad:

---

### Post by Jay Jay on 2007-12-31
The people who attempt to downplay the stability issues and claim they're not related to the distro are gravely mistaken, a google search with "ubuntu freezing up" shows that this is hardly an isolated issue. Even with a barebones instllation 7.10 would lock up randomly. In the past 24 hours I've had to power down my machine about 30 times from Xubuntu freezing, not good... :(

> Applications act as though I issued a kill. Randomly an applications just kills its self no warning nothing will slow down or act buggy before hand it just disappears from view suddenly and has to be relaunched.

This happens to me too, at first I thought I was imagining things, but after seeing Firefox vanish without warning on a regular basis I realised something was amiss. At the moment 7.10 (for me) just isn't usable: it will lock up at any moment - usually when I'm in the middle of something important and there's no way to recover the session so the only option is to reset/power off. :mad: 

Hopefully this problem will be ironed out soon, In the meantime I'm going back to 7.04.

---

### Post by Pumalite on 2007-12-31
Gutsy 7.10 functions better in some hardware, thats all. I have 64 bit working on an Intel D975XBX, Core 2 Duo, 2 GB RAM, Nvidia 7800 GT.

---

