---
title: "Artifacts and crashes with NVidia 185.x &amp; 190.x drivers"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2009-08-22
This morning, I was notified of a "partial upgrade" that was available. I clicked to accept and it installed ~24MiB of packages.

After it installed, it told me to reboot to complete the upgrade. Upon boot, it failed to get into X. As mentioned in another thread, this was due to a missing package, or something like that.

After properly installing the 185 driver, the computer did boot into X, but I was plagued with visual glitches, flickering, then a crash/automatic reboot.

I have tried the 173 drivers, but they don't compile with the Karmic kernel - apparently a patch is on the way to rectify that.

I have tried a PPA with the more "stable" 185.18.36 driver, and a 190.x driver. ALL exhibit the same behaviour.

I am running a Sony Vaio VGN-AR41E laptop with an NVidia 8400M GT video card.

It has been working in Jaunty, Intrepid and Karmic, until today's updated driver.

**Is anybody else experiencing this issue?** Only 173 and 185 are in the repository, so I can't downgrade to whatever I was using before this issue occurred.

---

### Post by cyberkilla on 2009-08-22
Bump;)

---

### Post by cariboo on 2009-08-22
If you haven't run apt-get clean lately, you should still have the previous driver in /var/cache/apt/archives. Your problem was caused by the partial upgrade, you are probably missing some dependencies. Partial upgrades have been a problem, if you wait for a day or two the dependencies may be satisfied.

Please don't bump until 24 hours has elapsed.

---

### Post by cyberkilla on 2009-08-23
> **cariboo907 said:**
> If you haven't run apt-get clean lately, you should still have the previous driver in /var/cache/apt/archives. Your problem was caused by the partial upgrade, you are probably missing some dependencies. Partial upgrades have been a problem, if you wait for a day or two the dependencies may be satisfied.

Please don't bump until 24 hours has elapsed.

Genius. Thanks for that. It seems that my last driver was *185.18.14*. I've installed it and I'm running Compiz with no issue.

Of course, I'm now nagged to do another "partial upgrade". I think I'll wait a week before braving the update manager again though.

With regards to these dependencies, have you any idea what the problem is? It seems odd that I could get 185.18.36 to boot into X, but suffer visual glitches (then crashing). I would have thought a missing dependency/file(s) would have resulted in something more abrupt, like the failure to execute at all. Utterly baffling.

---

### Post by cyberkilla on 2009-08-24
Is anybody else experiencing this issue?

Are there any clues as to if/when it is safe to upgrade to the 185.18.31/36 drivers that the update manager is peddling?

I have my 185.18.14 drivers working nicely still, but it would be nice to know if whether I'm the only one with this issue.

---

### Post by cyberkilla on 2009-08-25
Bump

---

### Post by cyberkilla on 2009-08-26
Bump.

Is anybody else having trouble with the NVidia drivers?

---

### Post by taavikko on 2009-08-26
> **cyberkilla said:**
> Bump.

Is anybody else having trouble with the NVidia drivers?

They're working correctly here...

G92 [GeForce 9800 GTX]
```
devil@core7:~$ dkms status
nvidia, 185.18.36, 2.6.31-6-generic, x86_64: installed
nvidia, 185.18.36, 2.6.31-7-generic, x86_64: installed
```

---

### Post by cyberkilla on 2009-08-26
> **taavikko said:**
> They're working correctly here...

G92 [GeForce 9800 GTX]
```
devil@core7:~$ dkms status
nvidia, 185.18.36, 2.6.31-6-generic, x86_64: installed
nvidia, 185.18.36, 2.6.31-7-generic, x86_64: installed
```

That's strange.

My card is older (GeForce 8400M GT), but it is on the list of supported ones. In addition, I can always get 185.18.14 to work for me, so it must be something about the new drivers.

I haven't a clue what the problem could be. It's not just artifacts though - it's more like the artifacts are created from pieces of the screen as it looked a few minutes earlier.

For instance, a notification bubble appeared, telling me I was connected to Wifi. A few minutes later, I dragged a gnome-terminal window and the image of the notification bubble was grafted rather crudely into the top-left of the screen.

The problem is hastened by triggering lots of repainting. Moving windows, making new ones, changing workspaces, etc, all make the problem occur more swiftly.

- I have tried the drivers with and without compiz.
- I have tried them with V-Sync disabled.
- I have monitored the card temp and it is fine. Usually 60-70C.
- The powermizer setting change appears to trigger a lot of the problems, but I have seen artifacts without that setting changing.
- The "Recovered GPU Errors" field in nvidia-settings will jump into the hundreds if I drag a window across the screen.

