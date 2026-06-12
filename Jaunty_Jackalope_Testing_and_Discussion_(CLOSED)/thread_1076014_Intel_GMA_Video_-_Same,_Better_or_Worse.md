---
title: "Intel GMA Video - Same, Better or Worse"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-02-20
I had to revert from Intrepid to Hardy on my new laptop due to VERY poor video performance with the Graphics Media Accelerator X3100.

Can I expect that Juanty will be the same, better or worse than Intrepid?

What do you think or know about this?

---

### Post by klange on 2009-02-20
Jaunty has UXA, which while unstable at the moment, is faster and does [this](http://oasis-games.com/~klange/screenshots/2009-02-06-194712_1280x800_scrot.png). Rest assured, things should be better in Jaunty (though nothing beats the performance of Hardy with XAA... or maybe Feisty even, it was quite quick, but the drivers lacked a number of crucial bits back then).

---

### Post by crjackson on 2009-02-20
> **WindowsSucks said:**
> Jaunty has UXA, which while unstable at the moment, is faster and does [this](http://oasis-games.com/~klange/screenshots/2009-02-06-194712_1280x800_scrot.png). Rest assured, things should be better in Jaunty (though nothing beats the performance of Hardy with XAA... or maybe Feisty even, it was quite quick, but the drivers lacked a number of crucial bits back then).

Good to hear. I look forward to the update then.

---

### Post by dixon on 2009-03-12
> **crjackson said:**
> I had to revert from Intrepid to Hardy on my new laptop due to VERY poor video performance with the Graphics Media Accelerator X3100.

Can I expect that Juanty will be the same, better or worse than Intrepid?

What do you think or know about this?
I have also X3100, but I wasn't using hardy for long time. I'm now intrepid user. What do you mean by very poor video performance. I only noticed video tearing which is very annoying. But what are other issues? Is desktop more responsive or battery life better in hardy? I just want to know the issues if I should consider installing hardy...

---

### Post by crjackson on 2009-03-12
> **dixon said:**
> I have also X3100, but I wasn't using hardy for long time. I'm now intrepid user. What do you mean by very poor video performance. I only noticed video tearing which is very annoying. But what are other issues? Is desktop more responsive or battery life better in hardy? I just want to know the issues if I should consider installing hardy...

[LIST]
[*]Video tearing
[*]Poor desktop responsiveness
[*]Demanding 3D games not playable due to slow screen updates
[*]Full Screen Video with 3-5 second gaps in playback (Video Lag)
[*]and on, and on...
[/LIST]

Installing Hardy fixed all issues, except that Full Screen Flash has laggy video. Downloaded to the HD however, Full Screen playback is great w/Hardy.

---

### Post by crjackson on 2009-03-22
Well, I just tried Alpha6 and the video is much better than on Intrepid for me. In fact, it's better than Hardy on this laptop.

I can't wait for the release now.

---

### Post by zorkerz on 2009-03-22
Ive got an x3100 on a thinkpad x61. I never noticed video problems specifically. There have been compiz problems in the past. Im unable to use compiz in jaunty because windows loose all there borders and cannot be moved or resized. See [Bug 340895]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/340895") though this one appears not to be GMA 965 specific. I still have problems in wine where I get logged apparently from programs using the graphics card, though Ive mostly only tested it with Civ IV and am not positive its caused by the x3100/GMA 965 card.

---

### Post by crjackson on 2009-03-22
Video playback is much improved for me with or without compiz. In fact, I get the same frame rates weather it's on or off. Intrepid for me was SO SLOW in the laptop I have to install Hardy for decent performance.

It looks like Jaunty will be a decent upgrade for me, I was worried it would have the same performance problems as stated but now I'm not so concerned.

---

### Post by Starks on 2009-03-22
Last I heard, Jaunty will not ship with UXA enabled.

---

### Post by crjackson on 2009-03-22
Is it enabled in A6? Either way I don't care. The performance I got was very acceptable and surprising.

---

### Post by zorkerz on 2009-03-22
@ Starks where did you hear that? I would love to learn more about this. Ive found info generally hard to find.

---

### Post by scaine on 2009-03-22
UXA is not planned for default, like Starks said, but I can't remember which thread I read that in.  Enabling it on a 9 series card has dramatic (positive) effect, while enabling it on a GMA4500 series has a slightly negative effect, which becomes dramatic if you also use Compiz (or at least, that's my experience).

Video in general has come along leaps and bounds in all the intel-based PCs I use (a Dell x300, a Tosh u400, and a MacMini).  As of yesterday's updates, full-screen video now only takes around 30% on my aging 7-year old Dell x300, while at Alpha2, it was easily hitting 80%.

---

### Post by zorkerz on 2009-03-22
How would you go about enabling it? What is a 9 series card (perhaps GMA 9xx)?

---

### Post by andrewabc on 2009-03-22
> **scaine said:**
> UXA is not planned for default, like Starks said, but I can't remember which thread I read that in.  Enabling it on a 9 series card has dramatic (positive) effect, while enabling it on a GMA4500 series has a slightly negative effect, which becomes dramatic if you also use Compiz (or at least, that's my experience).

