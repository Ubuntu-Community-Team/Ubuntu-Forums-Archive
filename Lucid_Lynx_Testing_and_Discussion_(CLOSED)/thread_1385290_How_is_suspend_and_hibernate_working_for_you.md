---
title: "How is suspend and hibernate working for you?"
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autark on 2010-01-19
I'm very dependent on having at least suspend to RAM working on my computer, since I like to suspend it whenever I leave it. Hibernate is also good to have, since shutting down and restarting will not return all applications to their state on shutdown (some apps not restarted, other apps opening on the wrong desktop, heavy reload of all open tabs in web browser, etc.). 

With Lucid, I'm having trouble with hibernate on one of my computers (my test machine), and trouble with suspend on my main machine. I never got to run Karmic successfully on these machines, but they both worked flawlessly with Jaunty. 

My test machine hibernates OK but it will not resume - it boots as if hibernation never took place. At the beginning of the Lucid cycle, I would not have this trouble, and I don't know what has caused the regression. I have filed a bug which so far has not received any attention whatsoever: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/499940](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/499940). 

I have not been able to test suspend and hibernate on my main machine until now, due to the trouble with the Nvidia drivers; suspend and hibernate has never worked without the proprietary video drivers on this machine. Now that I have Nvidia drivers working under Lucid, I find that the machine will not resume from either suspend or hibernate. 

So, I'm asking: how is suspend and hibernate working for you? Even if you don't personally need suspend or hibernate, I would be great if you tried it at least once and reported back. After all, we are testers, aren't we?

---

### Post by Jordanwb on 2010-01-19
> **autark said:**
> So, I'm asking: how is suspend and hibernate working for you?

Never use it, even on my laptop.

> **autark said:**
> Even if you don't personally need suspend or hibernate, I would be great if you tried it at least once and reported back.

Very well.

*Edit*

Standby works fine. My wifi gets disconnected but it reconnects quickly.

---

### Post by autark on 2010-01-19
> **Jordanwb said:**
>  Standby works fine. My wifi gets disconnected but it reconnects quickly.

Thanks for trying! And hibernate? Or is that asking too much?

---

### Post by ciem on 2010-01-20
I will be thankful for telling me how to make hibernate or/and suspend mode work. On my Lenovo Y530 (Karmic 9.10 x86) these modes simply doesn't work properly. Laptop is still working but the screen is black and I can't get back to system.

---

### Post by garcot on 2010-01-20
Well the machine goes to sleep fine, but when I press the wakeup button, I get a dirty, multicolor, stupid screen with no X. I just do control+Alt+F1 and without logging in, I press Control+Alt+F7 and the original gnome screen ( X ) is back. Wireless network also wakeup without any issues.

But, if compiz is installed, Ram usage goes up by 200Mb. 

Hope it helps.

Garcot

---

### Post by autark on 2010-01-20
> **ciem said:**
> I will be thankful for telling me how to make hibernate or/and suspend mode work. On my Lenovo Y530 (Karmic 9.10 x86) these modes simply doesn't work properly. Laptop is still working but the screen is black and I can't get back to system.

I don't really know. I suggest you search on the Ubuntu site, I think there is a wiki page with detailed information on debugging suspend and hibernation. 

But I know for certain that on my laptop with nvidia graphics, I have to use the proprietary drivers; otherwise the machine locks up on resume.

---

### Post by VMC on 2010-01-20
They both seem to work, but I never use the one because I can't seem to be able to get out of hibernate. I have Dell Optiplex and the power button flashes in hibernate. Probably seem strange key combination but I can't find it.

Edit: ok, now suspend works. I just push the flashing power light and it boots to previous state. The hibernate saves info then just powers the computer off. So it looks like hibernate doesn't work or I don't know how to work it.

---

### Post by hobo on 2010-01-20
Suspend is working for me on a Lenovo R61e

---

### Post by autark on 2010-01-20
> **garcot said:**
> Well the machine goes to sleep fine, but when I press the wakeup button, I get a dirty, multicolor, stupid screen with no X. I just do control+Alt+F1 and without logging in, I press Control+Alt+F7 and the original gnome screen ( X ) is back. Wireless network also wakeup without any issues.

But, if compiz is installed, Ram usage goes up by 200Mb. 


Do you have nvidia graphics? I have recently filed bug #510004, [https://bugs.launchpad.net/bugs/510004](https://bugs.launchpad.net/bugs/510004), which looks very similar. I have not observed the RAM usage on my machines.

---

### Post by autark on 2010-01-20
> **VMC said:**
> They both seem to work, but I never use the one because I can't seem to be able to get out of hibernate. I have Dell Optiplex and the power button flashes in hibernate. Probably seem strange key combination but I can't find it.

Edit: ok, now suspend works. I just push the flashing power light and it boots to previous state. The hibernate saves info then just powers the computer off. So it looks like hibernate doesn't work or I don't know how to work it.

Well, you shouldn't really have to know how to work it, so I'd say it's broken if you can't make it resume by pressing the power button. 

I have found a couple of bug reports concerning Dell Optiplex and suspend/resume, but none for Lucid. Would you mind filing one?

---

### Post by garcot on 2010-01-20
AutArk,

Yes, I do have nvidia graphics card. Have you tried 2.6.33 rc4 kernel and  install nvidia 195 beta driver through the installer? 

At present, You can always allow the machine to suspend as per power-manager settings. However, at wakeup, you may have to follow Ctrl+Alt+F1 then Ctril+Alt+F7 to get back a working graphical desktop.

Garcot

---

### Post by joey-elijah on 2010-01-20
*Sigh*

Suspend doesn't work (i hear a "bleep" and my harddrives spin back up as it tries) but hibernate does (though i find it pointless for my situation)

And yes i am a poor Nvidia user.

---

### Post by autark on 2010-01-20
> **garcot said:**
>  Yes, I do have nvidia graphics card. Have you tried 2.6.33 rc4 kernel and  install nvidia 195 beta driver through the installer? 

No, I'm afraid that would contaminate my test environment too much.

> **garcot said:**
> At present, You can always allow the machine to suspend as per power-manager settings. However, at wakeup, you may have to follow Ctrl+Alt+F1 then Ctril+Alt+F7 to get back a working graphical desktop.

Yeah, I found out something similar. But it's not something I can live with in the long run.

---

### Post by autark on 2010-01-20
> **joey-elijah said:**
> *Sigh*

Suspend doesn't work (i hear a &quot;bleep&quot; and my harddrives spin back up as it tries) but hibernate does (though i find it pointless for my situation)

And yes i am a poor Nvidia user.

Your problems seem different from mine. They may not be Nvidia-related in the first place. Have you searched for bugs?

---

### Post by phillw on 2010-01-20
All seem to work on my Gateway Laptop.

Regards,

Phill.

---

### Post by joey-elijah on 2010-01-20
> **autark said:**
> Your problems seem different from mine. They may not be Nvidia-related in the first place. Have you searched for bugs?

Hmm i probably should but my nvidia card has never worked with Suspend in all my time using Ubuntu (Hardy - now) so i always assumed it was just a Nvidia thing.

---

### Post by garcot on 2010-01-20
Autark,

I just tried patched NVIDIA 195.30 beta driver with 2.6.33 rc4 kernel and gnome-power-manager works fine.
No problems with X and all the funny problems and the required monkey tricks on Wakeup are gone. To add, 2.6.33 kernel is really very fast and quite stable considering it is still in rc.

The one issue which still persists however is mountall , which anyway is not connected to this thread.

Garcot

---

### Post by rogue_0111 on 2010-01-20
A bit flaky on my Dell laptop. I have a 50/50 chance of my wireless to work when I bring her back up. The desktop is a NoGo too. She won't come back at all from hibernation.

Kinda sux but I'll live. Got to work on my programming skillz'!!!

---

### Post by uBeer on 2010-01-28
Well, suspend works almost fine. Everything works except that the fans of my laptop don't work after waking up. That makes suspend/waking up useless because I almost burned my laptop last time while I was installing some packages after waking up the laptop and only noticed it when it got kinda hot...

Does anyone know which package I can file a bug against? Is this gnome-power-manager that is acting up (or actually not acting at all)?

---

### Post by Marlonsm on 2010-01-28
I'm in Kubuntu 9.10 and neither are working. When I click to suspend the system does suspend and the power light starts blinking, just like it should do. But when I try to wake it, the computer just turns on as if it was off. Same happens to hibernate.

In 9.04 and 8.10 both worked.

---

### Post by philinux on 2010-01-28
Kills net and mutes sound.

As autark says known bug.

---

### Post by autark on 2010-01-28
> **uBeer said:**
>  Does anyone know which package I can file a bug against? Is this gnome-power-manager that is acting up (or actually not acting at all)?

I think it's more low-level than that. acpid could be a good starting point. Or linux.

---

### Post by autark on 2010-01-28
> **Marlonsm said:**
> I'm in Kubuntu 9.10 and neither are working. When I click to suspend the system does suspend and the power light starts blinking, just like it should do. But when I try to wake it, the computer just turns on as if it was off. Same happens to hibernate.

In 9.04 and 8.10 both worked.

The "known bug" I've been referring to only concerns resume from hibernation, not resuming from RAM. I have filed another bug about resuming from RAM with nvidia, but it concerns strange graphics effects (nvidia).

---

### Post by uBeer on 2010-01-28
> **autark said:**
> I think it's more low-level than that. acpid could be a good starting point. Or linux.

And if I get it wrong, then somebody else can move it into the proper section, right?

For people that are interested/affected:
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/513798](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/513798)

---

### Post by Malzan on 2010-01-28
Hi,

Just transferred my install from Wubi to a dedicated install in order to enable hibernation (which is not supported for Wubi-based installs) - only to find that ubuntu resumed with a fresh desktop and none of my work was saved. D'oh! However, adding 

resume=/dev/sda4 (path to my swap partition) to the kernel entry in menu.lst 

resolved the issue (was mentioned in the bug report mentioned earlier: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940)). So, now it works just fine and I am a happy hibernator! :)

Bye,
Malzan

---

### Post by phenest on 2010-01-28
Dell Precision M90 (same as XPS M1710)

Standby: Screen is not lit on resume.

Hibernate: On resume, any previously open apps are not open. Network is disabled and needs enabling manually.

Works perfectly under Jaunty.

---

### Post by ikt on 2010-01-28
I asked about this in the previous cycle as well:

