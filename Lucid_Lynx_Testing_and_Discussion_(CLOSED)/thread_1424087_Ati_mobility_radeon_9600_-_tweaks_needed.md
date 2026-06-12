---
title: "Ati mobility radeon 9600 - tweaks needed"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-03-07
Okay here's the deal.  Out of the box, every Ubuntu distro. after Hardy has performed poorly with this video card until some tweaks to the xorg.conf were made.  This is what worked good for Jaunty & Karmic:

Section "Device"
Identifier     "Configured Video Device"
Option         "AccelDFS"                     "on"
Option         "AccelMethod"                  "XAA"
Option         "MigrationHeuristic"           "smart" # "greedy" works well also
Option         "EnablePageFlip"               "on"
Option         "EnableDepthMoves"             "on"
Option         "ColorTiling"                  "on"
Option         "FBTexPercent"                 "0"
Option         "RenderAccel"                  "on"
EndSection


Now, if my make an empty file, and paste this into the file I get a black screen on 1st boot.  Then 2nd boot works fine, but the tweaks seem to have no effect at all.

With or without the tweaks, I'm getting a black screen on some 3D games that work perfectly in Jaunty & Karmic.

Any suggestions would be appreciated.

---

### Post by lidex on 2010-03-07
What driver are you using?

Take a look at the configuring Xorg section of this page:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Rob2687 on 2010-03-07
KMS is enabled by default on Lucid so some of those options may not work or apply to the drivers anymore.

---

### Post by crjackson on 2010-03-07
> **lidex said:**
> What driver are you using?

Take a look at the configuring Xorg section of this page:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

```
charles@emachines-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
charles@emachines-laptop:~$ 
```

Currently installed driver:
[B]libgl1-mesa-glx
libgl1-mesa-dri[/B]

Since there is no xorg.conf by default I'll need to build one.  Isn't there a command that will generate a working file for me to edit as needed?

---

### Post by lidex on 2010-03-08
> **crjackson said:**
> ```
charles@emachines-laptop:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
charles@emachines-laptop:~$ 
```

Currently installed driver:
[B]libgl1-mesa-glx
libgl1-mesa-dri[/B]

Since there is no xorg.conf by default I'll need to build one.  Isn't there a command that will generate a working file for me to edit as needed?