Video in general has come along leaps and bounds in all the intel-based PCs I use (a Dell x300, a Tosh u400, and a MacMini).  As of yesterday's updates, full-screen video now only takes around 30% on my aging 7-year old Dell x300, while at Alpha2, it was easily hitting 80%.

You find that with default settings or with uxa enabled?

I have g965 x3000
intel video for me has improved a lot since Gutsy (when it was so bad ubuntu was useless). Intrepid was the release where it was good enough to use ubuntu full time.

I presume improved xorg and intel drivers will make jaunty even better. Live cd testing is showing no regressions.

---

### Post by dixon on 2009-03-22
[ This thread ]("http://ubuntuforums.org/showthread.php?t=1058915&highlight=uxa") is about not enabling UXA by default. About the improvements - is the tearing gone in Jaunty? Is DRI2 working as expected?

---

### Post by Starks on 2009-03-22
UXA causes crashes on my GMA950 (i945)

(Also, UXA has never been enabled by default on any daily or alpha release.)

---

### Post by crjackson on 2009-03-22
> **andrewabc said:**
> You find that with default settings or with uxa enabled?

I have g965 x3000
intel video for me has improved a lot since Gutsy (when it was so bad ubuntu was useless). Intrepid was the release where it was good enough to use ubuntu full time.

I presume improved xorg and intel drivers will make jaunty even better. Live cd testing is showing no regressions.

Intrepid was not acceptable at all on 3 of my laptos. Currently I'm using Hardy on them and a couple of desktops. A6 simply pleased me to no end as compared to Intrepid.

---

### Post by stats on 2009-03-25
I have a x3100. I still use hardy because of the horrible tearing on intrepid. jaunty is better than intrepid, bit i still see tearing. 
textured video really screwed things up, and in the 965gm (x3100) forcing xv overlay causes the system to crash randomly.
also uxa didnt work for me with compiz on.

---

### Post by crjackson on 2009-03-25
> **stats said:**
> I have a x3100. I still use hardy because of the horrible tearing on intrepid. jaunty is better than intrepid, bit i still see tearing. 
textured video really screwed things up, and in the 965gm (x3100) forcing xv overlay causes the system to crash randomly.
also uxa didn't work for me with compiz on.

Hopefully an update to the video driver is around the corner that will fix most of this. I'm going to give Jaunty a roll and see what happens. For me, video playback is better on Jaunty A6 LiveCD than it is on the fully installed Hardy 8.04.2.  In Hardy, I can't play full screen Flash from the web due to chopping and stalling (and tearing). On A6 full screen web flash was smooth playing with minor tearing.

I realize this could have something to do with Flash itself but the end result for me was a better user experience to that end. Fully installing and daily use may prove that Hardy is still better for me too, but I'm going to give Jaunty a chance at this point.

---

### Post by keypox on 2009-03-28
I just installed 9.04 beta on my laptop.  It runs like crap on gma 4500. Intrepid ran way way better.  But did have tearing in videos.  But i have never seen a ubuntu install without video tearing.

I hope they fix it

---

### Post by fondle-em on 2009-03-28
> **crjackson said:**
> Hopefully an update to the video driver is around the corner that will fix most of this.

