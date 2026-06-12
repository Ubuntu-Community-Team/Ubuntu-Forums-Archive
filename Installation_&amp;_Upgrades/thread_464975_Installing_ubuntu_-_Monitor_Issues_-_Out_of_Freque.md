---
title: "Installing ubuntu - Monitor Issues - Out of Frequency"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by creativ3rst on 2007-06-05
Hi, 

Fresh Download, new cd... Booted fine.
Some uBuntu loading screen came up after i selected to install. When the loading bar finished, i recieved the out of frequency message. No chance to do anything....

Any help, or suggestions?

---

### Post by dabl on 2007-06-05
> **creativ3rst said:**
>  after i selected to install

Are you saying it ran OK as a live CD?  You might boot it again, and while running as a live CD, check System>preferences and see what resolution and refresh that it is happy with.  That would be a good start to figuring out how to set it during installation.

---

### Post by 1mouseclick on 2007-06-05
I had the same problem with a brand new computer my students built. It was puzzling since Uuntu was sent to me on the pretext that it was easier to use. I have installed and used SuSE before and never had this problem.
Any help you find would also be welcome. :o

---

### Post by creativ3rst on 2007-06-05
Live CD doesnt work...out of frequency....

---

### Post by dabl on 2007-06-05
> **1mouseclick said:**
> I had the same problem with a brand new computer my students built Are you sure they got it right -- can it run with other OS's?

>  Ubuntu was sent to me on the pretext that it was easier to use. C'mon -- Ubuntu isn't sent on "pretexts" -- someone kinda had to ask for it, didn't they?

>  I have installed and used SuSE before and never had this problem. On THAT PC?????  I thought it was new, built by students ....

>  Any help you find would also be welcome. :o Usually, for video/graphics problems, during the installation routine if you will choose "no" on the screen that asks if you want to auto-detect the graphics card, and then on the next screen tell it to use "VESA" as the display type, you can get a GUI interface working. Then you can search this forum and Google for information about your particular situation -- some of the Via and S3 chips do prove troublesome to get performing well. You also might want to try using the "Alternate" installation CD, as it has more user options during the process.

Hope this helps! ;)

---

### Post by 1mouseclick on 2007-06-05
Quote:
Originally Posted by 1mouseclick View Post
I had the same problem with a brand new computer my students built
Are you sure they got it right -- can it run with other OS's?
[COLOR="Navy"]
Yup, XP loaded aand ran like a rock on the dual core box.[/COLOR]

Quote:
Ubuntu was sent to me on the pretext that it was easier to use.
C'mon -- Ubuntu isn't sent on "pretexts" -- someone kinda had to ask for it, didn't they?
[COLOR="Navy"][COLOR="Navy"]
I did send a response card, but there were interested in getting in the schools and I need something for the kids to play with and learn the linux system.


Quote:
I have installed and used SuSE before and never had this problem.
On THAT PC????? I thought it was new, built by students ....

[COLOR="Navy"]No not on that PC, I was just making the point that I had not run into this issue before.[/COLOR]

Quote:
Any help you find would also be welcome.
Usually, for video/graphics problems, during the installation routine if you will choose "no" on the screen that asks if you want to auto-detect the graphics card, and then on the next screen tell it to use "VESA" as the display type, you can get a GUI interface working. Then you can search this forum and Google for information about your particular situation -- some of the Via and S3 chips do prove troublesome to get performing well. You also might want to try using the "Alternate" installation CD, as it has more user options during the process.

[COLOR="Navy"]I will give it a 3rd try, I knew to look for an alternate video display, and I saw it at the bottom and hit F4, but it seemed to have not effect on the start up. This is where I seemed to run into the problem.
Thanks loads for the reponse btw. I would like to see if this distro is the one that will be easiet for my students to ease into. I looks like it has that poential.[/COLOR]

Hope this helps!

---

### Post by dabl on 2007-06-05
> **creativ3rst said:**
> Live CD doesnt work...out of frequency....

