---
title: "Black screen at startup after installation"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by DrKoi on 2009-12-30
**Problem:** Black screen at startup. The cause seems to be a problem with X. I've included the x log file.

**What I did:**

[LIST]
[*]Netbook with Windows 7, decided to try Ubuntu Netbook Remix
[*]Downloaded the ISO & created a bootable USB stick with USB Installer for Ubuntu
[*]Booted into a live session, tried everything out, looked interesting, decided to install it
[*]Installed it onto the HD from inside Ubuntu. No errors.
[*]Rebooted, removed USB stick, chose Ubuntu in GRUB, saw some text appear, then black screen - flickering
[/LIST]

So the weird thing is that X had no trouble in live mode, but once installed it stopped working. Why would it do that?

I don't get the flickering command line prompt as mentioned in the sticky, it's all black. The log file mentions "Unable to open /dev/agpgart" (see attachment).

**Fixes tried:**

[LIST]
[*]rebooted several times
[*]tried to follow advise found online & edit xorg.conf, but there is no xorg.conf anymore
[*]because of that, "sudo dpkg-reconfigure xserver-xorg" also doesn't do anything (no error msg either)
[*]edited grub.cfg and adding "nomodeset"
[*]booted in recovery mode & tried all the options that looked useful
[*]created a xorg.conf with "X -configure" & copied it to /etc/X11 & rebooted
[*]added "intel_agp" and "agpgart" to /etc/modules
[/LIST] 

**Info:**

[LIST]
[*]Ubuntu Notebook Remix 9.10
[*]Acer Aspire 1420P notebook
[*]graphics chip: Intel GMA 4500MHD
[*]resolution: 1366x768
[*]I don't seem to have Internet access in recovery mode (even when I select the 'root prompt with networking' mode)
[/LIST]

---

