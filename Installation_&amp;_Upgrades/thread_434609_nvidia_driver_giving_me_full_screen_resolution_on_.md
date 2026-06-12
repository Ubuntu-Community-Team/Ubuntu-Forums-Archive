---
title: "nvidia driver giving me full screen resolution on wide screen monitor"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Levander on 2007-05-06
Having just upgraded to Feisty from Edgy, where hardware acceleration used to work, now when I start X I get a full screen resolution of 1600x1200 instead of this monitor's native resolution of 1680x1050.  This full screen resolution is so bad because the screen actually extends about 10% off the side of the monitor, and down below the bottom of it too.

The video card in this box is just an Asus EN7300 LE. 

Interestingly, the xorg.conf file was not modified in the upgrade to Feisty.  It was the exactly same configuration as Edgy had where hardware acceleration worked.  So, I'm pretty sure this problem I'm having is due to changes in the software of the driver itself, and not in the configuration.

To get rid of the full screen resolution I ran 'dpkg-reconfigure xserver-xorg' and it is working fine with the open source nv driver.  However, as soon as I go into the xorg.conf file and change the nv driver to the nvidia driver, when I restart X, I'm back to the full screen resolution.  I hit Ctrl-+ and Ctrl-- to try to change the resolution, nothing happens.

I ran "aptitude remove --purge nvidia-glx" and installed nvidia-glx-new because I found somewhere that the new driver does support my graphics card.  After reboot, X starts again, and I'm back in the full screen resolution that I don't want.

Is there somewhere you can tell the nvidia driver to use widescreen and not fullscreen?  I'm just not sure what else to check at this point.

---

### Post by HowardDrake on 2007-05-06
It was doing the same for me and I wanted to be sure I had my resolution working before I installed Beryl.

What I did was:

[LIST=1]
[*]Fired up a terminal
[*]Typed 'sudo dpkg-reconfigure xserver-xorg'
[*]Used the nv driver
[*]Went through all the options, changing nothing until resolutions
[*]Enabled the desired resolutions
[*]Went to the end, and let it rewrite my xorg.xconf
[*]Did a Ctrl-Backspace to restart the X server
[*]Confirmed the correct resolution
[*]Went into Restricted Drivers Manager
[*]Enabled the NVIDIA driver
[*]Let it install, and then rebooted the system
[/LIST]

That worked for me, let me know if it works for you too. This might be something worthy of fixing for the next release, if its really something wrong.

---

### Post by Levander on 2007-05-07
You know, I bet that would have worked.  I actually followed the instructions you had above.  But, I did not restart my system after the System -> Preferences -> Restricted Drivers step...  I remember thinking, "why the hell would I have to restart the whole system? I'll just restart X."  I eventually did get it working by running gnome-display-properties (which is what "Screen Resolution" runs from the Gnome menus) from the command line and just changing the resolution in there.  

The only thing that is weird now is that gnome-display-properties reports my refresh rate as 57 Hz, not the LCD's native resolution of 60 Hz.  xvidtune does report the vertical sync as 59.95 Hz.  So, maybe there's just some math throwing xvidtune off a little?

I just tried reproducing your instructions and now it does not work.  This is due to my experimentation in trying to get this thing to work, I de-installed nvidia-glx and installed nvidia-glx-new.  Now, when I enable the nvidia driver via Restricted Drivers Manager, it removes the nvidia-glx-new package and installs the nvidia-glx package.  However, upon reboot, when X starts up, I get an error about the kernel having the newer nvidia driver version, and the nvidia driver itself having the older nvidia driver version.  I forget the exact message, but it's something like this.

Reading the documentation (especially trying to do this on Edgy) the doc's are so verbose on how to enable the nvidia driver, when there are really just a few simple steps.  Despite how much I've read, I still do not know what all the modules are that you need to run the nvidia driver.  I know you need one of the three nvidia-glx packages.  But, aren't there like a restricted modules and a specific kernel package you need also?  I'm assuming having the wrong kernel package installed when I tried to install various versions of the nvidia driver caused my version mismatch errors when I started X.  I'm thinking these people who write the Ubuntu documentation think information like restricted modules and kernel packages are just to technical for the average Ubuntu user to understand?  I know there are a *lot* of people new to Linux trying Ubuntu.  I personally would like to see documentation written at a higher level, and just let these newbies learn by learning to read more in depth technical articles.

Anyway, X is starting up with the correct resolution.  I would like to hear it if anyone can explain to me why gnome-display-properties is reporting my refresh rate as 57 Hz when xvidtune is reporting it as 59.95 Hz.  And, if someone can explain to me how these restricted and kernel packages that you need for the nvidia driver work. I would appreciate that also.  

Or, just point me towards less verbose doc's than what I've seen on the nvidia driver so far.  It just seems they spend so much time and basic prerequistes and basic procedures, they never really get around to explaining what the kernel is doing with this stuff.  They just barely touch the more in-depth issues I'd like to see.

---

