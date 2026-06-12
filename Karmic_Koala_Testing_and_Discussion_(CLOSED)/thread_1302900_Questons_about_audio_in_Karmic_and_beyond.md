---
title: "Questons about audio in Karmic and beyond"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Eddward on 2009-10-27
So, two basic questions.  Will Ubuntu ever address the user problems caused by pulseaudio?  There are many and they are unnecessary.  In the short term, will Ubuntu at least post directions to disable or remove pulseaudio for those of us who are broken with it and don't need what ever it is that pulseaudio is  supposed to be providing beyond ALSA's support?  Is there a better place to go to get these answers? 

I'm asking because I recently migrated to 9.04.  I had never used pulseaudio before.  When posting of sound problems to the forum I received no help.  In the end the only way I found to fix sound was to follow a guide that explained how to disable pulseaudio for Jaunty.  It seems many users are having similar trouble and they are also being ignored, told to stick with pulseaudio and hope it starts to work or told to buy new hardware.

I'm afraid to migrate to Karmic now because I've heard it's even more difficult to disable pulseaudio and I can't find a guide to do it.  While looking I just discovered a bug report that suggests that Ubuntu is too understaffed to fix this problem. ([https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465/](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465/))

I'm particularly irked because sound worked perfectly for me for years before I migrated.  Once I disabled pulseaudio in Jaunty it worked again.  But it looks like it keeps getting harder to disable.  Lastly, I have an emu10k card that works great with ALSA and I believe it does it's mixing in hardware so I don't even need dmix.  Even if I could get pulseaudio to work it will always be an unnecessary drain on CPU and memory resources for me.  From what I hear dmix is less of a drain than pulseaudio.

I'm also a little irked since I picked Ubuntu based on the existence Ubuntu Studio.  I assumed it would be an easy setup to be able to finally start recording and sequencing on Linux.  That's never been very easy to get right.  I've since found out that Ubuntu Studio doesn't even come with the jack sound daemon setup out of the box and you cannot do serious recording and sequencing work without it.  Jack can't even be run because pulseaudio clashes with it.  The only workaround is the unsupported step of disabling pulseaudio.  It's a mess.  Ubuntu Studio shouldn't even advertise recording until they get that fixed.

I guess that was a few questions and a lot of rant.  Still it's frustrating to have to go through this.  These sound problems are a silly regression in Linux and I'm surprised they've been allowed to go on this long since it can work.  It's odd that *the* user friendly distro is the one stonewalling on this.  And the Ubuntu Studio mess just feels like a bait and switch.  I mean I know it's volunteer work, but don't claim to be a recording distro if it doesn't work.  At least put a big notice in the release note that recording doesn't actually work out of the box yet.

Edd

---

### Post by georgelenzer on 2009-10-27
I'm not an official voice of authority, nor am I even a long time Ubuntu user, but the writing is on the wall about Pulseaudio:  It replaces the long in the tooth and very high latency Esound daemon which used to be Gnome's default.  ALSA can do some of what Pulse can do, but not all of it.  And, no one has developed any easy to use connection managers that would allow one to easily control the audio streams of multiple applications.

Also, for people like me, ALSA doesn't offer any kind of network transparency and Esound jas never been terribly good at it.  Pulse is very good at that and works well for when I want to watch something on my big screen media center but want to listen to it with headphones plugged into my laptop.  I also use a centralized app server for the family, so being able to move audio between laptops as thin clients is very useful.  Having said that, I understand your complaint.  I think what should be done is provide a way to have pure ALSA or Pulse optionally.  As far was where to get the answers officially I don't know.  This is probably coming from the Gnome project more than from Ubuntu.

When I installed Ubuntu Studio on my machines (for both Jaunty and Karmic) JACK was part of the system.  QJACKCtl was there, and when I ran it, I was able to get JACK up and running with no effort at all.  Considering there's really only one installer, I can't imagine what happened for you to wind up without JACK.  But it does appear to be the default if you select audio production apps.  And JACK worked fine with Pulse on my set up.  (I'm thinking of switching my Gentoo A/V workstation over to Karmic soon.  I have my pro-audio gear there instead of the crappy laptop sound.  It will be interesting to see how it works there with real pro gear.)

Getting Pulse working properly (when I was using it on Gentoo) was initially a challenge.  But once it was configured properly, it worked amazingly well for both pro audio work and just regular entertainment.  There are some conflicts however.  When I run Cinelerra, it doesn't like JACK running and the Esound portion of it doesn't seem to like Pulse either.  So it's possible that you're running into some application specific problems, but I don't know enough about your situation to say for sure.  Since I just installed Karmic last night, I have more learning to do.  But so far JACK and Pulse pluse the sound "just worked" for me, whereas I had some trouble with the ALSA side (always the worst part of the sound stack to configure) in Jaunty.  Good luck.

---

### Post by Eddward on 2009-10-27
I don't mind if pulseaudio replaces esd as long as it is not the CPU hog it currently is.  There's no excuse for using that much CPU to do that little.  Especially if part of what it is doing the sound hardware can do better and faster.

As far as my fears of Ubuntu Studio, I based that on info I found while trying to fix sound in base Ubuntu Jaunty.  Specifically I saw this question ([https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/71865](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/71865)) and this review ([http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904](http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904)) and several other similar things for Jaunty.  It was rather shocking to see how many users were broken with pulseaudio and offered no real help.

Looking at some more things I noticed that somehow pulseaudio even broken CD audio for users.  ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/247346](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/247346))  I'm afraid to know how.  There's a wire that runs from the CD player to the sound card.  Are the wasting more CPU to decode CD audio in software instead of letting the hardware do what it was made to do?

