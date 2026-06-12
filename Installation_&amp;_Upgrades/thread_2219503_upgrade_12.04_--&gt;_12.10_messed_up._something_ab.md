---
title: "upgrade 12.04 --&gt; 12.10 messed up. something about screens"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by p.callan on 2014-04-24
Wanted to upgrade to 14.04 but ubuntu.com said to upgrade one release at a time, so I started with 12.04 --> 12.10. Upgraded through update manager tobe able to keep my files, settings and software (i.e my master's thesis and all my cryptocurrencies). Went well until reboot where there was only a black screen. Booted into generic mode and get to command screen (only). On another computer I troubleshoot but there are a million variants of similar problems but not this one. Some people were yodeling something about pressing right shift at boot from USB... Well, I used update manager as I was told!

Added *nomodeset* to /etc/default/grub which got rid of the black screen. But at booting ubuntu normally it hangs while I get the normal "The disk drive for /dev/mapper/cryptswap1 is not redy yet or not present". This is the same across 3 machines and I guess a separate issue. However the comp is frozen at this point.

From what I gather I have a display/ graphics problem. I have a Flatron E2251 connected via VGA to my main machine; NP-X125 with a HD 4200 Radeon GPU. Has been working flawlessly on 12.04. Downloaded the drivers onto a usb stick and stuck it into the main machine. typed *dir* but this does not list the usb stick. If it had, I could have somehow installed the drivers.

I honestly don't have time to troubleshoot this for days on end. It is extremely frustrating that updates are "sold" as simple and easy when they actually mean that they render the entire computer unusable. If I hadn't trusted the native update process I could have just installed 14.04 on top of 12.04, but now I can't. I NEED to get my stuff back through one-step-at-a-time upgrades. 

Thanks to you pros out there who can help me.

Yeah, ok so... Can I install the next version (13.04) via this text/teminal/DOS version of 12.10 that is now all that I have access to, or do I need to get into the GUI to update via update manager (to keep my files & settings)??

---

### Post by Frogs Hair on 2014-04-24
Because 13.04 is not supported the next version offered via upgrade would be 13.10 that is if 12.10 is supported . 12.10 support ends this month but no date is given.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by p.callan on 2014-04-24
Well, I got 12.04 because of the support.

I have now done this:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and this:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)


and I got it working. Although it took all freaking day, I am now inside 12.10 GUI.
The key was to remove the (proprietary) drivers that were used for my ATI radeon 4xxx-series GPU.
Proceeding with install of 13.10 as directed by software updater, for the goal of 14.04.

---

