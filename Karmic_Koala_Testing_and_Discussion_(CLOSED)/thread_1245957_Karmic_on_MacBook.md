---
title: "Karmic on MacBook"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2009-08-21
Hi, have anyone got Karmic to work on your MacBook?
I tried to upgrade from Jaunty to my MacBook(5,1) but now gnome won't load.
It sais screen:0 is busy. I upgraded to see if Karmic would work better.

---

### Post by Richardcavell on 2009-08-21
Karmic's working on my MacBook2,1.  Obviously mine's an earlier generation.  In some ways it's better than Jaunty (particularly video support), but it's very, very buggy.

I guess with an alpha release you can only put in your bug report and wait for the final release to see if it works.  I think it's too early to make a general statement about whether Karmic is better than Jaunty for MacBooks.

Richard

---

### Post by Tompalaz on 2009-08-21
Yea, since it's a alpha I don't really have any expectations.
Jaunty don't work rely good so I thought I give Karmic a shot.

I will make a fresh install soon.

---

### Post by Tompalaz on 2009-08-21
Okay, that didn't work to good...
When I try to boot from cd it says fatal error: no screen found. I can't get X to start. Any clue on how I can move on?

I'm not that good with troubleshooting but I've tried to boot with safe grafic mode, same thing, X don't start :(.

Edit: Everything works great now. I just had to remove .gnome2 folder

---

### Post by brujoand on 2009-09-22
Well I'm running Ubuntu 9.10 alpha 6 and pretty much everything works perfectly out of the box. Only issue is some trouble with the touchpad. But finally reboot works like it should. Im on a Macbook Pro 5.1

---

### Post by robin.nightingale on 2009-09-25
I also had some issues with the Touchpad the regular > sudo gedit /etc/hal/fdi/policy/appletouch.fdi

doesent havent any effect on my Touchpad.
So i removed the file again and installed the Synaptic Touchpad driver via the new ubuntu software store. And now everything works like a charm.
The driver became realy handy compared to jaunty. Just install and configure it in your system settings and it works out of the box.


Most of the other things Work o.k. for me. Till now its the best ubuntu ever runnig on my macbook 3. Some things are still a bit flaky but you can see things getting more stabel ever day.

The developers did a realy nice work.

---

### Post by Bachstelze on 2009-09-25
5,5 here, pretty much everything worked OOTB, Just had to install ndiswrapper for the wireless.

---

### Post by produnis on 2009-09-25
> **robin.nightingale said:**
> 
... installed the Synaptic Touchpad driver via the new ubuntu software store. And now everything works like a charm..
I wonder how to configure the touchpad. Is there any application?

I would like to change right-click-emulation to "two fingers + click"  (default is "three fingers + click)

---

### Post by ssteph on 2009-09-25
Hi,

I agree with others. It works better out of the box (I was using since July
a MacBookPro5,1 under Jaunty). Started from a fresh install with alpha6.

I found the following output in the log that shows that the model had been
correctly identified.

Sep 25 16:48:51 macbookpro kernel: [    5.759760] applesmc: Apple MacBook Pro 5 detected:
Sep 25 16:48:51 macbookpro kernel: [    5.759763] applesmc:  - Model with accelerometer
Sep 25 16:48:51 macbookpro kernel: [    5.759764] applesmc:  - Model with light sensors and backlight
Sep 25 16:48:51 macbookpro kernel: [    5.759766] applesmc:  - Model with 20 temperature sensors
Sep 25 16:48:51 macbookpro kernel: [    5.760788] applesmc: device has already been initialized (0xe0, 0x00).
Sep 25 16:48:51 macbookpro kernel: [    5.760790] applesmc: device successfully initialized.
Sep 25 16:48:51 macbookpro kernel: [    5.761454] applesmc: 2 fans found.
Sep 25 16:48:51 macbookpro kernel: [    5.763738] input: applesmc as /devices/platform/applesmc.768/input/input8
Sep 25 16:48:51 macbookpro kernel: [    5.765464] Registered led device: smc::kbd_backlight
Sep 25 16:48:51 macbookpro kernel: [    5.765481] applesmc: driver successfully loaded.
[U]
Out of the box (alpha6) what works or not :[/U]

- Sound works (speakers). however headphone doesn't :-(.
- Nvidia requires a reboot after activating proprietary drivers.
- Keyboard need little adjust in System menu (after adjusting local).
- Keyboard Led (CAP-LOCK) works :-).
- Reboot works !!! however it's pretty long (20/30s).
- Still hotter than under OS X (to be confirmed because of desktop effect).

