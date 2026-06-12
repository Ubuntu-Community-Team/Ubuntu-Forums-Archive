---
title: "nouveau doubters take note"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gnomeuser on 2010-02-25
In the process of testing the nouveau driver on Lucid with the xorg-edgers ppa (to confirm a fix for an XV bug) I noticed that compiz now runs on nouveau on my machine. I decided to push my luck and add rgba as well for that pointless blingy edge.

Long short of it, while not extremely fast it works and is standing up to abuse rather well.

---

### Post by 23meg on 2010-02-25
> **gnomeuser said:**
> I noticed that compiz now runs on nouveau on my machine.

Nice. It would be useful to know about your hardware.

---

### Post by DeadSuperHero on 2010-02-25
Wow, that's really spiffy!

---

### Post by qra0 on 2010-02-25
> **gnomeuser said:**
> In the process of testing the nouveau driver on Lucid with the xorg-edgers ppa (to confirm a fix for an XV bug) I noticed that compiz now runs on nouveau on my machine. I decided to push my luck and add rgba as well for that pointless blingy edge.

Long short of it, while not extremely fast it works and is standing up to abuse rather well.

5KR says the performance will be poor & buggy for anything besides Compiz/Kwin.

---

### Post by Reiger on 2010-02-25
> **23meg said:**
> Nice. It would be useful to know about your hardware.

Probably posted "on" the same machine as that "meager nvidia ION based Acer Aspire Revo r3610" thing "running compiz now under nouveau" he posts about. It's all in the screenshot. :P

---

### Post by andrewabc on 2010-02-25
Since you have nvidia ion that is supposed to have hardware accelerated 1080p video playback, can you play 1080p video no problem on ubuntu?
Assuming compiz etc is disabled of course.

Looking at getting an ion based nettop at some point. Would be nice to know if ubuntu 10.04 can do same stuff windows can graphics card hardware wise (video playback).

---

### Post by gnomeuser on 2010-02-26
> **andrewabc said:**
> Since you have nvidia ion that is supposed to have hardware accelerated 1080p video playback, can you play 1080p video no problem on ubuntu?
Assuming compiz etc is disabled of course.

Looking at getting an ion based nettop at some point. Would be nice to know if ubuntu 10.04 can do same stuff windows can graphics card hardware wise (video playback).

GStreamer current doesn't support VPDAU so it won't work out of the box, the nouveau driver also doesn't support VPDAU (yet) so it will only work with the blob. As such that holds little value to me for testing so I haven't set it up but it should be possible.

The hardware might be meager but I have seen this box play Left 4 Dead, it's very capable. I highly recommend the Aspire Revo r3610, I am using it as my main desktop and it runs a very pleasant desktop experience. You get a lot of machine for your cash.

---

### Post by gnomeuser on 2010-02-26
> **qra0 said:**
> 5KR says the performance will be poor & buggy for anything besides Compiz/Kwin.

Early code, of course it isn't optimal yet. The same driver on different hardware though can run Quake 3 or TA: Spring. I haven't tried that yet though, not a lot of interest in gaming on my part.

As for the performance, it is right now perfectly capable of running a compiz desktop. It is stable and so far I haven't noticed any visual glitches. The progress from being 2d only to providing initial 3d support has been impressive. 

This is mostly about showing how mature nouveau is, for Lucid we will only see 2d support but for Lucid+1 it seems very feasble to turn this on by default.

---

### Post by Atermoon on 2010-02-26
I just added the xorg-edgers ppa to my Kubuntu, updated, tried to enable compositing in Kwin and my system froze. Now it keeps freezing on Plymouth. Not a biggie, my Kubuntu install is for testing purposes only and gets doomed pretty often anyway.

---

### Post by tito_torrisi on 2010-02-26
I don't understand how you get the 3d (gallium?) running. I thought they don't provide gallium support because it was too unstable right now (see the xorg-edgers nouveau ppa description). There is no gallium package, how do you 'activate' it?

edit: @gnomeuser: Did you test gnome-shell with it on our Revo yet?

---

### Post by Atermoon on 2010-02-26
> == New in Lucid ==
 Nouveau (gallium and mesa classic) support is enabled in mesa...



