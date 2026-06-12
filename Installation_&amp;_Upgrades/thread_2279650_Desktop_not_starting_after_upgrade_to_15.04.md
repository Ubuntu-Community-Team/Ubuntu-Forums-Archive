---
title: "Desktop not starting after upgrade to 15.04"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-05-25
Ausus Rampage IV Extreme
Intel(R) Core(TM) i7-4820K CPU @ 3.70GHz

[COLOR=#222222][FONT=Verdana]Not sure the title is a correct description!
[/FONT][/COLOR]I have a PC with xUbuntu, was running 14.10 perfectly well until, I upgraded to 15.04 yesterday when it prompted me that there was a new version available.  It ran the upgrade, but after rebooting the load stops (after Grub) at a point where it says new USB hardware found.  It goes no further.
I try a reboot - using the power button - and the same.  Will not go beyond the new USB device found....  I have removed the only USB device - Bluetooth for keyboard, but makes no difference.
Not sure the USB line is no more than a red herring.

No more info at this point.  If anyone can advise on how to get more info, happy to oblige.

EDIT:
Tried a few more times.  Getting slightly different results.  Seems to stick at a new point.  Screen shot/photo attached.

---

### Post by Frogs Hair on 2015-05-25
Moved to Installation & Upgrades.

---

### Post by Jonners59 on 2015-05-27
Thank you....

Seems to be going from bad to worse.  None of the images work and neither does the CD or boot recovery.  Getting frustrated now.

---

### Post by Elfy on 2015-05-27
have you got a keyboard/mouse you can swap for the wireless set? - see how much further it gets

it fails to boot with live session? 

tried using any of the F6 options at livesession? like nomodeset [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Jonners59 on 2015-05-28
Hiya Elfy

Long time!
I will try and dig out an old KB to give it a bash.  I recall that when I built this machine last year it failed for some reason on another upgrade and I put it down to the HD.  Goit a replacement and got the machine working, then plugge in the 1st HD and it worked fine, so i might just check them out too.  Though I suspect this is a glitch in the upgrade somewhere and has upset the machine.  Don't want to rebuild it as it has taken 7 months to get it set up!

I will be a while before I get back on this as I have to prep for an job interview at the end of next week...  :-)

Best
Jonners59

---

### Post by Jonners59 on 2015-06-03
OK, so I managed to boot in.  I suspected it maybe a HW issue, but caused by a config of some kind.

I tried the Ubuntuv recovery CD and the like but nothing worked.

Tried a plugged in keyboard, that allowed me to use the Boot-Repair, so things were moving fwd and I cioukld play with GRUB, but nothing really changed.
I then went in to BIOS and played with the settings, just tinkering...   I found it allowed me to boot up, but it would stop always the same place.

I then thought, maybe it was because I had 2 x Video cards, so took one out and first run it froze and rebooted at the log in screen... aftwer the reboot, worked fine....  So it was confused, it seems with the two video cards...   NOTE to self, upgrade with only one card...

Now 2 probs.
1. I would like to re-install the 2nd card.  HOW without having the same problems.
2. I get this message - yes it was also showing before this problem, but now seems as good a time as any to fix it...  

[HTML]UPDATE INFORMATION

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

wine-silverlight5.1-installer, netflix-desktop

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.[/HTML]

Netflix and these apps are installed and working already.

Best Jonners

---

### Post by Elfy on 2015-06-04
I'm not sure how you originally installed 2 cards, maybe do that again. 

I'd start with one working (and it's proprietary driver if there is one) then shutdown and see where you get to from there. 

This might help [https://cornerstone.multitouch.fi/cornerstone-documentation/multiple-graphics-cards](https://cornerstone.multitouch.fi/cornerstone-documentation/multiple-graphics-cards)

as far as the wine issue - I'd start a thread for that in [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by Jonners59 on 2015-06-04
Cheers Elfy

> **Elfy said:**
> I'm not sure how you originally installed 2 cards, maybe do that again. 

I'd start with one working (and it's proprietary driver if there is one) then shutdown and see where you get to from there. 

This might help [https://cornerstone.multitouch.fi/cornerstone-documentation/multiple-graphics-cards](https://cornerstone.multitouch.fi/cornerstone-documentation/multiple-graphics-cards)

To be honest when I installed it, I just incerted the card and it worked.  I did notice when messing about yesterday that NVIDIA settings manager was not the full config which from experience means it is not properly installed.  I have fixed this before on other machines by uninstalling all the proprietry NVIDIA drivers and some other NVIDIA bits n bobs and then reinstalling again.  I shall give that a go.  I suspect that is what has caused all the problems.  This has been a known bug...


> **Elfy said:**
> 

as far as the wine issue - I'd start a thread for that in [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Probably best...

---

### Post by Elfy on 2015-06-04
>  I suspect that is what has caused all the problems.If you upgraded with the nvidia driver in place it's possible. I'd certainly go for reinstalling that.

---

### Post by Jonners59 on 2015-06-13
OK, seems to finally be fixed, though does not remember where I put icons upon reboot, though I know this to be a bug...

Stuff that seemed to work

            [FONT=Arial]Boot in to Low Graphics mode[/FONT]            
            [FONT=Arial]Control+ALT+F1[/FONT]            
            ```
[FONT=Arial]apt-get clean && apt-get autoclean && apt-get autoremove[/FONT]
```
```
[FONT=Arial]dpkg –l  grep nvidia[/FONT]
```[FONT=Arial]lists everything installed for nvidia[/FONT]            
            [FONT=Arial]then remove everything except[/FONT]            
            [FONT=Arial]nvidia-cg-toolkit (if it or equivellent exists)[/FONT]            
            [FONT=Arial]nvidia-common[/FONT]            
            ```
[FONT=Arial]sudo apt-get purge nvidia-xxxx[/FONT][FONT=Arial]
```[/FONT][FONT=Arial] (where xxxx is anything from the list)[/FONT]
            ```
[FONT=Arial]apt-get autoremove[/FONT]
```
```
[FONT=Arial]sudo dpkg-reconfigure nvidia-common[/FONT]
``````
[FONT=Arial]sudo apt-get install xserver-xorg-video-nouveau[/FONT]
```
```
[FONT=Arial]apt-get clean && apt-get autoclean && apt-get autoremove[/FONT]
```
            ```
[FONT=Arial]apt-get update && apt-get install -f[/FONT]
```
```
[FONT=Arial]sudo reboot[/FONT]
```
AND/OR


                                    
[FONT=arial]boot with old kernel (3.13.0-44)[/FONT][FONT=arial]2) login without gui (ctrl-alt-f1)
[/FONT][FONT=arial]login with root (if enabled)
[/FONT][FONT=arial]stopping lightdm (```
sudo service lightdm stop
```)
[/FONT][FONT=arial]a little cleaning (```
sudo apt-get clean && apt-get autoclean && apt-get autoremove
```)
[/FONT][FONT=arial]update source and fix ```
sudo [/FONT][FONT=arial]apt-get update && apt-get install -f[/FONT]                
```[FONT=arial])
[/FONT][FONT=arial]install nvidia (```
sudo apt-get install --reinstall nvidia-331-updates-uvm
```)
[/FONT][FONT=arial]upgrade (```
sudo apt-get upgrade
```)
[/FONT][FONT=arial]reboot (```
sudo shutdown -r now
```)
[/FONT][FONT=arial]boot with new kernel (3.13.0-45)[/FONT]

---