Seriously dude, this is cool - check it out:
[http://ubuntuforums.org/showthread.php?t=1401835]("http://ubuntuforums.org/showthread.php?t=1401835")

---

### Post by krazyd on 2010-03-08
Hello crjackson.

Some of these options are set by default, so having them in xorg.conf is redundant:
> **crjackson said:**
> 
Option         "AccelDFS"                     "on"
Option         "RenderAccel"                  "on"


For the others:
> **crjackson said:**
> Option         "AccelMethod"                  "XAA"
This is the older acceleration method. EXA (default) should give better performance (you may find otherwise, though the lucid xserver should have solid EXA).

> **crjackson said:**
> Option         "MigrationHeuristic"           "smart" # "greedy" works well also
> ( from 2008: [http://www.botchco.com/agd5f/?p=28](http://www.botchco.com/agd5f/?p=28) )
If you have a “MigrationHeuristic” option in your configuration, remove it.  That option was a workaround that basically disabled acceleration to work around the lack of EXA composite support in the drivers and poor performance in the EXA core.  These have both been largely addressed in the drivers and xserver git.  To reach this wonderland, you’ll need the radeon driver (xf86-video-ati) from git and the xserver from git for optimal performance.

My advice would be to test the performance with *no* xorg.conf (delete it entirely and rely on the defaults). If you find this performance unsatisfactory, try playing with these other options.
> **crjackson said:**
> 
Option         "EnablePageFlip"               "on"
Option         "EnableDepthMoves"             "on"
Option         "ColorTiling"                  "on"
Option         "FBTexPercent"                 "0"


---

### Post by james_xxx on 2010-04-20
Crjackson,

I would be curious to know how things are going for you in creating a working xorg.conf for the Radeon 9600.

I am using a AGP Radeon 9600 in a desktop at work, and had a very rough time with it in Karmic. Using the video adapter would often cause the PC to lock up, until I found a working xorg config (which I believe was the same or very similar to yours).

I am running Lucid, with an abbreviated xorg.conf, based on the info provided by krazyd. The card's performance now is OK, but I have a feeling it could be a bit better. In particular, it seems like the GUI is using up a few too many CPU resources at the moment.

If you have found anything that seems to be working for you, I would be glad to hear about it!

---

### Post by psyke83 on 2010-04-20
A little run-down of some of the options you added:

> Option         "AccelDFS"                     "on" - *this enables an extra EXA performance enhancement, but has potential for instability.*

Option         "AccelMethod"                  "XAA" -* this enables the old XAA acceleration method. XAA is deprecated, and has render acceleration disabled by default due to instability.*

Option         "MigrationHeuristic"           "smart" # "greedy" works well also - *this should no longer be necessary; see below.*

Option         "FBTexPercent"                 "0" - *this causes the driver to allocate all pixmaps for EXA and leave only GART memory for OpenGL. Probably not a good idea and will slow down 3D operations.*

Option         "RenderAccel"                  "on" -* this is already the default (except with XAA on recent drivers, though XAA acceleration is disabled because it is unstable).*
As for the *MigrationHeuristic* option, there used to be a major performance issues for many users with the default setting (*smart*), and it was patched to use the *greedy* algorithm instead. A better fix was to leave the migration heuristic to its default, and enable a semi-documented option called *ExaOptimizeMigration*. As far as I can tell, recent drivers already use this option by default... so, there's nothing to do.

Almost all of the options you specified were EXA tweaks, which subsequently got overriden when you enabled the older XAA rendering. The morale of the story is - don't apply tweaks you find on the internet without doing some research yourself.

Let me suggest an alternative approach - delete your (badly-customized) xorg.conf file - most of it was useless. Instead, disable KMS (by adding the boot option* radeon.modeset=0* to your GRUB configuration). Most benchmarks are showing regressions in radeon KMS (and therefore DRI2) performance, so try the non-KMS (and DRI1) mode to see if it's any better.

In my case, my old integrated graphics (Radeon IGP 345M, which is a R100-based card) is very slow with DRI2 -for example, when scrolling a page with compiz enabled, there is noticeable delay. However, performance is acceptable with DRI1 - i.e., with KMS disabled.

---

### Post by james_xxx on 2010-04-20
Psyke83,

I think you **very** badly misread my post. Please read it again, as well as the previous post by krazyd.

Of the options you listed, 'FBTexPercent' was the only one I have attempted to use in Lucid. Thank you for your input on that one. I have now commented that line out. 

krazyd had already indicated the others should be removed. 

In Karmic, I do not believe that this was a bad customization. It was the only Xorg config I tried that would even work with this card, and I tried many. In Karmic it worked very well, although it was obvious to some of us that this would not be the case in Lucid, hence this thread.

To be honest, I will have to become much more desperate to consider disabling KMS. Out of the box, i.e. without and xorg.conf file, this card works much better than it did in Karmic out of the box.

---

### Post by crjackson on 2010-04-20
> **psyke83 said:**
>  The morale of the story is - don't apply tweaks you find on the internet without doing some research yourself.

Okay, the research I did was to search the Ubuntu forums.  This is where I got the information the 1st time, and it worked absolutely great for me on Jaunty & Karmic.

> **psyke83 said:**
> Let me suggest an alternative approach - delete your (badly-customized) xorg.conf file - most of it was useless.

I thought I mentioned that's what I did.  It was useless in Lucid. No matter how "badly-customized" it appears to you, it solved all my video related issues in J & K.

> **psyke83 said:**
> Instead, disable KMS (by adding the boot option* radeon.modeset=0* to your GRUB configuration). Most benchmarks are showing regressions in radeon KMS (and therefore DRI2) performance, so try the non-KMS (and DRI1) mode to see if it's any better.

This is the kind of information I was looking for. I already discovered the previous settings were useless IN LUCID.  That's why I posted here looking for help.

The LCD on that computer died so it doesn't matter for me right now.

---

### Post by crjackson on 2010-04-20
> **krazyd said:**
> Hello crjackson.

Some of these options are set by default, so having them in xorg.conf is redundant:


For the others:

This is the older acceleration method. EXA (default) should give better performance (you may find otherwise, though the lucid xserver should have solid EXA).




My advice would be to test the performance with *no* xorg.conf (delete it entirely and rely on the defaults). If you find this performance unsatisfactory, try playing with these other options.

Thanks for replying.  I find your post both HELPFUL and POLITE.

---

### Post by crjackson on 2010-04-20
> **lidex said:**
> Seriously dude, this is cool - check it out:
[http://ubuntuforums.org/showthread.php?t=1401835]("http://ubuntuforums.org/showthread.php?t=1401835")

Thanks.  That is a great read.

---

### Post by crjackson on 2010-04-20
> **james_xxx said:**
> Crjackson,

I would be curious to know how things are going for you in creating a working xorg.conf for the Radeon 9600.

I am using a AGP Radeon 9600 in a desktop at work, and had a very rough time with it in Karmic. Using the video adapter would often cause the PC to lock up, until I found a working xorg config (which I believe was the same or very similar to yours).

I am running Lucid, with an abbreviated xorg.conf, based on the info provided by krazyd. The card's performance now is OK, but I have a feeling it could be a bit better. In particular, it seems like the GUI is using up a few too many CPU resources at the moment.

If you have found anything that seems to be working for you, I would be glad to hear about it!

My LCD on that laptop has died, and I haven't fixed it yet so I don't really know.  Sorry.

---

### Post by psyke83 on 2010-04-20
> **james_xxx said:**
> Psyke83,

I think you **very** badly misread my post. Please read it again, as well as the previous post by krazyd.

My apologies for the confusion, but I wasn't replying to krazyd or yourself - it was a reply to the original post by crjackson. In fact, if I had seen krazyd's post before replying myself, I would have had a lot less to write ;).

The post from krazyd is very informative, though it's slightly inaccurate: render acceleration is disabled on XAA by default (at least on the newest ATI driver, as you can see from [this commit]("http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=5c256808cb5fea955eea96ffe9196473715156aa")), and DFS acceleration is disabled on some configurations due to potential reliability issues. Forcing these options to be enabled may have detrimental effects (but that's ok, since krazyd is indirectly suggesting to remove the lines from the configuration anyway).

You can see more detail on all those options from:
```
$ man radeon
```By the way, if you do try to disable KMS and see a performance boost, let us know.

---

### Post by psyke83 on 2010-04-20
> **crjackson said:**
> Okay, the research I did was to search the Ubuntu forums.  This is where I got the information the 1st time, and it worked absolutely great for me on Jaunty & Karmic.

I had problems with performance as well (in the case of Intel graphics, it was a problem with the driver versions shipped with Jaunty, which was resolved in Karmic - more or less).

As for the radeon driver, I found performance was quite bad in Karmic as  well.  Of all the options you listed in your xorg.conf, I believe that setting  "MigrationHeuristic" "greedy" would have resolved your problem in Karmic. However, the "ExaOptimizeMigration" option would have been a better alternative (greedy migration effectively disables acceleration, as krazyd explained).

In Lucid, I don't need *any *tweaks to my xorg.conf, but I do need to disable KMS or else I notice very slow 2D/3D performance (such as laggy scrolling in compiz). My conclusion is that *EXA+KMS* (which uses DRI2) has a problem on my card, but *EXA+no KMS* (which uses DRI1) works perfectly.

> I thought I mentioned that's what I did.  It was useless in Lucid. No matter how "badly-customized" it appears to you, it solved all my video related issues in J & K.My apologies if you took offense, but I was not being critical of you. I was being critical of the misinformation around (especially on the forums). The settings were a hodge-podge that showed no understanding of what they meant - half of the settings were EXA tweaks, and setting XAA acceleration was overriding them.

> This is the kind of information I was looking for. I already discovered the previous settings were useless IN LUCID.  That's why I posted here looking for help.The configuration you used was helping because it was enabling XAA acceleration - which in many cases was faster than EXA with older Xorg/drivers. The problem is that XAA is deprecated, [buggy]("http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/commit/?id=5c256808cb5fea955eea96ffe9196473715156aa") and no longer developed, and there may be regressions in its performance - especially considering that the majority of development effort is concentrated on DRI2/KMS/EXA.

---

### Post by james_xxx on 2010-04-20
psyke83,

I did not have a chance until now to restart X after removing the line pertaining to 'FBTexPercent' in xorg.conf. I just wanted to report back that I do believe this change improved performance. Many thanks!

This Radeon 9600 adapter now seems to be working very well. I am using Kubuntu along with a nice, Apple-branded monitor. The resolution is set to 1680x1050, and Kwin's desktop effects are enabled.

Here is my present xorg.conf:
```
Section "Device"
Identifier      "Configured Video Device"
Driver  "radeon"
Option  "AccelMethod"           "EXA"
Option  "EnablePageFlip"        "on"
Option  "EnableDepthMoves"      "on"
Option  "ColorTiling"           "on"
Option  "AGPMode"               "4"
Option  "TripleBuffer"          "true"
EndSection
```

If there is anything else there that stands out as being just simply wrong, please let me know!

It is still my impression that at least something in this list of options is having a beneficial effect on overall performance, when compared to how things were before an xorg.conf was added. I may get a chance at some point to spend time testing this further.

---

### Post by james_xxx on 2010-04-20
Reporting back again...

Although using KMS along with the xorg.conf shown above at first seemed to be working well, I eventually started experiencing instability, with X crashing several times this afternoon.

I then nuked my xorg.conf, and tried again without it. Everything worked, but a system monitor on my desktop showed my CPU's cores continuously running at between %80 and %100 usage. Not what I was looking for.

This prompted me to finally try out psyke83's advice. I added 'radeon.modeset=0' to my boot arguments in /etc/default/grub (after 'GRUB_CMDLINE_LINUX_DEFAULT='), and so far things seem stable, with CPU usage indicated as being within much more of a normal range. 

Although things are still not *quite* as snappy as I had hoped, they are close enough. If things remain this stable, I will likely stay with this configuration.

P.S. psyke83, would experimenting with the driver from the Git repository be worthwhile in your opinion? Thanks!

---

### Post by psyke83 on 2010-04-20
> **james_xxx said:**
> Reporting back again...

Although using KMS along with the xorg.conf shown above at first seemed to be working well, I eventually started experiencing instability, with X crashing several times this afternoon.

I then nuked my xorg.conf, and tried again without it. Everything worked, but a system monitor on my desktop showed my CPU's cores continuously running at between %80 and %100 usage. Not what I was looking for.

This prompted me to finally try out psyke83's advice. I added 'radeon.modeset=0' to my boot arguments in /etc/default/grub (after 'GRUB_CMDLINE_LINUX_DEFAULT='), and so far things seem stable, with CPU usage indicated as being within much more of a normal range. 

Although things are still not *quite* as snappy as I had hoped, they are close enough. If things remain this stable, I will likely stay with this configuration.

P.S. psyke83, would experimenting with the driver from the Git repository be worthwhile in your opinion? Thanks!

Feel free to experiment with the options, but you should test them one at a time, and read their description from "man radeon". I recommend you try to tweak EXA performance, rather than reverting to XAA, however.

I don't recommend building from the git sources, as there is a more convenient option: [the xorg-edgers PPA]("https://launchpad.net/%7Exorg-edgers/+archive/ppa"). Be sure to read the description/warnings before proceeding (though it's quite easy to revert packages thanks to the ppa-purge script which is included in the repository).

Yet another variable to test is the kernel. Certain options in the radeon driver do not work with KMS enabled *unless *you are using kernel version 2.6.34 (which is still in RC status). You can get unofficial 2.6.34-rc5 builds [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc5-lucid/"). Just keep in mind that newer kernels are not officially supported by Canonical, and you may lose functionality of restricted drivers. If that's not a problem for you, then it's worth checking out.

I recommend that you start testing without an xorg.conf file, with KMS enabled, with the latest kernel and using the xorg-edgers packages. If you're still not satisfied, experiment with the driver options (the ones you quoted in your recent post look fine), then try disabling KMS. However, I believe that using the newer kernel will have no benefit to a non-KMS (i.e. DRI1) mode.

P.S. crjackson: you may want to give this as try as well.

---

### Post by james_xxx on 2010-04-20
OK, new configuration is apparently not working the best, either.

Just as I was about to log-out and go home, I had another X crash-and-burn.

I wasted a completely ridiculous amount of time trying to get this card to work adequately in Karmic, and I cannot do that again in Lucid. 

I will likely tinker a little bit longer, but I believe this card is going to just get pulled and probably replaced by an Nvidia card.

---

### Post by Longinus00 on 2010-04-20
Why not try it with no xorg.conf and see how that goes?

---

### Post by james_xxx on 2010-04-21
Since trying things with KMS disabled, and no xorg.conf, still caused X crashes, I finally restored what had been my most recently used xorg.conf.

I also added this option back to the configuration, as X seems to crash unless it's there:
```
Option  "FBTexPercent"          "0"

```

After making this change this morning, I have gone the rest of the day with a stable system, but with CPU usage often being higher than I would wish.

---

### Post by psyke83 on 2010-04-21
Take a look at the new sticky - it seems that the X server has a memory leak.

I recommend you try the proposed X server update, but you should revert all other changes you have made: re-enable KMS, remove/backup your xorg.conf, use the official kernel, and if you have already tested the xorg-edgers packages, revert them with the ppa-purge script.

---

### Post by Longinus00 on 2010-04-21
> **james_xxx said:**
> Since trying things with KMS disabled, and no xorg.conf, still caused X crashes, I finally restored what had been my most recently used xorg.conf.

I also added this option back to the configuration, as X seems to crash unless it's there:
```
Option  "FBTexPercent"          "0"

```

After making this change this morning, I have gone the rest of the day with a stable system, but with CPU usage often being higher than I would wish.

What kind of crashes?

Also, some of the settings in your xorg.conf are just the default value and some I'm not sure help at all. If you're so sure FBTexPercent is necessary why not just have an xorg.conf with only that value in it?

---

### Post by james_xxx on 2010-04-21
psyke83,

I have followed the instructions in the sticky, and will report back on how things have gone after a while.

Longinus00,

X has not been crashing the same way each time. Sometimes the graphics (especially text) start to appear malformed, then the screen goes black, finally returning me to KDM.

Sometimes the screen just goes black. When this happens, I ssh into this machine from another box and reboot, if possible. There have been a few times where it would be fairer to say that there had been a system crash, as networking and everything has gone down, and I am forced to hit the reset button.

---

### Post by james_xxx on 2010-04-22
Since following the instructions in the wiki that the sticky pointed to, and installing the ubuntu-x-swat Xorg, everything seems to be running perfectly here!

---

