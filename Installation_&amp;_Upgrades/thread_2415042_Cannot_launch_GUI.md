---
title: "Cannot launch GUI"
date: 2019-03-19
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2019-03-19
18.04.2 desktop off a CD on hp ML110 from 2003 with video on motherboard AMD/ATI Rage 3 (Rage XL).
First install on this hardware was Redhat 9 which reported xrandr as 800x600.

Lubuntu system was running fine with display at 1024x768.
Then problems, with things happening that made me suspicious of hardware.
Much testing, multiple installs and general operation cannot fault operation on the tty, but no GUI.

Current install is: acpi=off, noapic, nolapic, edd=on, nodmraid, nomodeset, remove 'quiet splash', add after '--' vga=792.

startx fails with error (1).
inxi -G reports the driver as ati (unload: modesetting).
Log file points to the configuration used per directory xorg.conf.d.
The directory lists amdgpu, quirks and radeon.

There is no configuration file in /etc/....

Is the discrepancy between 'ati' and 'amdgpu, radeon' the cause of the problem ?

xrandr fails with 'can't open display'.

Previous advice on getting this system running initially was to use the radeon driver.
But it seemed to come up then with nouveau (that I muddled into), so I never tried to force radeon.
How do I force the use of radeon ?

Any other suggestions.
John.

---

### Post by mastablasta on 2019-03-20
nouveau would only load if you have an nvidia chip enabled. what does BIOS show you?

radeon is the only one that will work with that old chip. even that one will use CPU for any GPU acceleration.

it could also be a hardware issue. difficult to say.

[https://www.x.org/wiki/radeon/](https://www.x.org/wiki/radeon/)
[https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

what is the chip in the rage actually ?

---

### Post by electrosteam on 2019-03-21
The motherboard chip is Rage XL, 215R3LASB41.

Re-installed Redhat 9 and got graphics at 800x600, tending to remove the hardware fault possibility.

The only high-performance I need is youtube clips.

Back to Lubuntu 18.04.2, with a new twist.
Did an install off the CD, but a re-boot brings up Redhat !

Also discovered that the driver listed as 'ati' may be a wrapper that includes the radeon driver, so the discrepancy in the OP may be normal.
My plan is to resolve the Redhat, then write a configuration file.

The back-up plan has started, the acquisition of a PCI video driver card.

John.

---

### Post by electrosteam on 2019-04-03
The Redhat 9 problem was me running Lubuntu tty off the DVD/memory.

Used Redhat 9 to determine: 1280x1024@60 is possible and looks good, xrandr reports incorrectly as 800x600, the driver in use was mach64.
It may be the hardware failure mentioned in the OP is that part of the driver/monitor that does the EDID exchange.

Prior to the Lubuntu GUI demise, and suspected hardware fault, xrandr did report 1024x 780.

Managed to get a Lubuntu install on the serial 500 GB drive, but cannot reboot to GUI.
Started experimenting again and found the log files included a list of chips that the radeon driver supports, the Rage XL is not included.

It appears the Lubuntu install does not include mach64.

Plan B failed at the start, wrong bus, it was a PCIExpress and I have fast PCI.

Can anyone advise on where I could find a 32 bit mach64 driver suitable for Lubuntu ?

John

---

### Post by mastablasta on 2019-04-04
looks like it is in the repos:[https://launchpad.net/ubuntu/bionic/amd64/xserver-xorg-video-mach64](https://launchpad.net/ubuntu/bionic/amd64/xserver-xorg-video-mach64)


However it may or may not need some tricks to load it (this is for Arch): [https://wiki.archlinux.org/index.php/mach64](https://wiki.archlinux.org/index.php/mach64)

and here Debian documentation: [https://wiki.debian.org/AtiHowTo](https://wiki.debian.org/AtiHowTo)

looks like just installing the package might resolve the issues in Lubuntu. still don't expect much performance wise. I remember i have an older Rage (32mb) and while display and all was fine most other stuff was not even in 10.10 (when i started dabling in linux). it would make it a good server chip. I replaced it with old Radeon 9600XT.

anyway,  if you are cash strapped and would like to use the old hardware then it would be most elegant to look for second hand card. if you have a bit more, second hand PCs are quite cheap these days. a descent 5 or 6 years old "Gaming" PC can be obtained for about 100 EUR.  it is probably even cheaper without monitor.

edit: descent core2duos go for about 20-30 EUR here (if you don't need a "gaming" rig, this might be a cheap solution at least for spare parts if nothing else).

---

### Post by electrosteam on 2019-04-05
mastablasta,
Thanks for the heads up on where to look.

The link you provided was for the 64 bit version, but a little digging soon found the 32 bit version.
There are some noted actions to get operation for the Rage chip, and I will work through those and report back.

My Google searching produced a driver at [https://packages.ubuntu.com/bionic/x11/xserver-xorg-video-mach64](https://packages.ubuntu.com/bionic/x11/xserver-xorg-video-mach64) which may be the same one.

My task is to sort through all this information.

On the card front, another has been sourced.
John

---

### Post by electrosteam on 2019-04-08
Searched launchpad and found a number of mach64 packages, tried several, including a 18.04 ati wrapper.
No immediate success with any.

Went back to xorg.conf and generated a new one using all the data accumulated to date.
I used command "cvt 1280 1024 60" to make the modelines and "1280x1024" in the display Section.

Now I get to a login graphics screen, a few seconds of blinking cursor, no mouse at all, then frozen - power off to recover.

In Recovery Mode, the log shows no error, lots of warnings and information, loading of ati, vbe and Int10 drivers, then an enormous list of resolution trials with the assumed modelines entry rejected with "bad mode clock and interlace/doublescan".

Any suggestions on what to do next ?

John

---

### Post by electrosteam on 2019-04-16
Much searching and trials of various configurations/options.

Settled on doing a modeline generation with 1024x768-60, and generation of an xorg.config file with ranges for HorizSync and VertRefresh.
Then got an Xorg.0.log file that looked close to working - the only [EE] noted had to do with dri settings.

Lots of searching on dri, which led to attempts to upgrade of the system while in Recovery Mode.
Head scratching until I learned that networking is switched off as the default.
Networking switched on and apt-get update and upgrade initiated.
Quite a bit of downloading resulting in zero errors reported.

Reboot expecting to get a freeze repeat, but, ---- full graphics at 1024x768.
xrandr reports 1024x768-75.

Switched off overnight, and boots fine this morning.

I will now investigate if I can get the resolution up to 1280x1024, the monitor's rating.

I discovered on both Redhat 9 and Lubuntu 18.04.2 that xrandr does not report the actual capability of the monitor, only the current setting and smaller derivatives.

John

---

### Post by electrosteam on 2019-04-16
Is it possible to get the Title edited to include " ATI Rage 3 (XL), mach64" ?

John.

---