_Post install (alpha6) :_

[FONT=System]- Fix WIFI if it doesn't works with sudo apt-get install bcmwl-kernel-source[/FONT].
- sudo apt-get install pommed gpomme wmpomme. This will add backlite 
keyboard with the appropriate key. For me I need to launch pommed and 
gpomme at every boot.

Waiting now for the final release of this pretty cool Koala. 

Regards
Stéphane

---

### Post by Aybara on 2009-09-25
Stéphane:
Did wireless work OOTB for you? I have the same MBP, and the same experiences, except wireless doesn't work even after I installed the restricted Broadcom drivers. In Jaunty it worked OOTB without any restricted drivers.

---

### Post by ssteph on 2009-09-25
Hello Aybara,

I was on an ethernet link when I posted and unfortunatly didn't test the WIFI :-(.
As you said the wifi doesn't work OOTB.

Regards
Stéphane

---

### Post by alexmurray on 2009-09-25
Seems [others]("http://ubuntuforums.org/showthread.php?t=1236299") (ie. non MBP users) are having issues with Broadcom wireless as well. I seem to recall having similar difficulties getting the bcmwl-kernel-source package properly installed and set up when I first installed Karmic Alpha 4.. I would suggest using Synaptic and make sure the [bcmwl-kernel-source]("apt:bcmwl-kernel-source") and [dkms]("apt:dkms") packages are installed, and if they already are try re-installing them.

If that still doesn't work perhaps see [this post]("http://ubuntuforums.org/showpost.php?p=7794522&postcount=36") for a potential solution.

---

### Post by ssteph on 2009-09-27
Thanks you Alex for this information.

As you suggested I did :

[FONT=System]sudo apt-get install bcmwl-kernel-source[/FONT]

and after a reboot it works !

Regards
Stéphane

---

### Post by ssteph on 2009-09-27
I add this reply to trace the time to boot (wich seems very long
on the alpha6). But maybe it's normal for an alpha release :confused:.

Recorded on my Macbook Pro 5.1 (timing are not very accurate
but this is to give an idea).

T = 0s : Press Power
T = 39s : White screen (Mac like).
T = 52s : Grub text.
T = 1:18s : Ubuntu Splash screen.
T = 1:21s : Sound but Splash screen frozen.
T = 1:55s : Login screen (user input possible).
-> Here I logon.
T = ??s : Splash screen (again but not frozen)
with sound.
T = ??+~4s : Gnome Desktop.

---

### Post by emrys on 2009-09-27
On a MacBook Pro 5,3 the only problems so far:

#1. Sound initially not working. Had to install the alsa driver unstable and alsamixer. (Used the script attached for the first part. It is not mine but I don't remember the origin. My apologies) Now it is perfect.

#2. Suspend not working. It does not appear as an option.

#3. Can't play videos. No idea why.

Any help on #2 and #3 would be appreciated.

---

### Post by emrys on 2009-09-27
> **emrys said:**
> On a MacBook Pro 5,3 the only problems so far:

#1. Sound initially not working. Had to install the alsa driver unstable and alsamixer. (Used the script attached for the first part. It is not mine but I don't remember the origin. My apologies) Now it is perfect.

#2. Suspend not working. It does not appear as an option.

#3. Can't play videos. No idea why.

Any help on #2 and #3 would be appreciated.

Ok, #2 solved. For some reason, when upgrading from Jaunty the ubuntu-laptop-mode package was uninstalled. Bringing it back solved the problem.

And #3! Don't know why. When installing ubuntu-laptop-mode that was solved too... Strange... but great! Everything works now.

---

### Post by Tompalaz on 2009-09-27
Made a clean alpha 6 install some days ago. Everything but wifi and two finger scroll worked OOTB. It's easy stuff to fix. Install wifi driver from System - Administration - Hardware and fixed two finger scroll in System - Settings - Mouse / Touchpad.

---

### Post by amortvigil on 2009-09-30
My problem was that i couldnt boot. no grub after refit, made it a topic on the formums cus i fixed it.

---

### Post by damagu on 2009-10-02
> **robin.nightingale said:**
> I also had some issues with the Touchpad the regular 

doesent havent any effect on my Touchpad.
So i removed the file again and installed the Synaptic Touchpad driver via the new ubuntu software store. And now everything works like a charm.
The driver became realy handy compared to jaunty. Just install and configure it in your system settings and it works out of the box.


