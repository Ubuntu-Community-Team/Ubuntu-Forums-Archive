---
title: "Serious Installation Issues with 8.04"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Stargazer712 on 2008-05-16
Ok...This has been one long headache, and I would appreciate it if anyone has any advice.

First, I had Ubuntu 7.10 running and working fine.

Then I used the automatic Updater to upgrade to 8.04. Half way through the installation section of the upgrade, the installer stopped responding. The progress bar showed "4 minutes left" and stayed that way for nearly an hour, with absolutely no change in the screen. I could not find any way to revert the changes, nor anyway to stop the upgrade--It had just frozen. With no other options, I restarted the computer.

When I tried to reboot normally, it brought up a blank tan colored screen with a working mouse and froze. This happened every time that I rebooted. My GRUB menu still listed the version of Ubuntu as 7.10.

So, I hopped onto a different computer, downloaded the 8.04 iso image, burned it, and tried to run 8.04 live on my computer.

When trying to run 8.04 off of the CD, I select the "Run without changing my computer". The ubuntu logo shows up with the progress bar, the progress bar goes to the end, and then my screen goes blank. Same thing happens when I choose the "Install Ubuntu" option. I have checked the integrity of the 8.04 CD several times. It is fine.

The final thing that I have tried to do is to run Ubuntu in the 'safe' mode from the GRUB menu. From here, I have selected both the 'repair X windows' option, and 'repair dpkg' option. After having done this, the GRUB menu now shows Ubuntu version 8.04, but nothing else has changed.

I am at my wits end. I have no idea what to do. Anyone have any advice/suggestions?

---

### Post by nspur on 2008-05-16
You can do what I have done. I had a perfectly working 7.10 with programming tools and support for network, mobile broadband etc. etc. Upgrading (?!) produced a non-booting 8.04. Downloaded the distro separately (4 hours) and used Wubi to install. No network, more problems.

I can't be doing with the aggro, I've lots of demands on my time and the hassle of getting something to run which doesn't out of the box is not a priority. I was porting some applications written in Delphi to Ubuntu via the Lazarus project but I won't bother now.

So I've uninstalled Ubuntu and I'll maybe go back to it when it does work out of the box.

---

