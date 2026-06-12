---
title: "Downgrade to Gutsy?"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by sdegrace on 2008-05-11
I upgraded to Hardy Heron soon after it came out and I feel like I made a huge mistake. Hardy is the first Ubuntu release to come out that I have been truly disappointed with (I have been using Ubuntu exclusively since Edgy, having switched from Windows XP on my Compaq Presario 2100 laptop). Up to this point I have really loved Ubuntu and never been tempted to go back to Windows. Maybe my expectations were too high? I found that each release seemed like an improvement over the last, but Hardy has been like a big step backwards for me. Everything seems to run slower, Firefox "freezes" more, my desktop effects will no longer run, and a big personal peeve, interaction with digital cameras, which used to be great, has been "improved" to a state of near-uselessness. It honestly makes more sense for me now to take the SD card out of my camera and read it than to plug my camera into the computer.

For a LTS release this is so disappointing. You would expect it to be, well, conservative if anything, not experimental and flaky. It seems like Ubuntu is on its way to no longer being the Golden Child of Linux. There is pretty much no upside to having "upgraded" to Hardy. Short of wiping my computer and reinstalling is there any easy way to get rid of Hardy and going back to Gutsy?

---

### Post by UnderRedMountain on 2008-05-11
Though I haven't been using Ubuntu very long, I agree with that, and was actually wondering the same thing...
I'm sure there is a way, I just don't know what it is :/

Any help?

---

### Post by iaculallad on 2008-05-12
I don't think there is no easy way of downgrading Hardy to Gutsy since you had already overwritten the original files to Hardy's. The only way of getting back with Gutsy is simply backup your important files, then do a new Gutsy installation. That would put you back in the right track.

**-- Let's give the Ubuntu team a little more time to do a little tweaking with Hardy.

---

### Post by Kevbert on 2008-05-12
> **iaculallad said:**
> I don't think there is no easy way of downgrading Hardy to Gutsy since you had already overwritten the original files to Hardy's. The only way of getting back with Gutsy is simply backup your important files, then do a new Gutsy installation. That would put you back in the right track.

**-- Let's give the Ubuntu team a little more time to do a little tweaking with Hardy.

+1.  I agree.  Things like Firefox can be downgraded to 2.0.0.14 but if you don't get rid of all FF 3b5 files there can be problems (see FF website for details).  If you can copy all Home directory files to another disk or DVD if possible and then re-install Gutsy.  I had to do this due to FF locking up my PC solid.  When re-installing Gutsy (manual partitioning) make sure that the format box is selected on the Hardy partition.

---

### Post by bobnutfield on 2008-05-12
Check one thing before you make a final decision....

Many people when upgrading, when asked during the installation if they wanted to keep their original menu.lst, they said yes.  This resulted in a lot of people booting into the wrong kernel.

Type:

uname -a

and verify which kernel you are running.

Bob

---

### Post by sdegrace on 2008-05-12
I did uname -a and got:

Linux stephen-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by sdegrace on 2008-05-12
Also... I am all for giving the Ubuntu team more time to work out the kinks in Hardy. Ubuntu is a great operating system, easily the best and the friendliest Linux I have tried out of many (in my opinion), but Hardy is an LTS release - in my opinion, for it to be released in this state, bad decisions were made.

It would have been easy, I think, to make conservative decisions to err on the side of ruggedness and stability and make it closer to Gutsy but incorporating any changes learned over the last six months needed to harden Gutsy. The type of changes in Hardy would be more appropriate for a release like Intripid Ibex. I understand that they felt that since they would be supporting Hardy for a longer period of time that it should have more cutting edge software and features so that it would not obsolesce as much over its period of support, but in my view, this turned out to be very wrong-headed. I just hope that not too much damage is done to Ubuntu's reputation and community by this mistake.

---

### Post by jarrhed on 2008-05-12
I would agree with this. When I first tried out Hardy I felt something was wrong but that was probaly because I tried slackware just before that but anyway I've found that Gutsy was faster and everytime (not to say that you guys are bad developers) you guys make new versions of ubuntu it gets slower.

---

### Post by bobnutfield on 2008-05-13
> **jarrhed said:**
> I would agree with this. When I first tried out Hardy I felt something was wrong but that was probaly because I tried slackware just before that but anyway I've found that Gutsy was faster and everytime (not to say that you guys are bad developers) you guys make new versions of ubuntu it gets slower.