Um... I tried to do this but the synaptic touchpad driver doesn't appear to be in the app store. Did you have to enable other sources or something?

---

### Post by damagu on 2009-10-02
In fact, I am having trouble getting a lot of things working because app store claims a lot of things are "Not available with the current data"... whatever that means. 

Also when I go to the system > admin > hardware drivers window I get no list of drivers and a message at the top says there are no proprietary drivers in use on this system. I figure I need to install the NVIDIA drivers to get compiz working.
 
I've got wireless though. All of my keys are working as they should, although I suspect that's because I had configured them the way I wanted them on my previous install of intrepid and with the new installation I kept my home partition from the last one.

Global Menu doesn't seem to work at all. The desk bar is also gone and I can't seem to install it. I don't know if it's been replaced by something else but I really want it back (or to find out what the alternative is if there is one).

UbuntuOne doesn't appear to be working either. I just get the icon in the taskbar with a red x over it. I assume this means something is wrong. I'd never used it before so I don't know if it's just the new install or if there's something I'm not doing right.   

Really need to get the trackpad fixed. Then I'll feel better about tackling everything else. :D

---

### Post by hanzomon4 on 2009-10-02
From a fresh alpha 6 install:

Working OTB
*Wifi via opensource ath9k driver
*Sound
*Suspend
*Backlight
*Special hotkeys (volume, backlight, eject, numlock,)
*iSight camera

Almost OTB
*Installed the proprietary Nvidia drivers via restricted hardware manager

Not working
*Keyboard backlight

I'm using it full time at school this semester even for my sound art and art-tech studio classes! I've already freaked a few people out..

---

### Post by undoIT on 2009-10-03
I now have a fresh install of Karmic beta installed on my Macbook 5,1. Brightness adjustment for the screen was working before installing the restricted Nvidia driver 185. Now it is stuck at max brightness. Has anyone been able to get the brightness working after installing the Nvidia proprietary driver?

Note: I also installed pommed from Mactel PPA, after which the keyboard backlight is lit. However, the hotkeys don't work to adjust brightness.

---

### Post by e-rebus on 2009-10-03
I am on MacbookPro 5,3 here. After installing Alpha 6 with further updates to beta the only things that were not working OOTB were: sound, keyboard backlight hot keys (F1,F2), LCD backlight and hot keys (F5,F6). Had to install proprietary NVIDIA and wireless drivers to get accelerated video and wireless to work.

 To fix sound I had to compile the latest ALSA from sources after which pretty much everything works except I cant switch to external mic.

 To fix LCD backlight I had to install mbp-nvidia-bl-dkms_0.22~jaunty_all package from Jaunty's mactel ppa, maybe there's a better way but I did not find it.

 Keyboard backlight itself actually works OOTB, i.e. I can change it from command line, but I could not get the hotkeys to work.

Everything else works fine (suspend, bluetooth, webcam, internal speakers/mic, external headphone jack).

---

### Post by damagu on 2009-10-04
I've been having a bit more of a look at what I can and can't do with Karmic on my MBP 3,1.

[LIST]

[*]I don't seem to be getting any updates. However, I don't know if it's normal to get updates on a beta release.

[*]I don't have any drivers listed in the [FONT="Courier New"]system > administration > hardware drivers[/FONT] window. So I can't enable the drivers to make compiz work. 

[*]A lot of the entries in the app store say "not available with the current data". I don't know what that means. 

[*]UbuntuOne doesn't connect. Although I assume this is because it's not available yet.

[*]The trackpad isn't affected by changing the touchpad settings. And, I can't install synaptic touchpad control because, again, it's "not available with the current data". 

[/LIST]

Can someone tell me if it's just because it's the beta version? It seems other people aren't having the same problems. Either way it's not long till the official release.

---

### Post by nukedeath on 2009-10-04
On my MacbookPro5.3 on 9.10 Beta i had to go to hardware drivers to get wireless and GFX working. 

Downloaded and installed the newest ALSA snapshot, got sound on headphones, but not on the internal speakers.

Keyboard back-light don´t work, and can´t adjust LCD back-light with keyboard hot keys.

I will follow this threat, maybe someone finds some strange solution for these problems :)

----
Cheers from a Tri-booter

---

### Post by damagu on 2009-10-04
> **nukedeath said:**
> On my MacbookPro5.3 on 9.10 Beta i had to go to hardware drivers to get wireless and GFX working. 