That's unfortunate -- the live CD is pretty flexible in figuring out how to run a live session on most hardware setups.  Apparently it doesn't recognize your graphics chip, or perhaps it does recognize it but sets it to a refresh rate that your monitor can't stand.  If you Google around, you might find that there is a way to get the Ubuntu installer started in VGA mode, with a benign refresh rate, that will let you get started.  Otherwise, if you can get your paws on another monitor, for use just to get it installed, then you can change the refresh rate to the range that you normal monitor wants to see.  Sorry I can't provide a magic bullet for this one :(

EDIT:  If you get your system installed with a borrowed monitor, then go in to System>Preferences, get to the display settings and change the refresh rate(s) to what your normal monitor will accept.  Then just plug in your normal monitor and it should work.  Good luck!

---

### Post by 1mouseclick on 2007-06-05
> **dabl said:**
> That's unfortunate -- the live CD is pretty flexible in figuring out how to run a live session on most hardware setups.  Apparently it doesn't recognize your graphics chip, or perhaps it does recognize it but sets it to a refresh rate that your monitor can't stand.  If you Google around, you might find that there is a way to get the Ubuntu installer started in VGA mode, with a benign refresh rate, that will let you get started.  Otherwise, if you can get your paws on another monitor, for use just to get it installed, then you can change the refresh rate to the range that you normal monitor wants to see.  Sorry I can't provide a magic bullet for this one :(

EDIT:  If you get your system installed with a borrowed monitor, then go in to System>Preferences, get to the display settings and change the refresh rate(s) to what your normal monitor will accept.  Then just plug in your normal monitor and it should work.  Good luck!

[COLOR="Navy"]This has been helpful, it has given me some more things to try. I was disappointed for my guys last week.
I had just gotten the CD and was going to give them SuSE, but after reading about Ubuntu gave it first shot.
I will try more on my own.[/COLOR]

---

### Post by wpshooter on 2007-06-05
Am I correct in that you are probably using an ATI video card and probably an LCD monitor ?

---

### Post by creativ3rst on 2007-06-05
WOh, woh woh..... Look my thread is getting highjacked here. ALbeit he has a similar problem, lets not take the spot light off me!  :o

---

### Post by creativ3rst on 2007-06-05
> **wpshooter said:**
> Am I correct in that you are probably using an ATI video card and probably an LCD monitor ?

I am using 

Nvidia 6600GT 

Belinea 19" TFT

---

### Post by 1mouseclick on 2007-06-05
> **creativ3rst said:**
> WOh, woh woh..... Look my thread is getting highjacked here. ALbeit he has a similar problem, lets not take the spot light off me!  :o

No, I have the same problem as you do. Just trying to resolution. ;)

---

### Post by creativ3rst on 2007-06-05
lol, i was kidding :p

I just downloaded the "aternative" installation cd... weill let u know how it goes.

Are you gonna try the different monitor technique...?

*Edit*

Wont be able to try it till tomorrow. My sister just went into labour!!!

---

### Post by dabl on 2007-06-05
Nvidia 6600 GT is a popular card, and Ubuntu has no trouble with it.  Is your monitor integrated with the system, or can you possibly borrow another monitor and use it to get the system installed?  It seems that the installer is setting the graphics card at a refresh rate that your monitor can't accept.  I don't know how to fix it if you can't see a screen to install the system. :(

However, congratulations on becoming an uncle!  ;)

---

### Post by wpshooter on 2007-06-05
> **creativ3rst said:**
> I am using 

Nvidia 6600GT 

Belinea 19" TFT

I had this problem on 2 of my machines that are using ATI video cards and 19" Samsung LCD.  I can tell you how I fixed it on those but I doubt that would do you any good if you are using Nvidia.

But good luck.

---

### Post by lptr on 2007-06-05
Very possible that it has been mentioned in another thread (did you try searching ?)

so just in short and to see as a hint that should take you some further. Try to get to the console then

```
> sudo dpkg-reconfigure xserver-xorg
```follow the dialogs default settings until you are faced with monitor stuff. 
Select medium and choose your monitor resolutions that do match. 
Very important!! Select 60 Hz otherwise you will be out of sync again.

Hope that helps 

rob*

---

### Post by Wherdgo on 2007-06-06
I second lptr's strategy.  Try booting off of the CD instead of the live install, then modify the x-windows configuration on the disk with "sudo dpkg-reconfigure xserver-xorg"  This worked for me with some other resolution issues.  Good luck!

---