[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

Are we getting better?

---

### Post by Jordanwb on 2010-01-28
> **autark said:**
> Thanks for trying! And hibernate? Or is that asking too much?

I don't have a swap partition or volume to use.

---

### Post by Ibidem on 2010-01-28
With pm-suspend, suspend "works" except it kills wireless.  IIRC, that seems to be  a standard bug with Atheros chipsets.  No graphics issues, don't think there's trouble with sound.
No idea how to hibernate...while using IceWM.  If there's a command to do it, I'll try.
Ibidem

---

### Post by llawwehttam on 2010-01-28
Both work fine on my laptop. However after the newest kernel update neither work on my desktop. Not too bothered though as boot time is low.

---

### Post by msrinath80 on 2010-01-28
For those of you with the Suspending console(s) followed by a hang problem, try to run just these two commands as root:

1. echo shutdown > /sys/power/disk
2. echo disk > /sys/power/state

It caused my Fujitsu S7110 Lifebook to hibernate without any issues whatsoever. Whenever I tried using either pm-hibernate or s2disk even after issuing the first command, it would hang. But Using the second command caused the system to hibernate peacefully. BTW I'm using Debian Lenny 32 bit.

---

### Post by ikt on 2010-01-29
bump

---

### Post by Ibidem on 2010-01-29
> **Ibidem said:**
> With pm-suspend, suspend "works" except it kills wireless.  IIRC, that seems to be  a standard bug with Atheros chipsets.  No graphics issues, don't think there's trouble with sound.
No idea how to hibernate...while using IceWM.  If there's a command to do it, I'll try.
Ibidem

OK, it's pm-hibernate to hibernate--will try very soon.
Workaround for the wireless bug (to be run as administrator...)
```
#!/bin/bash
#Workaround for wireless that doesn't work on resume from suspend
#Replace 'ath5k' with the appropriate module for your computer
sudo modprobe -r ath5k
sudo pm-suspend
#And this runs after resume...
sudo modprobe ath5k
```

That fixes it for me.
Now I'll see about hibernate.

---

### Post by Ibidem on 2010-01-29
As for others, resume from hibernate isn't working.  Some message about "hibernate state detected, run..."
flashed by too quick to read.
Network does run, but it seems that Ubuntu is just ditching all the info.

Anyone else figured out how to get past that?  I suspect it's some sort of playing with GRUB, but I haven't figured it out.
Ibidem

---

### Post by autark on 2010-01-30
Funny, what with all the other issues I'm having with suspend and hibernate, I'm not having any network trouble. Or I haven't looked carefully enough.

---

### Post by dimeotane on 2010-01-31
This sounds like what happened on my Sony Vaio desktop.  Some funky multicolor modern art squares all over the screen.  

> **garcot said:**
> Well the machine goes to sleep fine, but when I press the wakeup button, I get a dirty, multicolor, stupid screen with no X.

---

### Post by autark on 2010-01-31
> **dimeotane said:**
> This sounds like what happened on my Sony Vaio desktop.  Some funky multicolor modern art squares all over the screen.

Nvidia graphics?

---

### Post by Ibidem on 2010-01-31
Hibernate: doesn't work "out of box" because the kernel needs an option 
resume=/dev/sd**
where /dev/sd** is the swap partition where the hibernation data was stored.
If this is added to the boot entry, hibernate works.
Suspend: Some drivers (especially graphics and wireless) must be reinitialized when resuming.
Wireless drivers of this sort, at least, should be specified in /etc/pm/config.d/modules for reloading.
E.g., 
SUSPEND_MODULES="ath5k othermodule"

uBeer may want to specify his fan module in this file, I think.

There are provisions for reinitializing the screen.   See "man pm-suspend" for details.
If you're using suspend or hibernate, you're using pm-utils; Gnome & KDE both use this as a backend.

Not all cards need workarounds, and not all wireless drivers need reinitializing.

Ibidem

---

### Post by Starks on 2010-01-31
Too scared to try:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/496842](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/496842)

---

### Post by ranch hand on 2010-02-01
I was reading in the blue print last night and I think that is supposed to be fixed for A3.

---

### Post by autark on 2010-02-01
> **ranch hand said:**
> I was reading in the blue print last night and I think that is supposed to be fixed for A3.

Good to see that. But I'm afraid it will take longer than that. Right now there are a number of regressions to deal with, and I have not yet seen any developer interest concerning these bugs.

---

### Post by code850 on 2010-02-01
One weird thing with suspend is the following: if i click logout button on gnome panel and then select suspend, it suspends fine. And it resumes perfectly. But, if i close the laptop lid, then it suspends fine, but now it can't resume. The screen is dead and the keyboard is working.

---

### Post by dimeotane on 2010-02-02
Yes, I've got an Nvidia card and drivers on this system.  Good guess.

> Quote:
Originally Posted by dimeotane View Post
This sounds like what happened on my Sony Vaio desktop. Some funky multicolor modern art squares all over the screen.

Nvidia graphics?

---

### Post by Ibidem on 2010-02-03
I've been looking at the docs on pm-suspend (the backend for GNOME's suspend functionality, designed to work around driver/hardware issues)
"man pm-suspend" has some interesting info:
1. pm-suspend uses HAL when available to detect the proper quirks to use
IE, no HAL==no hardware detection.  Installing HAL should solve the screen issues.
2. --quirk-dpms-on
Forces the screen on when resuming.  
If you've got the black screen on resume, that's the best choice.