From [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by tito_torrisi on 2010-02-26
Yeah I read that, I thought support means you can 'use' it with self-compiled gallium code. 
So I guess that means it just works...
Well then gnome-shell doesn't run with it, because I tried that a couple of days before!

When there is vdpau and gnome-shell support, I will use nouveau as default.

---

### Post by gnomeuser on 2010-02-26
> **tito_torrisi said:**
> I don't understand how you get the 3d (gallium?) running. I thought they don't provide gallium support because it was too unstable right now (see the xorg-edgers nouveau ppa description). There is no gallium package, how do you 'activate' it?

edit: @gnomeuser: Did you test gnome-shell with it on our Revo yet?

You have to use the full xorg-edgers ppa not the now closed xorg-edgers/nouveau ppa. Now this is unstable code and the repo warnings should be taken seriously. ppa-purge is your friend to help recover if it fails. The builds are updated daily and as such if it works today it is not a sure thing that it will work tomorrow.

As for gnome-shell, just for you I installed ricos daily builds and fired it up. Good news, it runs. Bad news, it's still gnome-shell.

---

### Post by tito_torrisi on 2010-02-26
I don't believe it! I removed the nvidia driver and restartet, and   (after a faster boot I noticed) everything's the same. Gnome-shell works great. 1 or 2 updates before it crashed on my system. Amazing work! Of course vdpau isn't working any more, that is bad on a ION system, but I heard they are working on it.

Thank you, I forgot you are not a gnome-shell fan ;-) I like it, because it gives me a compositing manager without beeing forced to use compiz. With compiz I have problems with my refresh rate and videos. It is way too much than I want. I just need compositing for docky or cairo-dock etc.

---

### Post by tito_torrisi on 2010-02-26
> **gnomeuser said:**
> As for gnome-shell, just for you I installed ricos daily builds and fired it up. Good news, it runs. Bad news, it's still gnome-shell.

I guess you also want to stay with nouveau. Do you have any idea how to replace vdpau until it works with nouveau? Because we rely on it on our ION system. I tried to switch to va-api, but I found out it also uses VDPAU to work (at least on nvidia graphics chip). I don't know of any other way to speed up video playback!

---

### Post by Tompalaz on 2010-02-26
> **tito_torrisi said:**
> [...]Gnome-shell works great.
If gnome-shell works I'll switch to the nouveau driver.
Is it slower, faster?

I have a 9400M card.

---

### Post by gnomeuser on 2010-02-26
> **Tompalaz said:**
> If gnome-shell works I'll switch to the nouveau driver.
Is it slower, faster?

I have a 9400M card.

Likely slower, the code is still young and unoptimized. It runs at an acceptable speed here though.

---

### Post by tito_torrisi on 2010-02-26
> **Tompalaz said:**
> If gnome-shell works I'll switch to the nouveau driver.
Is it slower, faster?

I have a 9400M card.

I also have a 9400M (ION) and it definitely is faster. I just compared and esp. going into the overlay mode and back goes much smoother than before.

---

### Post by SevenMachines on 2010-02-26
well, that went surprisingly well!
* OpenGL renderer string: Gallium 0.4 on NVA0!!!

- gnome-shell works fine
- ran a few games and benchmarks, worked fine
- compiz, inactive window bars :*(
- google-earth, tiny window :*(

apart from the compiz bugs, i wouldnt have noticed the difference from the nvidia binary, apart from that nice solar theme of course :)

obviously pushing opengl hard will illustrate the speed difference but i'm impressed, it may yet be my default!

Nvidia gtx 260 (219)

---

### Post by bladerunner6 on 2010-02-26
when do we get support for 2.6.33 back!!

---

### Post by tito_torrisi on 2010-02-26
Is it possible to install 2.6.33 kernel with nouveau?

---

### Post by Tompalaz on 2010-02-27
Yes, finally! 
I can replace my nVidia drivers with opensource drivers and STILL run Gnome-shell without any performance drawback.

---

### Post by gnomeuser on 2010-02-27
I am very surprised at the lack of any major reports of breakage, crashing and so forth from people. I was kinda thinking that I was lucky to hit a combination that was supported and stable but it seems the nouveau 3d support is generally in a much better state than I could have ever hoped.

I am really getting excited about the possibility that this might be shippabe in Lucid+1. It would bring us to a point in time I have been eagerly awaiting, 3d support using open source for all 3 major video cards (nvidia, ati ad intel). It feels so close now that I can taste the victory.

---

### Post by autumnraine on 2010-02-27
I love Nouveau! I just bought a new 24'' Samsung SyncMaster 2494HM monitor with a 1920X1080 resolution, and Nouveau is the ONLY driver that recognized my optimal resolution AND rendered it well. nv only used 2/3rds of the screen space, and Nvidia achieved the proper resolution but screwed up all the fonts so they looked huge, and then wrong looking even after I adjusted the fonts. Not to mention the Nvidia driver doesn't allow for rotation by default, and my screen rotates (though I haven't tried it with Nouveau yet). All in all I'm VERY happy with it!

