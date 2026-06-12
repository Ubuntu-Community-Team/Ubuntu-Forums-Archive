---
title: "Gutsy issues - mostly resolved but more of a rant on pains"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by xanas3712 on 2007-09-25
Well, I'm sure this is a common post but let me breakdown some issues I had with gutsy.

Please note the following:
1) I have installed prior versions of ubuntu
2) I realize gutsy is pre-release (but close to release)
3) I am a gentoo user for the most part, so I'm used to source based things and having to hack things a bit.

All of this said I was kind of annoyed installing gutsy today because I expected a little bit more of a smooth experience but ended up taking around 3 hours on it.

Why?

1) No splash screen?  For whatever reason, at least with my 8800 GTS and tribe 5 I got no splash screen. Because I didn't, I wasn't sure if the bootup sequence was working and I restarted a few times.  I tried various key combinations to see if I could get a text startup or whatever else, and finally just waited it out and sure enough it came up, but because it took so long I wasted time trying it a few times.  Even after install I had this issue, and I'm still not sure if I can do the normal boot.  I keep going to recovery because at least there i get a text boot that I can do something with (even if I have to start gdm manually, but I am certainly capable of that).

2) Driver issues - for some reason resricted still thinks that the 9600 series is an appropriate driver for my 8800 GTS.  After a year of the GTS being out (almost) I'd think this should be resolved by now.  That series of driver doesn't work with the 8800 (and probably none of the other 8000 series cards).  In any case due to this I had to search around a bit in synaptic for what I was looking for 

3) Ok, when I got what I needed in synaptic for the video card (the kernel 2.6.22-12 w/ nvidia-glx), I had a new problem that started with sound.  This issue was due to the fact that the 2.6.22 kernel didn't install my snd-hda-intel module (and I had forgotten the exact name of the module).  In any case I followed the guide and it didn't work quite right.  For some reason trying to build alsa manually from source failed to compile (even though I did have kernel headers, etc. installed).  Seemingly by chance, I noticed that apt-get was saying I could install alsa-base and alsa-modules for the new kernel (I'm not sure why it didn't upgrade this in the first place though when I first selected the kernel???) 

4) I noticed that totem w/ gstreamer is still default.  I don't know about anyone else but for me this video player is pretty bad.  It's not totem itself (which is just a front-end) but gstreamer.  Gstreamer will play x264 video but it plays very slowly.  I don't know why gstreamer is a default if it's performance is so horrible even on new cards and new processors?  I'd noticed in gentoo that some of the newer gstreamer versions seemed a bit better, but the version in gutsy that I just installed is still pretty jumpy.

Well so there it is, sorry for the rant but I hope some of my comments might prove a little useful.  The guides, etc. on the forums were useful (thanks!) but I just wish I didn't have to read all of them to get what I wanted because I was expecting (for a late release on relatively standard hardware) a little smoother ride than I got.  

Nevertheless once it's running ubuntu is still cool and all, or I wouldn't bother trying it from time to time again.  Hopefully some of the install issues will be fixed down the line and hardware will get better support.

---

### Post by Pumalite on 2007-09-25
Run these commands:

sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose the default settings for everything except:
1. For the video driver, select nvidia (you might have to scroll up or down to find it).
2. For screen resolutions, select all of them. (Don't worry, it will only allow the ones that your card can provide).
3. Choose "Advanced" options near the end, and then continue to choose all defaults.

Then:
sudo reboot

---

### Post by xanas3712 on 2007-09-25
> **Pumalite said:**
> Run these commands:

sudo apt-get install nvidia-glx-new
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose the default settings for everything except:
1. For the video driver, select nvidia (you might have to scroll up or down to find it).
2. For screen resolutions, select all of them. (Don't worry, it will only allow the ones that your card can provide).
3. Choose "Advanced" options near the end, and then continue to choose all defaults.

Then:
sudo reboot

Yeah I know this now (or are you just saying this for those who might read here since I brought it up?) 

In any case I actually chose to use synaptic instead of the console to install all the stuff.  I'm not familiar with package names and such since this is all different for every distro.  My issue was more with the fact that the automatic restricted drivers thing (a good idea I think) doesn't really get you the right things as I think it really should by now if they are going to keep it in, that and the fact that once I did install it I didn't have sound modules anymore.

---

### Post by Pumalite on 2007-09-25
'I'm not familiar with package names and such since this is all different for every distro.'

You shouldn't be fooling around with Gutsy then. It's in testing. Wait for stable in October.

---

### Post by xanas3712 on 2007-09-26
October is 5 days lol, and I don't think the package name issue would be different then.  In any case things didn't work as they are supposed to work (in my opinion of course) and I was just stating that.  I shouldn't have had to go to synaptic or read the forum to get fairly standard hardware working. 

It should have simply been a matter of using the restricted driver wizard it already has, but that doesn't work since it still offers the driver that doesn't work with the 8000 series.  I doubt this will get fixed by release.  It's been a year since this was an issue and I'm guessing it's just not a priority, hence my mention of it. (please note it has gotten better, a year ago there was no nvidia-glx-new)

You may think that people should know synaptic/apt well enough to find what they need (which I did by the way, before you ever even posted) but I think while it's something I was able to do it's a hold up for new users.  I'm familiar with linux, but others who are not would have been frustrated by the multiple issues I brought up; no splash screen making them unable to see progress in boot, especially when combined with the particularly slow cd boot times, drivers not being installed correctly for their card with the wizard designed to help them.   And then there is the problem with gstreamer, which I think most would prefer the default video backend be xine.  Why? Because xine is not jumpy and gstreamer is.

---

### Post by eentonig on 2007-09-26
Did you file bug reports? 

Don't complain about pre-release software. Help solve the issue by following the established ways of communicating issues. Screaming on a forum how something under development doesn't work, isn't going to solve the issue.

If these were Feisty problems, I would agree with you that this is a problem. But Gutsy not being released yet, I fail to see why this should be posted under installation and upgrades.

---

### Post by xanas3712 on 2007-09-26
.. accidental dupe post..

---

### Post by xanas3712 on 2007-09-26
> 
Did you file bug reports?


No, I actually don't know where to do this though(basic google search didn't get me to it sadly).  As far as the forum I chose to post in I didn't see one that is gutsy specific (perhaps hidden in sub forums I can't see???) 

> 
Don't complain about pre-release software. Help solve the issue by following the established ways of communicating issues. Screaming on a forum how something under development doesn't work, isn't going to solve the issue.

Who is screaming?  I said these are issues, and that's all.  As far as "don't complain" goes speak for yourself.  I complain about whatever bothers me.  If I don't like it I'm going to complain, you can tell me not to all you like or what your opinions are on matters concerning pre-release software.  I don't care if it's pre-release or not, if something doesn't work as expected I'm going to say so.  If I knew of a better place to post I would post there, sadly at this time I'm not really sure where that is.  I'll look harder though.

> 
If these were Feisty problems, I would agree with you that this is a problem. But Gutsy not being released yet, I fail to see why this should be posted under installation and upgrades.

The splash screen is not a feisty problem, but the other 2 issues I mentioned ARE feisty problems which is exactly why I was checking out gutsy to see if they might have fixed some things.  Sadly, that answer is no to my particular issues.

All of this said I have another issue now.  I imagine this is due to gutsy being a pre-release so I can handle it happening but I'm still going to "complain" about it because I don't think it should occur.   The problem I'm having now is that some update broke networking and now /etc/init.d/networking start doesn't do anything (it says ignoring interfaces eth0).  I managed to get networking up (the driver/module is loaded) because I was able to ifconfig eth0 -broadcast 192.168.0.100 and route add default gw 192.168.0.1 , but I personally don't think it makes sense to allow publically available (even if it is pre-release) software to break to that degree.  That said, everyones opinions on what should and should not constitute beta/alpha are very different.  I use firefox betas/alphas with few issues generally (and not any major game-breaking ones)

The no splash thing appears to be something worse than I thought.  On restarting I can't get the system to get past the black screen.  So I HAVE to use recovery mode.

---

### Post by andrew.46 on 2007-09-29
Hi,

> **xanas3712 said:**
> No, I actually don't know where to do this though(basic google search didn't get me to it sadly).  As far as the forum I chose to post in I didn't see one that is gutsy specific (perhaps hidden in sub forums I can't see???) 

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Is the place and they are a good lot :-)

                Andrew

---

### Post by ptn107 on 2007-09-29
I did a quick 'update-manager -d' at the terminal and voila! Gutsy 7.10 beta no hitches or glitches!

---