3. For the screwed-up screens:
--quirk-vbe-post  (MAY CAUSE LOCKUP if you don't need it but still use)
Reinitializes the screen on resume by running bootup video code.

--quirk-vbemode-restore  (NOT FOR INTEL GRAPHICS)
Save & restore current screen VESA mode  (avoids X corruption)

--quirk-vbestate-restore
save & restore some low-level hardware state

--store-quirks-as-lkw
Saves working quirks (system-dependent); will be used thereafter

Despite the warnings about running it directly, I find that pm-suspend works well.
I'd run just the terminal, try 
sudo pm-suspend --quirk-vbestate-restore 
(safest), if it fails try 
sudo pm-suspend --quirk-vbemode-restore
(for those with NVIDIA graphics; should work)

If either works, repeat with the --store-quirks-as-lkw option
I suspect that after that, the standard suspend should work.
You could also try installing HAL, running sudo pm-suspend --store-quirks-as-lkw,
and then removing HAL; if you're lucky, it would autodetect quirks and save them.

This is just per my reading of the man page; don't try it if you aren't willing to reset the computer manually if needed.  I don't think it will do anything after reboot (beyond storing successful options).

Ibidem

---

### Post by code850 on 2010-02-03
>>IE, no HAL==no hardware detection.  Installing HAL should solve the screen issues.

But Lucid droped using hal, no?

>>2. --quirk-dpms-on
>>Forces the screen on when resuming.  
>>If you've got the black screen on resume, that's the best choice.

Any idea where to put '--quirk-dpms-on'?

---

### Post by Jordanwb on 2010-02-03
Has anyone had a problem with unlocking the screen after resuming from suspend? For me, after powering on my laptop after suspension, the unlocking window sort of lags.

---

### Post by mikeyphi on 2010-02-03
On my Desktop - when not in use, the screen goes dark....on subsequent input I'm presented with the log-in screen and have to log in.

---

### Post by phillw on 2010-02-05
Just coming through on the release e-mails...

> gnome-power-manager (2.29.2-0ubuntu1) lucid; urgency=low

  * New upstream release:
    - Move the power management preferences into the hardware section of  the
      control center.
    - Use the name of 'Power' for the power management preferences  capplet
    - Don't rely on the cached value of the lid status, to fix a double
      suspend issue (LP: #425411)
    - Add a flag to inhibit consolekit events just after we resumed
    - Don't automatically suspend if there are suspend inhibits
    - Do not exit if hal is not available
    - Only connect to HAL if there is no xrandr backlight hardware
    - Fix compile when using an ld that defaults to --as-needed
    - Enable the help action in gnome-power-statistics. Fixes #607005
    - Ensure the window is realized before we invalidate it. Fixes  #604918
    - Don't show the user a sleep failed link pointing to the quirk site
    - Show the device name even when using UPower
    - Translation updates.
  * Drop patches accepted upstream:
    + 03-run-without-hal.patch
    + 04-dont-connect-to-hal-with-xrandr.patch
    + 09-fix-double-suspend.patch
  * Regenerate 90-autotools.patch.



It should hit for update shortly. I'm hoping it sorts (some of) the problems out.

Regards,

Phill.

---

### Post by phenest on 2010-02-06
> **phillw said:**
> Just coming through on the release e-mails...



It should hit for update shortly. I'm hoping it sorts (some of) the problems out.

Regards,

Phill.

I hope so. Nothings working here at all.

---

### Post by Yanno on 2010-02-06
I use the same PC as you.I have a bothering problem in suspending in Karmic,it never resume.The hibernation is just okay.It seems like something incompatible with some hardware driver.

---

### Post by timosha on 2010-02-07
On my IBM Thinkpad R51 2887:

Suspend/hibernate works perfectly in Karmic. Doesn't work at all in Lucid.

---

### Post by odysseusjak on 2010-03-01
> **philinux said:**
> Kills net and mutes sound.

As autark says known bug.

Ditto.

---

### Post by timosha on 2010-03-01
But surprisingly resume/suspend works perfectly on my Thinkpad R51 in Kubuntu 10.04 Alpha 3.

---

### Post by timosha on 2010-03-03
With today's update of gnome-power-manager my suspend/hibernate problem is solved. Gnome-power-manager makes now a call to upower instead of devkit-power. This solved the problem.

---

### Post by sgage on 2010-03-03
Still no resume for me as of today's updates. Things seem to power up, but no signal at all to the display. Oh well.

---

### Post by nerdy_kid on 2010-03-03
> **autark said:**
> I'm very dependent on having at least suspend to RAM working on my computer, since I like to suspend it whenever I leave it. Hibernate is also good to have, since shutting down and restarting will not return all applications to their state on shutdown (some apps not restarted, other apps opening on the wrong desktop, heavy reload of all open tabs in web browser, etc.). 

With Lucid, I'm having trouble with hibernate on one of my computers (my test machine), and trouble with suspend on my main machine. I never got to run Karmic successfully on these machines, but they both worked flawlessly with Jaunty. 

My test machine hibernates OK but it will not resume - it boots as if hibernation never took place. At the beginning of the Lucid cycle, I would not have this trouble, and I don't know what has caused the regression. I have filed a bug which so far has not received any attention whatsoever: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/499940](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/499940). 

I have not been able to test suspend and hibernate on my main machine until now, due to the trouble with the Nvidia drivers; suspend and hibernate has never worked without the proprietary video drivers on this machine. Now that I have Nvidia drivers working under Lucid, I find that the machine will not resume from either suspend or hibernate. 

So, I'm asking: how is suspend and hibernate working for you? Even if you don't personally need suspend or hibernate, I would be great if you tried it at least once and reported back. After all, we are testers, aren't we?

i had had suspend and hibernate issues with the nvidia driver as well, i am currently running the beta (195.36.03) drivers and so far no issues :)  My card is in my sig so maybe this driver will help you.

---

### Post by autark on 2010-03-03
> **nerdy_kid said:**
> i had had suspend and hibernate issues with the nvidia driver as well, i am currently running the beta (195.36.03) drivers and so far no issues .

Maybe it's time for a status update (it was I who started this thread):

[LIST]
[*]Hibernation has been fixed.
[*]On my main laptop, with a GeForce 8600M GS card and nvidia 195.36.03, I'm still having difficulty activating the screen, and I get corrupted graphics after resume. Also, if I'm running Gnome, the screen will come back dimmed to the lowest setting.
[*]On my second laptop, with Intel graphics, my major remaining problem is that the screen saver is not consistently actived under KDE. Furthermore, KDE does no longer respond to the suspend button, and KDE is very reluctant about suspending on lid close.
[/LIST]
So, it's something of a mixed bag. And this used to work almost perfectly under Jaunty. With the graphics problems on my main laptop, it looks like I won't be able to make the switch from Jaunty to Lucid, which is quite sad.

---

### Post by phenest on 2010-03-03
Oddly, a few days ago, I lost the ability to hibernate. It doesn't appear in the shutdown dialog. Any ideas?

And I've also noticed I can invoke the shutdown dialog with music playing in Rhythmbox (with the Power Manager plugin enabled). But that might be a Rhythmbox issue.

---

### Post by alexandari on 2010-03-03
The both never worked for me...so I stopped using them. I'm gonna try today,see what happens...

---

### Post by Ibidem on 2010-03-03
If it doesn't work, check where you have swap mounted:
```
cat /etc/fstab|grep swap
```and specify the first partition listed with resume=/dev/sdXY.
I.e., if you get something like this: (my own output)
```
# swap was on /dev/sda11 during installation
UUID=0f6fb455-fd8c-418b-90dc-59735c3aaf68 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=4dcd85cb-ac09-46e1-9913-4595ac8320e7 none            swap    sw              0       0
# swap was on /dev/sda9 during installation
UUID=518c7fd8-1a31-45ef-8dc3-7958fc468299 none            swap    sw              0       0
```append to the boot options:
resume=/dev/sda11

Then hibernate should work.

Ibidem

---

### Post by phenest on 2010-03-03
> **Ibidem said:**
> If it doesn't work, check where you have swap mounted:
```
cat /etc/fstab|grep swap
```and specify the first partition listed with resume=/dev/sdXY.
I.e., if you get something like this: (my own output)
```
# swap was on /dev/sda11 during installation
UUID=0f6fb455-fd8c-418b-90dc-59735c3aaf68 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=4dcd85cb-ac09-46e1-9913-4595ac8320e7 none            swap    sw              0       0
# swap was on /dev/sda9 during installation
UUID=518c7fd8-1a31-45ef-8dc3-7958fc468299 none            swap    sw              0       0
```append to the boot options:
resume=/dev/sda11

Then hibernate should work.

Ibidem

Yeah, for some reason it wasn't mounted. The UUID had changed (!). Corrected it now. Do I need that boot option? Never used it before, and hibernate has always worked.

---

### Post by cariboo on 2010-03-03
Why do you have three swap partitions? you can share a single swap partition amongst all the distos you have installed.

---

### Post by autark on 2010-03-03
> **phenest said:**
> Do I need that boot option? Never used it before, and hibernate has always worked.
No, you shouldn't need it. But it was needed to work around a bug which has now been fixed. To me it sounds like your resume information is out of sync with your partitions.

Have a look in these files (depending on your hibernation method) and see whether they point out the correct partition:
/etc/initramfs-tools/conf.d/resume
/etc/uswsusp.conf
/etc/suspend.conf

---

### Post by phenest on 2010-03-03
> **autark said:**
> No, you shouldn't need it. But it was needed to work around a bug which has now been fixed. To me it sounds like your resume information is out of sync with your partitions.

Have a look in these files (depending on your hibernation method) and see whether they point out the correct partition:
/etc/initramfs-tools/conf.d/resume
/etc/uswsusp.conf
/etc/suspend.conf

Not really. The swap issue is recent, but suspend and hibernation have never worked in Lucid. I'm going to do some more tests shortly and will report the outcome.

---

### Post by Ibidem on 2010-03-03
@cariboo907-Just because I felt like seeing if it worked.
Each is 1.5-2 GB, so one would not provide the same free space.
Last I knew, Linux supported 32 swap partitions up to 4 GB each in size; that's very old info, though...

Hibernate had not worked for me OOB; right now, I'm sticking with 2.6.32-12 and xorg 1.7.3 (I think) till I *know* that modeset works with my 945GME graphics.
Ibidem

---

### Post by phenest on 2010-03-03
Both hibernation and suspend fail to resume. Suspend resumes with a corrupted display, and has to be restarted. Computer starts with LCD brightness at minimum after resuming from hibernation, there's an error reported but too quick to read it, and then a normal start.

Dell Precision M90: nVidia GeForce 7950GTX with restricted drivers.

---

### Post by phenest on 2010-03-03
> **phenest said:**
> Both hibernation and suspend fail to resume. Suspend resumes with a corrupted display, and has to be restarted. Computer starts with LCD brightness at minimum after resuming from hibernation, there's an error reported but too quick to read it, and then a normal start.

Dell Precision M90: nVidia GeForce 7950GTX with restricted drivers.

Better results with the nouveau drivers: Suspend resumes with a correct display, prompts for a password and then just sits there. Hibernation is no change.

---

### Post by autark on 2010-03-03
> **phenest said:**
> ... Suspend resumes with a correct display, prompts for a password and then just sits there. ...

Getting stuck on the password prompt after resume sounds like another bug I've been seeing lately; you could try switching to another console and killing the gnome-keyring-daemon (use signal 9).

---

### Post by uRock on 2010-03-03
I don't bother with use hibernate, but suspend is a 50/50 on performance. It works well on my Netbook and my Lenovo desktop, but doesn't work on my Dell desktop nor my HP laptop.

---

### Post by autark on 2010-03-05
I have managed to fix all my (nvidia) graphics trouble by switching to a 2.6.33 kernel (2.6.33-020633-generic).

---

### Post by sgage on 2010-03-05
Ditto to autark's post.

The 2.6.33 kernel works great here with nvidia-current. Plymouth more or less works (you still have to log in twice), and resume from suspend works properly.

I am very pleased.

---

### Post by timosha on 2010-03-08
On my Thinkpad R51 it worked fine with kernel 2.6.32.15 but is not working anymore with the new kernel 2.6.32-16.

---

### Post by chek2fire on 2010-03-08
with last update suspend in kubuntu works fine and better from karmic

---

### Post by cristianrosa on 2010-03-11
I am also a Dell Precision M90 user, today I tried the 03/11 daily build live cd and suspend/resume is working great (nouveau by default).
The only problem I have is that on resume the brightness is set to minimum (I was experiencing this also in Karmic)
There is a bug report on this [#451282]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/451282")

---

### Post by krige on 2010-03-11
Suspend works fine: the system does suspend and the power light starts blinking, but in order to wake it up I need to press the power button (waking up with the keyboard space bar doesn't work).

Hibernation doesn't work: the screen gets black for a couple of minutes, with the cursor blinking in the upper-left corner of the screen, and then gets back on by itself, with the user lock-screen window asking for the password.

System: desktop computer with an Asus P5Q-PRO motherboard.
OS: Ubuntu 9.10, kernel 2.6.31-20.

> **Ibidem said:**
> Hibernate: doesn't work "out of box" because the kernel needs an option 
resume=/dev/sd**
where /dev/sd** is the swap partition where the hibernation data was stored.
If this is added to the boot entry, hibernate works.

Why doesn't this work "out of the box"? Is it really that hard to automate this procedure? And why isn't hibernation disabled by default since it's known it doesn't work?

---

### Post by itachi46 on 2010-03-11
i dont know about you guys but my suspend is more like log-out + suspend...  i.e. if i have a webpage open and suspend when i wake it up.. it only has start up apps... anyone else getting this?
i cant remember if it was doing this with plymouth

---

### Post by Ibidem on 2010-03-11
@Krige: Did you notice the date?  By now, from what I hear, it's been fixed.
The "doesn't work" was "hibernate=another way to shut down" (normal boot on power on).  It seems you have it set to lock the screen on hibernate (defaults; not sure how to change that), unless you are just getting the standard log in.
Suspend-Suspend only wakes up from the power button.  (there are other low power states that wake up with a keypress).

---

### Post by krige on 2010-03-11
> **Ibidem said:**
> @Krige: Did you notice the date?  By now, from what I hear, it's been fixed.

Yes, I noticed the date and currently it has not been fixed, at least it has not on my computer (I've installed the OS a couple of weeks ago).

> **Ibidem said:**
> The "doesn't work" was "hibernate=another way to shut down" (normal boot on power on).  It seems you have it set to lock the screen on hibernate (defaults; not sure how to change that), unless you are just getting the standard log in.

Which "doesn't work" are you referring to? Mine was for "it does not hibernate": i.e. the computer stays on with a black screen and blinking cursor for a couple of minutes and then displays the lock screen password window. I don't care about the password request, I am just reporting what happens when I try to hibernate.

By the way, I have tried to add that resume=/dev/sda6 to the boot options and now it complains it doesn't have enough space to do that. Of course it doesn't, the swap partition size is only 700MB while I have 4GB of RAM!

What bothers me is that it chose the swap size by itself during the installation: I think it should have given me the option to have it the same size as my RAM in order to make the system be able to hibernate.

Personally I think that it shouldn't be an option at all, hibernation should be enabled by default and available on all machines: if properly used by everybody, together with suspension, it may lead to a consistent reduction of the global energy consumption.

---

### Post by cariboo on 2010-03-11
Hibernate works as it's supposed to for me on my netbook, suspend seems to be hit or miss though, sometimes it works, another times it doesn't. I very rarely use suspend, hibernate always works for me.

---

### Post by cyberkilla on 2010-03-12
Suspend became volatile for me recently. Sometimes my wlan is "disabled" yet the hardware switch is set to on. Haven't tried hibernate in a few days because it is SLOW now.

Seriously, I can hibernate really quickly, but when it resumes it can take 5 minutes or more (and this is with no programs open). It is definitely a new problem, because it used to work within a minute or so in Karmic.

---

### Post by Rackstar on 2010-03-12
Suspends without errors, but will never resume. I hadn't had the time to check why.

Acer Aspire 9420

---

### Post by RonObvious on 2010-03-12
Don't remember if I've tested hibernate, but waking after suspend yields a black screen and unresponsive computer.  The system is a HP Pavillion zv6000 laptop.

Sorry, I've posted this in the wrong forum.  My issues is with 9.10, not with Lucid.

---

### Post by buzzmandt on 2010-03-12
kubuntu compaq presario cq60, suspend and hibernate both work perfectly

---

### Post by xlash on 2010-03-12
Suspend & Resume used to work flawlessly in Karmic Koala, resume  stopped working correctly after Lucid Lynx updates.

It goes to a black screen indefinetely. 

(nvidia driver, twinview, x86_64)

---

### Post by timosha on 2010-03-12
Thinkpad R51:

1) Works perfectly in 9.10
2) Works perfectly in 10.04 - kernel 2.6.32-15
3) **Does not work in 10.04 - kernel 2.6.32-16**
4) Works perfectly in Kubuntu 10.04 - kernels 2.6.32-15 and 2.6.32-16

---

### Post by tulskiy on 2010-03-12
> **itachi46 said:**
> i dont know about you guys but my suspend is more like log-out + suspend...  i.e. if i have a webpage open and suspend when i wake it up.. it only has start up apps... anyone else getting this?
i cant remember if it was doing this with plymouth

Same issue. After resume from suspend I only a get login screen. So the session is not saved. Sometimes I just get black screen.

Network and sound work fine, though, but I still have SUSPEND_MODULES="$SUSPEND_MODULES via-rhine snd-hda-intel"

I don't use swap, so can not test hibernate.

---

### Post by svaens on 2010-03-13
I haven't tried hibernate yet (will after this posting) but sleep doesn't work. 

Different symptoms than others i've read of. 

Mine goes black nicely like it should, but the fans are still working away, and the green light is still on (should indicate sleep by an orange light on my vaio) and I think it isn't really asleep, but just  has blacked out the monitor .... .like it can be configured to do after a period of inactivity. 

Should I file this as a bug?

Note: usually I am using the proprietary driver on my machine, but it isn't available yet for lucid.... so that is a big difference. 

ATI HD 3470 Mobility

EDIT:! That was quick wasn't it! Just tried the hibernate! Surprisingly does the same as sleep. Just blacks the screen. I hit the spacebar and up comes the authentication dialog, and i'm back up! didn't hibernate at all! (slightly better than freezing or blacking indefinitely!)

---

### Post by sgage on 2010-03-13
If I'm running with the nouveau drivers, suspend seems to suspend OK, but it won't come back - no drives spinning up or fans or anything.

If I'm running with the nvidia drivers, suspend works perfectly the first time I try it after a reboot, but subsequent suspends resume back to the GDM login.

---

### Post by tulskiy on 2010-03-13
Hmm, suspend works fine with nouveau for me. But is it possible to get compiz on nouveau? I installed xorg-edgers/ppa but it still doesn't work.