---

### Post by exploder on 2010-02-27
Nouveau at the moment is working better than the proprietary drivers. I have an NVidea GT 220 and an HP 25' Wide Screen HDMI monitor, using Nouveau, my screen resolution is consistent from the time I press the power button until the desktop loads. With the proprietary drivers the screen resolution is inconsistent through the boot process. The only thing with the open source drivers is that desktop effects are not working.

I think with a little more work, the open source driver is a better choice.

---

### Post by skymera on 2010-02-27
Just removed my Nvidia driver and testing out the Nouveau driver.

It works :|

Compiz does work, little less performance than proprietary drivers.
Though everything seems overbright with Compiz running.

Sauerbraten didn't work, but i didn't expect it to :P

Good start, looking forward to some updates

---

### Post by Tompalaz on 2010-02-28
I have a monitor that i'd like to use as primary monitor with my laptop, while the laptop lid is closed. How can I accomplish this?
Do I have to use the nVidia driver?

---

### Post by gnomeuser on 2010-02-28
> **Tompalaz said:**
> I have a monitor that i'd like to use as primary monitor with my laptop, while the laptop lid is closed. How can I accomplish this?
Do I have to use the nVidia driver?

If it is supported then using the System->Preferences->Monitor tool and it should be self explanatory.

---

### Post by Tompalaz on 2010-02-28
Guess it's not supported yet, look at image..

9400M, mini display port, and a HPw2207 monitor.
edit: sorry for the image rotation.

---

### Post by gnomeuser on 2010-02-28
> **Tompalaz said:**
> Guess it's not supported yet, look at image..

9400M, mini display port, and a HPw2207 monitor.
edit: sorry for the image rotation.

randr 1.2 should be supported which I believe is what is used for this, so we might be looking at a bug. At any rate it is nice to document what doesn't work.

ubuntu-bug xserver-xorg-video-nouveau

The Fedora guys wrote some test cases for people to use which might be useful in gathering additional data.

[http://fedoraproject.org/wiki/QA:Testcase_nouveau_multihead](http://fedoraproject.org/wiki/QA:Testcase_nouveau_multihead)

It would be good if we could get this working for you by the time Luci goes final. 

btw are you using stock Lucid Nouveau or are you also using xorg-edgers?

---

### Post by Tompalaz on 2010-02-28
I'd be happy to help, more happy if you help me :D

I'm using xorg-edgers.
Do you think that this might be caused by Gnome-shell or the composite. I'll try without gnome-shell.

---

### Post by gnomeuser on 2010-02-28
> **Tompalaz said:**
> I'd be happy to help, more happy if you help me :D

I'm using xorg-edgers.
Do you think that this might be caused by Gnome-shell or the composite. I'll try without gnome-shell.

I will do what is in my power, I would advice you to follow the directions I gave you before, preferably after trying to configure the monitor since that should show up in the logs. I will subscribe to your bug and we can see where to go from there.

---

### Post by Tompalaz on 2010-02-28
Well, I did try the display application and that "crashed" the screen, like you saw on the picture.

Here is two funny things:
1) When I booted up the Live-CD and tried the Display app, my laptop screen goes point blank like it was switched off. Can't really do anything except turn off my computer since I can't see anything. 
I'd say it would be the same with the stock drivers in lucid. 


2) If I boot up with the mini display port connected the laptop shows the plymouth ubuntu logo. Normaly it's just blank. However, it seems like the laptop freeze. Under the ubuntu logo there is the letter C. Never get passed the logo.


So, I must plug in the contact after I've logged in.  



Output from the ubuntu-bug command:
> tomas@macbook:~$ ubuntu-bug xserver-xorg-video-nouveau
hook /usr/share/apport/package-hooks//source_xserver-xorg-video-nouveau.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 639, in add_hooks_info
    symb['add_info'](self)
  File "/usr/share/apport/package-hooks//source_xserver-xorg-video-nouveau.py", line 29, in add_info
    codename = command_output(['lsb_release','-c']).split(": ")[1]
IndexError: list index out of range
 
And a gtk window that sais it can't be reported because it's not a genuine package.

edit:
I've turned off gnome-shell and compiz, no change.

---

### Post by gnomeuser on 2010-02-28
first of all, crashing the crash reporter.. that is impressive :)