I guess it's great if Ubuntu wants to make Linux suitable for the home entertainment center.  We don't want Linux to fall behind.  But if it breaks the basic desktop then they're doing it wrong.  You don't penalise people for features they don't use.  My computer isn't a home entertainment center.  It doesn't have bluetooth.  I don't even have surround sound.  Pulseaudio doesn't belong on this kind of system.

I do appreciate the response.  I'd like to get a feel for the official roadmap of Ubuntu though because I'm ready to dump it before I grow attched to something in the system.  Back with Gentoo I may have had to heavily customize the system to get some of the things I wanted, but at least it was made easy to do so.  Ubuntu looks very nice, but it was way to difficult just to get a game to work and a few seconds on Google show the same problem keeps repeating without any honest attempt to address the root cause.  Pulseaudio is breaking or wasting system resources for the common cases of sound usage in order to make a niche case easy.

Edd

---

### Post by georgelenzer on 2009-10-28
I think the Ubuntu folks should work on some Pulse/ALSA configuration tools.  I went to a lot of trouble to learn how to get the "perfect" Pulse set up on Gentoo and it worked flawlessly.  Remote streams with no sync issues (which I had a lot of with ESD), local streams with no problems and support for ALSA, OSS and ESD aware apps.  It really was excellent.

I could have Youtube from the app server playing something at the same time that I was playing a Youtube stream on the local Firefox on my laptop.  Individual volume controls for the streams too.  And once I'd figured out which GStreamer and Pulseaudio plugins were needed along with a custom .asoundrc (for setting Pulse as the default ALSA HW), everything played together nicely.  I was just looking into getting JACK to run on top of Pulse before I decided to give Ubuntu Studio a spin.

Looking that the links you sent, I recognized quite a few of the issues.  Particularly I ran into issues with audio that would stutter and crackle when Pulse was running when I first installed it in Gentoo.  I even had problems where local sound would be completely muted when I'd used remote sound from the app server.  I too was convinced that it was a CPU hog and a terrible piece of software.  But, then I went back and read the info at the Pulseaudio project site itself as well as ALSA documentation.

What I discovered is that the various media apps were connecting to Pulse using their default sound systems (OSS, ALSA, or ESD).  Some of those emulations weren't the best choices in Pulse.  Installing the correct Pulse and Gstreamer plugins on Gentoo as well as setting Pulse as the default ALSA HW device fixed everything.  Also making sure that the apps used either Pulse or ALSA only went a long way to low latency audio, even over the network! :)  The only server better for low latency audio is JACK.

Unfortunatley, it doesn't look like the people in many of the various distribution developer communities have been talking about this out in the open.  So the users are beginning to develop negative ideas about Pulse as well as fixes that might actually set them back worse once Pulse is the only option for Gnome.  (I'm not as familiar with KDE, but I know they've deprecated the old ARTs server and I believe they're also going for Pulse).  The development community should definitely make a concerted effort to fix these problems by shipping with sane configs for Pulseaudio and new tools to make configuration easy.

The Pulse project itself has some tools, but they're not easy to use for most.  (I still don't understand why people are shifting volume faders from vertical to horizontal orientation.  Vertical is far more natural for pointing devices like mice and track pads)  And ALSA... well they provide THE best drivers for the widest array of sound cards, but there really still haven't been any easy to use configuration tools for the average user.  I don't mind mucking about with text config files (which isn't stictly necessary anymore if you're purely ALSA) but some people just need to be able to hit the ground running and ALSA doesn't yet do that.

So this is a problem.  But I believe it is one that can be solved.  Speaking of problems... are you having issues with Pulse now?  I wouldn't mind helping out as I've had a good deal of experience following the Pulse project's "perfect setup" guide.  I will say that the one thing I haven't done myself yet is getting JACK running on top of Pulse.  But... there is 'pasuspender' which will force the Pulse sound daemon to release the ALSA device and allow JACK to connect.  Of course, during that time you can only use JACK aware apps.  But how many people who need JACK are watching Youtube at the same time?  :)