Personally, I don't think my system is misconfigured. I haven't done anything particularly "custom" with it, and since the old drivers work, it seems like a regression or some error in the packaging of the drivers.

I could probably test the drivers directly from NVidia, but they look like a pain to install. Besides, the ones in the Karmic repository will hopefully work reliably at the final release.

I would file a bug report, but I don't know what I'm filing against. I have been told to run a command, but I wouldn't have thought it would be very useful unless I ran it after the issue occurred (but that usually ends in a system reset).

Any suggestions? Ideally, ones to resolve the problem, rather than to just have me report it and let the problem fade away into obscurity:P
What baffles me is that nobody else is reporting the issue. Does nobody here have the same card as me? It's only coming up to ~2 years old.

---

### Post by cyberkilla on 2009-09-15
Bump.

I have still not found a resolution to this problem, aside from using old drivers. What is the problem? Does anybody know?

Is anybody else having this issue too?

Summary:
Karmic with 185.18.36 and 190.x.x cause artefacts then spontaneous rebooting on my laptop (Sony Vaio VGN-AR41E, NVidia 8400M GT).

Installing 185.18.14 drivers work, but they aren't in the repository (I found them in my package cache folder).

I have tried purging every package which matches "nvidia*", then reinstalling the latest driver - no change. The problem still exists.

I don't want to resort to reinstalling Ubuntu. Does anyone recognise this problem? Thanks in advance.

---

### Post by dabl on 2009-09-15
You might want to give the 190.32 Beta driver a try -- it is working fine here.

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

I recall seeing those "artifacts" -- bits of recent screens, on a previous card that I owned -- I think it was my 7900GS. And of course a prior driver version. Basically it is a "squirt" out of the card's video memory, when first booted and turned on. As far as I know it is benign, even if annoying.

---

### Post by djurny on 2009-09-15
i have experienced spontaneous reboots and suspend refusals ('spurious' irq complaint from nvidia kernel module) due to nvidia 190.25 and 190.32 (iirc).. reverting to 185.x solved those things (at least for me)..
nvidia 9400m & 8600gt

---

### Post by cyberkilla on 2009-09-15
Thank you both for responding.

I'm not keen on the strange "residual" image that sits in the frame buffer either. I have often wondered about that.

However, this is a much more annoying issue than that. I can get to the login screen (GDM). Often, if I do it carefully, I can get to my desktop too.

Unfortunately, once I start moving windows about, clicking buttons, or even just moving my mouse (although big changes to the screen make the issue appear more swiftly), strange horizontal artifacts appear, which are formed from pieces of the screen from a moment before.

After a while, the density of the artifacts become too much, and the laptop reboots itself entirely.
I can actually "reset" the problem, if I switch to a TTY the moment I notice an artifact. It buys me more time, but it's hardly an ideal situation to be in.

Could it be incorrectly referencing video memory? The nvidia-settings dialog claims I have 512MB of VRAM, but I happen to know it's half of that, at most. It could be dynamically shared system RAM though. Also, 512MB is displayed even when I'm using the working [older] drivers, so that doesn't seem to be the problem.

---

### Post by dabl on 2009-09-15
> **cyberkilla said:**
> 

once I start moving windows about, clicking buttons, or even just moving my mouse (although big changes to the screen make the issue appear more swiftly), strange horizontal artifacts appear, which are formed from pieces of the screen from a moment before.

After a while, the density of the artifacts become too much, and the laptop reboots itself entirely.



What is the chance that this is actually a thermal problem, disguised as something related to video driver performance?  When you're dragging windows around and such, it works the CPU as well as the GPU - might induce a thermal shutdown if the laptop is already at the margin.

---

### Post by cyberkilla on 2009-09-15
> **dabl said:**
> What is the chance that this is actually a thermal problem, disguised as something related to video driver performance?  When you're dragging windows around and such, it works the CPU as well as the GPU - might induce a thermal shutdown if the laptop is already at the margin.

It's possible that the heat increase is dramatic and too quick to detect, however, I did try it with nvidia-settings open. The temperature did not spike at all.

From what I gather, a few years ago, the exact model of card I use was found to be part of a massive manufacturing failure for NVidia. The material that coated the die on the graphics card was of low quality, leading to the inevitable BSoD in Windows, after the card had been used for a few month. The constant heating and cooling that happens on any card, could not be handled by this batch of cards.

However, my card is ~2 years old now, and I have no problems when using Vista, or the older drivers in the Ubuntu repository. Perhaps the latest drivers are tapping into the card in a different way, which it doesn't like very much.
I don't know. I would have thought that a hardware failure would happen with any of the drivers though, not just the latest ones.