I forgot, it weeds out non-supported packages such as those from ppas. You'll have to go to bugs.launchpad.net and do it manually. Also be nice and start the report out by mentioning that you are using xorg-edgers since that is highly unsupported.


Does your laptop have a button or button combination to set the display in use? (typically this is Fn + Fxy). It might be that you simply need to hit that a few times till you reach the desired setting.

---

### Post by Tompalaz on 2010-02-28
There isn't a key combo nor a button.
I just need to press in the mini display adapter and it's automatically on.

A solution from the apple people.

I'll report this tomorrow.

I've never filed a bug before, do I need anything special or will they be nice to me and maybe tell me what they need? :D

---

### Post by gnomeuser on 2010-02-28
> **Tompalaz said:**
> There isn't a key combo nor a button.
I just need to press in the mini display adapter and it's automatically on.

A solution from the apple people.

I'll report this tomorrow.

I've never filed a bug before, do I need anything special or will they be nice to me and maybe tell me what they need? :D

you should at the very least attach:

/var/log/Xorg.0.log
The output of dmesg (do dmesg > dmesg.log and attach the file).
The output of lspci (do lspci > lspci.log and attach the file).

I am sure ROAF will tell you what else he needs, he is a nice guy.

---

### Post by Tompalaz on 2010-03-01
hopefully this is good enough.
[#529921]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529921")

---

### Post by gnomeuser on 2010-03-01
> **Tompalaz said:**
> hopefully this is good enough.
[#529921]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529921")

It's very odd, I looked over logs and everything looks fine (a few minor bumps but no big red honking warning signs), however clearly it is not.

Can you attach the output from xrandr as well?

---

### Post by Tompalaz on 2010-03-01
Alright, it's updated with xrandr.
Btw, what about this one:
> [   22.711104] [lbm-drm:drm_mode_getfb] *ERROR* invalid framebuffer id


---

### Post by gnomeuser on 2010-03-01
> **Tompalaz said:**
> Alright, it's updated with xrandr.
Btw, what about this one:

that one does stand out but still it correctly detects both displays and I assume their correct resolutions. 

All logic says that this should work, and yet it does not..

---

### Post by Tompalaz on 2010-03-01
What if it's a hardware problem, that the mini display port to vga adapter do something. Strange though, it have worked with the proprietary nVidia driver. and it works flawless in OS X.

Edit: Works tested with nvidia driver and it works. Still, could it be that nouveau sends different signals?

At update-initramfs I get this:
> W: Possible missing firmware /lib/firmware/nouveau/nva5.ctxprog for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva0.ctxvals for module lbm_nouveau
W: Possible missing firmware /lib/firmware/nouveau/nva0.ctxprog for module lbm_nouveau

and it continues..

edit2: I reinstalled lucid, and the stock drivers doesn't work, it just turns off both displays.

---

### Post by Tompalaz on 2010-03-02
Bug has been confirmed.
There have been a couple of xorg-server and nouveau updates today.
I'll try again.

Edit: the new updates didn't get it to work.

---

### Post by yoasif on 2010-03-03
Really enjoying the newest updates from xorg-edgers. 

The latest updates from git provides composite, and compiz works (although opacity in menus isn't working properly). Gnome shell also doesn't work. 

This is on a Acer Aspire 4530. 

VGA compatible controller: nVidia Corporation C77 [GeForce 9100M G] (rev a2)

Also, suspend when using composite causes issues (freezes input every few seconds).

---

### Post by gnomeuser on 2010-03-03
> **Tompalaz said:**
> What if it's a hardware problem, that the mini display port to vga adapter do something. Strange though, it have worked with the proprietary nVidia driver. and it works flawless in OS X.

Edit: Works tested with nvidia driver and it works. Still, could it be that nouveau sends different signals?

At update-initramfs I get this:

and it continues..

edit2: I reinstalled lucid, and the stock drivers doesn't work, it just turns off both displays.

Is the nouveau-firmware package installed?

---

### Post by Tompalaz on 2010-03-03
No, it isn't. I'll install it right now.
Edit: Alright, the error messages is gone.
Should I repost the logs with the monitor connected?

---

### Post by Tompalaz on 2010-03-03
> **yoasif said:**
> ..Gnome shell also doesn't work. 
...

Really? works perfect for me.

---

### Post by phenest on 2010-03-03
I just switched to nouveau using the Hardware Drivers app. I tried doing it manually before to no avail, but this time it's working better. I get the correct resolution (1920x1200), but the colour depth is too low (16 bit). Metacity works with composition too.

nVidia GeForce 7950GTX

---

### Post by Tompalaz on 2010-03-03
> **phenest said:**
> I just switched to nouveau using the Hardware Drivers app. I tried doing it manually before to no avail, but this time it's working better. I get the correct resolution (1920x1200), but the colour depth is too low (16 bit). Metacity works with composition too.

nVidia GeForce 7950GTX
It's worth trying xorg-edgers ppa if you haven't already.
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

---

### Post by yoasif on 2010-03-03
> **Tompalaz said:**
> Really? works perfect for me.depends on your chipset -- or do you have the same chipset as me? if so, are you using gnome-shell from the ppa, or running it from lucid's repos?

---

### Post by phenest on 2010-03-03
> **Tompalaz said:**
> It's worth trying xorg-edgers ppa if you haven't already.
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

That's what I'm using.

---

### Post by andrewabc on 2010-03-05
> **gnomeuser said:**
> GStreamer current doesn't support VPDAU so it won't work out of the box, the nouveau driver also doesn't support VPDAU (yet) so it will only work with the blob. As such that holds little value to me for testing so I haven't set it up but it should be possible.

The hardware might be meager but I have seen this box play Left 4 Dead, it's very capable. I highly recommend the Aspire Revo r3610, I am using it as my main desktop and it runs a very pleasant desktop experience. You get a lot of machine for your cash.

To add to the thread.
[NVIDIA ION Support In xf86-video-nv](http://www.phoronix.com/scan.php?page=news_item&px=ODAzOA)

I also presume the ion nettops are all SATA II? Not like the older laptops that had sata II but were disabled to save power?
Also, what ICH does the ion nettops have? wondering how an SSD in them would perform (max performance or limited in some way because of nettop form factor). As you can tell I'm very interested in them since my desktop is 3.5 years old and these nettops are faster than my original desktop config (mostly video card).

---

### Post by Tompalaz on 2010-03-06
> **yoasif said:**
> depends on your chipset -- or do you have the same chipset as me? if so, are you using gnome-shell from the ppa, or running it from lucid's repos?

I have a 9400M and build gnome-shell from source.

---

### Post by _R2D2_ on 2010-03-06
LOL :D:D:D
[http://lkml.org/lkml/2010/3/5/196](http://lkml.org/lkml/2010/3/5/196)
Nouveau team ask Linux Torvald to exclude their stuff from the vanilla kernel :D
BTW, yesterday I tried default 2.6.32 kernel from repos. Of course, the new splash is nice, but overall expirience with nouveau is quite bad: it's so slow and unstable (8800gtx).

---

### Post by gnomeuser on 2010-03-06
> **_R2D2_ said:**
> LOL :D:D:D
[http://lkml.org/lkml/2010/3/5/196](http://lkml.org/lkml/2010/3/5/196)
Nouveau team ask Linux Torvald to exclude their stuff from the vanilla kernel :D
BTW, yesterday I tried default 2.6.32 kernel from repos. Of course, the new splash is nice, but overall expirience with nouveau is quite bad: it's so slow and unstable (8800gtx).

Well, Linus was being some what of a dick, first he demands that Nouveau goes in, they say they would like to be able to assure API stability before asking for inclusion. He says that isn't a problem. They comply to his demand, then the time comes where a breaking API change is needed and Linus complains.

---

### Post by RAOF on 2010-03-06
> **_R2D2_ said:**
> LOL :D:D:D
BTW, yesterday I tried default 2.6.32 kernel from repos. Of course, the new splash is nice, but overall expirience with nouveau is quite bad: it's so slow and unstable (8800gtx).

It's likely that you don't have the nouveau-firmware package installed; without it, there's no acceleration for GeForce 8 & newer cards, and will be very slow.  That may also explain some forms of instability (particularly, playing video will fail if you've got the video output set to Xv).

There will soon be a new -16 kernel out; that will support acceleration on all cards without needing the nouveau-firmware package installed.

Please file bugs for any issues you encounter.  There aren't many good bugs on nouveau at the moment!

---

### Post by yoasif on 2010-03-06
> **RAOF said:**
> Please file bugs for any issues you encounter.  There aren't many good bugs on nouveau at the moment!I thought 3d support was unsupported, or are you just talking about 2d acceleration?

thankfully, that works great on my card. :)

---

### Post by RAOF on 2010-03-06
> **yoasif said:**
> I thought 3d support was unsupported, or are you just talking about 2d acceleration?

thankfully, that works great on my card. :)

3D is very thoroughly unsupported, yes.

_R2D2_ mentioned that the archive packages were slow; GeForce 8 cards don't get *any* acceleration - 2D or 3D - without the nouveau-firmware package.  Also the memory layout on the GeForce 8 makes unaccelerated rendering with nouveau really slow.

If you're using the packages from the main repositories, and are seeing problems with nouveau, please file a bug[1] - “ubuntu-bug xorg” will attach all the information to make it a good bug.

[1] Errors about being unable to switch to a VT or about not getting any display until X comes up will be resolved by the -16 kernel, coming soon.  See the bug against linux-backports-modules with vga16fb in the title.

---

### Post by Regenweald on 2010-03-06
> **gnomeuser said:**
> Well, Linus was being some what of a dick, first he demands that Nouveau goes in, they say they would like to be able to assure API stability before asking for inclusion. He says that isn't a problem. They comply to his demand, then the time comes where a breaking API change is needed and Linus complains.

In this case I don't get linus' logic. The Nouveau devs weren't begging for their driver to be in the kernel because they know it's still early days and the architecture is still being hashed out somewhat. You demand that the driver be included then get mad when they continue to make it better ? No api breaks can mean stagnancy in some cases, and that is not what the nouveau project needs at the moment.

---

### Post by nanog on 2010-03-07
2d nouveau has been stable for me in fedora 11/12/rawhide. helping other distros run nouveau is not at the top of red hats to do list.

---

### Post by LKjell on 2010-03-07
> **Regenweald said:**
> In this case I don't get linus' logic. The Nouveau devs weren't begging for their driver to be in the kernel because they know it's still early days and the architecture is still being hashed out somewhat. You demand that the driver be included then get mad when they continue to make it better ? No api breaks can mean stagnancy in some cases, and that is not what the nouveau project needs at the moment.

What would you think if you had to download the daily cd each time to test Lucid because upgrading through apt-get? Or for the matter you have to reinstall every time you upgrade something?

---

### Post by Tompalaz on 2010-03-07
don't know if this have something to do with the nouveau driver but plymouth won't play nice with me. I just get a blank screen.

---

### Post by LKjell on 2010-03-07
> **Tompalaz said:**
> don't know if this have something to do with the nouveau driver but plymouth won't play nice with me. I just get a blank screen.

Even if you hit enter?

---

### Post by Tompalaz on 2010-03-07
> **LKjell said:**
> Even if you hit enter?

No, its just grub -> blank screen -> gdm
really fast boot though.

---

### Post by LKjell on 2010-03-07
If you get to gdm then login? I mean hit enter when you get the blank screen. Or use the magic key to restart X. Eventually remove plymouth from recovery mode or live cd.

---

### Post by cristianrosa on 2010-03-07
I have the same problem than Tompalaz, there is already a bug report on this [#530451]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/530451"). The problem seems to be that the module vga16fb races with nouveau module for the fb0.

---

### Post by Tompalaz on 2010-03-07
> **cristianrosa said:**
> I have the same problem than Tompalaz, there is already a bug report on this [#530451]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/530451"). The problem seems to be that the module vga16fb races with nouveau module for the fb0.

so a simple solution would be to blacklist vga16fb module?
edit: yep that did the trick
blacklist vga16fb in /etc/modprobe.d/blacklist.conf
then sudo update-initramfs -u

So the only problem I have right now is my monitor problem.
Bug: [#529921]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529921")

---

### Post by autumnraine on 2010-03-08
> **gnomeuser said:**
> As for the performance, it is right now perfectly capable of running a compiz desktop. It is stable and so far I haven't noticed any visual glitches. The progress from being 2d only to providing initial 3d support has been impressive. 

This is mostly about showing how mature nouveau is, for Lucid we will only see 2d support but for Lucid+1 it seems very feasble to turn this on by default.

Do you think they will offer an optional gallium package in the repositories of the mature Lucid, with a warning? I'd really like to use it but don't want to risk daily builds.

edit: or does the default mesa package in Lucid actually implement Gallium?

---

### Post by Owen.C93 on 2010-03-08
Just installed the 16 headers and now they aren't listed in the hardware dirvers. Uninstall from synaptic and re-install?

---

### Post by uBeer on 2010-03-08
I don't think you have to worry:
[http://swiss.ubuntuforums.org/showpost.php?p=8927261&postcount=55](http://swiss.ubuntuforums.org/showpost.php?p=8927261&postcount=55)

---

### Post by nperry on 2010-03-08
Can someone help me, I'm getting (EE) [drm] failed to open device in my xorg.0.log.  My lspci says i've got "01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)"

Has anyone got any ideas?


EDIT, 
This is my Xorg.conf: [http://pastebin.com/2nnLMA77](http://pastebin.com/2nnLMA77)
This is my Xorg.0.log: [http://pastebin.com/KDnd3pn1](http://pastebin.com/KDnd3pn1)

---

### Post by nanog on 2010-03-08
i got more x crashes running the @#$$#!@! binary driver. 
edgers nouveau has been very stable for me. and if gallium+compiz gives me trouble after an update i just switch to tty1 and issue metacity --replace & or mutter --replace (depending on my mood).

---

### Post by nanog on 2010-03-08
you need to have a valid xorg.conf.

---

### Post by nperry on 2010-03-08
> **nanog said:**
> you need to have a valid xorg.conf.

Was that aimed at me?

---

### Post by sroecker on 2010-03-08
> **nperry said:**
> Can someone help me, I'm getting (EE) [drm] failed to open device in my xorg.0.log.  My lspci says i've got "01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)"

Has anyone got any ideas?


EDIT, 
This is my Xorg.conf: [http://pastebin.com/2nnLMA77](http://pastebin.com/2nnLMA77)
This is my Xorg.0.log: [http://pastebin.com/KDnd3pn1](http://pastebin.com/KDnd3pn1)

Did you use the xorg-crack ppa? I did and had some packages left:
```
dpkg -l | grep sarvatt
```After I "downgraded" them to lucid nouveau worked. (had the same error before)
You can "downgrade" packages like this:
```
apt-get install libdrm-nouveau1/lucid
```

---

### Post by nanog on 2010-03-09
your xorg.conf are invalid. you can try deleting them or just use a minimal one: 

> Section "Device"
        Identifier "n"
        Driver "nouveau"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


---

### Post by nperry on 2010-03-09
> **nanog said:**
> your xorg.conf are invalid. you can try deleting them or just use a minimal one
I have already tried that, still not working. 

> **sroecker said:**
> Did you use the xorg-crack ppa? I did and had some packages left:
```
dpkg -l | grep sarvatt
```After I "downgraded" them to lucid nouveau worked. (had the same error before)
You can "downgrade" packages like this:
```
apt-get install libdrm-nouveau1/lucid
```
Downgraded to lucid version, still getting the same message. Very odd.

EDIT, take it this is the right one.
> Selected version 2.4.18+git20100302.9a37455b+rebuilt1-0ubuntu0raof (Nouveau packages for testing:10.04/lucid) for libdrm-nouveau1


---

### Post by gnomeuser on 2010-03-09
> **autumnraine said:**
> Do you think they will offer an optional gallium package in the repositories of the mature Lucid, with a warning? I'd really like to use it but don't want to risk daily builds.

edit: or does the default mesa package in Lucid actually implement Gallium?

I doubt we will see an official package in the repos, it replaces a package that is already there and it is still considered unstable (and it is for some people).

For now, xorg-edgers is probably the sanest place to keep it and frankly I am happy with that.

---

### Post by Tompalaz on 2010-03-09
Can you guys use the 2.6.32 -16 kernel?
My screen gets all messed up, I think it's related to nouveau.

---

### Post by Owen.C93 on 2010-03-09
> **Tompalaz said:**
> Can you guys use the 2.6.32 -16 kernel?
My screen gets all messed up, I think it's related to nouveau.
16 shouldn't need nouveau. Infact it was removed from my hardware drivers list and I'm now on nvidia. Try updating that is you can.

---

### Post by nanog on 2010-03-09
nperry, do you have the nouveau-firmware package installed? this does not necessarily get pulled in but is required for compiz.

---

### Post by Tompalaz on 2010-03-09
> **Owen.C93 said:**
> 16 shouldn't need nouveau. Infact it was removed from my hardware drivers list and I'm now on nvidia. Try updating that is you can.
I forced a update named xorg-xserver-nouveau. 
Now it works.

---

### Post by gnomeuser on 2010-03-09
I would just like to say, this is ROAFs world, we just live in it.

I have been hammering at nouveau for a while now, filing plenty of issues and he has been right on top of those suckers fixing things left and right. Always very helpful and ready to offer suggestions and help for potential fixes.

Right now though nouveau is going to present a problem for a number of users due to the module being moved. Users wanting to try the xorg-edgers ppa or the driver as presented in the ubuntu repos should be careful to avoid those nasty situations where X doesn't come up. Users on the preempt kernel also should know that neither nouveau nor the proprietary driver currently are not working properly (in fact the latter won't even install correctly, the prior won't install at all).

---

### Post by nperry on 2010-03-09
> **nanog said:**
> nperry, do you have the nouveau-firmware package installed? this does not necessarily get pulled in but is required for compiz.

Yes i do, Same is happening on .14, .15, .16

---

### Post by Taijitu on 2010-03-16
Just to add my 2 cents, the noveau packages from the xorg-edgers ppa works absolutely stunningly with the 9650M in my laptop. A lot more smooth in compiz than the nvidia packages.

But I can't use it. 3D plots in Maple 13 crashes X with noveau and I use that for math reports at my university... Rather sad, but damn, this project is going somewhere :-D

---

### Post by nanog on 2010-03-16
> A lot more smooth in compiz than the nvidia packages.

thats my impression too -- transitions now are smooth instead of jerky. 1080p is also completely tear free (for me). 


not having to deal with nvidia-settings, which has one of the worst user interfaces ever created, is a great relief.

---

### Post by vishalrao on 2010-03-16
> **nanog said:**
> not having to deal with nvidia-settings, which has one of the worst user interfaces ever created, is a great relief.

so where would i make settings like "enable vertical sync" vblank/refreshrates etc to (try to) ensure complete tear-free graphics/video? i dont think i found that info while casually browsing nouveau wiki etc...

---

### Post by Tompalaz on 2010-03-19
I dont get this should I have a xorg.conf or not?
What should it contain?

---

### Post by plun on 2010-03-20
Why spill time with buggy development software within an LTS.... ???


This is just STUPID !  Nouveau in present state is just CRAP, IMHO..!

Just makes NORMAL users disappointed !


--

---

### Post by cyberkilla on 2010-03-20
> **plun said:**
> Why spill time with buggy development software within an LTS.... ???


This is just STUPID !  Nouveau in present state is just CRAP, IMHO..!

Just makes NORMAL users disappointed !


--

Works for me, on a 8400M GT. The nVidia binary drivers are worse atm. Powermizer crashes the computer every time. I have to disable it, but then it runs at max performance forever.

This bug has been annoying me for months. Since the 185.x drivers even.

---

### Post by gnomeuser on 2010-03-20
Sadly the good times have ended, the xorg-edgers ppa stopped working with 3D for me and a number of users. A mere speedbump on the road to epicness I am sure though.

---

### Post by ibuclaw on 2010-03-20
> **gnomeuser said:**
> Sadly the good times have ended, the xorg-edgers ppa stopped working with 3D for me and a number of users. A mere speedbump on the road to epicness I am sure though.

On the bright side ... suspend now works for me (8400GS) :)

hibernate seems to just hang though... (not that I use it anyway)

---

### Post by ibuclaw on 2010-03-22
Nouveau + 3D rendering is back up and working again. :)

---

### Post by Tompalaz on 2010-03-22
> **ibuclaw said:**
> Nouveau + 3D rendering is back up and working again. :)
Yay!
But gnome-shell still won't work for me :frown:

---

### Post by gnomeuser on 2010-03-22
> **ibuclaw said:**
> Nouveau + 3D rendering is back up and working again. :)

Hurrah, the dark times are over. My windows wobble again and I can go back to focusing on more important things.

---

### Post by Tompalaz on 2010-03-27
I'm just curious, does gnome-shell work for you guys with the nouveau driver?

---

### Post by uRock on 2010-03-27
> **gnomeuser said:**
> In the process of testing the nouveau driver on Lucid with the xorg-edgers ppa (to confirm a fix for an XV bug) I noticed that compiz now runs on nouveau on my machine. I decided to push my luck and add rgba as well for that pointless blingy edge.

Long short of it, while not extremely fast it works and is standing up to abuse rather well.

Looks good. Buttons are on the wrong side though.

---

### Post by strobe on 2010-03-27
I have enabled the xorg-edger ppa's but can't get any desktop effects or compiz to work.  I notice in jockey I only see the Nvidia 173 and 96 drivers available.  What are the steps to activate the nouveau 3d functions.  

I love how well it works for desktop and video, I just really miss my compiz and emerald themes.  Any help?

---

### Post by Tompalaz on 2010-03-28
Can I enable nouveau for the 2.6.33 kernel?

---

