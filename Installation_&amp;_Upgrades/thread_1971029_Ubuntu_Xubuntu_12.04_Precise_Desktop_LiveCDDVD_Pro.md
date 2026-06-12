---
title: "Ubuntu/ Xubuntu 12.04 Precise Desktop LiveCD/DVD Problem: No Video"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by shreepads on 2012-05-02
Hi

Tried to run, in order
- Ubuntu 12.04 LiveDVD (64-bit Desktop): Burnt to DVD and booted from disk
- Ubuntu 12.04 LiveCD (64-bit Desktop): Written to USB stick via usb-creator and booted from USB
- Xubuntu 12.04 LiveCD (64-bit Desktop): Written to USB stick via usb-creator and booted from USB

In each case, got the same behaviour
- System would boot from the disk/ USB
- Would be presented with the splah/ progress screen (the one with the dots on plain background for Ubuntu and bouncing progress bar with background image for Xubuntu)
- After that screen would fill up with coloured noise, random black/ coloured pixels all over the screen
- Unable to do anything other than a hard reboot

This was with using an old NVidia GT 240 card (which works fine with Lucid 10.04.4 64-bit Desktop). Complete system specs in the signature...

Next I went into BIOS and forced it to use the onboard Intel graphics (Intel DG33FB board with Inteal GMA 3100 graphics) and Xubuntu booted up fine and got into the desktop with no problems. Launched a few apps and all seems fine.

Based on my advanced analytical skills (!) I conclude there is a problem with the graphics driver on the LiveCD/DVD in Ubuntu/Xubuntu.

I guess I could fix this by installing with the onboard Intel video and then upgrade to the latest NVidia drivers via the safe mode command line (have done this many times before) but I guess I'll just wait for 12.04.1 instead!

---

### Post by amdr on 2012-05-15
I have the same problem running Xubuntu 12.04 64b on my ASUS A6M notebook (Turion X2, GF6100). I haven't tried 32b version, 64b Ubuntus 10.04, 10.10 and 11.04 run fine. I use the same Xubuntu on my desktop (Athlon X2, AMD690G, HD3850) without problems.

It looks like only a test installer may do the job, but not for sure :/

---

### Post by shreepads on 2012-05-21
Have filed a bug for this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907)

Please open this and indicate this affects you, if you are using GT 240 and face this problem as well.

---

### Post by shreepads on 2012-05-30
Tried with Linux Mint 13 (Cinnamon 64-bit) Live DVD on USB and faced the exactly same situation
- Coloured noise on NVidia
- All well on integrated Intel graphics (G33)

Not suprising I guess seeing how Mint 13 is directly derived from Precise.

To try something else, I installed Linux Mint 13 (Cinnamon 64-bit) to another large USB and booted from it (using the Intel graphics).

I then followed the instructions I'd written earlier for installing the proprietary NVidia drivers ([link]("http://ubuntuforums.org/showthread.php?t=1665630")) with some minor tweaks.

Now posting this from Linux Mint 13 (Cinnamon 64-bit) running off the larger USB and with the NVidia graphics running fine!! :)

Long story short, the same should work on Precise as well, will give it a shot when I have some time and report... But Cinnamon is such a blessing (over Unity) that I'm tempted...  :P

---

### Post by shreepads on 2012-08-25
Problem persists in 12.04.1

Interestingly the corrupted Desktop screen contained parts of the Snow Mountain track in Tuxcart. My son was playing this in Lucid just before I restarted and booted into Precise via USB stick...

Here's the screen photo, see the bug report for complete details:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/993907)

---

### Post by jibawakee on 2012-08-25
try all the boot flags when

---

### Post by shreepads on 2012-08-26
> **jibawakee said:**
> try all the boot flags when

Can't touch any of the boot flags, the initial boot screen (where if you hit a key it shows the language options and then the boot options) is also not displayed. Just shows up as a tiny grey bar in the bottom left corner of the screen...

See the bug report...

---

### Post by shreepads on 2012-08-29
Switched mobo to integrated Intel G33 graphics and everything worked fine (almost). 

Completed the installation (Precise 12.04.1 64-bit desktop DVD), but skipped the 3rd party software for MP3 etc option, as on the first install try it (ubiquity) shut down with an error re 3rd party software, AFTER formatting the existing / partition.. Grrrrrr.

Booted the installed Precise 12.04.1 and was able to view the desktop and install patches and applications fine.

Then restarted, switched mobo back to the NVidia GT240 card and booted, corrupted desktop as usual...

Restarted Precise in 'safe mode' from the grub menu, display worked and now was able to see the safe mode options. Selected the failsafeX option but that too didn't work, the next option screen froze, keyboard and mouse not working.

Restarted Precise in 'safe mode', in the safe mode options enabled Networking (which also mounts the filesystem in read/write mode) and then dropped to root shell. Ran

```
#apt-get install nvidia-current
```

This installed v295.40 of the Nvidia proprietary drivers. Once done, issued reboot and this time chose the regular Precise option in the grub menu... 

And the desktop was up and running with GT 240 card in all its glory. Looks spectacular, the only thorn is the app menus appear in the top panel and which only appear on mouseover.. Terrible design that...

This workaround is, obviously, only for those fortunate enough to have integrated graphics in addition to the NVidia card. Although I suspect that people with only an NVidia card should be able to do this from the alternate text based installer.

---

