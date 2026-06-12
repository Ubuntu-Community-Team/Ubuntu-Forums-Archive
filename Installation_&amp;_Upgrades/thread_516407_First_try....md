---
title: "First try..."
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by CD Baric on 2007-08-03
I am posting this message in the hopes that Ubuntu may be improved as a result of my experience.

Just to clear the air I have been a Linux user and deployer since 1995 and a Linux desktop user since 2001. I have lived Windows free at home for 6 years.

I just completed a Ubunto 7.04 download and burned it to a CD-R using my Slackware 12 desktop.

I loaded it into a Toshiba Tecra 8000 laptop with the thought to install it in place of Windows 98se.

20 seconds - I chose Run/Install at the menu.

The next thing that happens is I get the Ubunto logo and the Cyclon Eye of Death thing happening for over 5 minutes - this is not an exageration.

I had no idea if the machine had hung or was thinking or whatever - I seriously recommend you loose the eye and put some sort of status bar or something.

After 8 minutes I finally got a graphical screen but it had a 1" black border on the right hand side and a 1/4" black border on the bottom - the screen is locked at 640x480 and of course looks like crap.

After 11 minutes Ubuntu 7.04 was running at 640x480 and would refuse to allow me to change the resolution or update the xorg.conf file.

It was time to end this experiment because the laptop was running dangerously HOT because Ubunto wasn't running the fan. Would you guys be liable if somebody toasted their laptop trying your Live CD?

Well, that was that my friends - the beginning and the end of Ubunto 7.04 for me.

Just so we know that the Tecra runs Linux, I dropped in a Slax 6.0 rc3 Live CD into the drive and hit the power button:

(1) Am presented with a menu in under 20 seconds - I quickly select KDE desktop.

(2) 120 seconds later I have KDE with the right screen resolution (1024x768), sound, irda, battery condition, and mouse stick controller all work. Behind the scenes the parallel port is enabled, the serial port is enabled, the pcmcia slot is enabled, my one USB port is enabled and even the ps/2 connector was found and enabled. My last task was to install ndiswrapper and my WiFi card binaries (from a USB stick memory) and BINGO, I was online.

As a matter of fact the only thing not detected and installed was a driver for the WinModem.

Here is an interesting datum - Slax LiveCD 6.0 rc3 is only 200MBs and yet it found everything quickly (except the winmodem) and was up and running in under 3 minutes whereas Ubunto 7.04 was still giving me the Cylon Eye of Death after 5 minutes!

If I sound acrimonious it is because I feel let down!

I cannot in good concience recommend Ubuntu because I know it isn't ready yet.

I am now going to install Slackware 12 on the Tecra 8000. I know it won't burn out my CPU because at least it turns on the fan periodically.

I have taken some time to record and report these deficiencies so please pay attention. And PLEASE no debates - I am not here to get into a pissing contest.

Best regards and bye for now,

CD 'Bar' Baric

---

### Post by HeavyAl on 2007-08-03
According to the information I found the Tecra 8000 is a pretty old machine in terms of laptop technology. It's standard loadout includes a P2 266Mhz processor 64MB of RAM, an internal 24x CD-ROM drive, an internal 6GB hard drive, a built-in modem, a 13.3-inch display, and originally came with Windows 95.

If that is anything like what you are trying to run the live cd on I would suggest you give it another shot with the alternate cd installer. It works without booting you into a graphical environment. The graphical environment for the live cd is X11+Gnome which in and of itself is pretty hefty memory wise and not recommended for use on anything with less than 256 megs of ram.

With a machine of this age I would personally use the alternate install cd and once the system was up install XFCE or something similarly light weight as a desktop environment.

Good hunting to you.

---

### Post by Pumalite on 2007-08-03
Xubuntu Alternate CD. actually if he wants to have anything that 'moves' in that machine.

---

### Post by KIAaze on 2007-08-05
> **CD Baric said:**
> 
120 seconds later I have KDE with the right screen resolution (1024x768)

He managed to get KDE running on his PC with a 1024x768 resolution...
If that runs, shouldn't Gnome be able to run too?

And I agree with him on the loading screen problem.
Console text scrolling by or progressing loading bars are fine.
But loading bars like the one of XP for example, which don't show any progress but only keep moving are horrible!

---