On nvidia it logs out most of the time. Does anyone know how to stop it? Sometimes I get a black screen, ctrl-alt-f4 the f8 usually get me back to the login screen.

> **sgage said:**
> If I'm running with the nouveau drivers, suspend seems to suspend OK, but it won't come back - no drives spinning up or fans or anything.

If I'm running with the nvidia drivers, suspend works perfectly the first time I try it after a reboot, but subsequent suspends resume back to the GDM login.

---

### Post by keithpeter on 2010-03-14
T42 thinkpad. Hibernate same as Ubuntu 9.10, ie broken. There is a bug on this one already.

---

### Post by AClark on 2010-03-17
Thinkpad A31 - ATI Graphics - Goes into suspend OK - comes out with corrupted graphics - looks like plaid fabric - Worked most of the time in Jaunty although same graphic corruption occasionally.

Has never worked in Lucid so far.

Asus P4PE MB With ATI Radeon 8500 Goes into suspend OK - comes out with blank black screen.  On this machine Lucid is a first time Linux install but I remember on other machines with ATI graphics that suspend only worked with the proprietary drivers.

When I get a chance I will investigate PM-Suspend as mentioned in previous posts.

I am interested to see if tomorrows beta release makes any difference.

---

### Post by PenguinInside on 2010-03-17
I haven't tested hibernation, but suspend half works.

It suspends. And it comes back up again.

But when it comes back, my session is gone. I.e., all running programs are aren't running anymore.

I did a quick ps aux in case there was another session running under my username, with my programs (such as gedit) still running.

But there wasn't.

Anyone else encounter this?

---

### Post by JoeWheeler on 2010-03-17
Hibernate works great, but suspend leaves my backlight turned off on wake.

I saw tried a fix but it didn't work

---

### Post by uBeer on 2010-03-17
Tried to suspend and that worked nice.

Tried to resume and that worked nice, except for the fans of the laptop that don't turn on... Only fix is a restart, so this alas doesn't work for me. Previous releases have been kind to me I realise...

---

### Post by ElSlunko on 2010-03-18
I just noticed I don't have suspend as an option. Weird.

---

### Post by PenguinInside on 2010-03-18
> **ElSlunko said:**
> I just noticed I don't have suspend as an option. Weird.

Do you have S3 suspend set to On in your BIOS settings? (When you first turn on the computer?)

I turned that on, and Suspend showed up in the menu.

Please tell the forum if this worked or not.

---

### Post by PenguinInside on 2010-03-18
> **itachi46 said:**
> i dont know about you guys but my suspend is more like log-out + suspend...  i.e. if i have a webpage open and suspend when i wake it up.. it only has start up apps... anyone else getting this?


I'm getting that too. It's like a totally new session when you unsuspend.

---

### Post by zoomy942 on 2010-03-18
suspend and hibernate work if i use the sleep button but the lid doesnt tell my netbook to do anything.  lame  ;)

---

### Post by ElSlunko on 2010-03-18
> **PenguinInside said:**
> Do you have S3 suspend set to On in your BIOS settings? (When you first turn on the computer?)

I turned that on, and Suspend showed up in the menu.

Please tell the forum if this worked or not.

That fixed it. I only had S1 enabled, now I have S1 & S3 enabled

---

### Post by aysiu on 2010-03-18
The actual resume itself works, but I'm still experiencing these three bugs:
["could not switch the monitor configuration" error when resuming from suspend](https://bugs.launchpad.net/ubuntu/+bug/538619)
[Network Manager prompts for already saved password upon resume (makes me click Connect without re-entering password)](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/538614)
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

Am I the only one?

---

### Post by wdaniels on 2010-03-18
They were completely missing actually last time I looked on my netbook running Lucid. But when they were there, both used to work fine :D

---

### Post by seenthelite on 2010-03-19
suspends okay but does not resume properly, hibernates okay (slowly) resumes from hibernation but very slow and not every time. At this stage it's just quicker to reboot.

---

### Post by PenguinInside on 2010-03-19
> **seenthelite said:**
> suspends okay but does not resume properly, hibernates okay (slowly) resumes from hibernation but very slow and not every time. At this stage it's just quicker to reboot.

What do you mean by doesn't resume properly? No display?

Also, what build are you using?

---

### Post by sxmaxchine on 2010-03-19
perfectly because i dont use it

---

### Post by michaelzap on 2010-03-19
Neither work for me on my Lenovo Y530 running Karmic. I'm hoping that they will in Lucid. Between having no suspend and having to killall pulseaudio every half hour Karmic has been a rather annoying release for me (it started out catastrophic, so annoying seemed great once I got to that stage).

---

### Post by tekstr1der on 2010-03-19
Clean install of 2010.03.18 Daily Lucid CD results in:

Suspend-resume works as expected exactly one time only. The system will then suspend again successfully, but when a resume is prompted, it will reboot, resulting in loss of apps/data.

This behavior occurs if suspended more than once during the same session and also persists between logins. The only fix is a full reboot. Rebooting allows for another single successful suspend-resume cycle.

I filed the following bug:

Multiple suspend-resume cycles fail to resume
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/542035](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/542035)

---

### Post by kyleabaker on 2010-03-19
Suspend (now "Sleep") works great on my desktop (AMD Athlon 64 X2 Dual Core Processor 6000+, 2GB Ram), but Hibernate restarts with corrupt graphics to the point that its completely unusable.

On my HP dv1000, suspend starts, but aborts or something so that it doesn't actually go to sleep and I just have to log back in. Hibernate doesn't work either.

What is the best way to report and send data for these problems?

---

### Post by autark on 2010-03-19
> **sxmaxchine said:**
> perfectly because i dont use it
What is your reason to share that piece of information with anybody but yourself?

---

### Post by seenthelite on 2010-03-19
> **PenguinInside said:**
> What do you mean by doesn't resume properly? No display?

Also, what build are you using?

Thanks for your interest the build was alpha 3 32 bit downloaded on 01/03/10 and updated when updates arrived. But I have removed it and am installing Beta 1 64 bit and I'll see how suspend and hibernate works then.

---

### Post by travishume on 2010-03-20
Yay, suspend AND resume are working after today's updates.  Quickly too!

---

### Post by michaelzap on 2010-03-20
> **michaelzap said:**
> Neither work for me on my Lenovo Y530 running Karmic. I'm hoping that they will in Lucid.
Doesn't seem to work for me in Lucid beta either. I only have a Sleep option, and choosing it puts my laptop into a half-asleep state (keyboard lights stay on, fan actually seems to start spinning faster, screen goes black but the backlight stays on), but it refuses to wake up so that's not very useful.

I'm running Lucid from a USB version of the Live CD with persistent changes (I used the Startup Disk Creator to make it). I suppose this may have something to do with this issue, although I would expect sleep to work in this context. I guess I won't be sure unless I try it installed to the hard drive.

This is pretty much my make-or-break issue for Lucid. If neither suspend nor hibernate works on my laptop and I can't figure out a fix for this, then I'll probably switch to Debian for at least the next six months. On a positive note: Pulseaudio is consistently using less than 2 megs of RAM in Lucid, whereas in my Karmic system it grows to over 2 gigs if I don't kill it every half hour.

---

### Post by seenthelite on 2010-03-20
> **PenguinInside said:**
> What do you mean by doesn't resume properly? No display?

Also, what build are you using?

Okay installed Beta 1 AMD64 (no updates yet ) and it suspends and resumes perfectly, excellent.

---

### Post by cristianrosa on 2010-03-20
Now with Lucid Beta1 LiveUSB (nouveau driver) suspends/resume works but it has some glitches.
The first suspend/resume cycle resumes with the display brightness dimmed to minimum.
In the subsequent suspend/resume cycles, brightness is correctly restored but instead, on resume a screen with horizontal black and white lines is showed for a few seconds and then a black screen. If I move the mouse or press any key the desktop is finally shown but the first and last column of pixels of the screen are white, however the systems works fine.
Anyone else is experiencing this artifacts?

---

### Post by cristianrosa on 2010-03-20
The white lines I get at the edges of the screens seems to be related to the bug  [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263) and there is a fix already commited that didn't made to beta1.
Anyway, I still have the artifacts starting from the 2nd suspend/resume cycle.

---

### Post by sgage on 2010-03-20
Suspend works fine - resuming from suspend not so much. Not at all, in fact. Same as with the alpha: 

- with nouveau drivers, system powers down. Attempt to resume does nothing at all.

- with nvidia drivers, system powers down. Attempt to resume spins up the disk and fans, but a black screen is all. Can reboot with SysRq-B. In the alpha, it would resume to the gdm login screen.

I have been using Ubuntu for a long, long time, and this is the first time I've ever encountered any trouble with suspend/resume. Oh well.

---

### Post by timosha on 2010-03-20
Status Quo here on my Thinkpad R51 with Intel 855GM:
Works perfectly with kernel 2.6.32-15
Doesn't work at all with kernel 2.6.32-16

(Yes, I did all updates)

---

### Post by zoomy942 on 2010-03-21
i havent seen much progress on this lately.  think it will be cleared up by release?

---

### Post by tulskiy on 2010-03-21
> **PenguinInside said:**
> 
I did a quick ps aux in case there was another session running under my username, with my programs (such as gedit) still running.

But there wasn't.

Anyone else encounter this?

I think there are at least 3 or 4 posts about this issue in this thread, but no responses or possible solutions were given.

---

### Post by ElSlunko on 2010-03-21
Suspend works for me. I wonder though since I never really used it before except in windows, am I suppose to hit the power button to wake it?

---

### Post by sgage on 2010-03-22
Suspend (or more properly, resume-from-suspend) is now working fine for me with the new nvidia drivers (196.36.15). One more item checked off the list...

I should add that resume still does NOT work with the nouveau drivers. Nothing happens when attempting to resume. Can't even reboot with SysRq-B

---

### Post by jbslaw on 2010-03-22
Like several others here, my laptop suspends fine but on resume loses my session and any work in progress.  That would be fairly serious breakage on a production machine.

A fix for the lost sessions would be nice.

---

### Post by tulskiy on 2010-03-23
Looks like lost session on resume is fixed on nvidia driver for me.

---

### Post by uRock on 2010-03-23
I have the desktop version installed on my Netbook and Suspend is working flawlessly.

---

### Post by ElSlunko on 2010-03-23
I have to admit, suspend is working wonderfully with my nvidia card. I don't even shutdown anymore, just suspend.

---

### Post by mcooke1 on 2010-03-23
> **ElSlunko said:**
> I have to admit, suspend is working wonderfully with my nvidia card. I don't even shutdown anymore, just suspend. 


I have Kubuntu  10.04 on a Dell Laptop and Ubuntu 10.04 on a Toshiba Laptop and resume from suspend works  perfectly on both. I normally will just leave these on suspend. Who cares about plymouth.

---

### Post by zoomy942 on 2010-03-23
I have been seeing lots of posts/threads about sleep and hibernate not working on certain laptops under certain conditions.  

My reason for this thread was maybe a better understanding of the pattern of sleep and hibernate across different devices.  Instead of a myriad of posts about stuff, with no distinguishable pattern, maybe post here who has it non functioning and in what way?

I just want to get an idea of the progress of this.  I have a bug filed but there hasnt been any updates and I think it's a large Lucid issue thus far.  Maybe we can help each other fix it.

Me for example - nothing happens when I close my lid.  Sleep and hibernate work fine when I use the sleep button, but nothing when i close the lid.

---

### Post by timosha on 2010-03-23
On my Thinkpad R51 - Intel 855GM Graphics:

Kernel 2.6.32-15 : Hibernate and suspend work perfectly, resume from suspend is very fast;

Kernel 2.6.32-16 : Hibernate works, suspend does not work;

Kernel 2.6.32-17 : Hibernate works, suspend does not work;

Kernel 2.6.32-18 : Hibernate works, suspend does not work;

Kernel 2.6.32-19 : Hibernate and suspend work perfectly, resume from suspend is very fast;

Kernel 2.6.32-20 : Hibernate and suspend work perfectly, resume from suspend is very fast;

Kernel 2.6.32-21 : Hibernate and suspend work perfectly, resume from suspend is very fast;

---

### Post by tajreed on 2010-03-23
Acer Aspire 5610 with Intell Graphics wake up from sleep intermittenly. Overnight will not wake up, after an hour it will.

---

### Post by AClark on 2010-03-23
Still can't resume from suspend on either of the 2 machines with Lucid installed.

Thinkpad A31 comes out with corrupted video - Can restart with SysRq + RESUB & Alt+Ctr+Del

Desktop with ASUS MB comes out with black screen and does not respond to keyboard.

None of the pm-suspend options help

Both have ATI Grapics but are too old to be supported by fglrx

---

### Post by spiritech on 2010-03-23
my suspend works fine, hibernate does not. starts waking up loads some of the screen then freezes. i read somewhere that using a usb mouse can cause problems, not sure though.

---

### Post by michaelzap on 2010-03-24
I'm having some odd hibernation behavior. When I choose Hibernate from the Shut Down menu, the screen goes black but the backlight stays lit, as do the various keyboard LEDs and the fan keeps running. I have to hold the power button down to shut it off. But then when I reboot it shows BIOS and Grub but then goes right to a login screen and my previous session is restored. So apparently it is hibernating, but it's not able to complete the job. I do have a USB mouse connected, so perhaps I need to try it without that.

Also: Sleep doesn't work for me, but I have no swap partition. I didn't make one because I have 4 GB of RAM and I didn't want unencrypted files hanging out in there. I wonder if I created one if I would be able to get sleep to work. Anyone have tips on ecrypting swap in Lucid? Perhaps using a swap file instead of a partition?

EDIT: Just tried hibernating without my USB mouse and it behaved exactly the same as with it.

---

### Post by ViperScull on 2010-03-24
AFAIK swap is needed for hibernate (unless you specify a file for doing it) but no for suspend, where you copy everything in RAM. So yes, it's a little weird your case.

Mine, suspend fails, and hibernate fails as well.

Using ATI oss drivers (ATI HD4200), xorg edgers, with kernels 2.6.33 and 2.6.32-17

---

### Post by zoomy942 on 2010-03-25
so are all these issues kernel related or power-management package related?  There are different problems on all different types of PC's.

---

### Post by uRock on 2010-03-25
From what I have been reading, the issue may be caused by different variables, from Video cards to sleeplessness.
I have one machine that doesn't do suspend nor hibernate.

---

### Post by timosha on 2010-03-26
As far as my five (5) machines are concerned it is a kernel issue in Ubuntu (not in Kubuntu).

Suspend/Hibernate does not work with kernels: 2.6.32-14, 16 and 17, with whatever pm. **But it works perfectly and very fast with kernel 2.6.32-15, with whatever pm.** So, I pinned this kernel.

In Kubuntu Suspend/Hibernate works with every kernel and every pm so far.

My machines are: Thinkpad R50, R51, R52, HP dx2400 and Pavillion 5200, all with an Intel graphic chipset.

---

### Post by zoomy942 on 2010-03-26
maybe i will DL 9.10, make a live cd and test it on my laptop.  That would help settle it.

---

### Post by timosha on 2010-03-26
> **zoomy942 said:**
> maybe i will DL 9.10, make a live cd and test it on my laptop.  That would help settle it.

In 9.10 I had to apply a few small patches to get suspend/hibernate working. And it worked excellent with kernel 2.6.31-20.

But, today kernel 2.6.31-21 came in for 9.10. Guess what happened ? Yes, suspend/hibernate didn't work anymore ;-(

Ubuntu is like a lottery, sometimes you win, sometimes you loose.

---

### Post by shafin on 2010-03-26
Suspend/hibernate is working fine, I don't use them, but tested and got good results.

---

### Post by zoomy942 on 2010-03-26
> **timosha said:**
> In 9.10 I had to apply a few small patches to get suspend/hibernate working. And it worked excellent with kernel 2.6.31-20.

But, today kernel 2.6.31-21 came in for 9.10. Guess what happened ? Yes, suspend/hibernate didn't work anymore ;-(

Ubuntu is like a lottery, sometimes you win, sometimes you loose.

lol - lottery.  thats awesome.  

fair enough - i just want my laptop to do *something* when i close the lid.

---

### Post by kyleabaker on 2010-03-26
After finally fixing my video card (nvidia), I'm able to use both suspend and hibernate (hibernate is slow in and out). Seems nouveau was conflicting.
[http://ubuntuforums.org/showthread.php?t=1431440&page=3&p=9032083](http://ubuntuforums.org/showthread.php?t=1431440&page=3&p=9032083)

---

### Post by timosha on 2010-03-27
> **zoomy942 said:**
> lol - lottery.  thats awesome.  

fair enough - i just want my laptop to do *something* when i close the lid.

The solutions are simple:
In Karmic I pinned kernel 2.6.31-20 and removed the new kernel. In Lucid I pinned kernel 2.6.32-15 and removed all other kernels. Suspend/Hibernate is working excellent with these kernels.

On another UltraBay with Lucid on my Thinkpad I continue testing with the latest Lucid kernels. Maybe, when I am lucky, some day suspend/hibernate will also work with a newer kernel.

But it still amazing to experience that basic laptop functions don't work in kernels 2.6.32-14, 16 and 17. But works perfectly in -15. 

Ubuntu regression bugs have a very long live, they even reincarnate ;)

---

### Post by Gregorybekkers on 2010-03-27
I've got no problems with it.

---

### Post by psaras on 2010-03-27
> **timosha said:**
> In 9.10 I had to apply a few small patches to get suspend/hibernate working. And it worked excellent with kernel 2.6.31-20.

But, today kernel 2.6.31-21 came in for 9.10. Guess what happened ? Yes, suspend/hibernate didn't work anymore ;-(

Ubuntu is like a lottery, sometimes you win, sometimes you loose.

I am interested in the patches you talk about. Might those be an option for Lucid? I cannot get suspend/hibernate working in whatever kernel I tried. Until 9.10 suspend/hibernate worked flawlessly.

---

### Post by timosha on 2010-03-27
> **psaras said:**
> I am interested in the patches you talk about. Might those be an option for Lucid? I cannot get suspend/hibernate working in whatever kernel I tried. Until 9.10 suspend/hibernate worked flawlessly.

In 9.10 I changed /etc/default/grub with this : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 nomodeset"
After changing run: sudo update-grub

But, this is for Intel graphic chips. This patch doesn't work in Lucid as the Lucid kernels don't accept UMS.

---

### Post by Mulenmar on 2010-03-27
Hello, I'm using an Acer Aspire One 751h with the accursed US15W Poulsbo chipset. Suspend-to-RAM works, but on resume the screen is not turned back on. Didn't test Hibernate, since I don't use a swap partition.

I saw a post earlier in this thread saying that installing HAL helped them, I'll try that and post my results. I'm also going to create a separate thread afterwards, since searching for "Acer Aspire One Lucid" and variations thereof returns nada. :)

EDIT: Tried install HAL, didn't help. Tried switching to a tty and then entering, "sudo pm-suspend" -- didn't help either.

---

### Post by mitchellcipriano on 2010-03-27
> **timosha said:**
> As far as my five (5) machines are concerned it is a kernel issue in Ubuntu (not in Kubuntu).

Suspend/Hibernate does not work with kernels: 2.6.32-14, 16 and 17, with whatever pm. **But it works perfectly and very fast with kernel 2.6.32-15, with whatever pm.** So, I pinned this kernel.

In Kubuntu Suspend/Hibernate works with every kernel and every pm so far.

My machines are: Thinkpad R50, R51, R52, HP dx2400 and Pavillion 5200, all with an Intel graphic chipset.

Were you ever able to get your R51 to suspend with Ubuntu?

---

### Post by timosha on 2010-03-27
> **mitchellcipriano said:**
> Were you ever able to get your R51 to suspend with Ubuntu?

Absolutely !

In Ubuntu 9.10 with kernel 2.6.31-20 (which I locked) and in Ubuntu 10.04 with kernel 2.6.32-15 (which I also locked).

And in Ubuntu 8.04 with every kernel just out-of-the box. Ditto for Debian Lenny.

Ubuntu is a like a Jaguar car, you need two. One to drive and one in the garage. I have vanilla 9.10 an 10.04 installations on a separate UltraBay with a 160 GB hdd. And whenever Canonical releases new kernels I first test them on those installations. If everything works fine, which seldom happens, then I upgrade my driving Jaguar.

---

### Post by maestrobwh1 on 2010-03-27
IMB T43 Thinkpad

Resume from suspend results in screen "tearing" after a while.  Works okay for a few minutes to an hour.  Sometimes the screen goes totally white.  Resolution is to close lid and let it suspend again, then resume it.  Reboot or wake from hibernate results in stability again.

Resume from hibernate works for the first time ever.

---

### Post by fargle on 2010-03-28
New Dell Studio 14z here, with an nVidia 9400M GPU and Broadcom 4312 wireless, and suspend works fine with nVidia-current.  I can't do hibernate because I full-disk encrypt.  Wish I could, I know there was some work being done on that with swsusp2, I believe!

Haven't tried it with the wired Ethernet but I'm sure that works as well, it normally doesn't cause a problem.

---

### Post by mitchellcipriano on 2010-03-28
> **timosha said:**
> Absolutely !

In Ubuntu 9.10 with kernel 2.6.31-20 (which I locked) and in Ubuntu 10.04 with kernel 2.6.32-15 (which I also locked).

And in Ubuntu 8.04 with every kernel just out-of-the box. Ditto for Debian Lenny.

Ubuntu is a like a Jaguar car, you need two. One to drive and one in the garage. I have vanilla 9.10 an 10.04 installations on a separate UltraBay with a 160 GB hdd. And whenever Canonical releases new kernels I first test them on those installations. If everything works fine, which seldom happens, then I upgrade my driving Jaguar.

I am already on kernel 2.6.32-17 and it does not work. Is there an easy way to go back? How do you lock to a particular kernel?

---

### Post by timosha on 2010-03-28
> **mitchellcipriano said:**
> I am already on kernel 2.6.32-17 and it does not work. Is there an easy way to go back? How do you lock to a particular kernel?

In Synaptic I just locked the kernel when I notice that Canocical wants to suprise me with another kernel. But, to be absulotely sure that Canonical will not delete my working packages I always do a dpkg-repack before installing new bugs.

You can also do: sudo aptitude hold "kernel name"

---

### Post by Djalmahal on 2010-03-30
I just bought a Asus G60jx with i5 and nvidia 360 and suspend/hibernate doesn't work, it ends of with a blinking cursor and doesn't react anymore

Andreas

---

### Post by cheapsaket on 2010-03-30
Suspend does not work for me.
I can hibernate but its very slow.
Resuming from hibernate is EXTREMELY slow.

Also there is no visual indicator to show hibernate percentage or resume percentange, nothing on the screen except for a blinking cursor.

It would have been nice to have some visual feedback.

---

### Post by timosha on 2010-04-01
With kernel 2.6.32-19 suspend and hibernate work again, as they did in kernel -15.

