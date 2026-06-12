---
title: "Gutsy resolution problem"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2007-10-18
Hi,
I successfully installed Ubuntu 7.10 (fresh install). I have a resolution problem. Ubuntu is only recognizing 800x600 and 640x480 in system>preferences>screen resolution.

Before fresh install I was using Ubuntu 7.04 and before this Ubuntu 6.10. Both of them automatically recognized 1024x768 screen resolution. What is wrong with Ubuntu 7.10? How to fix screen resolution on my notebook?
Thanks,
Abcuser

---

### Post by louieb on 2007-10-18
I guess they didn't think of everything. Gutsy has more screen resolution options. Run around the menus I think it even has a graphical xorg configuration tool somewhere.  or try the ole manual way. Heres how [http://louboldt.com/ilinuxmisc.htm#xorg](http://louboldt.com/ilinuxmisc.htm#xorg)

---

### Post by abcuser on 2007-10-18
Hi,
is there any other way. I don't like to play with xorg tool, because in previous version it lead me to corruped system and I need to reinstall.

In system>administration>screens and graphics >graphics card tab: there is recognized "vesa-generic-vesa-compliant video card" on Screen tab there is Screen 1: Model: LCD Panel 1024x768 and Resolution is only 800x600 and 640x480 from drop down list.

Is there any simple method to tell Ubuntu I would like to use 1024x768 resolution?

Thanks,
Abcuser

---

### Post by digital_exhaust on 2007-10-18
Fire up a terminal and try this...

```
sudo dpkg-reconfigure xserver-xorg -p high
```

Use the spacebar to select the resolution you want... Hope it helps...

---

### Post by abcuser on 2007-10-18
Hi,
xorg window opened up. The default was vesa. I seleced Intel and then 1024x768. Reboot and got the error that graphics can't be set and default are set again.

I know my graphic card is "Intel 945 GM" and max resolution is 1024x768 LCD monitor. I use IBM notebook Thinkpad T60.

Any idea what to do?
Thanks,
Abcuser

---

### Post by jsladek on 2007-10-18
I have the same problem with a Samsung 515V and nVidia GeForce4 card.  The same " defaults" came up with no option for 1024x768.  I went to the GUI and changed it to the video card and monitor that is installed, but the settings won't stick. 

So, for the moment, I gave up on 7.10 and restored back to 7.04 and see if the smoke settles on this problem.

Jim

---

### Post by abcuser on 2007-10-19
Can we say this is a bug in Gutsy?

Is there any work around to solve resolution problem?

---

### Post by PrinceArithon on 2007-10-19
I'm almost thinking it is.  I know I'm having the same exact problem as you, and we aren't the only ones not getting this fixed.  I just wish something could be done...this resolution is killing my eyes...

Aaron

---

### Post by abcuser on 2007-10-19
Hi,
I have SOLVED THE PROBLEM!

I started the terminal and lunch xorg tool (backup your system first if needed!):
```
sudo dpkg-reconfigure xserver-xorg
```

Then gone through selections (choose defaults in most cases - if I didn't know what to choose let default) and then on resolution page I selected 1024x768, 800x600 and 640x480 (use spacebar to select resolutions). All other settings left default.

Then reboot Linux and my resolution is 1024x768.

Now the settings are:
In system>preferences>screen resolution: Resolution 1024x768, Refresh rate: 60 Hz, Rotation: Normal (greyed out), Options: Make default... is not checked.
In system>administration>screens and graphics>Screen tab: Screen 1: Model: Custom 1, Resolution: 1024x768 at 60 Hz, Default option box enabled

Hope this helps to anyone out there... it just took me xxx hours to make work. ;)
Abcuser

---

### Post by jinhr on 2007-10-19
Thank you abcuser for having the solution. I will try on my 19" inch samsung (1280x1024).

Anyway, we still should report resolution problem as a bug.

---

### Post by jsladek on 2007-10-19
Thanks abcuser for the note.  The cli worked - nv worked for nvidia while nvidia didn't seem to work i my case.  Looks like the "Screens and Graphics" tool is pretty useless.  Didn't do a thing for making changes .. it only read the changes after they were made in the xserver.

Jim

---

### Post by Drakkor on 2007-10-20
Yeah, I definitely think this is a  bug. Had the same problem as OP, and edited xorg.conf to
say "nv" ,instead of "nvidia", and then I was able to set the screen resolution right,but then
when activating the nvidia "restricted drivers" , it went right back to 640X480 :(

---

### Post by abcuser on 2007-10-20
@Drakkor: IBM would say: It is not a bug it is just not supported. ;)
@jsladek: it looks like this Screen and Graphic tool is not ready yet. But it is nice that Ubuntu comunity is thinking this tool is needed, because it will improve over time.