Strangely wireless worked OOTB for me. Perhaps because I had it working on intrepid and I kept my /home from the previous install.

---

### Post by thinktyler on 2009-10-06
Reporting for 5,2 macbook pro users:
Bluetooth working paired mighty mouse + iphone
Compiz gfx working via 185 prop drivers
Sound not working (contrary to docs, I did an upgrade instead of fresh install and was running jaunty alsa patch)
Wireless not working - Tried deactivating, activating. Reinstalling packages as stated in this forum. currently installing ath9k.
Boot averages 120 seconds.
Shutdown averages 180 seconds.

I would recommend not doing an upgrade (of course)[I was being adventurous.

Unfortunately, I have a paper due Thursday and I need wireless, so I'm going to install jaunty. Thought I would report my experience, thus far. I hope to experiment more, but not until next week.

---

### Post by stephana on 2009-10-06
after installing the available updates today, the backlight-control on my macbook 4.1 is working.

---

### Post by produnis on 2009-10-06
after installing the updates of today, wireless network is broken... :( (MacbookPro4,1)


Additionally, I have the following Problem since Jaunty on my MacbookPro4,1:
In random time, the keyboard and mouse seem to hang for about 5 Seconds. During that time, the mouse freezes and there is no response from the keyboard (by the way: It does not matter if I plug in an external usb-mouse or usb-keyboard).

After this 5 seconds, I am able to hit some keys again, but it looks as if CapsLock is activatet (but it is not). If I am writing a text while the problem comes up, some of the following letters are cAPiTaliZED (<-- like I did there) and some are not... 

After freezing for 2-4 times, everything is fine again for hours.
I cannot say that this problem is connected to a specific software or task I am working on...
... it occures whenever it "wants" to do... no matter which software is active...
CPU / RAM and SWAP don't show any strange things, everything looks just normal...
:(

In System/Prefernces/Keyboard, I selected MacbookPro(INTL) and German Layout... and I tried just "Apple-Laptop", but without any resuölt

Does anyone face(d) the same problem?
Does anyone have a workaround?

---

### Post by zevans on 2009-10-08
> **damagu said:**
> 
[LIST]

[*]I don't seem to be getting any updates. However, I don't know if it's normal to get updates on a beta release.

[*]I don't have any drivers listed in the [FONT="Courier New"]system > administration > hardware drivers[/FONT] window. So I can't enable the drivers to make compiz work. 



You should be getting updates, I've had loads since first installing. The beta is most definitely updated!

I -think- from reading changelogs on some of the updates your missing "hardware drivers" window has already been fixed in one of those updates.

---

### Post by tgui on 2009-10-10
You don't need the latest version of alsa to get the headphones to work. I've had similar issues after fresh installs since alpha 4. The problem in each case was that the sound app doesn't provide total (or easily found) control over all the channels.

My solution, install gnome alsa mixer. Far right option uncheck the mute button and scale volume as needed. This will also get all speakers on you mac working.

---

### Post by N_Nick on 2009-10-10
After reading all your posts about successfully installing Karmik on Macbook's and Macbook Pro's i downloaded and installed the beta on my 4.1 Macbook Pro. I have to say that Karmic was the best OOTB experience i had so far.

The only "fuss" i went through was launching "Hardware Drivers" for the wireless and Nvidia driver. :)

I haven't timed anything but i *think* that boot times are a bit slower, that doesn't concern me though.

---

### Post by Tompalaz on 2009-10-10
Anyone of you got your iPod working?

---

### Post by undoIT on 2009-10-13
Does anyone remember the command to adjust brightness from terminal? At least this would suffice until the brightness controls are working on the Macbook 5,1

---

### Post by &#30333;&#12356;&#29066; on 2009-10-13
> **tgui said:**
> You don't need the latest version of alsa to get the headphones to work. I've had similar issues after fresh installs since alpha 4. The problem in each case was that the sound app doesn't provide total (or easily found) control over all the channels.

My solution, install gnome alsa mixer. Far right option uncheck the mute button and scale volume as needed. This will also get all speakers on you mac working.
Something must've changed for the Beta.

I've done a fresh install of the Karmic beta, MacBook Pro 5,2. And no sound. Nothing is muted in alsamixer.

Even got the latest dev alsa, compiled installed, still no sound, don't know what's wrong.

---

### Post by rifak on 2009-10-13
i'm running macbook3,1 and everything worked out of the box (well, except fn keyboard functions, but pommed fixed it). ive been keeping up with all updates, kernel updates and everything, and it has been very smooth. the macbook3,1 has intel video card and i havent noticed any performance issues really. it has been a WAY better experience then jaunty.

---

### Post by thinktyler on 2009-10-14
> **&#30333 said:**
> Something must've changed for the Beta.

I've done a fresh install of the Karmic beta, MacBook Pro 5,2. And no sound. Nothing is muted in alsamixer.

Even got the latest dev alsa, compiled installed, still no sound, don't know what's wrong.

Agreed.

No sound. Have you tried installing the ALSA patch for Jaunty on Karmic? 
Do you have wireless? Because I don't.

---

### Post by &#30333;&#12356;&#29066; on 2009-10-14
> **thinktyler said:**
> Agreed.

No sound. Have you tried installing the ALSA patch for Jaunty on Karmic? 
Do you have wireless? Because I don't.
Sound doesn't work even with the jaunty patch, as well as with the latest alsa.

I think it's related to linux-modules-restricted disappearing from the repositories, as before that sound worked.

Maybe they will fix it for the final 9.10 release in two weeks.

---

### Post by eragon100 on 2009-10-14
> **&#30333 said:**
> Sound doesn't work even with the jaunty patch, as well as with the latest alsa.

I think it's related to linux-modules-restricted disappearing from the repositories, as before that sound worked.

Maybe they will fix it for the final 9.10 release in two weeks.

Hello! I don't have a macbook, but I don't think that linux-modules-restricted would have anything to do with your problem :wink:

I do think however that that package will be put back before final release, since I believe it is essential for some things to function. So I figure that if it has anything to do with it, you will indeed have :guitar: in the final, White Bear.

---

### Post by &#30333;&#12356;&#29066; on 2009-10-14
Well, sound was working somewhere around Alpha 3. Now on a clean install it doesn't and no matter how I fiddled with it, and all the tricks I tried, couldn't be enabled.

Plus, I saw [http://ubuntuforums.org/showthread.php?t=1281990&highlight=macbook](http://ubuntuforums.org/showthread.php?t=1281990&highlight=macbook)

So, thought it could be connected :O)

Hell, I'm tempted to try the daily snapshot, but don't know if it's worth another two hour round of installing, not working, and then restoring 9.04 :O(

The Bear

---

### Post by undoIT on 2009-10-14
I figured out how to get brightness adjustment working for Macbook 5,1:

[http://ubuntuforums.org/showpost.php?p=8104672&postcount=10](http://ubuntuforums.org/showpost.php?p=8104672&postcount=10)

---

### Post by &#30333;&#12356;&#29066; on 2009-10-16
I've figured out the sound issue, it's a pulseaudio thing, doh...

Anyhow, to get sound working on the MacBook Pro in Karmic:

**sudo aptitude purge pulseaudio**

after that apply the Jaunty alsa-driver fix, compiling and installing the driver.

Then reboot, increase the respective volumes in alsamixer, and your sound will work.

---

### Post by benjamimgois on 2009-10-16
Somebody could post some pictures or even a video of a Macbook booting Karmic ? It would be nice to see.

---

### Post by e-rebus on 2009-10-16
> **benjamimgois said:**
> Somebody could post some pictures or even a video of a Macbook booting Karmic ? It would be nice to see.

It would be no different than any other computer booting Karmic :)

---

### Post by &#30333;&#12356;&#29066; on 2009-10-16
> **&#30333 said:**
> I've figured out the sound issue, it's a pulseaudio thing, doh...

Anyhow, to get sound working on the MacBook Pro in Karmic:

**sudo aptitude purge pulseaudio**

after that apply the Jaunty alsa-driver fix, compiling and installing the driver.

Then reboot, increase the respective volumes in alsamixer, and your sound will work.
After this, reinstall pulseaudio, and it'll work, and you'll have the volume control back.

---

### Post by mabovo on 2009-10-16
Why Touchpad doesn't have a unique menu option in Karmic ?

How someone would have to guess searching on System > Preferences > Mouse ?

Touchpad is the only not "ootb" on my MackBook2,1.

---

### Post by undoIT on 2009-10-17
> **benjamimgois said:**
> Somebody could post some pictures or even a video of a Macbook booting Karmic ? It would be nice to see.

It is quite nice. It's not perfect yet but I am very pleased with Karmic on my Macbook. Mactel team et al are doing a good job :)

---