---

### Post by srikumar on 2009-10-11
I am seeing the same problem too. Vaio AR520E with 8400M GT. 185.18.14 works, anything newer doesn't. Something is seriously broken here. Have you found any solution?

---

### Post by Lod on 2009-10-19
I have the same problem. Funny part is, I have the same problems in Windows 7 with the same driver version.
Laptop Asus M50Vn with the GeForce 9650M GT videocard.
I had to go back to the 173 driver because I couldn't find an older version of the 185 driver.

---

### Post by cyberkilla on 2009-10-19
No, I haven't found a solution. I have apt-pinned the old drivers for the time being. I'm glad I'm not alone with this driver issue.

Perhaps we should file a bug report. The problem is, I don't know what the problem is, or the team to notify.

> **Lod said:**
> I have the same problem. Funny part is, I have the same problems in Windows 7 with the same driver version.
Laptop Asus M50Vn with the GeForce 9650M GT videocard.
I had to go back to the 173 driver because I couldn't find an older version of the 185 driver.

Interesting. I haven't updated my Vista NVidia drivers for a year or so, and only via Sony's driver update website. This is looking more like a problem with the drivers, rather than the way Ubuntu has packaged them.

---

### Post by Lod on 2009-10-20
I found this thread on a nvidia forum.
[http://forums.nvidia.com/index.php?showtopic=102344](http://forums.nvidia.com/index.php?showtopic=102344)

In Windows I looked for the suggested files but couldn't find them. So I stopped searching, more so because I'm not that into hardware related issues. At post 13 someone might mention something interesting however.

---

### Post by srikumar on 2009-10-20
> **Lod said:**
> I found this thread on a nvidia forum.
[http://forums.nvidia.com/index.php?showtopic=102344](http://forums.nvidia.com/index.php?showtopic=102344)

In Windows I looked for the suggested files but couldn't find them. So I stopped searching, more so because I'm not that into hardware related issues. At post 13 someone might mention something interesting however.

I found the answer in the link you posted. Create a file called /etc/modprobe.d/nvidia.conf with this in it:

**options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222**" 

And reboot. Looks like this is a common problem with the latest nvidia drivers and the mobile series cards (laptop), on all platforms. Basically, the screen flicker and artifacts are caused by nvidia's "powermizer" feature, that continually adjusts the cards's clock speed to save on power. The command I posted above turns off powermizer, i.e. the card runs at max clock speed. This will obviously reduce battery life for laptop users, but there it is.

Please post your experiences here with the fix above. Maybe the Ubuntu maintainer can optionally offer this in the package? Looks like a lot of users will be affected by this problem.

---

### Post by Lod on 2009-10-20
It seems to work for me. I activated the 185 drivers and without the file I experienced instant crashes and so. With the file none (for the moment :popcorn:). It would be great if this is indeed the solution. Thanks for finding this out.

---

### Post by srikumar on 2009-10-20
> **Lod said:**
> It seems to work for me. I activated the 185 drivers and without the file I experienced instant crashes and so. With the file none (for the moment :popcorn:). It would be great if this is indeed the solution. Thanks for finding this out.

Hi,

This is not a fix. I guess you could call it a workaround. IMHO nvidia is the culprit here, because everything was fine until 185.18.14 and started breaking after that version. And the thread you mentioned in your earlier post had windows users complaining about the same problem. If it is really an nvidia problem, it is unlikely that the Ubuntu developers will be able to fix it. So I think the workaround I posted should be integrated into the nvidia driver package. In fact I have already opened a bug report along those lines: bug #456637

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/456637](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/456637)

If you and others are affected by the same problem and the workaround works for you, please lend your voice to that bug report.

---

### Post by cyberkilla on 2009-10-21
Thanks for reviving the thread. I will have to test this for myself - hopefully it will make compiz a bit more responsive too, if it doesn't have a 1-2 second lag prior to the mode increasing whenever I scale windows:)

I can't believe NVidia hasn't been alerted to this already. I've had the issue for weeks and there are a number of more recent driver releases which do nothing to fix the problem. #-o

**Update:** It works for me:) I'm not sure what the effect of locking it into maximum performance mode will have in the long term.

My core temp is 62C idle, so almost identical to what it was beforehand.
On a positive note, whether it is the drivers or the forced max performance mode, Firefox is a lot less choppy when scrolling:)

---

### Post by srikumar on 2009-10-21
> **cyberkilla said:**
> Thanks for reviving the thread. I will have to test this for myself - hopefully it will make compiz a bit more responsive too, if it doesn't have a 1-2 second lag prior to the mode increasing whenever I scale windows:)