### Post by creativ3rst on 2007-06-09
I have installed ubuntu using the alternative text based installation. But obviously still out of sync. Atleast it is installed now tho...

I booted in recovery mode to run the cmd u suggested and followed all the instructions. Rebooted. It started in a console and i loged in. Then it came up with an error saying the Xserver could not start, and if i wanted to view the report or something =S

The report said the following EE errors:

Unable to find a valid framebuffer device.

NV(0): Failed to open the framebuffer device, consult warnings and/or errors above for possible reasons
(You may have to look at the server logs to see the warning)

Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found.



Any suggestions?

---

### Post by creativ3rst on 2007-06-09
I just went throught the detailed report thing, and spotted some warnings i thought might be useful. These are identified as (WW)

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path.

(WW) NV(0): Bad V_BIOS checksum

(WW) open /dev/fb0: No such file or directory
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory

(EE) Unable to find a valid framebuffer device.

(EE) NV(0): Failed to open the framebuffer device, consult warnings and/or errors above for possible reasons
(You may have to look at the server logs to see the warning)

(EE) Screen(s) found, but none have a usable configuration.

(EE) Fatal server error: no screens found.

---

### Post by creativ3rst on 2007-06-09
-------------------- Problem Solved -------------------------------

After playing around with my xorg.config manually trying the correct feq trying to comprehend why it wasnt working, it thought... "what about the nvidia drivers"

so i did this:

   1. Open a terminal and type sudo apt-get update
   2. Type sudo apt-get install nvidia-glx
   3. Type sudo apt-get upgrade
   4. Type sudo dpkg-reconfigure xserver-xorg
          * Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration
   5. Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working
   6. You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes)
   7. You can also type glxgears to watch your card at work

every cmd ran smoothly, and i started xserver working great! I feel pretty stupid as it doesnt seem like a hard fix, and the people helping my must be thinking (oh yeah, obviously)

Anyways, hope this helps anyone else, and thanks for your help!

---

### Post by bdlio on 2007-07-01
Hi & sorry for hijacking your thread... 

I also have "out of frequency" problems with the 7.04 live CD (had those with 6.10 as well).
I have a gf6600gt and a 21'' crt monitor connected to it - Ubuntu apparently tries to run the desktop at 180Hz (!) for some reason (at least that's what my Monitor's OSD tells me) - the same thing happens with a lcd monitor attached to my gf6600gt's DVI Port (no out of frequency error here but just garbled images so I guess something is wrong with the refresh rate settings here as well).

After having read some other posts where people seemingly fried their monitors that way I guess I can consider myself lucky that mine still work... but it certainly is a bit of a show stopper when you want to try Ubuntu for the first time and it is not even able to pick a proper screen resolution and refresh rate.
I also tried it with Kubuntu, Knoppix (even though the problem was different here - had no mouse cursor even with hardware acceleration turned off) and Linux Mint for that matter with the same results.

the safe mode in the 7.04 works however so that is something after all and I might have some luck with Ubuntu after all...

---

### Post by 1mouseclick on 2007-07-02
Wow 180Hz is the base start up? That seems really odd. I tried loading it again on a new computer I built with same "out of frequency" result. I am going to try and down load v6 and see if that is any better.

> **bdlio said:**
> Hi & sorry for hijacking your thread... 

I also have "out of frequency" problems with the 7.04 live CD (had those with 6.10 as well).
I have a gf6600gt and a 21'' crt monitor connected to it - Ubuntu apparently tries to run the desktop at 180Hz (!) for some reason (at least that's what my Monitor's OSD tells me) - the same thing happens with a lcd monitor attached to my gf6600gt's DVI Port (no out of frequency error here but just garbled images so I guess something is wrong with the refresh rate settings here as well).

After having read some other posts where people seemingly fried their monitors that way I guess I can consider myself lucky that mine still work... but it certainly is a bit of a show stopper when you want to try Ubuntu for the first time and it is not even able to pick a proper screen resolution and refresh rate.
I also tried it with Kubuntu, Knoppix (even though the problem was different here - had no mouse cursor even with hardware acceleration turned off) and Linux Mint for that matter with the same results.

the safe mode in the 7.04 works however so that is something after all and I might have some luck with Ubuntu after all...

---