That mythical driver update to eliminate the horrendous Intel video tearing (which I've only seen on Linux, and never on Windows or OS X machines using the same Intel video hardware) has been just "around the corner" since at least late 2007 and possibly longer.  Driver updates come and go; somehow this issue always gets bumped to "we'll fix it next time". Permanently broken video is apparently the reward one gets for going out of one's way to buy a Dell that shipped with Ubuntu pre-installed in a recommended, allegedly *officially supported* configuration.

That's cool though; I'm *sure* that the Intel video drivers will be fixed in time for Karmic Koala.  :lolflag:

I'll believe it when I see it... and it's been broken so long that I may not believe it even *then*.

---

### Post by tjeremiah on 2009-03-28
I gotta say its a lot worst with 9.04 than Intrepid. Though in Intrepid there was screen tearing, if that was annoying for you than 9.04 is a disaster! Well at least for me. I seriously hope the final realease will fix this problem.

---

### Post by tjeremiah on 2009-03-28
can someone explain to me how to enable UXA in detail?

---

### Post by zorkerz on 2009-03-28
> **tjeremiah said:**
> can someone explain to me how to enable UXA in detail?
Open a terminal by going to applications -> accessories -> terminal
In the terminal type the following command. 
```
sudo nano /etc/X11/xorg.conf
```NOTE: nano is a text editor you can use any you like by replacing nano with the name of another. For example many people use gedit.

Scroll down to the Device Section (should appear similar to mine below).
> Section "Device"
                  Identifier      "Configured Video Device"
EndSectionAdd the following line under Identifier 
 ```
option "AccelMethod" "uxa"

```The Device section should then look similar to this.
> 
Section "Device"
                  Identifier      "Configured Video Device"
                  option          "AccelMethod"   "uxa"
EndSectionSave your modifications to the file (to save in nano press ctrl+o).
Restart your computer. 

It is my understanding that this is how you enable uxa though I confess I don't know how to test to make sure it is actually enabled. Hope its helpful.

---

### Post by tjeremiah on 2009-03-28
> **zorkerz said:**
> Open a terminal by going to applications -> accessories -> terminal
In the terminal type the following command. 
```
sudo nano /etc/X11/xorg.conf
```NOTE: nano is a text editor you can use any you like by replacing nano with the name of another. For example many people use gedit.

Scroll down to the Device Section (should appear similar to mine below).
Add the following line under Identifier 
 ```
option "AccelMethod" "uxa"

```The Device section should then look similar to this.
Save your modifications to the file (to save in nano press ctrl+o).
Restart your computer. 

It is my understanding that this is how you enable uxa though I confess I don't know how to test to make sure it is actually enabled. Hope its helpful.

Thanks. Ill try it anyway and give it a go.

---

### Post by crjackson on 2009-03-30
Well I tried the livecd of 9.04 on my laptop with the GMA X3100 and it was much better than the Intrepid Install when playing online flash content. 

Currently I have Hardy installed with minimal issues, but full screen online flash movies won't really play. You can get about 3 seconds of play, then 3 seconds of pause. This is continuous and never stops, but only happens on full screen - online flash movies.

If the movie is on the HD is plays perfectly every time.

With Jaunty even from a liveUSB stick, online video plays back perfectly in full screen.

I must admit, I didn't do much else in the way of testing, but it's definitely better here. I could be flash itself is being handled better, or some other unknown improvement, but it is an improvement for me at this point. Testing was done with A6 rather than beta.

---

### Post by tjeremiah on 2009-03-30
Silly question I guess but how do I obtain Alpha6? I updated to the beta from Intrepid when it was released the other day but it saids version 5, not 6.

---

### Post by crjackson on 2009-03-30
> **tjeremiah said:**
> Silly question I guess but how do I obtain Alpha6? I updated to the beta from Intrepid when it was released the other day but it saids version 5, not 6.

Alpha 6 would be a downgrade from the beta version, but it seems you have alpha 5 if I'm reading your post correctly. But if you want to test A6 anyway, I got mine from the link below. It would probably be best if you just did a fresh install of the actual beta version and then grabbed all the updates

For A6 go to:

[http://distrowatch.com/?newsid=05374]("http://distrowatch.com/?newsid=05374")

For the Beta go to:

[http://www.ubuntu.com/testing/jaunty/beta]("http://www.ubuntu.com/testing/jaunty/beta")

---

### Post by dixon on 2009-03-30
About the tearing while watching videos issue. In SMPlayer you can use Xv(1 - Intel Video Overlay) output driver. I've tested it only in intrepid and it works fine - video is without tearing, but it doesn't play very nice with compositing. Give it a try in jaunty and please report back...

---

### Post by zorkerz on 2009-03-30
> **tjeremiah said:**
> Silly question I guess but how do I obtain Alpha6? I updated to the beta from Intrepid when it was released the other day but it saids version 5, not 6. Just update. Once you have installed all the newest updates from the default repositories you will have the newest jaunty available. At this point beta. To install it fresh download from here [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by TrueTom on 2009-03-30
> **dixon said:**
> About the tearing while watching videos issue. In SMPlayer you can use Xv(1 - Intel Video Overlay) output driver. I've tested it only in intrepid and it works fine - video is without tearing, but it doesn't play very nice with compositing. Give it a try in jaunty and please report back...

Tearing is more or less fixed in Jaunty without compositing.

---

### Post by crjackson on 2009-03-30
> **zorkerz said:**
> Just update. Once you have installed all the newest updates from the default repositories you will have the newest jaunty available. At this point beta. To install it fresh download from here [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

He said he already has the beta and requested Alpha 6, but after re-reading the post it seems he had Alpha 5 installed rather than the beta.

---

### Post by zorkerz on 2009-03-30
Hmm I it appears ubuntu.com is no longer hosting the old alphas for jaunty. Here is where they used to be but the links no longer work. [http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

To get alpha 6 and not the beta you would have to find somebody who has the iso leftover. Generally I would go with the most up to date version possible though.

---

### Post by crjackson on 2009-03-30
> **zorkerz said:**
> Hmm I it appears ubuntu.com is no longer hosting the old alphas for jaunty. Here is where they used to be but the links no longer work. [http://www.ubuntu.com/testing/jaunty/alpha6](http://www.ubuntu.com/testing/jaunty/alpha6)

To get alpha 6 and not the beta you would have to find somebody who has the iso leftover. Generally I would go with the most up to date version possible though.

Yep, just checked it here too. It really shouldn't matter I would think. The beta+ is the only way to go in my estimation.

---

### Post by keypox on 2009-04-01
My gma 4500 ran terrible in the 9.04 beta.  So bad i had to reinstall 8.10.  Hope they fix it soon.

---

### Post by crjackson on 2009-04-01
> **keypox said:**
> My gma 4500 ran terrible in the 9.04 beta.  So bad i had to reinstall 8.10.  Hope they fix it soon.

I'm sure it will get fixed some day. What is your definition of soon? I'll be surprised if it's decent before next year..

---

### Post by Amaranth on 2009-04-01
From what I've seen it seems X3100 and older were worse in intrepid then hardy but is better in jaunty. Newer chips seem to be better in intrepid then jaunty though so it's a tradeoff.

---

### Post by crjackson on 2009-04-01
> **Amaranth said:**
> From what I've seen it seems X3100 and older were worse in intrepid then hardy but is better in jaunty. Newer chips seem to be better in intrepid then jaunty though so it's a tradeoff.

I guess that's good news for me since I have an X3100. It was not uasble under interpid so I installed hardy (which works fine).

I tested it with jauty a6 and video playback was better than in Hardy. If video performance for the x3100 holds the same on the final release, then I'll upgrade it from hardy to jaunty.

Fingers Crossed!

---

### Post by andrewabc on 2009-04-01
I have g965 x3000 and compiz worked good in Hardy, much better in Intrepid (actually usable on daily basis), and as far as the liveusb and livecd of the alphas/beta it is working great.

compiz was useless in gutsy, and even x3000 was blacklisted at that time.

---

### Post by crjackson on 2009-04-01
> **andrewabc said:**
> I have g965 x3000 and compiz worked good in Hardy, much better in Intrepid (actually usable on daily basis), and as far as the liveusb and livecd of the alphas/beta it is working great.

compiz was useless in gutsy, and even x3000 was blacklisted at that time.

Good to hear andrew...

---

### Post by psyke83 on 2009-04-02
For those of you suffering from performance problems (even with UXA), I recommend you try EXA with "optimized migration". It's not enabled by default due to some minor corruption issues, but it's worth a try anyway.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
EndSection
```

---

### Post by keypox on 2009-04-02
> **crjackson said:**
> I'm sure it will get fixed some day. What is your definition of soon? I'll be surprised if it's decent before next year..

soon is like about the time 9.04 is released...

anyways what is the intel video driver that was updated today. ON 8.10

---

### Post by bofphile on 2009-04-02
I have a Thinkpad T500 with a GMA 4500MHD and the performance is definitely worse in Jaunty than in Intrepid. Compiz is slower, there's more CPU load when maximizing/minimizing windows, and there's tearing when moving windows or when using Super+E.
Also scrolling in firefox is sluggish (especially on site like slashdot).

UXA doesn't make any difference.

---

### Post by crjackson on 2009-04-02
> **psyke83 said:**
> For those of you suffering from performance problems (even with UXA), I recommend you try EXA with "optimized migration". It's not enabled by default due to some minor corruption issues, but it's worth a try anyway.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
EndSection
```

Thanks for the tip. I'll play with it when the full release is out and ready for my laptop.

---

### Post by Kareeser on 2009-04-02
Mm... I noticed a definite degredation in performance with UXA enabled. Unfortunate.

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
	Subsystem: Dell Device [1028:018d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	Region 2: I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb
```

---

### Post by cyclist23 on 2009-04-02
> **psyke83 said:**
> For those of you suffering from performance problems (even with UXA), I recommend you try EXA with "optimized migration". It's not enabled by default due to some minor corruption issues, but it's worth a try anyway.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
EndSection
```

Thank you, psyke.  This has greatly improved my Mini 9's performance.

---

### Post by ghindo on 2009-04-02
UXA has definitely improved performance for me.  There have been a few lock-ups, but I'm unsure if they were caused by UXA.```
michael@ubuntu:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
```

---

### Post by SnickerSnack on 2009-04-02
My thinkpad x61 should arrive tomorrow and I should have time to put ubuntu on it next weekend.  From this thread it seems like I should install hardy.  Or did I misread?

@zorkerz: If you can offer any advice for putting ubuntu on an x61, I'd appreciate a pm.  I've been to thinkwiki.org, but you might have discovered some things that aren't there.

---

### Post by crjackson on 2009-04-02
> **SnickerSnack said:**
> My thinkpad x61 should arrive tomorrow and I should have time to put ubuntu on it next weekend.  From this thread it seems like I should install hardy.  Or did I misread?

@zorkerz: If you can offer any advice for putting ubuntu on an x61, I'd appreciate a pm.  I've been to thinkwiki.org, but you might have discovered some things that aren't there.

It's hard to say. Try them both and keep the one that works best. I'm running Hardy on an HP with the same X3100 and it's fine. I do expect to upgrade to Jaunty with little or no issues based on how the A6 LiveCD performed.

---

### Post by psyke83 on 2009-04-02
> **psyke83 said:**
> For those of you suffering from performance problems (even with UXA), I recommend you try EXA with "optimized migration". It's not enabled by default due to some minor corruption issues, but it's worth a try anyway.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"exa"
	Option		"EXAOptimizeMigration"		"true"
EndSection
```

An update on my previous post: I'm testing packages from [these]("https://launchpad.net/~xorg-edgers/+archive/ppa") [repositories]("https://launchpad.net/~tjaalton/+archive/ppa") and I'm experiencing better stability and (subjective) performance with UXA so far. My configuration is simply:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
EndSection
```

Hopefully the performance issues with Intel cards will be resolved in time for the final release!

P.S. Don't bother testing unless you know how to downgrade packages from the command line, as there's a chance of breaking X... ;)

---

### Post by crjackson on 2009-04-03
> **psyke83 said:**
> An update on my previous post: I'm testing packages from [these]("https://launchpad.net/~xorg-edgers/+archive/ppa") [repositories]("https://launchpad.net/~tjaalton/+archive/ppa") and I'm experiencing better stability and (subjective) performance with UXA so far. My configuration is simply:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
EndSection
```

Hopefully the performance issues with Intel cards will be resolved in time for the final release!

P.S. Don't bother testing unless you know how to downgrade packages from the command line, as there's a chance of breaking X... ;)

Hopefully but I won't hold my breath. As long is it's usable in a non-annoying way I'll be upgrading.

---

### Post by Kareeser on 2009-04-03
> **SnickerSnack said:**
> My thinkpad x61 should arrive tomorrow and I should have time to put ubuntu on it next weekend.  From this thread it seems like I should install hardy.  Or did I misread?

@zorkerz: If you can offer any advice for putting ubuntu on an x61, I'd appreciate a pm.  I've been to thinkwiki.org, but you might have discovered some things that aren't there.

I'd just go with Intrepid or Jaunty, if only for the newer kernel and up-to-date packages.

For some people, getting the best performance out of their cards is top priority, but I personally can't tell the difference between 60 fps (UXA-enabled) and 700 fps (UXA-disabled).

If you were gaming, this method of acceleration would be applicable, but it is not. Your call!

---

### Post by biji on 2009-04-03
For me.. jaunty is better... using UXA
see my thread and post your result: [http://ubuntuforums.org/showthread.php?t=1108866](http://ubuntuforums.org/showthread.php?t=1108866)
thanks

---

### Post by klange on 2009-04-03
New Mesa was just uploaded. It fixes the transparency issues in UXA/DRI2, and a bunch of other stuff. Quite nice.

---

### Post by zevans on 2009-04-03
> **klange said:**
> New Mesa was just uploaded. It fixes the transparency issues in UXA/DRI2, and a bunch of other stuff. Quite nice.

Yeah, it fixed a bunch of stuff for me too. :D Unfortunately everything REALLY only works properly with 2.6.29git8 for me, and there's no way that will be in the release of Jaunty...

---

### Post by densou on 2009-04-03
> **psyke83 said:**
> For those of you suffering from performance problems (even with UXA), I recommend you try EXA with "optimized migration". It's not enabled by default due to some minor corruption issues, but it's worth a try anyway.

I'll try that. :p

Jaunty is good so far (since Gutsy) for this desktop, however I felt it lacks something compared to FC11 Beta regarding mere performance. (FC11 Beta contains out-of-the-box: Linux 2.6.29, Gnome 2.25.90, Compiz 0.7.8, Mesa 7.4 + Xserver 1.6) 

I have updated Jaunty today, so I have seen the availability of Mesa 7.4 ! Compiz runs a bit better, however not so smooth as I saw on FC11. Perhaps a good comparison might be made when Canonical'll say: '2.6.29 is ready for Jaunty' (I hope they'd consider to skip it and concentrate to .30 instead, imo)

---

### Post by Jay_Bee on 2009-04-04
> **klange said:**
> New Mesa was just uploaded. It fixes the transparency issues in UXA/DRI2, and a bunch of other stuff. Quite nice.

Yeah! Now's the time to party, DRI2, here I come! \\:D/:KS

---

### Post by goodrench on 2009-04-04
I have edited my xorg.conf to look like this.

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod" "EXA"
	Option		"EXAOptimizeMigration"	"true"
	Option		"DRI2"	"true"
EndSection

```
"UXA" gave me a black screen and it appeared that the monitor was not even powered up.
Immediatly switched back to "EXA"
I have tried glxgears and it only gives me 190.?? fps at best. I have read some people reporting 2000 fps. wow!
glxgears also gives me an error "Failed to initialize GEM.  Falling back to classic"
I am not even sure if dri2 is enabled. Is there any more diagnostics for gem or dri2 or xorg in general?
I am using jaunty with all updates as of 8:50 April 4 '09.
Scrolling in firefox is jittery but scrolling in synaptic is absolutely painfull.
Video seems not too bad but flash is still a hog.( not sure if that is related)
Spinning the cube is hit and miss. Sometime last week the cube was incredibly fast and used absolutely no processing power.
Now it is slow and jittery and the landscape background may or may not show up while spinning the cube.


```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

---

### Post by Amaranth on 2009-04-05
DRI2 (and GEM) only work if you enable UXA.

---

### Post by goodrench on 2009-04-05
> **Amaranth said:**
> DRI2 (and GEM) only work if you enable UXA.

In xorg.conf???

---

### Post by TrueTom on 2009-04-05
> **goodrench said:**
> In xorg.conf???

Yes, something like:

```
Section "Device"
	Identifier	"intel"
	Driver 		"intel"
	Option          "AccelMethod" "UXA"
EndSection
```

---

### Post by scaine on 2009-04-06
Here's the WIKI entry :
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

And if you find that you don't actually have an xorg.conf, you can run this command to generate one (from Tich's post in [this thread]("http://ubuntuforums.org/showpost.php?p=6838965&postcount=62")) :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Asham on 2009-04-06
Sorry, didn't read through all 7 pages, but my question is how do I see the current active gfx drivers?

```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)

```

---

### Post by tjeremiah on 2009-04-08
there has to be a winning formula somewhere. I tired all the xconfg people here recommended and still have screen tearing. Still waiting for the april 23.

---

### Post by andrewabc on 2009-04-08
> **tjeremiah said:**
> there has to be a winning formula somewhere. I tired all the xconfg people here recommended and still have screen tearing. Still waiting for the april 23.

You could try the release candidate when it is released on April 16, a week before final.

---

### Post by DizzyTech on 2009-04-08
I'm very upset with Jaunty, right now... Xorg, running on my GMA X3100, randomly crashes leaving me only with a moving mouse and nothing else.  Ooh, what fun!  :mad:

---

### Post by mabovo on 2009-04-08
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

With UXA enabled and today updates (9.04-2009), 
Planetpenguim running smoothly
glxgears almost double fps
Moving window gears don't leave track shadows on display.
No sign of frozen X !


MacBook2,1

---

### Post by crjackson on 2009-04-08
> **mabovo said:**
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

With UXA enabled and today updates (9.04-2009), 
Planetpenguim running smoothly
glxgears almost double fps
Moving window gears don't leave track shadows on display.
No sign of frozen X !


MacBook2,1

SWEET!!! Looks like it will be good to go by release... :guitar:

---

### Post by serezha on 2009-04-13
Hi. I installed Kubuntu 9.04 from scratch on Lenovo T61 with Intel GMA X3100 and 3GB of main memory.
```

lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

```

```

lshw -class display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```

Intel driver seems to be installed: 
```

sudo apt-get install xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg-video-intel is already the newest version.

```
 
After installation xorg.conf was almost empty. I added the line:
```
Driver          "intel"
```
Xorg.0.log does not have any errors.
I don't have any crashes so far, but the graphics is extremely slow! I am not talking about any fancy effects, I turned them off. Simply moving things around, resizing windows, switching windows takes a long time. I've never had such a slow desktop.
Here is what the top shows when I am resizing konsole window:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7033 root      20   0  871m 444m  57m R   71 15.0  35:07.24 Xorg

```
X uses lots of memory, and lots of  CPU, but everything is very slow. Every mouse movement I do with the mouse takes effect a second or two later. Intellj IDEA (Java Swing) is, surprisingly, the only application that is responsive.

---

### Post by biji on 2009-04-13
you should try uxa, see this [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

---

### Post by serezha on 2009-04-13
> **biji said:**
> you should try uxa, see this [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
I am trying it right now. From Xorg.0.log:
```
(**) intel(0): Using UXA for acceleration

```

No difference, It may even worse than was before.

---

### Post by Starks on 2009-04-13
Anyone here having problems with fullscreen?

---

### Post by zorkerz on 2009-04-13
Fullscreen what?

When I put openoffice full screen it flickers alot, so that I can see an empty desktop behind (no icons or panels), only the mouse does not flicker. Ive been meaning to file a bug but have not gotten to it.

---

### Post by Starks on 2009-04-13
I see bands of color whenever I play fullscreen games.

---

### Post by tjeremiah on 2009-04-13
Maybe its compiz. I was having the same problem with fullscreen flickering until I went to compiz manager > general option >  unchecked "Unredirect Fullscreen Windows."

---

### Post by Starks on 2009-04-13
Anyone get this when playing games?

[http://img102.imageshack.us/img102/9808/0413091216a.jpg](http://img102.imageshack.us/img102/9808/0413091216a.jpg)

---

### Post by darrenn on 2009-04-13
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

It's fixed! Excellent now I can get a partition ready for a jaunty install.

---

### Post by crjackson on 2009-04-13
> **darrenn said:**
> It's fixed! Excellent now I can get a partition ready for a jaunty install.

Are you saying it was fixed by following some particular method found in this thread? Or was it fixed by Ubuntu updates?

Please elaborate...

---

### Post by tjeremiah on 2009-04-14
> **crjackson said:**
> Are you saying it was fixed by following some particular method found in this thread? Or was it fixed by Ubuntu updates?

Please elaborate...

wondering the same...

---

### Post by darrenn on 2009-04-14
> wondering the same... 

It was a update that fixed it. I don't bother to try and fix something unless it's past the release date.

---

### Post by geekygirl on 2009-04-14
> **keypox said:**
> I just installed 9.04 beta on my laptop.  It runs like crap on gma 4500. Intrepid ran way way better.  But did have tearing in videos.  But i have never seen a ubuntu install without video tearing.

I hope they fix it

I had the same concerns initially with my laptop (Vaio TT with an Intel 4500MHD) - Live CD of the beta runs really well, carry out the install, no problems, and do an update...BIG issues!

Firstly I had to remove compiz and compiz-core to get past the GDM login screen in recovery mode at boot up....then it would work nice..

But there is no accelerated graphics, nothing, and a fair bit of tearing from just moving an open window across the screen *cry*

I was about to return to Intrepid at this point - as others have stated it runs really well on the Intel 4500!...

Peserverance and a read through of this thread and the X/UXA Testing page saw me enable UXA in xorg.conf, re-install compiz and compiz-core...and viola!...a very quick and snappy install of Jaunty...

Now I must say that this has been the most troublesome beta I have ever had a play with since Breezy Badger and Edgy on different machines - I HOPE this is sorted prior to the release date otherwise there will be some rather annoyed laptop owners out there me thinks if they have to muck around and do that just to get it to run (its not hard, but some people might find the recovery console daunting :p)

Otherwise I can now honestly say I am thus far pleased with my current Jaunty install....

---

### Post by InfernalNeutrino on 2009-04-14
I have the following on a Sony Vaio SZ430N:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


Before moving to the Xubuntu 9.04 beta this morning I ran 8.10 with no noticeable performance issues. After the upgrade I had rather severe issues with the desktop responsiveness, particularly noticeable when scrolling through text (i.e. surfing these forums or even looking at code in vim). Switching between desktops rapidly caused momentary hangs. Generic bad news lol. However, on the suggestion of this thread I edited my xorg.conf to have this:

> 
Section "Device"
	Identifier	"Configured Video Device"
        Option      "AccelMethod"            "exa"
        Option      "EXAOptimizeMigration"   "true"
EndSection


And all the issues went away. I haven't thoroughly tested everything, but so far I have yet to run into any problems (either performance or stability). Cheers!

---

### Post by tjeremiah on 2009-04-14
well, i created a bug report. Basically the screen tearing. Please comment on the bug. I figure the more people, the quicker it can get resolved : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359124)

---

### Post by geekygirl on 2009-04-15
Nice work - added my comments about my Intel experience with Jaunty to the bug - hopefully this can get sorted prior to release...

---

### Post by meanimal on 2009-04-17
i was running Intrepid until today.

in intrepid i had pretty good performance by default (running EXA i would assume...) however there was pretty bad tearing (depending on how much you notice these things)

one way of completely working around it was documented here:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318)

(basically disabling textured video, has other side effects)

oh p.s. above options in Xorg will only work for you if running intrepid AND you have enabled proposed packages in your apt/synaptic repository settings.

this option does not appear to work for me now in jaunty.  not sure why as above bug report states it does.

---

### Post by goodrench on 2009-04-17
This procedure does not work while running under the server kernel. As soon as I rebooted into the generic kernel, everything worked very well. Now it is a question of what I want to perform better? My processor or my graphics card?
Hmmmmm.....

---

### Post by densou on 2009-04-18
I dunno if EXAOptimizeMigration was a real or fake myth however it didn't work at all when I tried it.

Few days ago, after I read Jaunty RC's release notes I discovered an odd paragraph: 
*_Some_ users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.*

I gained 6-7% under EXA (UXA works already well and it's nearly God-like on this GMA950) using that. :o :popcorn:
I wonder if you could obtain the same result, let me know :D




P.S. why did I read on every release notes (not Jaunty only), "if you desire to enable Ctrl+Alt+Backspace again for restarting X, add ...." instead of "AltGr+Print+K replaced Ctrl+Alt+Backspace for restarting X" :confused:

---

### Post by goodrench on 2009-04-20
> **goodrench said:**
> This procedure does not work while running under the server kernel. As soon as I rebooted into the generic kernel, everything worked very well. Now it is a question of what I want to perform better? My processor or my graphics card?
Hmmmmm.....



compiz and 3d effects are gone completely now. I cannot enable them from the Appearance menu.
Any Ideas? I have tried going back to original xorg.conf and still nothing. I have tried server kernel as well as generic.

---

### Post by goodrench on 2009-04-20
> **goodrench said:**
> compiz and 3d effects are gone completely now. I cannot enable them from the Appearance menu.
Any Ideas? I have tried going back to original xorg.conf and still nothing. I have tried server kernel as well as generic.

Just launched fusion icon. Selected "Reload Window Manager" and all is good.
Very Strange.

---

### Post by tjeremiah on 2009-04-20
fushion icon? Where is that located?

---

### Post by jblackhall on 2009-04-20
> **goodrench said:**
> compiz and 3d effects are gone completely now. I cannot enable them from the Appearance menu.
Any Ideas? I have tried going back to original xorg.conf and still nothing. I have tried server kernel as well as generic.

The Intel cards have been blacklisted until this bug is resolved: [https://bugs.launchpad.net/bugs/359392](https://bugs.launchpad.net/bugs/359392) To get compiz working, you'll either need to unblacklist the card or wait for the bug to be resolved.  As of right now since they blacklisted it a few days ago, you should have no 3D support.

---

### Post by stewacide on 2009-04-20
I'm gonna' stick with the Intrepid drivers until UXA+2.6.30 is further along (which I hope will help with Flash video performance, my one gripe about Intrepid graphics)

Obviously we're all very grateful to the work that goes into Intel's drivers, but you'd think they'd be in a better state given Atom+GMA+Linux netbooks and nettops are the one growth segment in the PC industry these days.

edit -- Took the plunge and installed 2.6.30 and UXA works perfectly now! Would highly recommend to all GMA users!!

---

### Post by goodrench on 2009-04-20
> **tjeremiah said:**
> fushion icon? Where is that located?

compiz fusion icon.
it is in the repositories
```

sudo apt-get install fusion-icon
```

---