I can't believe NVidia hasn't been alerted to this already. I've had the issue for weeks and there are a number of more recent driver releases which do nothing to fix the problem. #-o

**Update:** It works for me:) I'm not sure what the effect of locking it into maximum performance mode will have in the long term.

My core temp is 62C idle, so almost identical to what it was beforehand.
On a positive note, whether it is the drivers or the forced max performance mode, Firefox is a lot less choppy when scrolling:)

This has been discussed a lot in nvidia forums, windows users are affected too. So obviously nvidia knows about this issue. There is even a thread about should powermizer be off by default.

About the effect of turning off powermizer, AFAIK powermizer underclocks the card from time to time to save power. If powermizer is turned off, that means your card is now running at native speed, it's not overclocked or anything. So I think it will be OK, except for drain on battery if you're running a notebook.

---

### Post by fedexnman on 2009-10-22
i have a 9800gt in my pc i built and the 185 driver killed my karmic beta install, i have errors and cant login etc. etc. i hope things will be iron'd out before  oct 29th. i see alot of launchpad and bug reports for the nvidia 185 driver.:confused:

---

### Post by srikumar on 2009-10-22
> **fedexnman said:**
> i have a 9800gt in my pc i built and the 185 driver killed my karmic beta install, i have errors and cant login etc. etc. i hope things will be iron'd out before  oct 29th. i see alot of launchpad and bug reports for the nvidia 185 driver.:confused:

So, did turning off powermizer help or not?

---

### Post by fedexnman on 2009-10-22
so the workaround is to turn off the powermizer, i thought that was for laptops, i guess ill have to try that on my desktop, i guess this is a nvidia problem n not an ubuntu problem ?? ill be waiting for oct 29th and download the actual 9.10 release n try again.

---

### Post by cyberkilla on 2009-10-23
Well, I've been using this workaround for a few days now, and I've had no problems:)

Thanks again for pointing it out.

---

### Post by NRDNick on 2009-10-26
> **srikumar said:**
> I found the answer in the link you posted. Create a file called /etc/modprobe.d/nvidia.conf with this in it:

**options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222**" 

And reboot. Looks like this is a common problem with the latest nvidia drivers and the mobile series cards (laptop), on all platforms. Basically, the screen flicker and artifacts are caused by nvidia's "powermizer" feature, that continually adjusts the cards's clock speed to save on power. The command I posted above turns off powermizer, i.e. the card runs at max clock speed.

Well I'm still worried about the placebo effect, but this seems to have solved my issues with the NVidia driver 185.18.36. I had been experiencing random memory squirts causing artifacts and usually resulting in the pc becoming unresponsive. Most of the time the issue would spring up while running ET an online FPS, in the background while browsing the web using Opera. Although sometimes the issue did occur while not running any opengl apps or cpu/memory intensive tasks as well.

Granted it has only been 8 hours since I've changed this, I have yet to see the error repeat itself and I have been running ET in the background the whole time. It even stopped my conky from flashing periodically(I read somewhere that this was a solution but never tried it /me slaps forhead)

 I had previously installed the 190 series drivers and after the problem persisted I returned the the drivers in the repos. I did however notice that in the Nvidia-settings app for the 190 drivers, there is an option to change the state of the powermizer. Presumably NVidia put this in because they are aware of the issues that it can cause.

I'll post back in a day or two to make sure that this indeed was the culprit. I'm thinking this could solve a lot of other peoples issues with karmic freezing like over in this thread [http://ubuntuforums.org/showthread.php?t=1276146]("http://ubuntuforums.org/showthread.php?t=1276146") One of the suggestions there is to switch to the rt kernel, I wonder if it interacts differently with powermizer making it actually work? Although I'm sure switching to the rt kernel could solve loads of other issues, and at the same time cause some new ones :P Also not all of the people having issues like this are using nvidia drivers, just trying to draw a correlation. Oh and btw thank you very much for your help srikumar, I'll post on your bug report as soon as I can confirm my issues have stopped.

---

### Post by NRDNick on 2009-10-26
Uptime 22h 15m since forcing Powermizer to performance mode, with ET running in the background constantly and not one hiccup so far :D Someone should probably make a sticky about this for anyone trying to run NVidia drivers. I'm honestly surprised it took me so long to figure this out as I've been putting up with artifacts and frequent lock-ups since I installed Alpha 5 almost 2 months ago. It would be nice to hear from anyone else in the same situation, so we can completely confirm this issue. Again thank you srikumar, you have ironed a big crease in my Karmic experience and I believe it will do the same for many others.

---

