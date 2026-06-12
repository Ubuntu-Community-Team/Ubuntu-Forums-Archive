---
title: "Can I ask Linux to boot live CD with specific video settings?"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by Idlewild1888 on 2014-11-14
This is a bit of a specific one for getting my installation running from a Live CD, so please bear with me.

I have tried various different Linux distros on an old screen with integrated barebones machine that used to run XP embedded, but have failed when trying to launch a live session or installer. It seems that the weird video set up on the machine just won't allow any form of desktop environment to load? I' m a little out of my depth with this and have been poking around int he dark, literally at some points!

On the Ubuntu Live CD I have tried launching sessions with nomodeset in the Kernel options and that got one one stage further, I managed to get the purple Ubuntu splash screen, but then as it tired to load lightdm for the login (I presume) the screen just went blank and wouldn't go any further, although I could launch a terminal session.

So my guess is that I need to pass some sort of video settings to Ubuntu at some point during this process, so that it knows how to display the desktop environment?

As I said, it's an old machine and a bit of a niche set up I think, so finding out exactly what settings I need has been difficult.

But I managed to track down some info from an online manual and for example, I can tell you that:


[LIST]
[*]The screen is driven from the machine by an ATI graphics card and the xorg driver required to display Linux should be radeon.
[*]I know that the max resolution the screen can support is 1360 x 768
[*]I know the display colour is 16.7 M
[*]I know the Horitzontal Frequency range is 30 - 81 kHz and the Vertical is 56 - 85 Hz
[/LIST]

So I have all of this information and need a way to tell Linux how to use it really.

Normally I'd just leave it, but whilst playing with the video wizard (xorgwizard) in Browser Linux (based on Puppy) I did manage to get it to boot to a viable desktop - unfortunately the desktop resolution must have been set too high because all I could see was the top corner of the desktop and wallpaper with the mouse in the middle of the screen. Even more unfortunate was the fact I rebooted and tried to launch the same wizard settings with a lower resolution and then was not able to remember or replicate the steps to success again! :mad:

Here is a look at my X test results:

[IMG]http://i.imgur.com/gootyosl.jpg[/IMG]

 My point is then that I do believe it is possible for this to work and that the machine, some way or another, is capable of booting to a live version and displaying a desktop...I just need to figure out how!

I've pretty much given up on the project, which is a shame as I feel so close to getting it working. However, if anyone takes the time to read the very specific scenario I find myself in and offer some words of advice, I'd really appreciate it.

---

### Post by grahammechanical on 2014-11-14
We can do more with the live session than just adding nomodeset to the boot parameters. See this wiki page and the section, Changing the CD boot options configuration line. Also keep in mind that you my need a combination of the F6 options including noapic. We can add more than one F6 option to the boot parameters. 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you do get to a live session and install from there then my advice would be to not tick the box Install Third Party Software. That will bring in a proprietary video driver and it may well be that the manufacturer has dropped support for that video card from its driver. Manufacturers have a habit of dropping support for what they consider obsolete hardware.

Regards.

---

### Post by Idlewild1888 on 2014-11-14
I didn't realise I could add more than one boot option to the boot parameters on the edit line!

So I could perhaps tell it to boot with -- nomodeset noacpi vga=XXX

Do you think it is possible that this might kick it into the desktop environment? The frustrating thing is I know the machine can handle displaying the desktop environment, it is just very particular in the settings it will take on board to allow me to do this and I'm determined to find out what they are!
 
Don't suppose you have any idea how to create a VGA number from the specs of my screen? This may sound silly, but if I have a screen with the max resolution of 1360x768, for example, could I set a VGA number based on a lower resoltuion of say, 800 x 600?

Thank again for the help.

---

### Post by mörgæs on 2014-11-14
vga=791 is always a good first try. More here:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