Regarding the Linuxtimes review, I took a different approach from the reviewer.  (I did have too many problems with Ubuntu Studio 9.04 and moved to Karmic though)  I installed from a pure Ubuntu Studio ISO instead of installing a standard Ubuntu Desktop and applying the Studio metapackages.  I'm wondering if the difference in his experiences vs. mine have to do with more than just the Studio metapackages being applied.  I installed Ubuntu Studio 64-bit (9.04) last week and other than needing to tweak the ALSA config for my specific audio hardware on the laptop, Pulse and JACK just worked.

Interestingly, when I run JACK on Ubuntu Studio with qjackctl, it seems to play nice with Pulse.  I haven't looked into what they're doing yet.  Could be that they ship the real Studio distro with qjackctl running pasuspender first.  Or... it could be that they have a JACK plugin for Pulse.  It's unlikely that it's the other way around since I have to start the JACK server, but GNOME sound is already working when I log in.  My offer to help people with Pulse issues is open to anyone reading this comment thread as well.  Just send me a private message if you want to talk about it.  I'm not a coder, or an expert, but I think I know a little more about Pulse audio than a person should.  :)

> **Eddward said:**
> I don't mind if pulseaudio replaces esd as long as it is not the CPU hog it currently is.  There's no excuse for using that much CPU to do that little.  Especially if part of what it is doing the sound hardware can do better and faster.

As far as my fears of Ubuntu Studio, I based that on info I found while trying to fix sound in base Ubuntu Jaunty.  Specifically I saw this question ([https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/71865](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/71865)) and this review ([http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904](http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904)) and several other similar things for Jaunty.  It was rather shocking to see how many users were broken with pulseaudio and offered no real help.

Looking at some more things I noticed that somehow pulseaudio even broken CD audio for users.  ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/247346](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/247346))  I'm afraid to know how.  There's a wire that runs from the CD player to the sound card.  Are the wasting more CPU to decode CD audio in software instead of letting the hardware do what it was made to do?

I guess it's great if Ubuntu wants to make Linux suitable for the home entertainment center.  We don't want Linux to fall behind.  But if it breaks the basic desktop then they're doing it wrong.  You don't penalise people for features they don't use.  My computer isn't a home entertainment center.  It doesn't have bluetooth.  I don't even have surround sound.  Pulseaudio doesn't belong on this kind of system.

I do appreciate the response.  I'd like to get a feel for the official roadmap of Ubuntu though because I'm ready to dump it before I grow attched to something in the system.  Back with Gentoo I may have had to heavily customize the system to get some of the things I wanted, but at least it was made easy to do so.  Ubuntu looks very nice, but it was way to difficult just to get a game to work and a few seconds on Google show the same problem keeps repeating without any honest attempt to address the root cause.  Pulseaudio is breaking or wasting system resources for the common cases of sound usage in order to make a niche case easy.

Edd

---

