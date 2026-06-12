---
title: "Installing Ubuntu"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2006-10-25
I've read the topics regarding X server, and have had no luck getting it to work for me.  I've already posted once in another topic, but I've made a few more discoveries and figured I'd update with a new topic specific to my machine instead of spamming the other topic.

I'm running a 256 MB NVidia GeForce FX 5500.  Upon trying to boot from the CD in normal mode X server crashes, and I get booted to a very skewed command line mode.  Upon trying to boot into safe graphics mode X server crashes and I get booted to a command line.  At this point I tried installing nvidia-glx and then reconfiguring X, at which point I selected the newly available, "NVIDIA" driver set.  Still no luck, so then I tried following the steps of walkthrough I found instructing me on how to enable the driver by editing xorg.

Still no luck even after that, so I decided to take out my NVidia card, install Ubuntu with my default Intel integrated card, and then install/configure the nvidia driver from there after I get it up and running.  Well in normal boot mode it looked like it was going to work, and when it got to "Starting GDM" where, on my wife's laptop, it booted with no issues, the screen blanks out like it lost signal, however I hear the startup sound like it's starting up normally.  No response or occurrances after that, so I rebooted into safe graphics mode, and when using safe graphics mode, X just crashes outright and boots me to a command line.  Note that this is on my generic on-board Intel video card with the NVidia card not even in the machine at the time.

Could someone please help me I really want to get Ubuntu running.

---

### Post by bigken on 2006-10-25
You could try this at the command promt sudo dpkg-reconfigure xserver-xorg and select vesa as your drive this will at least get you into ubuntu ;)

---

### Post by gerowen on 2006-10-25
> **bigken said:**
> You could try this at the command promt sudo dpkg-reconfigure xserver-xorg and select vesa as your drive this will at least get you into ubuntu ;)

Tried that first, cause' it's the default driver chosen, and it said something like VESA couldn't read from BIOS and that it detected some devices but none of them had a usable configuration.  I also tried installing the xserver-xorg-driver-via(suggested in the other topic) package and it said it was already installed and up to date, so needless to say that makes no difference.  I'll retry the VESA driver though just for the heck of it.

---

### Post by Elshadii on 2006-10-25
Just a note: "nv" will designate your X server to use the nvidia drivers that are stock kernel drivers.  They don't have OpenGL support but they may be what you need to get you into a graphical mode.

---

### Post by gerowen on 2006-10-25
I'll give that a shot, but I'm trying to figure out what the problem is because it also failed by my generic onboard card.  Here's some relevant system info just for the record:

2.2 Ghz Intel Celeron Processor
1 GB Dual Channel DDR1 SDRAM
Gateway EV700 CRT Monitor

---

### Post by Elshadii on 2006-10-25
> **marcusdean.adams said:**
> I'll give that a shot, but I'm trying to figure out what the problem is because it also failed by my generic onboard card.  Here's some relevant system info just for the record:

2.2 Ghz Intel Celeron Processor
1 GB Dual Channel DDR1 SDRAM
Gateway EV700 CRT Monitor

The xorg.conf req. the Horizontal and Vertical refresh rates to be explicitly defined for CRT monitors.  That could also be an issue for it failing on both video cards; esp if Ubuntu doesn't recognize your monitor.  That is if you aren't setting them, if you are setting thme then it's something different. :-k

---

### Post by gerowen on 2006-10-25
> **Elshadii said:**
> The xorg.conf req. the Horizontal and Vertical refresh rates to be explicitly defined for CRT monitors.  That could also be an issue for it failing on both video cards; esp if Ubuntu doesn't recognize your monitor.  That is if you aren't setting them, if you are setting thme then it's something different. :-k

I didn't explicitly define it, but I did look at them and they appeared to be within acceptable range.  My Windows drive runs at 60 Hz, my Fedora Core 5 hard drive runs at 85 Hz.  Could setting it to 85 Hz in there make it work?

---

### Post by Elshadii on 2006-10-25
Very sorry I misspoke.  I meant to say HorizSync and VertRefresh is what we are speaking about.  As an example my old xorg.conf file was this:

Identifier     "My Monitor"
   HorizSync       31.5 - 50.0
   VertRefresh     40.0 - 90.0
EndSection

you should refer to your monitor's hand book for the correct values.  Once you find the correct values you can restart your x server and see if it worked correctly.

---

### Post by gerowen on 2006-10-25
> **Elshadii said:**
> Very sorry I misspoke.  I meant to say HorizSync and VertRefresh is what we are speaking about.  As an example my old xorg.conf file was this:

Identifier     "My Monitor"
   HorizSync       31.5 - 50.0
   VertRefresh     40.0 - 90.0
EndSection

you should refer to your monitor's hand book for the correct values.  Once you find the correct values you can restart your x server and see if it worked correctly.

I will try that, I'll just mount my existing FC5 partition and see what the values are in that xorg.conf file, and set the ones in my Ubuntu xorg.conf to the same.  If this works and lets me boot, will I have to do it over again after I install Ubuntu, or will the current settings carry over?

---

### Post by gerowen on 2006-10-25
Doesn't work.  I have managed to get Ubuntu running on my laptop in VMWare, b/c on this proprietary piece of crap laptop performance is the least of my concerns.  If I try installing "any" distro on this laptop, it fails, Ubuntu's installer just crashed out with a kernel panic.  Anyway, on to the desktop, changing the Horizsync and Vertrefresh values to match those in my FC5 xorg.conf file didn't work, and I tried it with the default Intel onboard card and still the same results.  I'm even more pressed to install Ubuntu now because a bunch of the Fedora repos just went down and I didn't know until I'd uninstalled a bunch of software, including my nvidia driver, in preparation for updating the kernel, and then tried to update/re-install the software, only to find out that it's either down, or no longer supported since FC6 was just released, and I am "not" going to download 3.9 GB worth of CDs for an operating system unless it is proven to be impossible to put Ubuntu on my desktop.  Does anybody have any other suggestions?  I'm done, I can't think of anything else to try.

---

### Post by gerowen on 2006-10-25
Apparently the next one will be out supposedly at midnight tonight, maybe I'll just stay up and download that one and see if I have any better luck.  Any suggestions in the meantime would still be greatly appreciated, just in case I have the same issues with Edgy.

---

### Post by gerowen on 2006-10-26
Edgy made no difference.  The graphical loading screen came up, then it went all black around it except the loading bar, and when it finished loading I got the same scrambled blue screen telling me that X had crashed.  I really wanted to use Ubuntu because it's really easy to install and start using, but it looks like I'm going to have to shoot for another distro that will support my Gateway EV700 CRT monitor, b/c I'm 99% sure that's what the problem is given the fact that it says, "No Screens Configured" and crashed while using both video cards.

---

### Post by gerowen on 2006-10-26
I printed off a copy of my working xorg.conf file from FC5, and copied the contents of the "Screen", "Device", and "Monitor" sections exactly, word for word, and while everything else picks up fine, I still get the error, "No Screens Detected" when I just put the screen section there myself.  I saw a report on bugzilla about Ubuntu not working on these monitors.  Figures that's my luck, the one monitor that brings out a bug in Linux distro voted number 1 desktop linux distribution, and it's got to be my model.

---

### Post by gerowen on 2006-10-26
ZOMG WOOOOOOOOOOOOOOOOOT!!!

FINALLY, I got it working, turns out the problem all along was that it was not properly detecting the PCI bus of my NVidia card, and it was trying to use the on board card, that's why it said, "No screens found", because there weren't any connected to that card.  Still kind of leaves me wondering about why it wouldn't work on the on-board card, but I DON'T CARE IT'S WORKING!!!  I just kept leaving the PCI area at default when running dpkg-reconfigure xserver.xorg and it hit me, maybe I should boot Windows and make sure this is right, and sure enough it wasn't, I wrote down the PCI bus address info, put it in to the xorg configuration and it took right off.

/dance
/cheer
WOOT!

---