Well, you have the correct kernel running.  It was just a thought as many have experienced this.

I have to agree with your comments about Hardy's release.  These forums are rife with similar problems for people previously running stable Ubuntu's.
I myself find it very buggy still three weeks after the final LTS release.  There are those who will say "We hear this after every new release", but I am sure that Hardy has caused more problems for more people than ANY previous release.  I have Hardy on my main workhorse laptop and it STILL gets the occassional lock-up/freeze requiring a power-button shutdown.  THIS IS BAD FOR HARD DRIVES!  I also have Hardy on my desktop (an upgrade from Gutsy), and it is also buggy with particular problems in the Update Manager GUI.  I am going to be looking at this carefully in the next few weeks and decide if I want to continue to put my expensive laptop at risk of a damaged hard drive.  As a side note, I also have a "testing" laptop that I have installed Fedora 9 on.  Fedora uses the 2.6.25 kernel as stock, and it has been stable as a rock.  Better memory usage, no freezes or lock-ups, and considerably faster on a laptop with weaker specs.  Further, Fedora also installs Firefox Beta 5 by default and there have been NONE of the problems people have experienced with it in Hardy.

Ubuntu has become a large and influencial distro with considerable backing.  Our "whining" about Hardy is probably not going to change a thing.  But, for me at least, it is sad to see a once well-deserved leader come to this.

---

### Post by gypaete09 on 2008-05-13
Hi all, I *had* do reinstall gutsy after a total lockup, because my only PC is running Ubuntu and my one-man company depends on it. 
No, I did not expect such a *major* problem, but I had chosen to live on the front line, so I knew it was dangerous. I reluctantly sit back now, using Gutsy again, "until Hardy is harder", but I was Novell, then MS certified, not a Unix expert, so it's hard for me to help myself, and two hard days of work, backing up from the console and reinstalling from scratch were "fun" enough to calm me down.

Please let the guys take the time to fix it, after all they are not swallowing millions of US$ for their work, like M$ does, and don't judge them too quickly.
Yes, to release it a bit later would have been wise. We all are wiser now.

Keep going Ubuntu! It's the best Linux I ever tested, and it made me decide to jump off XP and avoid Vista and it's successors FOR GOOD. 
I won't turn back.

J

---

### Post by mithritades on 2008-05-13
i'm a noob to ubuntu also,and i upgraded from 7.04 to 7.10,but from what i've seen in the forums i think i'll wait till winter b4 i upgrade to hardy but for all u good folks on the forums who's on the frontlines testing hardy for us mere mortals who brings up the rear i thank u,i don't know where i'd be without ya'll...just my $.02:KS

---

### Post by sdegrace on 2008-07-01
Well, with Hardy out for a couple of months and a ton of updates out, I'm starting to warm to it. I still don't like F-spot and wish for the old camera interface, but I *love* SPE (Stanni's Python Editor), which didn't work very easily in Gutsy, and for that alone I can reconsile myself to Hardy :). Although, a friend asked me to install Ubuntu on their (extremely underpowered and old) laptop and I actually installed Xubuntu Gutsy to be on the safe side. Note: From my experience, Ubuntu is the only distro I would ever install for a computer-semi-literate person, which to me is a sign of how great it really is.

Still, I was thinking today how much I love Ubuntu and how incredibly fortunate I feel to have access to so much great and mature free software. These days I can get all my work done entirely with stable, reliable free software without anything even approaching the instability and constant (justified) paranoia over security that comes wth Windows, and it feels great. I'm glad there are so many talented programmers who dedicate their time to free and open source software.

---

### Post by stani on 2008-08-06
> **sdegrace said:**
> I still don't like F-spot and wish for the old camera interface, but I *love* SPE (Stanni's Python Editor), which didn't work very easily in Gutsy, and for that alone I can reconsile myself to Hardy :).
Well, I put some effort together with MOTU and Debian Python to make SPE work better, so it is nice to hear that! I use SPE daily myself on Ubuntu, so I want it to be in good shape.

---

### Post by sdegrace on 2008-08-09
Your editor is awesome :). It's the best editor I've ever used for Python, without exception - I love it :)

---

