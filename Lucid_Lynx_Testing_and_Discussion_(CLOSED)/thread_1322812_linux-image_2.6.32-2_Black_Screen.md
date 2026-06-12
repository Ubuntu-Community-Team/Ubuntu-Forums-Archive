---
title: "linux-image 2.6.32-2 Black Screen"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-11-11
Black screen on boot of 2.6.32-2 on lucid. I can workaround with "nomodeset" or by booting 2.6.31-14.  This is IBM Thinkpad R31 with i845 video.  

[oops, this edit is a correction, the R31 has i830 video which goes black with Lucid 2.6.32-2 but not with lucid 2.6.31-14.  The Xorg driver 2.9.0 is the same on both, it's the linux-image that changed.  The IBM ThinkCentre with i845 still works with 2.6.32-2. ]

Tried to report this bug with apport and launchpad.  After climbing thru tons of windows with launchpad and apport, it says "send the report to the developers", then "something went wrong with launchpad" therefore I can't report the bug.

Jerry

---

### Post by VMC on 2009-11-11
> **jerrylamos said:**
> Black screen on boot of 2.6.32-2 on lucid. I can workaround with "nomodeset" or by booting 2.6.31-14.  This is IBM Thinkpad R31 with i845 video.

Tried to report this bug with apport and launchpad.  After climbing thru tons of windows with launchpad and apport, it says "send the report to the developers", then "something went wrong with launchpad" therefore I can't report the bug.

Jerry

I'm surprise it doesn't work for you. I have i865 and it was fixed weeks ago with kernel upgrade and intel newest driver.
 You do have the latest driver:
```
$ aptitude show xserver-xorg-video-intel|grep Ver
Version: 2:2.9.0-1ubuntu2
```

---

### Post by ranch hand on 2009-11-11
I would try updating.  I am now using 2.6.32-3.  Might help.

---

### Post by ls8 on 2010-01-12
Same problem here with ASUS L1400 notebook, i830m graphics, latest daily build Ubuntu 8.10 installed.

---

### Post by zika on 2010-01-12
> **ls8 said:**
> Same problem here with ASUS L1400 notebook, i830m graphics, latest daily build Ubuntu 8.10 installed.You are in Lucid forum...

---

### Post by VMC on 2010-01-12
> **zika said:**
> You are in Lucid forum...

Not only that, but this is a really old topic. At least as far as the kernel is concerned. I wonder if the OP's problem is fixed with todays updates and the newer kernel (2.6.32-10-generic).

---

### Post by lykwydchykyn on 2010-01-12
> **VMC said:**
> Not only that, but this is a really old topic. At least as far as the kernel is concerned. I wonder if the OP's problem is fixed with todays updates and the newer kernel (2.6.32-10-generic).

I've been testing Lucid on an old Dell with an 845 chipset and haven't been able to get X working for a while now.  I updated today and still no luck.  It works with the VESA driver but locks up when I log out or restart X.  But the intel driver fails every time.

Same thing happened on a second machine also with an 845 chipset.  These chipsets have never been exceptionally happy with Linux, but they at least worked.

---

### Post by LiquidMeson on 2010-01-12
Although I'm on 2.6.32-10 I had the same problem happen when updating yesterday, started up in single user, root, did a dist-upgrade and sudo apt-get install --reinstall upstart xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-core xserver-xorg and it seemed to fix my problem. :0 just randomly reinstall stuff

I'm on an lenovo x200

---

### Post by jalmargyyk on 2010-01-14
> **LiquidMeson said:**
> dist-upgrade and sudo apt-get install --reinstall upstart xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-core xserver-xorg

This helped me with my problems too. I'm running HP2510p with Intel GM965/GL960 Graphics driver and 2.6.32-10 kernel.

---

### Post by dziki on 2010-01-14
> **LiquidMeson said:**
> Although I'm on 2.6.32-10 I had the same problem happen when updating yesterday, started up in single user, root, did a dist-upgrade and sudo apt-get install --reinstall upstart xserver-xorg-video-all xserver-xorg-video-intel xserver-xorg-core xserver-xorg and it seemed to fix my problem. :0 just randomly reinstall stuff

I'm on an lenovo x200
I'm on Athlon64, kernel 2.6.32-10, graphics driver 'radeon' for HD3650 ati card, it helped me as well! Thanks :)

---

### Post by Peter09 on 2010-01-14
I have been having real problems following the Lucid release. For the last months I have struggled with a kernel error and a poor wireless connection.

Currently I have a crashing radeon driver that lets me operate for a few minutes (if I'm lucky) before a black screen, and I guess is connected to this thread, and a poor wireless connection which will only connect sometimes and then has poor performance. 

This is compounded by the fact that the wireless will not connect in recovery mode - so that makes it difficult to update without going into a GUI ...... sigh.

This is on a Toshiba Satellite Pro

---

### Post by zika on 2010-01-14
> **Peter09 said:**
> I have been having real problems following the Lucid release. For the last months I have struggled with a kernel error and a poor wireless connection.

Currently I have a crashing radeon driver that lets me operate for a few minutes (if I'm lucky) before a black screen, and I guess is connected to this thread, and a poor wireless connection which will only connect sometimes and then has poor performance. 

This is compounded by the fact that the wireless will not connect in recovery mode - so that makes it difficult to update without going into a GUI ...... sigh.

This is on a Toshiba Satellite ProI think it's not radeon driver. Look [at]("http://ubuntuforums.org/showthread.php?t=1347430")...

---

### Post by Peter09 on 2010-01-14
Hi Zika,
don't think this is relevant as I can get the crash at the login screen - but it does seem to be related to opening a window or application.

---

### Post by jerrylamos on 2010-01-14
> **Peter09 said:**
> 
Currently I have a crashing radeon driver that lets me operate for a few minutes (if I'm lucky) before a black screen, and I guess is connected to this thread, 
This is on a Toshiba Satellite Pro

First try to shut off KMS by doing "nomodeset".
at the initial grub menu, do 
e
then down arrow to the line with
quiet splash
then push end to add
nomodeset
then ctrl-x to boot.

If that works, then to make it permanent
sudo gedit /etc/default/grub
add nomodeset right after quiet splash so it looks like
"quiet splash nomodeset"
save
then do 
sudo update-grub

If you can get a wired or wireless connection running (good luck) read
[http://webmail.aol.com/30361-111/aim-2/en-us/mail/DisplayMessage.aspx?ws_popup=true](http://webmail.aol.com/30361-111/aim-2/en-us/mail/DisplayMessage.aspx?ws_popup=true)

which essentially says KMS is screwed up again.  Their recommendation is to do 
sudo apt-get install --reinstall xserver-xorg-core

That DOES NOT work on this IBM Thinkpad R31 with i830 video graphics.  I have to use nomodeset.

Good luck.  There is a littered history of problems with KMS.

Jerry

---

### Post by ls8 on 2010-01-14
> **zika said:**
> You are in Lucid forum...

My bad. I meant latest daily build 10.04 of course.

---

### Post by VMC on 2010-01-14
We have yet another xorg-sever-core and common update as of today, 01/14/2010. Maybe that will fix things.

---

### Post by ls8 on 2010-02-09
Latest update to linux kernel broke it again, even with "nomodeset" the LCD screen remains black.

---

### Post by DutchKillerBee on 2010-02-10
> **ls8 said:**
> latest update to linux kernel broke it again, even with "nomodeset" the lcd screen remains black.
Same here. :(
I am using a Dell latitude D600 with the radeon driver.

---

### Post by ratcheer on 2010-02-10
> **ls8 said:**
> Latest update to linux kernel broke it again, even with "nomodeset" the LCD screen remains black.

2.6.32.12 ?

Tim

---

### Post by gjoellee on 2010-02-10
> **ls8 said:**
> Latest update to linux kernel broke it again, even with "nomodeset" the LCD screen remains black.

You can do as I do...boot in recovery mode and select "resume", log in with your username and password and run:
```
startx
```

---

### Post by Kenny_Strawn on 2010-02-10
Have you tried updating "linux-modules" and "linux-image" at the same time?

If not, that's your problem. The kernel modules are just as important as the image. I tried installing "linux-image" by itself in Mint, and got a kernel panic.

---

### Post by ls8 on 2010-02-10
> **ratcheer said:**
> 2.6.32.12 ?
Tim
Yes. 2.6.32-12.


> **gjoellee said:**
> You can do as I do...boot in recovery mode and select "resume", log in with your username and password and run:
```
startx
```
Unfortunatelly I can't choose the Recovery mode, because the screen is black from the very start, neither the Grub menu is displayed.


> **Kenny_Strawn said:**
> Have you tried updating "linux-modules" and "linux-image" at the same time? If not, that's your problem. The kernel modules are just as important as the image. I tried installing "linux-image" by itself in Mint, and got a kernel panic.
I was updating the entire system, not just the linux-image. Now I tried to reinstall the whole system from latest daily build alternate CD, still the same problem. Probably the video driver for i810 does not work at all.

---

### Post by ls8 on 2010-02-10
_

---

### Post by gjoellee on 2010-02-10
> **ls8 said:**
> _

Can you even see BIOS load?

---

### Post by ls8 on 2010-02-10
_

---

### Post by ls8 on 2010-02-10
Yes, I can see BIOS to load, then this

[http://img713.imageshack.us/img713/1953/img0001ti.jpg](http://img713.imageshack.us/img713/1953/img0001ti.jpg)

 and then the screen goes black. A few seconds later I can hear the sound notifying that the system is up, but the screen is still black.

---

### Post by gjoellee on 2010-02-10
> **ls8 said:**
> Yes, I can see BIOS to load, then this

[http://img713.imageshack.us/img713/1953/img0001ti.jpg](http://img713.imageshack.us/img713/1953/img0001ti.jpg)

 and then the screen goes black. A few seconds later I can hear the sound notifying that the system is up, but the screen is still black.

Maybe GRUB does not appear because it is set to wait in 0 or 1 sec before it boots...Can you boot up a live and reinstall GRUB?

```
grub-install /dev/(you disk, usually "sda" i think)
```
NOTE: I am not sure if the solves your problem

...or you can open the grub conf (that is installed on your HDD) and post it in the forums so we can help modify it.

---

### Post by VMC on 2010-02-10
> **gjoellee said:**
> Maybe GRUB does not appear because it is set to wait in 0 or 1 sec before it boots...Can you boot up a live and reinstall GRUB?

```
grub-install /dev/(you disk, usually "sda" i think)
```
NOTE: I am not sure if the solves your problem

...or you can open the grub conf (that is installed on your HDD) and post it in the forums so we can help modify it.

Grub selection has to be working or he wouldn't get the the fsck message. I wonder if its not the plymouth problem that I was having. I chrooted to the defective install and removed plymouth than it booted ok with the "can't load plymouth..." message.

---

### Post by gjoellee on 2010-02-10
> **VMC said:**
> Grub selection has to be working or he wouldn't get the the fsck message. I wonder if its not the plymouth problem that I was having. I chrooted to the defective install and removed plymouth than it booted ok with the "can't load plymouth..." message.

He said:

> Unfortunatelly I can't choose the Recovery mode, because the screen is  black from the very start, neither the Grub menu is displayed.
So the grub menu obviously don't appear...

---

### Post by VMC on 2010-02-10
> **gjoellee said:**
> He said:


So the grub menu obviously don't appear...

It has to appear. Look at his image. It shows fsck command executing. That's late in the boot process, for post#26.

Edit: ok , I see, we were talking about the same thing. Your saying grub executes just it doesn't appear. I thought you said grub doesn't run. I was looking at his fsck image to determine that grub does in fact run. Seeing it to make a selection is something else...

---

### Post by VMC on 2010-02-10
> **ls8 said:**
> Yes, I can see BIOS to load, then this

[http://img713.imageshack.us/img713/1953/img0001ti.jpg](http://img713.imageshack.us/img713/1953/img0001ti.jpg)

 and then the screen goes black. A few seconds later I can hear the sound notifying that the system is up, but the screen is still black.

ls8, Look at your "/etc/default/grub" file.

Here's a portion of mine, and I have a full 10 seconds window to select:
```
...
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
...
```

---

### Post by ls8 on 2010-02-11
Something is happening with the X.org and/or with ihe 'intel' video driver. Today's update changes the situation, the login screen appears, but the computer freezes a few seconds later, probably this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001) ?

---

### Post by falconindy on 2010-02-11
This is a known bug -- one that I'm unfortunately personally familiar with on my laptop. If I boot with KMS enabled, DRM crashes when the i915 driver is installed. If I boot without KMS, X hangs on starting. I've tried throwing every git version of DRM, DRI, or video driver at the issue and have made zero headway.

Problem persists even through 2.6.32.8 (released yesterday).

I can't find the lkml post that referenced this, but I was able to dig up something off [Redhat's Bugzilla]("https://bugzilla.redhat.com/show_bug.cgi?id=540218"). Unfortunately, the proposed solution (which is sent upstream to freedesktop) isn't even related to the initial reporter's issue (who fixed his ish by downgrading to .31).

---

### Post by VMC on 2010-02-11
> **ls8 said:**
> Something is happening with the X.org and/or with ihe 'intel' video driver. Today's update changes the situation, the login screen appears, but the computer freezes a few seconds later, probably this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001) ?

I'm not sure if this will help, but remove quiet and splash from linux line and see if it freezes shortly after plymouth and before fsck comes up. When that happened to me, removing plymouth remedied the situation. I have an Intel i865 video chip.

Also, when I used "nomodeset" it booted but froze shortly thereafter.

---

### Post by zika on 2010-02-11
> **VMC said:**
> Also, when I used "nomodeset" it booted but froze shortly thereafter.Funny, my machine reacts completely the opposite: with KMS it freezes (randomly distributed accreoss the interval of several minutes to 12+ hours), with nomodeset it is solid as a rock... 2.6.3{2,3}-{12,13,999}-{generic,preempt}...

---

### Post by ls8 on 2010-02-12
I removed "quiet splash" and "nomodeset" from the kernel configuration in /boot/grub/grub.cfg. Now I can see the entire boot process, everything looks fine. The machine freezes at the moment when X.org starts, screen turns black and I have to hard reboot the machine. So it really looks like some problem in X.org and driver for intel i810. (?)

Edit: recovery mode freezes too, so it might not be related to X.org???

Edit2: with nomodeset I can access the recovery mode, I am now upgrading the system, kernel 2.6.32-13 is out.

Edit3: with kernel 2.6.32-13 I am back in game, as long as I keep the 'nomodeset' option in the grub configuration

---

### Post by johncc330 on 2010-03-19
Hi guys,
I believe I'm having exactly the same problem, and though I'm not an Ubuntu user, this may actually eliminate a lot of guessing. Here are some my adventures:

- I had a small aesthetic problem with the old xf...intel driver (version 1.2 or so), so I decided to install a newer version of Xorg from Slackware (my system _is_ Slackware). So I installed from version 13.0, and everything went south. With KMS on, the screen goes black (no backlight either) in the middle of the boot sequence (in text mode!). With nomodeset, booting goes fine, but startx doesn't work with a message indicating 'no mode switcher detected'.

- I tried with the original kernel,2.6.29, with 2.6.31, and now have 2.6.33 installed. No go.

- I tried with xf86video-intel versions 2.10.0 (from Slackware current), didn't work. I tried, as indicated on a SW board, to install older versions from the SW CD extras, but didn't even run, lacking a symbol somewhere. Finally, I downloaded the 2.8.1 source, compiled it, and have the same 'mode switcher' message.

I'm about to give up - there is something very strange going on with the latest kernel versions + xorg versions. I've seen quite a few heated words, even from Linus himself.

About to delete the entire X server and go back to a non-mode switcher version.
Any ideas?

John

Just an additional hint: I'm not even using Grub (LILO here).

---

### Post by jerrylamos on 2010-03-20
Johncc330, I'm not familiar with Slackware but have run Slax on this Thinkpad R31 intel i830 video graphics.  

"nomodeset" is absolutely required even now with Lucid Beta 1 linux 2.6.32-16.  I haven't tried 2.6.33 yet.

I have seen some statements from Ubuntu developers that claim KMS helps something or other, but to me it is a pain.

No I don't switch users.  Why would I?  I'm the only user on this PC.  I use 4 pc's for testing, my wife uses 2 others for website work, we're both the only users on our pc's, so what use is KMS anyway??

Thanks, Jerry

---

### Post by foxy123 on 2010-03-20
I've got the same problem with Beta 1. Firstly I had to use an alternative CD to install it because teh LiveCD did not boot for the same problem. Now I have it installed but I cannot boot into Beta. I've got nomodeset. One more thing. I use 2.26.32-10 kernel in Karmic on the same laptop and while booting up the screen also going black but moving a mouse brings GDM up again. If the problem is not fixed I will have to stick to Karmic even after Lucid is released.

---

### Post by noobie1 on 2010-03-20
I have i845G card which I would really like to get working, and so am willing to follow any pointers of things to do and report to get the 10.4 working well.

Lucid(beta1) had trouble on start up, so I removed "quiet splash" which worked most of the time with Karmic (although some kernel/xorg/other updates broke it).  

To the person not seeing Grub menu, you may need to hold shift at boot for it to appear.

At least it boots but now need to resolve a couple other issues (shutdown not working (may be fixed now), get wireless settings to be default, screen remains off after power management turns it off, etc)

---

### Post by dentaku65 on 2010-03-21
> **ls8 said:**
> Something is happening with the X.org and/or with ihe 'intel' video driver. Today's update changes the situation, the login screen appears, but the computer freezes a few seconds later, probably this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/511001) ?

I think that your bug is here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/447892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/447892)
Mine too :-)

---

### Post by DougEdey on 2010-03-21
I had to use nomodeset as well to get anything to work

---

### Post by johncc330 on 2010-03-22
> **jerrylamos said:**
> Johncc330, I'm not familiar with Slackware but have run Slax on this Thinkpad R31 intel i830 video graphics.  

"nomodeset" is absolutely required even now with Lucid Beta 1 linux 2.6.32-16.  I haven't tried 2.6.33 yet.

I have seen some statements from Ubuntu developers that claim KMS helps something or other, but to me it is a pain. ... snip... So what use is KMS anyway??


Hi Jerry.

As far as I can ascertain, KMS is kernel mode switcher, which does some of the work which before was done in
either Xorg or the actual Intel driver, I don't know. I you 'nomodeset', then mode switching can
either be done manually (not any more with 2.6.32), or not at all. (X complains on startup)

So, again, as far as I know, you _need_ KMS now, unless, maybe, you are running an older xorg
version, with older intel drivers that don't depend on it. Maybe you are updating the kernel separately from the
distro? You need KMS for the new version, else X won't start with Intel drivers.

John

---

### Post by foxy123 on 2010-03-23
> **johncc330 said:**
> Hi Jerry.

As far as I can ascertain, KMS is kernel mode switcher, which does some of the work which before was done in
either Xorg or the actual Intel driver, I don't know. I you 'nomodeset', then mode switching can
either be done manually (not any more with 2.6.32), or not at all. (X complains on startup)

So, again, as far as I know, you _need_ KMS now, unless, maybe, you are running an older xorg
version, with older intel drivers that don't depend on it. Maybe you are updating the kernel separately from the
distro? You need KMS for the new version, else X won't start with Intel drivers.

John

So does it mean if the hardware does not support KMS I  cannot use Lucid? In my case it is what seems to happen. If I do not use 'nomodeset' I've got a black screen from the beginning, but if I use it, the boot hangs up before GDM starts.

---

### Post by jerrylamos on 2010-03-23
On i845 intel Graphics, the latest Lucid Beta 2.6.32-17 is booting with KMS on.  Most of the releases/updates since KMS started won't boot modeset=1 default but it is at the moment.

All I can tell about KMS is if I switch to a command line with Ctrl-Alt-F1 I get little tiny print, and Ctrl-Alt-F7 gets me back to the desktop.  I only do this when something is busted as in xorg or xserver or firefox crash.

Jerry

---

### Post by johncc330 on 2010-03-26
> **foxy123 said:**
> So does it mean if the hardware does not support KMS I  cannot use Lucid? In my case it is what seems to happen. If I do not use 'nomodeset' I've got a black screen from the beginning, but if I use it, the boot hangs up before GDM starts.

As I wrote before, I am not an Ubuntu user (many of my students are), which does make this
problem non-distro related. I don't know the intricacies of Lucid, but I suspect you are experiencing
the same problem as I.

I also suspect the problem is not the hardware not supporting KMS, but the kernel driver failing,
as the black screen problem appears before I start X and mode switching was present
earlier. As I understand it, the kernel switching code was moved from X to the kernel, 
and has since caused problems (at least for Intel 855GM).

That said, I experienced several freezes while using the VESA driver today. Only exit was the
power button being detected and starting an orderly shutdown. Never had so many problems
before. And KMS is not the only change. Libxcb-xlib was eliminated in Xorg, and several other
packages were dependent on that library and have to be updated (pango, pangoui, gtk+, 
and several others).

John


John

---

### Post by jerrylamos on 2010-03-27
> **jerrylamos said:**
> On i845 intel Graphics, the latest Lucid Beta 2.6.32-17 is booting with KMS on.  Most of the releases/updates since KMS started won't boot modeset=1 default but it is at the moment.

All I can tell about KMS is if I switch to a command line with Ctrl-Alt-F1 I get little tiny print, and Ctrl-Alt-F7 gets me back to the desktop.  I only do this when something is busted as in xorg or xserver or firefox crash.

Jerry
I update, safe-upgrade every day.  Haven't gotten black screen on 2.6.32-17 for the last 2 days on this intel i845 video graphics with KMS on.  I've also had trouble with 2.6.32-17 on IBM Thinkpad T40 with ati video graphics however not for with the last 2 days updates either.
 Do note I run with visual effects none because visual effects doesn't do much on full screen applications and does insert in-line code.

Jerry

---

### Post by foxy123 on 2010-03-27
I now drop to shell. No graphic interface :(

---

### Post by foxy123 on 2010-03-28
OK, I do not have to use 'nomodeset' but I drop to shell instead of GDM login screen. If I try to start GDM I have some errors. However, I can run startx to get to a graphic mode. Though no daemon runs there: no sound, no network.

---

### Post by seattle vic on 2010-03-28
I'm currently stuck in the maintenance shell, I think since the upgrade to 2.6.32.17.

I've tried pretty much everything I can find on these forums.  KMS disabled, nomodeset, plymouth splash file deleted, plymouth package removed, nouveau disabled, no xorg,conf file, then xorg.conf file with nv driver, removed and reinstalled plymouth, mountall and several other packages I thought might be relevant.  I also checked all my packages for errors.

Nothing has worked.  However, I do still notice a couple things:

I get the initial login screen with graphics, so X and gdm seem to be working.  I log in and then get the maintenance shell screen in the upper left corner.  Gdm is running and if I restart it, same thing.  Same with startx, it's running also.

During the boot up I still get a message that plymouth is terminated with status 1.

When I pull the logs, the xorg log looks OK, but I keep getting a message in the syslog:

gdm-session-worker[1538]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

I haven't figured that out.

So I'm stuck, and can't think of anything else to try except wait around for package updates.  Anybody else figured this out?

---

### Post by seattle vic on 2010-03-29
Well, just before giving up for the night, I was going through bug reports related to this and came across one that suggested to install gnome-session.  I did not look to see if I already had it installed, but presume that I did.

Anyway, it worked.

---