It is also interesting that in system>administration>screens and graphics there is no Custom1 to select from menus, which is now my settings after playing around with xorg.

---

### Post by Drakkor on 2007-10-20
Actually, I have 2 Gustys, each on a different hard drive. One is a Fiesty to Gutsy upgrade,which  I'm on now, and the graphics and resolution are fine, with the Nvidia restricted driver enabled, and Compizfusion working. And the "fresh install" Gutsy which
was downloaded this morning,and that has a boatload of problems,at least for me !
First , the install hung for a while,in a couple of places , then spent 4 hours just trying to get the resolution and
restricted driver fixed, no luck with either. I even downloaded and tried the alternate text install disk.
I've installed Dapper/Edgy/Fiesty and never had these kinds of problem with a fresh install. Here's my upgraded Gutsy

---

### Post by aam-aadmi on 2007-10-21
Hi Abcuser,

I was facing the same problems that you had faced; so I used the method that you had outlined. It worked. But then I re-started the machine and I was back at the old resolution! What do I need to make the new resolution permanent?

My current resolution: 640X480
Graphics card: NVIDIA GeForce FX (generic)
Driver: nvidia

I want my default resolution to be: 1024X768.


Thanks.

Aam-aadmi

---

### Post by Tahi_Kiwi on 2007-10-21
Misery loves company.

I've been able to change my resolution. It appears to be stuck at 1280 x 800, even though my wide display goes higher than that.

No matter what I do in System > Preferences > Screen Resolution, the resolution stays fixed. Clicking the Apply button does nothing. This was not a problem with 604 or earlier releases of Ubuntu.

I tried the command line suggestion, but I guess I need to reboot, which I will do momentarily.

---

### Post by Motyoj on 2007-10-21
I did the sudo dpkg-reconfigure xserver-xorg command and it fixed my problem without doing anything but reboot. It backed up the faulty file and after things work fine, I tossed it. Seems like this problem is affecting a lot of users.

---

### Post by Genotrius on 2007-10-21
I just finally got GNOME to work for the first time since I upgraded (it somehow set my session default to "none" or something), but my resolution's off, too. It's suppose to be at 1280x800 (I had to set this in xorg.conf, and it's still set that way there), but it's at 1024x768. I tried to check the System > Administration > Screens and Graphics thing, but for some reason, that dialog won't even come up.

---

### Post by tripplep on 2007-10-21
Same problem for me.  I use a Geforce4 ti4200 card and fixed the resolution problem
for my system. Possible solution in the thread below, give it a try.

[http://ubuntuforums.org/showthread.php?t=584187&highlight=geforce4](http://ubuntuforums.org/showthread.php?t=584187&highlight=geforce4)

---

### Post by Genotrius on 2007-10-21
Any ideas how to fix the on non-Nvidia-using systems? Besides having xorg redetect everything?

---

### Post by Genotrius on 2007-10-21
WOW.
I just tried to reconfigure xorg, despite how much I dread screwing something up by doing so, and it says that it's "broken or not fully installed." Explains a lot, you know? I'll see if I can reinstall it in Synaptic to gt it fixed; you all might want to try, too.

---

### Post by Brian Dempster on 2007-10-21
I found that if I selected System-Preferences-Appearance and change from the standard that the system would see that it needed a new video driver. It then added the new driver and requested a restart. All is now great!:KS

---

### Post by Brian Dempster on 2007-10-21
The forward button could not be seen during install and resolution could not be reset, the window would not resize and I could not move the window up enough to see the buttons.
My 13 year old son found the fix to this by setting all of the fonts to 6. System-Preferences-Appearance-Font.

After making this font size change I could then see the bottom of the page and could complete the install. All is working great!:KS

---

### Post by Genotrius on 2007-10-22
Well, what do you know? Reconfiguring xorg fixed it, once I fixed dpkg and xorg with dpkg --configure -a, and now everything's just dandy again! And I've got all these neat desktop effects. 

I think I'll wait a while before upgrading my other system, until it's all a tad bit more streamlined.

---

### Post by diskotek on 2007-10-22
i have the same problem with with "ati radeon x200"

and this line
 > sudo dpkg-reconfigure xserver-xorg
doesn't worked for me. i can not configure xorg.conf!

i thinki2ll switch back to feisty, or dapper...

---