### Post by flowtron on 2008-08-09
I'm currently having to work with an old "gutsy" installation myself,
because - roughly 1 1/2 months ago - after having run a benign-looking set of updates my "hardy" installation began showing weird freezes and lockups.
The symptoms vary, as does the time until it happens; I have everything from an extended freeze (that may or may not recuperate) to a involuntary restart of gdm right down to a full reboot happening without warning.
Initially this only happened in graphics intensive situations - like playing some OpenGL game, but also when using Macromedia's Flash-Player (youtube).
I had also noticed it happening spontaneously in regular Desktop sessions .. but wasn't ever sure I hadn't missed an odd browser instance or maybe something else that might've taxed the graphics card (which BTW is an NVidia 8800 GT).
Well, when the problem first cropped up I thought I'd missed a kernel update .. no, that wasn't it .. okay, let's re-install the newest drivers via that nice EnvyNG tool ... still getting freezes ...
then 3-4 days later - directly after another update - I had one wonderful day where I could play a whole evening without any problems.
The day after that the problems were back - no further updates or indeed any changes to the system.
Since then the intensity of the problem has been varied - as long as I don't play any games it seemed I could use my PC .. so I was content and hoped for a sponatenous find on the forum, bug-tracker or whatever I could find on the interwebs.
Now - after a small vacation - I come back, boot up the old box and .. while I was checking my mails .. it crashed. Nothing for it but the reset-button (as always with this problem, no more keyboard/mouse - no virtual terminal, no ping, no ssh) ... rebooted ... same problem ... running time was ~ 2-3 minutes. After the third time I gave up and went to bed. The next morning the behaviour was identical. I switched the old harddrive (physically) to be the boot-device again .. it still holds the old gutsy but was actually used more for backups .. well, yes, that was a system-backup (for any nit-pickers) .. as I've had a couple of mildly annoying problems with my PCs/Ubuntu-Installations this whole year ... "be prepared" has served me well in that respect.

Well - this installation is currently working .. I'm not going to risk any updates and will leech and burn myself an installation medium for something that is NOT ubuntu .. I'm finally sick of it.
If you look, you'll find my first post on this forum (of my handful) was already in a sour mood toward this distribution .. as it was trying to tell me it knew better than me how to set things up.
All in all it always felt a bit Microsoft in that way .. now it's finally begun having un-fixable bugs too .. as mentioned above I've scourged the interwebs for a solution to these freezes, there's tons and tons of people that describe exactly what's happening here, but no solution has presented itself.

---

### Post by bomanizer on 2008-10-02
Downgrade? I'm thinking of it. Hardy brought some annoying issues, mainly with the 2.6.24 kernel and acpi. My trusty Thinkpad freezes when removing an ultrabay device, suspend is out of the question and hibernate fails sometimes also. Pulseaudio is a bit flaky too, when my CPU is hitting 100% the sound goes "zhzhzhzhrzrhzrh", or something :D

yeah... I think I'm hitting the download mirrors today after work. I tried to find a support schedule for Gutsy, but I did not find any info. Does anyone know how long it is still supported?

---

### Post by louieb on 2008-10-02
rofl: Been using Ubuntu since 5.10.  New releases break something- see post just like this one about them all. 

Wait till next month you'll see post saying Intrepid Ibex broke my machine and Hardy is the greatest thing since sliced bread. 

> ... support schedule for Gutsy ... long it is still supported?
18 months its got a year of support left. 

BTW: the upgrade to Dapper broke my desktop. Now I've learned to use partimage to backup my install before  doing a distribution upgrade.

---

### Post by sdegrace on 2008-10-02
Hardy has honestly been pretty good for me since about June. No lockups, no crashes, everything works well, and I've gotten used to the ugly, Gnome-ified Firefox 3 default theme. As much aggravation as it has caused me, there are a few applications that I use regularly which are genuinely better in the version that comes with Hardy so I'm no longer tempted to go back to Gutsy.

Fool that I am, I plan to upgrade to Intrepid some time in late November... I'm hoping that this release will fix many of Hardy's problems without introducing new ones. I did have to figure out how to get USB camera to launch GThumb instead of Fspot, because with Fspot's inability to burn CDs it is basically useless... plus I hate the way versioning makes hard drive space for pics balloon out of control... it has promise, though and I'm hoping for a new version soon.

Stephen

---

### Post by bomanizer on 2008-10-03
> **louieb said:**
> .. Hardy is the greatest thing since sliced bread. 

LOL
> **louieb said:**
> .. 
18 months its got a year of support left. 


Nice. Though I was hitting download mirrors, but not Ubuntu. I have a shiny Debian/Lenny install now. If that proves usable then I might be submitting a "Goodbye Ubuntu" post somewhere, we'll see...

---

