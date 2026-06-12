---
title: "Upgrading Feisty Fawn to Gutsy Gibbon with Dual Monitors - TIPS"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Martin T Wirth on 2007-11-20
If you have dual monitors then the longest distance between two points is the upgrade shortcut from Feisty Fawn to Gutsy Gibbon.

Misery will come from bad video drivers left over from your Feisty installation. Tracking these down is like picking fly dung from pepper. The direct upgrade leaves some of these untouched and your video performance will be intolerably slow. My dual monitor configuration was completely trashed by this upgrade and I found it to be unrecoverable without the procedure that follows.

Because I'm too cheap to buy two of the same monitor, I have this weird configuration:

Video Card: ATI Radeon 9500
Monitor on VGA: LG Flatron L2010P (a notoriously ill-behaved LCD to configure on Linux)
Monitor on DVI: Samsung SyncMaster 204B (which is a beauty)

:popcorn:Here's is how you upgrade your dual monitor system from Feisty Fawn to Gutsy Gibbon when all else fails:

1. Back up all the data that you want to keep. If you do not have a Feisty Fawn CD for rollback purposes, you may want to download the ISO image and burn one just in case.

2. Download and burn (or order) a Gutsy Gibbon installation CD.

3. Do a clean installation of Gutsy Gibbon (not an "upgrade").

4. After installing, go into System->Administration->User and Groups and assign yourself a root password that you can use for recovery operations.

5. Pull up a terminal, su root, and back up your /etc/X11/xorg.conf file to xorg_gg.conf or something you will remember.

6. Use the xorg.conf that I've provided as a template and customize it for your video card and monitors. Be aware that the nifty little GUIs provided with Gutsy Gibbon do not work for some dual monitor configurations and will probably break what works.

7. If something goes wrong then use recovery mode on boot, enter your root password, cd to /etc/X11, copy your back-up of xorg.conf (such as xorg_gg.conf) to xorg.conf, and reboot. If it works better as you go along then back up your improved xorg.conf file.


I attached both Feisty Fawn and Gutsy Gibbon xorg.conf files so that you can see the differences. The new fglrx video card driver in Gutsy seems to know more about monitors than the previous version.

Further Notes:

If you are not using a video card connected to an AGP slot then the AGP settings do not apply. Try your device with minimal settings first UNLIKE what I show in my own xorg.conf files. Add optimizations carefully and back up what works as you go along. Be aware that some parameters must be accompanied by others or breakage occurs.

The monitor settings for the LG L2010 also work for single monitor configurations on Linux systems that have older video card drivers such as Feisty Fawn and prior versions.

Being meticulous about this configuration brings better luck. Look for mismatched names, missing quotes, or misspelled parameters.

There are more amusing things to do in life than configuring dual-monitors on Linux, try to remain calm while doing this. Your back-up is your ally.

---

