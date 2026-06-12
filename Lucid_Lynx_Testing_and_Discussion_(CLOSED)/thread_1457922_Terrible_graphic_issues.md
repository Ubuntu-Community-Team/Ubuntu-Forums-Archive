---
title: "Terrible graphic issues"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by makitso on 2010-04-19
I installed Beta-1 on my Gateway Netbook Model: LT3103 with the ATI  Radeon X1270 chip.  Immediately, I switched the open/close buttons back to the right side with a Python script.  I then installed quite a few of my base applications, AWN, etc.  

I have upgraded to Beta-2 and have a current system as of last night.  My problem is that the graphics go nuts anytime I open Firefox, Chrome, of any number of other apps.  The top header bar goes scrambled eggs and I need to reboot.  

My question is:  I booted with the beta-1 liveCD yesterday and it does not exhibit any of these issues.  I have also booted with all the kernels in grub and non seems to be any better.  So, might the Python script to move the open/close to the right side have caused this instability?

Second question:  Would updating form B1 to B2 be a wise idea?  Perhaps I should reinstall the April 22 release that is due out this week?

:(

---

### Post by dino99 on 2010-04-19
seems to be related to memory: how much memory have you on the graphic card ? Special effects activated ?

---

### Post by makitso on 2010-04-19
Thanks for the reply.  I have no idea about the video memory, its a  netbook with an ATI chip.  I have tried deselecting display effects with no change.

---

### Post by dannyboy79 on 2010-04-19
so this doesn't happen on the beta1 live cd in which you DID not do anything with the open/close buttons correct? sounds to me like your python script did a little more than just move them from left to right. at least look into that.

---

### Post by makitso on 2010-04-19
So, I can reinstall.  But, then is the correct way to move the "buttons" from the left back to their old position on the right side of windows?

---

### Post by makitso on 2010-04-19
Actually, it was the script from OMG Ubuntu release April 19th.  That should be reliable right?

[http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html)

---

### Post by Kirk M on 2010-04-19
The newest version of *Ubuntu Tweak* includes an "left to right" and "right to left" option directly related to Lucid Lynx' placement of the buttons on the title bar.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) (the .deb download says it's for Karmic but it's compatible with Lucid)

I've used it to switch the buttons from the new left position to the right without a problem. This is on an old desktop PC with a dedicated Nvidia based video card though. Even so, I'd give it a try rather than the script since you can easily change the position back to the left if you run into problems.

---

### Post by mcduck on 2010-04-19
> **makitso said:**
> Actually, it was the script from OMG Ubuntu release April 19th.  That should be reliable right?

[http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html)

You don't need any script (or any other extra application, like Ubuntu Tweak) to do that.

Just hit Alt-F2, run "gconf-editor" and use that to browse to apps/metacity/general. Then change the "button_layout" as you like it (the old setup would be menu:minimize,maximize,close", but there's a helpful text at the bottom of the screen that tells you what to do).

Or if you prefer scripts and commands, then just run this in a terminal:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```
To change it back all you need to do is select the theme again in Theme settings, or run this command (or use gconf-editor again):
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "close,minimize,maximize:"
```

edit:
As the developers have done some amazing stuff with the Ambiance/Radiance themes, you can even go for some stranger layouts without the theme breaking. For example to get the *original* Windows layout you could use this:
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "close:minimize,maximize"
```
(well, "menu:minimize,maximize" would be appropriate as well, as the button in the left was a combined menu/close button and you had to double-click it to close a window...)

---

### Post by dino99 on 2010-04-19
can simply do it with gconf into console

mcduck goes faster than me  :)

---

### Post by Tricast on 2010-04-22
> **makitso said:**
> I installed Beta-1 on my Gateway Netbook Model: LT3103 with the ATI  Radeon X1270 chip.  Immediately, I switched the open/close buttons back to the right side with a Python script.  I then installed quite a few of my base applications, AWN, etc.  

I have upgraded to Beta-2 and have a current system as of last night.  My problem is that the graphics go nuts anytime I open Firefox, Chrome, of any number of other apps.  The top header bar goes scrambled eggs and I need to reboot.  

My question is:  I booted with the beta-1 liveCD yesterday and it does not exhibit any of these issues.  I have also booted with all the kernels in grub and non seems to be any better.  So, might the Python script to move the open/close to the right side have caused this instability?

Second question:  Would updating form B1 to B2 be a wise idea?  Perhaps I should reinstall the April 22 release that is due out this week?

:(


Hey, i have the same problem on my 11,6 inch Packard Bell Dot 711 with x1270 gpu. Booted the 10.04 RC from usb and didn't change any settings before clicking the firefox icon. Screen went nuts when going to webpage other than default homepage(google). Problem with flash?

9.10 worked well.

---

### Post by KlavKalashj on 2010-04-22
You both have the same graphics chip... tried other drivers? Fglrx, open soure...

---

### Post by makitso on 2010-04-22
Ok, forgive for being dumb.  

I have an ATI Radeon RS690M Xpress 1200 Series Graphics IPG.  I am up  and running on the 10.04 RC downloaded today.  The only way the system is usable is to run with NONE for Visual Effects.  However, when the screen saver pop in its screen garbage again.  SO,
how do I use Fglrx or the open source version?  

Quote: You both have the same graphics chip... tried other drivers? Fglrx, open  soure...

---

### Post by Tricast on 2010-04-22
I switched to Chromium browser, disabled visual effects and inserted GRUB_CMDLINE_LINUX="radeon.modeset=0" to the /etc/default/grub file. Now everything i use works so far except Firefox. Can live without that i guess.

---

### Post by makitso on 2010-04-22
Well, my stock system did not have the fglrx drivers installed.  So, I installed them and could not set anything other than None for vusual effects.  Then I resinstalled the open source items and again could not get anything other than None.  Whatever

---

### Post by Tricast on 2010-04-23
Adding pic of garbage screen when trying to open FF and happens occasionally with other apps too. Using the open source driver. The proprietary driver does not support my card.

---

### Post by Yellow Pasque on 2010-04-23
Try the open-source radeonhd driver (it supports X1k chips): [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Even if you don't want to do that, make sure you purge all of the proprietary crap off your system: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Tricast on 2010-04-24
This is my experiences with ati drivers and x1270. On my small notebook i use the web, play games on zsnes emulator and watch movies.


Ubuntu 9.10 radeon:

Stable.
720p Slow. Unwatchable.
Emulator smooth and good speed.


Ubuntu 10.4 radeon:

Unstable(scrambled screen).
720p ok speed, watchable.
Emulator choppy but playable.


Ubuntu 10.4 radeonHD:

Stable.
720p slow. Unwatchable.
Emulator extremely choppy, even in menus. Unplayable.

---