---

### Post by zoomy942 on 2010-04-01
> **timosha said:**
> With kernel 2.6.32-19 suspend and hibernate work again, as they did in kernel -15.

did the updates and no dice on the lid closing and having it intitiate hibernate or sleep.  lame

---

### Post by dcstar on 2010-04-01
I just tested Suspend and Hibernate on my desktop (GA-MA78GM-S2HP MB, 4GB RAM and swap) and they both worked fine.

Resume from suspend to the password prompt was **very** quick.

---

### Post by mitchellcipriano on 2010-04-04
> **timosha said:**
> With kernel 2.6.32-19 suspend and hibernate work again, as they did in kernel -15.

It works for me now as well. I plan to stay with this kernel until I hear that a newer one is working.

---

### Post by Rackstar on 2010-04-04
Suspend doesn't work, didn't test hibernate.

Acer Aspire 9420, NVidia Geforce Go 7300, 195.xx driver

Maybe somebody should start a poll?

---

### Post by brimondyl on 2010-04-04
How come I am still at 2.6.32-16-generic and everyone else has -19?

---

### Post by recluce on 2010-04-05
I have a Dell Latitude D830 (Intel Core 2 Duo, 4 GB RAM, NVidia Quadro NVS 140 graphics) and I run Lucid x64. No problems here whatsoever with Suspend, it works perfectly and fast (with all Lucid kernels since -15, did not test Suspend before). This is a major improvement over Jaunty and Karmic, where all I got on Resume was a black screen and a blinking cursor.

I have no idea about Hibernate - it is slower than restarting the machine, so why bother?

---

### Post by FrancoNero on 2010-04-05
why not attach a poll to this thread to get some real numbers on this....

---

### Post by the_one(2) on 2010-04-05
Suspend has been working on and off for me since i started using lucid in late alpha (alpha 2-3?). It didn't work yesterday which I noticed when it was still on today=) I upgraded some stuff and restarted and now it works again.

---

### Post by chek2fire on 2010-04-05
Suspend is not working for me. Was working when i have upgrade to alpha 3 but from then until now is not working.
Same for the hibernate. My system is with nvidia chipset.

---

### Post by Rackstar on 2010-04-05
I searched the thread, but didn't find what I was looking for. How can I debug suspend? In which log do I have the most chance of finding anything interesting or shouldn't I bother at all?

---

### Post by AClark on 2010-04-06
```
Man pm-suspend
```
Has some interesting info.

/var/log/pm-suspend.log  Sometimes has a clue

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

I followed the procedure in the above link and was able to determine that the problem is probably my video driver on the ASUS MB desktop with old ATI graphics.

fglrx has solved the problem in the past but ATI has dropped support for this card so I'm hoping the OS driver will work by final.

The Thinkpad A31 still resumes with corrupted graphics but as of todays updates I can now see a 1" square where the mouse cursor is and was able to guess at where to click for shutdown on the top panel. Baby steps.

Other than the suspend problems both machines have worked remarkably well in all other areas and with all of the apps I normally use from Alph2 to now.

Looking forward to upgrading my production machines now running Hardy32 & Jaunty64 after final release and when I am reasonably sure I can get suspend/resume to work.

---

### Post by cheapsaket on 2010-04-06
both working now with 19

---

### Post by sgosnell on 2010-04-07
Both work fine on my Asus EEE 900, with the .19 kernel, and also with the 2.6.33 and 2.6.34rc kernel.

---

### Post by SecretCode on 2010-04-07
> **recluce said:**
> I have no idea about Hibernate - it is slower than restarting the machine, so why bother?

It is frustratingly slow to get a responsive desktop, but then I have all my apps & documents open where they were. If I shutdown and restart, only some apps reopen. And some of them open on the wrong desktop, or don't reopen the document to the last working position. So after working out where I was and reopening everything it ends up taking about the same time.

I tend to run a lots of apps in parallel and distribute them over several desktops. If you don't, rebooting is for sure going to be better.

---

### Post by manoynmonic on 2010-04-07
It didn't work at all on my Dell d830 until I added acpi_osi=Linux to the kernel options.  Now suspend works perfectly.  Can't speak for hibernate, as I almost never use it.  This was also the case with my (pre-upgrade) hardy install.

---

### Post by mitchellcipriano on 2010-04-10
Suspend and resume are working great with kernel 2.6.32-19, I am afraid to move from this kernel. Does anyone have any experience with newer kernels?

---

### Post by oobuntoo on 2010-04-11
With the latest kernel 2.6.32-19, I get weird problem resuming from suspend to RAM. I have to do it twice. On the first try, it would take me all the way back into desktop ( while there I could actually run an app) without asking for password and then it would suspend again in about 10~15 seconds later. That's a security risk in my opinion. The second try would work normally; I'd get password prompt and then desktop.

---

### Post by wadam on 2010-04-11
So I've read through the last few pages of this post, and didn't see it.  Is anybody else having a problem where, when you go to either suspend or hibernate, you end up with a locked screen and nothing else?

Running Beta 2 and the 2.6.32-19 kernel on a gigabyte h44m-usb3 mb, that's what's happening to me.  In both suspend and hibernate modes, according to pm-suspend.log, the system seems to indicate that it suspends, then immediately awakens and resumes.  Also, when I tell it to hibernate, the error "device USB9 failed to freeze" flashes on the screen early on in the process.  Which is strange because it doesn't seem to be reflected in the log, and is even more strange because it does so regardless of whether I have any USB devices plugged in.

---

### Post by cyberkilla on 2010-04-11
As of a few days ago, resuming from suspend leaves me with a disabled wireless card which fails to respond to the hardware switch, or the "Enable Wireless" checkbox in KDE.

---

### Post by zoomy942 on 2010-04-12
with the -20 kernel, its still not knowing when i close the lid.  does anyone know any commands or edits i can do that would make it work?

---

### Post by dannyboy79 on 2010-04-12
i used to just always leave my computers on but now with electricty throught the roof, i tried out hibernate and suspend on my main desktop (c2d, nvidia 6200-yes, i am running prop drivers, 2gb ram, 1.5 swap partition) and either I don't know what to press to get them to wake up or they don't work! on my win 7 box, i put it to sleep, the power button is used to wake it up and it works great. sleep actually shuts the computer totally off, no power is being used that I am aware of (at least all fans are off). i would very much like to learn how to get lucid (2.6.32-20 kernel) to work with suspend or hibernate. thanks

---

### Post by Taoye on 2010-04-12
I don't use hibernate so I haven't tried it out.

Suspend is working for me, on my MacBook Pro 13" (5,5). The power manager thing doesn't always load properly, however... sometimes when I start Lucid it doesn't detect my battery and just shows a little power symbol and thinks I'm solely on AC, in which case it also refuses to suspend at all, whether by closing the lid, or selecting suspend from the power menu.

---

### Post by cheapsaket on 2010-04-12
> **dannyboy79 said:**
> i used to just always leave my computers on but now with electricty throught the roof, i tried out hibernate and suspend on my main desktop (c2d, nvidia 6200-yes, i am running prop drivers, 2gb ram, 1.5 swap partition) and either I don't know what to press to get them to wake up or they don't work! on my win 7 box, i put it to sleep, the power button is used to wake it up and it works great. sleep actually shuts the computer totally off, no power is being used that I am aware of (at least all fans are off). i would very much like to learn how to get lucid (2.6.32-20 kernel) to work with suspend or hibernate. thanks

I read somewhere that the swap partition needs to be 2.5x the amount of RAM.
I had my swap the same size as the RAM and when doing suspend or hibernate it would take a really long time going down and coming back up.
I then resized my swap partition and now its much faster.
Also I noticed that the screen will stay blank (maybe because I am not using a screensaver) and I have to move the mouse or click a key for the login box to show up.
HTH

---

### Post by Funnnny on 2010-04-12
My new computer cannot suspend.
When I resume from suspend, the screen goes black and the machine completely unusable. When I  reboot the machine, Ubuntu boot with disables network

---

### Post by TheNessus on 2010-04-12
All this Swap size debate is irrelevant! I have 4gb SWAP and 2GB RAM and never had trouble hibernating or sleeping with Karmic and previous -- on same computer -- until Lucid. Hence it is purely a Lucid issue. Maybe an Nvidia issue too?

---

### Post by mrowth on 2010-04-12
Linux 2.6.32-20-generic, Ubuntu 10.04 (testing) 32 bit, KDE 4.4.2
Mainboard: Asus A8V Deluxe Wi-Fi G (VT8237 chipset)
CPU: AMD 64 X2 4800+
Video: Geforce 7950 GT (proprietary driver)
RAM: 3 GB (suspension does NOT work with more RAM)

Suspend to RAM: mostly works (and I use it all the time, too) - ancient Hauppauge WinTV PCI card doesn't work afterwards.

Suspend to disk: resumes, but I'm back at the KDM login screen so I might as well have rebooted. TTY sessions resume properly, though. Get the same messages about some WinTV chip reset failure.

---

### Post by sgosnell on 2010-04-12
@Dannyboy:  To wake up from suspend, you should be able to press any key, or move the mouse and get it to wake up.  I generally use the space bar.  It may take a few seconds, but it should wake up.  I haven't actually tried suspending a desktop, I haven't turned mine on in months.  It does work fine on my laptop, though.

---

### Post by dannyboy79 on 2010-04-12
> **sgosnell said:**
> @Dannyboy:  To wake up from suspend, you should be able to press any key, or move the mouse and get it to wake up.  I generally use the space bar.  It may take a few seconds, but it should wake up.  I haven't actually tried suspending a desktop, I haven't turned mine on in months.  It does work fine on my laptop, though.

thanks, will look into it. i may have even turned off a lot of the power management stuff within services because i didn't want them started long ago. but now I want them running.

---

### Post by BrokeMahPC on 2010-04-12
Resuming from Suspend I get a crash report: WARNING: at /build/buildd/linux-2.6.32/kernel/power/suspend_test.c:53 suspend_test_finish+0x89/0x90() Your kernel may be unstable and you may need to restart your system There are bugs reported about this.

 Resuming from Hibernate My wired internet connection is disabled - clicking "Enable Networking" does not restore it. I had to Reboot - so neither of the above working - suspend did in 9.10  Ubuntu

Lucid 10.04 Desktop i386 32bit Beta2 Kernel 2.6.32-20-generic 
CPU Intel E7300 dual core
ATI Radeon HD 4670 
ATI proprietary FGLRX driver 
2GB RAM

---

### Post by sagefool on 2010-04-12
Suspend killed my WiFi, and I can't get it to turn back on. I've tried full shutdown, restart, and logout.

My wife closed the laptop...either shut it off, or leave it on, but she likes suspend...ughhh.

Edited my network interfaces configuration, and nothing. Anyone else having this problem?

---

### Post by mcduck on 2010-04-13
Well, Suspend works fine, apart from the fact that the very second it suspends, the machine wakes up again. Not really useful.

Hibernate works fine. Not that I'd eve use it, as it takes the same time as normal boot.

---

### Post by Artemis3 on 2010-04-13
Suspend works nice in my desktop machine. Before with jaunty, my analog wintv card would become unusable (unable to tune channels) but now its resetting properly, and i can use it after coming back from suspend :)

Can't test hibernate as i don't have a swap file or partition ^_^

---

### Post by michaelzap on 2010-04-13
> **Artemis3 said:**
> Can't test hibernate as i don't have a swap file or partition ^_^

