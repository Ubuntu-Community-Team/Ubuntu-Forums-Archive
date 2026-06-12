---
title: "Feisty Fawn Freeze Issue"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by AdHavoc on 2007-05-03
I successfully installed Ubuntu 7.04 Feisty Fawn via the text based alternate .iso CD.  Now, however, when I boot into the OS, Ubuntu freezes after about (roughly) 10 seconds.  I am able to use the mouse and keyboard up until that point, but at that point, everything freezes up and I am forced to reboot my computer.  Are there any measures I can take to resolve this issue?

---

### Post by john.wheeler on 2007-05-03
I upgrade from 6.10 to 7.04 and also find that the system freezes shortly after startup. I read a post that suggested this has to do with the initramfs package. Try waiting for 3-4 minutes to see if you get a kind of shell login. This is not the full OS shell, but it might help you.

Please let me know if you solve your problem; I'll do the same!

Cheers,

John Wheeler
[email]john.wheeler.au@gmail.com[/email]

---

### Post by rob_65 on 2007-05-03
I'm definitely getting this exact same issue too. I'd be most grateful for any help! 
I'm very very new to linux. I've tried adding the noapic option to menu.lst, but this has not helped at all.

Any help much appreciated,

Rob 
ry[at]blueyonder.co.uk

---

### Post by finalzero on 2007-05-03
What CPU are you using in your system?

I have found Ubuntu to be very unstable with any 64bit cpu's, especially the AMD X2 CPU's (in  fact most linux distro's failed for me).

If your having issues after doing a clean install or from upgrading your existing 6.10 distro then I recommend you do a clean install of 6.10, once the installation is complete and you have rebooted into your desktop, ignore any update message and wait for the upgrade option.

When you see it accept the option and allow the upgrade to finish, I found this method has worked for me and other people who have had similar issues.

Hope that helps,

Fz

---

### Post by rob_65 on 2007-05-03
Thanks for such a quick reply!

I'm using a E6600 Core 2 Duo 2.4Ghz CPU. It's a totally clean install, no upgrades. It hung like this on the live CD, but I got around this by using the alternate install disk.

Now the problem is replicating itself, annoyingly. I've installed it on a laptop with a T5500 1.66Ghz Core 2 Duo CPU with no problems whatsoever.

Kindest regards

Rob
ry[at]blueyonder.co.uk

---

### Post by finalzero on 2007-05-03
Aye similar to me then.

I have a system running two P4 Xeon 3.2 Ghz processors - interestingly seems many dual core/dual cpu users are having issues with the new release.

Try the clean install of 6.10 and then upgrade to 7.04 as I mentioned, seems to work fine.

---

### Post by rob_65 on 2007-05-03
Would 6.06 be okay to install and then upgrade?

Rob

---

### Post by AdHavoc on 2007-05-03
Mmm, yes, I was wondering that too.  I have several CD's of Dapper Drake that I got from Canonical's ShipIt that work perfectly; I didn't know if it would be wise to go from 6.06 > 6.10 > 7.04 or not.

---

### Post by rob_65 on 2007-05-04
Just tried installing Debian on the same computer, and it's hanging at the point at which the network drivers are loaded and configured. So maybe it's something to do with the networking in the kernel? - If it's similar to the kernel in Ubuntu..

Any ideas?

---

### Post by rob_65 on 2007-05-06
Update - I managed to get X working:

Pressed F6 at startup, removed quiet and nosplash from the parameters.
Added ```
single vga=791
```

This brought me to a terminal
I ran ```
apt-get install nvidia-glx
```
I'm aware that most places advise you run nvidia-glx config-enable but that produced errors for me so I rolled back my xorg.conf (?) file

Ran startx and everything worked fine, keyboard fine, mouse fine.
From terminal I ran ```
gksudo --desktop %k ubiquity gtkui
```

This brought me to the GUI setup, everything went fine until it came to the partitioning, where when I tried typing "/boot" as where I wanted to mount one of my drives, my keyboard decided to stop responding, and constantly inputted "d" and "[".

Tried disabling legacy USB in the BIOS, but then I don't get any keyboard response at all.

Any ideas?

Rob

---

### Post by PatsM on 2007-05-06
I had the same issue. Re-installing Evolution solved the problem for me!

---

### Post by rob_65 on 2007-05-06
Update:

Having been made aware of the Feisty S-ATA / ATA conflict, I tried typing

```
sudo killall -9 hald-addon-storage
```
and it returned that no processes had been killed.

It's still freezing in the GUI stage of the install, whenever I use the keyboard, either in the partitioning section or the Who are you? section. The keyboard input doesn't get recorded, then when I press escape it effectively holds down the d, [, or ] key constantly.

Just to clarify, if I boot off the Live CD normally, the keyboard and mouse lock up within a matter of 3 seconds. However if I add the parameters to the startup and run starx manually, it doesn't lock up until I'm in the GUI install. And also for further information I was able to install fully with the alternate CD, but upon arriving at the logon screen it wouldn't let me type anything in the username field.

PatsM, do you mean reinstalling Evolution from the live CD?

---

### Post by rob_65 on 2007-05-06
I've managed to install Feisty using the alternate CD and by starting X from the terminal in recovery mode, EVERYTHING IS FINE!!! :)

So what's going wrong in the normal startup JUST after I see the login screen?

Can anyone help?

---

### Post by defishguy on 2007-05-07
I've reinstalled Feisty several different ways to try to determine the freezing problem.

My hardware is an Acer Aspire 5100
2Ghz AMD
1GB ram.
ATI 200m Express (shared video 128MB)
PCMCIA Bluetooth card.

My current install has yet to freeze after 24 hours of solid use.  This is what I had to do to get there:

*Removed the broadcom bluetooth card.
*Disabled the integrated wireless (using the switch on the front of the laptop case)
*Installed Feisty with the alternate cd
*Enabled the integrated wireless 
*Installed Envy and then installed the current ATI drivers accepting all the defaults and allowing envy to config xorg.conf
*Put the bluetooth card back in


Since then I've installed XGL and enabled the desktop effects and I've installed uswsusp to fix the power management issues.

I've been working all day without so much as a single freeze and I am very happy again!  Before  that I couldn't log out or restart without a freeze.  I have no idea why disabling wireless (ath_pci) during the installation seems to have a benefit for me, so if anyone knows I'd be interested in finding out.

Just thought I'd share this in case someone else might want try it out.

8 May  07 - Another day without freezing..... I can see the sweet composited graphic light at the end of the tunnel.

---

### Post by rob_65 on 2007-05-07
I've now FIXED my problem!

In the end, [annoyingly] adding acpi=off to my bootup completely fixed these errors.

Hope this helps,

Rob

---

