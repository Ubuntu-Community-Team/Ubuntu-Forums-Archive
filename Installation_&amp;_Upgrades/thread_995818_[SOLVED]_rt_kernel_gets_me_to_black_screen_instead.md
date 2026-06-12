---
title: "[SOLVED] rt kernel gets me to black screen instead of login"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-11-28
** You can cut to the chase and go to my third post for a fix. Ended up being a known bug/conflict between the Ubuntu Studio real time kernel and the nvidia-glx-new driver. Can't identify the screen.

Hi all.

Was resurrecting my Ubuntu Studio which I haven't used for about 6 months. 8.04; downloaded about 230 updates but no joy, problems all over and thought I would just install Ubuntu straight, then install the bits of Ubuntu Studio I needed (I am quite fond of these blends). In this case, I didn't think about the rt kernel (**r**eal** t**ime for good low latency), but figured that shouldn't matter too much, all should be fine. 

Not quite. Had Ubuntu installed and all running fine. Install the required bits for ubuntu studio the first time by:

```
sudo apt-get install ubuntustudio-desktop
```which, of course, doesn't give me all the apps. So I find another site which gives a much more comprehensive command for the appropriate apps to be downloaded. I uninstall ubuntustudio-desktop and go ahead with the comprehensive list, leaving out the bits I didn't want, namely ubuntustudio-desktop (don't dig the themes) and the rt kernel, so I delete them from the command and go with this:

```
sudo apt-get update && sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```I realised as things were downloading that I should have grabbed that rt kernel, but too late, try it anyway.

I reboot when all is done and lo and behold, the rt kernel is top of the list, so I select it and it goes through the motions, tells me Ubuntu Studio is loading, progress bar etc. Then when we should be at the login screen, I get a blank, black screen instead. Wait awhile ... nothing. No change.

Wondering if the rt kernel is leftover from the original install of ubuntustudio-desktop and when I have unistalled that, installed the other packages instead and left off the rt kernel, it is using the old one. Doubt that would be the problem but just a thought ...

Any suggestion greatly appreciated as Jack is not loving it in the non-rt kernel and can't get much happening on the audio side. Bottom line? Booting fine, initial splash fine, dies at login screen and gives me black screen indefinately. Every other kernel on the machine works faultlessly (so far). Windoze XP also boots no problem. Not partition issue if anyone is heading down that track. 

Tnx in advance, Ubunteers. :)

---

### Post by Bucky Ball on 2008-11-28
Well, I've tried most the things I know of for now. If anyone has any idea, fire away any time ...

Ubuntu working fine with the latest kernel (.22) but the black screen on the latest kernel for UStudio (.22). Ctl/alt/f1 doesn't get me out of the hang. Recovery mode lets me drop to a shell though. Have tried 

```
sudo apt-get update
```... then go for a 'normal boot' but nothing. When I updated from .21 to .22 for Ubuntu, I had the same problem but the code above seemed to fix everything there. ](*,)

I use this box as a DAW for high-end audio software (Pro Tools, Sibelius, Cubase) with Windoze and want to see what I can do with a Linux DAW. Not worth trying until I can get the real time kernel happening.

---

### Post by Bucky Ball on 2008-11-29
Well, I got my problem fixed. The problem was with the Ubuntu Studio rt (real time) kernel and nvidia-glx-new driver. Start to finish I followed the original instructions from the first post here:

```
sudo apt-get update && sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```From this page:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

... you will note my code omits the ubuntustudio-desktop from the one on that page. Boot up and black screen where the login screen should be. So, then I did this:

[quote=overdrank]1) Open a modules file for editing with:-
 
 ```
sudo nano /etc/default/linux-restricted-modules-common
``` 2) Edit the DISABLED_MODULES line to make it look like this:-
 
 ```
DISABLED_MODULES="nv nvidia_new"
```[/quote]

from this page:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

(Thanks overdrank). Rebooted and said there was a problem with the X server this time around. No screen (obviously why it was going to black at login). So ran the rt (recovery) kernel, chose the option to fix the X server, and voila! All working fine. Basically gave me a clean xorg.conf with no nvidia, so that is the only downside. You should be right to go with that code even though it says it is for 7.10, and if you are not using nvidia-glx-new driver, you won't have the same problems as I did. It is not a problem with the way I was doing it (installing the studio packages from inside an existing Ubuntu install), but a known bug with Ubuntu Studio and the nvidia-glx-new driver, so it wouldn't have mattered if I went for a clean install anyhow (unless Studio loads an appropriate nvidia driver that it can work with). Good luck to all! And if anyone knows of an nvidia driver that will work with the Studio real time kernel, that would be great. Good luck ... :)

---