What's really strange is that I also don't have a swap partition (or file), but hibernate (sort of) works for me. When I choose it from the Shut Down menu, the screen goes blank (but not dark) and I see disk activity for a few seconds. Then the disk activity stops, but the fan, backlight, and keyboard lights stay on. It's clearly still powered on, and I have to hold down the power key to force a reboot. The odd thing is that when it comes back up and I move the mouse, I get the locked-screen login as if it had hibernated properly, and any open windows that I had before are still there. So it must have saved the session state somehow. I don't get it...

Suspend also blanks the screen but doesn't turn off the backlight or power down the machine, but when I force-reboot from there it just restarts normally.

So neither Suspend nor Hibernate work properly on my Lenovo Y530 running vanilla 64-bit Ubuntu Lucid beta with the 2.6.32-20 kernel and all updates installed.

---

### Post by papangul on 2010-04-13
I have installed beta-2 and the suspend option is absent altogehter. Though suspend did not work on karmic at-least the option was present.

On the other-hand hibernate never worked for me on ubuntu earlier but is working now!

---

### Post by dannyboy79 on 2010-04-13
im back, suspend works but does me know good if it can't resume. i can pound on the keyboard, move the mouse, push the power button once but it will not resume for nobody! i have to hard reset the machine, then it takes forever because of recovering journals and whatnot. darn it.

asrock 775Dual-VSTA
c2d 1.8 ghz
2gb ddrII ram
nvidia 6200 128 mb ram (agp)


it's an old board, maybe i need to update the bios? although the website does say it supports ACPI 1.1 Compliance Wake Up Events

---

### Post by conradin on 2010-04-13
In the alpha versions of lucid suspend / hibernate was locking my computer in that state. The Betas Its been working fine for me. I have a IBM Thinkpad T43.

---

### Post by jdw300 on 2010-04-14
I had this same issue with suspend/hibernate. I have a compaq c500. i went into System>preferences>power management.

I unchecked the box that says Spin down hard disks when possible. And this seemed to work my computer goes into hibernation mode and when I push the power button to wake it up I get the message that says Waking up please wait.. Then I get my login screen and I log in and everything is good.

I am not sure how often I will use this because Ubuntu boots up so fast.:P

---

### Post by michaelzap on 2010-04-14
> **jdw300 said:**
> I had this same issue with suspend/hibernate. I have a compaq c500. i went into System>preferences>power management.

I unchecked the box that says Spin down hard disks when possible. And this seemed to work my computer goes into hibernation mode and when I push the power button to wake it up I get the message that says Waking up please wait.. Then I get my login screen and I log in and everything is good.

I am not sure how often I will use this because Ubuntu boots up so fast.:P

Seemed like a promising idea, so I tried it. My Lenovo Y530 still won't go completely into hibernation. After a hard reboot it comes back out as if it had hibernated properly, but it never actually shuts off the fan, backlight, etc. unless I do a force shutdown.

---

### Post by bcbc on 2010-04-14
Hibernate works fine in karmic and used to work in Lucid Beta1 for me - with 1GB ram and 1GB swap. But with beta2, I get this in syslog:
```
PM: Need to copy 134134 pages
PM: Normal pages needed: 117468 + 1024, available pages: 110923
PM: Not enough free memory
PM: Error -12 creating hibernation image

```
That's without running anything - other than terminal. 

I doubled the swap, updated resume settings in initramfs, and retried. It hibernated and resumed fine, but took a l-o-n-g time to get wireless reconnected. Also there are no visual cues - used to say something at least on the resume in Karmic (not on shutdown), but now that seems to have gone.

This seems way trickier than it needs to be.

Edit: suspend works fine - very fast, with lid close and open (and without). Network reconnects quickly with suspend.

Dell inspiron 6400, T2400 1.83Ghz, 1GB ram, 2GB swap, Intel Corporation PRO/Wireless 3945ABG, ATI Radeon mobility X1300.

---

### Post by manoynmonic on 2010-04-14
> **wadam said:**
> So I've read through the last few pages of this post, and didn't see it.  Is anybody else having a problem where, when you go to either suspend or hibernate, you end up with a locked screen and nothing else?

Running Beta 2 and the 2.6.32-19 kernel on a gigabyte h44m-usb3 mb, that's what's happening to me.  In both suspend and hibernate modes, according to pm-suspend.log, the system seems to indicate that it suspends, then immediately awakens and resumes.  Also, when I tell it to hibernate, the error "device USB9 failed to freeze" flashes on the screen early on in the process.  Which is strange because it doesn't seem to be reflected in the log, and is even more strange because it does so regardless of whether I have any USB devices plugged in.


I had that exact same problem on my Dell until I added acpi_osi=Linux to the kernel options.

---

### Post by openBA on 2010-04-14
10.04 beta 2, with today's updates:

On ThinkPad R51 (ATI Mobility R250, 1,5GB RAM) no waking after suspend to RAM. Just black screen. (Ubuntu 9.10 works fine)

Suspend to disk is also not working, neither on 9.10.

There are also unsolvable problems with selecting the correct resolution for external monitor.

---

### Post by P4man on 2010-04-14
> **dannyboy79 said:**
> 
asrock 775Dual-VSTA
c2d 1.8 ghz
2gb ddrII ram
nvidia 6200 128 mb ram (agp)


it's an old board, maybe i need to update the bios? although the website does say it supports ACPI 1.1 Compliance Wake Up Events

I have the same motherboard, similar cpu and another (PCI-E) nvidia card. Suspend/resume works fine here on beta 1 and 2 except for the network card not working after resume. That bug has been around for years now but can still be worked around. Anyway, try updating your bios indeed.

On my laptop, a Dell latitude D600 (ATI 9500 videocard) wake up from standby doesnt work. Not responding to anything, not even reisub. Worked fine on Karmic ](*,) Hibernate does work, but is so slow its kinda pointless.

---

### Post by a-user on 2010-04-14
neither suspend nor hybernate is wokring for me on lucid. with karmic on same machine it works.

detailed description i have in my own thread. there is also to find a log-file of a suspend try with shows no errors at all, but still it does not power down.

as i saw, i'm not the only one with this same problems.

---

### Post by jeggen on 2010-04-14
It worked great for me on the proprietary nvidia driver.  It does not work with the nouveau driver.

---

### Post by a-user on 2010-04-14
for me it does not work we either of the drivers. and i still don't get any failor message in the log.

---

### Post by mitchellcipriano on 2010-04-18
> **timosha said:**
> With kernel 2.6.32-19 suspend and hibernate work again, as they did in kernel -15.

Any experience with the latest kernels? I have -19 working well and I am reluctant to upgrade. I was hoping to benefit from you testing.

---

### Post by cariboo on 2010-04-18
@mitchellcipriano

Whats the sense in running a testing version, if you don't want to do any testing?

I've got a Compaq Mini 110, hibernate and suspend work as they should. I found that if I don't set wireless to auto connect, and initiate the connection manually I don't have a problem. The only reason I do that is because I have a router in my house, and an access point in my shop and sometimes my wireless device gets confused as to which one it should connect to and sometimes it ended up not connecting to either.

---

### Post by timosha on 2010-04-18
> **mitchellcipriano said:**
> Any experience with the latest kernels? I have -19 working well and I am reluctant to upgrade. I was hoping to benefit from you testing.

Since kernel -19, thus also -20 and -21, suspend/hibernate is working perfectly on our Thinkpads R50, R51, R52 and HP dx2400/Pavillion ax5400. It did not work on the previous kernels except for -15.

---

### Post by chek2fire on 2010-04-18
Suspend hibernate still not work in my system. Was work fine in karmic and in lucid until alpha 3. From then is break and never work again.

---

### Post by drewsus on 2010-04-18
Im using Lucid beta 2 on my Acer Aspire One and suspend/hibernate/resume is working perfectly. Ive used both a few times.

---

### Post by zoomy942 on 2010-04-18
whatever the updates were yesterday - my laptop lid works now

---

### Post by AClark on 2010-04-18
All updates current - including 2.6.32-21

Desktop with ASUS P4PE & ATI 8500 still about the same.
Suspends OK & starts to come out of suspend after pushing power button
optical drive lights flash fans come on hard drive access light flashes for several seconds but screen stays dark and there is no sign of any response to keyboard including REISUB.

Thinkpad A31 still comes out with corrupted video - I can sort of see the mouse cursor & responds to keyboard - system sounds work & I can shut down if I happen to click in the right place.

On the up side I'm still learning interesting new stuff every day.

---

### Post by bobarry on 2010-04-18
I haven't been able to use hibernate or suspend for the last couple releases on my Dell Mini9. It originally worked fine with probably the third release back. (I'm no good with names).

I tried several 'tips' to no avail, and even re-installed Ubuntu.
I even enlarged my swap file to 2.2GB since I have a 2GB memory stick in it.

Hibernate was really a nice feature when I first got my Mini and I wish I could get it going again.

Bo Barry
Harrisburg, NC

---

### Post by Sin@Sin-Sacrifice on 2010-04-18
No dice on xfx 750a

---

### Post by mitchellcipriano on 2010-04-18
> **cariboo907 said:**
> @mitchellcipriano

Whats the sense in running a testing version, if you don't want to do any testing?

I've got a Compaq Mini 110, hibernate and suspend work as they should. I found that if I don't set wireless to auto connect, and initiate the connection manually I don't have a problem. The only reason I do that is because I have a router in my house, and an access point in my shop and sometimes my wireless device gets confused as to which one it should connect to and sometimes it ended up not connecting to either.

@cariboo907

I agree, this is supposed to be a test system, but it is actually a system I use. Typically, I only run beta versions on my test machines, but when I updated my IBM R51 to Karmic my suspend/resume broke and I have been waiting for this release to hopefully fix it. Which, I am happy to say, it did, but I am fearful any kernel change may regress and I am pretty happy with it as is.

---

### Post by mitchellcipriano on 2010-04-18
> **timosha said:**
> Since kernel -19, thus also -20 and -21, suspend/hibernate is working perfectly on our Thinkpads R50, R51, R52 and HP dx2400/Pavillion ax5400. It did not work on the previous kernels except for -15.

Excellent, many thanks for the update. I can safely upgrade.

---

### Post by zoomy942 on 2010-04-18
dang.  updates today broke it again

---

### Post by mitchellcipriano on 2010-04-18
> **mitchellcipriano said:**
> Excellent, many thanks for the update. I can safely upgrade.

Unfortunately, the update did not go so well. I cannot get -21 to boot at all. I can still boot into -19, but my graphics are now limited to no effects. Previously, it was working on any setting. Any ideas?

---

### Post by cariboo on 2010-04-19
You would be better off creating a new thread, and describe the problem as well as you can, as it will probably get lost here.

---

### Post by a-user on 2010-04-19
suspend and hibernate never worked for me since i installed lucid first time and this was if i remember right with the 32.14 kernel. and the logfile never reports any failor.

i hope the final release will work or i have to stick to 9.10.

bug ticket is opened.

---

### Post by timosha on 2010-04-19
> **mitchellcipriano said:**
> Unfortunately, the update did not go so well. I cannot get -21 to boot at all. I can still boot into -19, but my graphics are now limited to no effects. Previously, it was working on any setting. Any ideas?

If you are using an Intel graphics chip remove xserver-xorg-video-intel 2:2.9.1-3Ubuntu3 via Synaptic and install version 2:2.9.9.1-3Ubuntu1 out of cache. 

Then pin this diver in Synaptic and type in a terminal:
sudo aptitude hold xserver-xorg-video-intel

---