### Post by Eddward on 2009-10-28
[COLOR=#000000]I also think Ubuntu needs to do something about the setup of Pulse and ALSA, but I'm becoming more and more convinced that Pulse-only or Pulse hogging the hardware isn't it.  One size does not fit all.  I understand that it's nice if you want to do remote streaming. But I don't and it seems I'd still pay the price for it with Pulse.  If I have a 3D accelerator card, I wouldn't let Gnome tell me I have to use software rendered 3D for everything. If I have a multicore, multiprocessor CPU I wouldn't let Gnome tell me I have to serialize everything through user-space threads and a single processor thread. I have a sound card that does hardware mixing of 32 sound streams. I'm not going to let Gnome/Pulse tell me I have to cripple if and force everything through a software mixer.  If Gnome intends to force users to Pulse and cripple hardware for people like me, I'll just go back to XFCE, enlightenment or something else a little less power hungry.[/COLOR]

Also about Jack, putting Jack on top of Pulse sounds backward.  Jack needs reliable low latency.  From what I've seen low latency isn't a concern to the Pulse team.  They just want constant latency.  Putting Pulse on top of Jack would be a better idea.  On aside note, I have seen cases where qjackctl was configured to suspend pulse.

I guess you might be able to get better sound if you can get all of your apps rewritten to use and/or work around Pulse.  My original problem was the game Sacred ported by LGP.  The LPG game X2 also had some problems.  I also had some clicks in World of Goo.  Zaz cause me trouble, but it's open source so I'm guessing it will be forced to be rewritten for Pulse unless the project dies before that.  I'm afraid I can't make all of my apps use Pulse directly.  I buy proprietary games and I tend to expect them to work.  But I can't get them to rewrite for Pulse Audio.  But vendors shouldn't be penalized because some devs decided to break the world in the name of the new hotness.  Backwards compatibility needs to be maintained for a while.  I believe that LGP still targets OSS to this day and compatibility was maintained in the OS prior to Pulse.  This non-backwards compatibility introduced by Pulse is not acceptable to me.  Pulse blaming the hardware is also not acceptable since it worked without Pulse.  If new hardware is needed for new function, fine.  More should mot be required of the hardware just to maintain the existing functionality.

Right now I don't exactly have any problems with Pulse Audio on my system because I disabled it.  My system runs fine at the moment.  I just migrated to Ubuntu and Jaunty a few weeks ago.  I had trouble with games and found a guide for disabling Pulse on Jaunty.  I'm afraid to move on to Karmic now because I haven't seen a way to disable Pulse on it.  I would be willing to work through trying to fix and use Pulse just to get something more documented and to use a more mainstream configuration, but I'd have some conditions before I'd want to take the time.


[LIST]
[*]I'm not buying a new card because of Pulse.  Mine works perfectly with ALSA.
[LIST]
[*]   I've seen Pulse developers complain about emu10k cards and creative labs rather than address a failure using the card/driver.
[*]If they don't want to support my hardware that's ok, but I probably  shouldn't be using their software then.
[/LIST]
 
[*]I can't change the proprietary games.  I do want them to work.
[LIST]
[*] If they don't work with Pulse like they do without it, we've failed.
[/LIST]
 
[*]I don't want an end game where 31 hardware channels in my card go unused while software mixing is loading my CPU.
[LIST]
[*]   I still want to access my hardware sound acceleration just like I want to access my hardware video acceleration.
[/LIST]
 
[*]I can tolerate suspending all other sound on my system while using Jack to sequence and record, but honestly that should not have to be a requirement.
[LIST]
[*]   Putting Jack on top of Pulse still sounds backwards.
[*]If anything, Pulse should go on top of Jack.
[/LIST]
 
[/LIST]

I'm not sure all my requirements are possible with Pulse or if they are even on the roadmap.  For what it's worth, I'm perfectly happy editing files to get things tweaked just so if you have ideas on how to do it.  Linux (and UNIX) do not intimidate me in the least.  What I am afraid of though is customizing things so much that an upgrade will break me because I've deviated too far from the middle of Ubuntu's safe path.  Having to disable Pulse scares me for the same reason and that's why I'm on the verge of moving back off Ubuntu.  I'm not willing to cripple my sound hardware for Ubuntu and the only way I've found to get it working (disabling Pulse) looks like it will cause (more?) problems with every upgrade.

Thanks, and sorry for being rant-ish, yet again.  It's just the more I think about it, the clearer it becomes that Pulse seems to be trouble and inconvenience without an upside for me.  Ubuntu let me turn off the unneeded compositor in X11 without even logging out or killing any of my jobs.  Why can't I turn off the unneeded remote sound daemon and get better performing local sound?

Edd

---

### Post by gordintoronto on 2009-10-29
I'm with you completely!  Forcing people to use pulseaudio is one way to achieve 0.2% market share -- when what you want is 5%, or 10%, or 20%.

---

### Post by Eddward on 2009-10-29
Based on the complaints I've seen on the forum and the net, it seems Ubuntu (and I guess Fedora) are shooting themselves and their users in the foot with it.  But don't get me wrong.  If at some point they fix backward compatibility, stop the crackling, lessen the latency I've heard affects realtime-ish apps like games (it didn't even work well enough for me to tell if there was a delay) and utilize the hardware I bought to take the load of my CPU, I'd be ok with it.

Adding the new features they are trying to enable could bring more users to Linux.  They've just done it wrong and dumped it on a couple of the biggest distros for new Linux users.  I almost feel that Pulse should have been enabled and stablized on the likes of Gentoo, Slackware and/or Debian before you crater the user experience for the audiences of Ubuntu and Fedora.

Progress needs to happen.  It just needs to be done without so much regress.

Edd

---

### Post by joey-elijah on 2009-10-29
I've never noticed an issue... i expect I'll start noticing everything now you guys have been pointing out =o P

Development is development; PulseAudio and Ubuntu will find their feet with one-another at some point - integration has to start somewhere, it'll get better in the near-so future.

---

### Post by Seventh Reign on 2009-10-29
Whats wrong with Pulseaudio?  Its 1000 times better than what we had before on all of my systems.  I Love it.

---

### Post by t.rei on 2009-10-29
I'm getting sick and tired of fixing the audio on my computer so it muted the freakin speakers when I plug in my headset. Just recently it stopped working properly - again - and this time it's not the alsa-base.conf. -.-

---