### Post by FrancoNero on 2010-04-19
suspend has always worked nicely (thinkpad here), but hibernate has always been a ridiculous mess, and it still is. there's just no way to use it. it's hard to believe. with every single ubuntu release I'm hoping they fix a feature that's just old news in operating systems on laptops, but no....  whenever i hit hibernate by accident i run around the house cursing, because hibernate just makes my laptop unusable for about 20 minutes ,makes weird noises, shows weird thigns on screen and once it's back it behaves weird, so i need to do a proper reboot to be back to normalo. what a f**ng mess

---

### Post by openBA on 2010-04-21
kernel ...21 suspend/hibernate status report:
ThinkPad R51 with ATI R250, 15" 1400x1050 1,5GB RAM, 4GB free space on HD
- suspend (to RAM) - wake's-up to black screen and mouse cursor. It was possible to blindly login, but only to the partly visible desktop without any menus ...
- hibernate - after a long wait, .. no wake-up! Just black screen.

IMHO the related problems:
 -still not properly working xrandr/Monitor settings:
    - it is not possible to set second display resolutions
    - even on the primary monitor, if one select the lower resolution it is not possible to return to the native one!
  - after playing with suspend/hibernate I lost permanently ethernet connection!


VMWare virtual machine:
  - hibernate works fine, with the small beauty fault - it wakes-up to the black screen (similar to R51 suspend to RAM), but after blind login it works fine!

---

### Post by dcstar on 2010-04-21
Suspend and Hibernate work on my desktop system - although because 10.04 boots so fast normally Hibernating and Resuming from Hibernate is probably a lot slower than a boot now.....

The more RAM you have the longer the Hibernate/Resume cycle may be because I suspect that cached data is also preserved - and if you have a few gig of RAM used for cache, then it all takes time to write and read from the Swap space (after Swap has been cleared of program data).

People with 16G of RAM may need to go out for a meal when Hibernating.....

---

### Post by a-user on 2010-04-21
dcstar:
when you resume from hibernate, does your pc goes through bios post messages? i mean do you have this about 12 seconds drive detection messages and scuh stuff?

additionally: for me neither suspend nor hibernate is working and never worked with lucid. suspend works until the point where it should power off. but it doesnt. it freezes with black screen. no reation on keypress. same with hibernation.

logfile shows no fails, all went correct.

on same machine ubuntu karmic suspend and hibernate still works (but on resume of hibernation it runs through bios postmessages first :( )

---

### Post by timosha on 2010-04-21
> **openBA said:**
> kernel ...21 suspend/hibernate status report:
ThinkPad R51 with ATI R250, 15" 1400x1050 1,5GB RAM, 4GB free space on HD
- suspend (to RAM) - wake's-up to black screen and mouse cursor. It was possible to blindly login, but only to the partly visible desktop without any menus ...
- hibernate - after a long wait, .. no wake-up! Just black screen.

IMHO the related problem is still not properly working xrandr/Monitor settings:
  - it is not possible to set second display resolutions
  - even on the primary monitor, if one select the lower resolution it is not possible to return to the native one!


On my Thinkpad R51 - 2887 with Intel 855GM graphics chip suspend/hibernate works perfectly. So, it must be something with the video driver.

---

### Post by TheNessus on 2010-04-21
I believe suspending has been resolved? works perfectly for me now, as opposed to total failure about 3 weeks ago.

---

### Post by StuartN on 2010-04-21
Suspend / resume works beautifully, most of the time on Dell Inspiron 1501 laptop.

Sometimes the system appears to have lost track of its mount points on resume, with extremely variable symptoms. In most cases this requires a (hard) reboot, upon which a fsck is performed on the / partition.

(something like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981))

---

### Post by csaket on 2010-04-21
On Ubuntu beta 2 with latest updates, supend/hibernate/resume works perfectly.

On Kubuntu beta 2 with latest updates I find that suspend/resume does not work and if it does, it kills my wireless.

---

### Post by Kubiack on 2010-04-21
With ubuntu lucid beta 2 up-to-date with today's packages, on a ASUS N71JV-TY002V, none are working.

Suspend : lock the screen but doesn't go any further.
Hibernate : lock the screen, stop applications, then applications restart by themselves and typing the password unlock the screen.

---

### Post by Cavsfan on 2010-04-21
All of the sleep functions work perfectly for me and have since day 1 on Lucid.
And it wakes as expected - pretty much perfectly for me.
That is the main reason I installed Lucid from Karmic.
You can see my system from my sig. except I have an MSI mobo.

---

### Post by russianbandit on 2010-04-21
HP dv4t-1000 and Lucid Lynx beta 2 (up to date).
Both Suspend and Hibernate don't power the laptop off. Nothing can wake the computer on either. The screen just sits there black, but not turned off.

---

### Post by kouter on 2010-04-21
dell latitude d600 haven't been able to use suspend or hibernate since beta 2... just simply won't wake up.  tried compiling 2.6.33.2 to see if it was a kernel issue, and that had no effect either.  could it be something to do with ureadahead?

---

### Post by Student Driver on 2010-04-21
> **bobarry said:**
> I haven't been able to use hibernate or suspend for the last couple releases on my Dell Mini9. It originally worked fine with probably the third release back. (I'm no good with names).

I tried several 'tips' to no avail, and even re-installed Ubuntu.
I even enlarged my swap file to 2.2GB since I have a 2GB memory stick in it.

Hibernate was really a nice feature when I first got my Mini and I wish I could get it going again.

Bo Barry
Harrisburg, NC

Mine did the same thing until I ejected the SD card.  I found a reference to the bug in another bug filing on LaunchPad, and tried it out when I got home.  Sure enough, if I eject the SD card from the Mini 9 before suspending, 10.04 will suspend and resume perfectly fine and quickly.  I haven't gone so far as to hibernate yet, but will try that tonight.

---

### Post by sgage on 2010-04-21
I have an NVIDIA GeForce 8500 GT. With the nouveau drivers, suspend/hibernate doesn't work. Well, it suspends/hibernates, but never wakes up.

With the nvidia proprietary drivers, all works perfectly. So if you have an NVIDIA card and suspend/hibernate problems, try the proprietary nvidia drivers.

---

### Post by sgage on 2010-04-21
I have NVIDIA graphics (GeForce 8500 GT).

With nouveau drivers - won't wake from suspend/hibernation.

With nvidia drivers, works perfectly.

---

### Post by wbar2 on 2010-04-21
Hibernate and sleep ultimately work for me right now, but sometimes I get odd behavior. Like just now, coming out of sleep my caps lock key indicator light is inverted. It says its on but clearly its not, and when the light is off I get all caps. Also, I always have to adjust my brightness from the minimum back to the maximum coming out of sleep.

---

### Post by cariboo on 2010-04-21
Threads merged.

---

### Post by cubeist on 2010-04-22
for a while, I would try to suspend and nothing would happen; like I didn't even press the button, but I found that if I type sudo pm-suspend in a terminal it works perfectly.  I haven't checked to see if there is a bug report for this.

---

### Post by polki@mac.com on 2010-04-23
Asus EeePC 1001HA both supend and hibernate work perfectly!

---

### Post by radzfoto on 2010-04-24
I have Lenovo Y530 also and neither suspend nor hibernate work properly. Both suspend and hibernate appear to start working, but screen backlight is left on and all button lights are also on. Pressing buttons including power button does nothing.

To get out of this, I do the following:
From attempted suspend, I press and hold the power button until computer fully turns off. Then I press power button to start the machine. Machine then boots normally. However, wireless networking is disabled and I have to manually re-enable it. This behavior has been consistent since Lucid Beta 1, 2 and RC.

From attempted hibernate, hibernation appears to work. Computer turns itself off briefly (about 1 second) and then immediately restarts, but screen is black with back light turned on and all button lights on. To regain control, I press and hold the power button until computer fully turns off. Then I press the power button to start the machine. It then boots into last session. Which means that hibernation was able to save the state, but failed to properly shut off the machine.

I hope that this very consistent behavior can help someone to fix suspend and hibernate on the Lenovo Y530.

---

### Post by michaelzap on 2010-04-24
> **radzfoto said:**
> I have Lenovo Y530 also and neither suspend nor hibernate work properly. Both suspend and hibernate appear to start working, but screen backlight is left on and all button lights are also on. Pressing buttons including power button does nothing.

To get out of this, I do the following:
From attempted suspend, I press and hold the power button until computer fully turns off. Then I press power button to start the machine. Machine then boots normally. However, wireless networking is disabled and I have to manually re-enable it. This behavior has been consistent since Lucid Beta 1, 2 and RC.

From attempted hibernate, hibernation appears to work. Computer turns itself off briefly (about 1 second) and then immediately restarts, but screen is black with back light turned on and all button lights on. To regain control, I press and hold the power button until computer fully turns off. Then I press the power button to start the machine. It then boots into last session. Which means that hibernation was able to save the state, but failed to properly shut off the machine.

I hope that this very consistent behavior can help someone to fix suspend and hibernate on the Lenovo Y530.

This is a very accurate description of exactly what happens to me on my Y530 (the "Y" stands for "Y doesn't Ubuntu handle this hardware properly - you'd think it would!").

---

### Post by keithpeter on 2010-04-24
> **keithpeter said:**
> T42 thinkpad. Hibernate same as Ubuntu 9.10, ie broken. There is a bug on this one already.

Update: using fresh install from Lucid RC CD-ROM, suspend seems to work ok, using the lid close with appropriate setting in Power Management, and with the Fn F4 button,

Hibernate did actually work once, then after that it either never hibernates or hibernates but won't restore. I'm wondering if it is to do with other stuff left in the swap from the first hibernate?

---

### Post by mitchellcipriano on 2010-04-24
> **timosha said:**
> If you are using an Intel graphics chip remove xserver-xorg-video-intel 2:2.9.1-3Ubuntu3 via Synaptic and install version 2:2.9.9.1-3Ubuntu1 out of cache. 

Then pin this diver in Synaptic and type in a terminal:
sudo aptitude hold xserver-xorg-video-intel

I currently have the 2:2.9.9.1-3Ubuntu4 version installed. I do not seem to know how to get the old version out of cache. I can boot in the -19 kernel, but I cannot enable any desktop effects. How do I get the older driver?

---

### Post by artofsnow on 2010-04-25
I've just upgraded my Dell D630 from 9.10 to 10.04 (64 bit). Suspend/wake-up & hibernate/resume are working but resume (from hibernate) brings the laptop with a very high system load (8 or higher) and it takes a couple of minutes before the load goes down and the system becomes responsive. 
The system monitor doesn't show any special activity on the processes that could explain such a high load :confused:

---

### Post by Knowle on 2010-04-25
Works perfect, then again it's suppose to when it comes pre-installed. Lappy is a Inspiron 15n.

---

### Post by ed_qta on 2010-04-25
after instally radeonHD driver, my inspiron 6400 freezes after suspending :confused:

---

### Post by DrWig on 2010-04-29
Neither suspend or hibernate work for me.

Hibernate does it's thing, but never shuts down.  Moving the mouse brings up the password prompt.

Suspend will suspend, but coming out of it, I get no gfx (it seems as though it has come out, in other respects, but I don't know where to go, debugging wise, from here.......)

These issues are the deal breakers for me (my old laptop battery is rubbish, and so I really, really, need suspend!)

cheers

DrWig

---

### Post by tica vun on 2010-04-29
Suspend works as intended. I don't use hibernate as I didn't designate any swap space on my netbook, seeing as how I've only got a 20GB SSD in there.

---

### Post by kdnoel on 2010-04-29
I am having shutdown problems on one pc but my laptop is fine.

---

### Post by pmos69 on 2010-04-29
- Suspend doesn't work (or should I say "resume from suspend")
- Hibernate works

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

---

