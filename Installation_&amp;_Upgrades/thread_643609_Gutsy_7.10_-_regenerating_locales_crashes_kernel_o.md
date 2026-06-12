---
title: "Gutsy 7.10 - regenerating locales crashes kernel on AMD64"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by ironstorm on 2007-12-18
EDIT:  [Bug#25660]("https://bugs.launchpad.net/ubuntu/+source/belocs-locales-bin/+bug/25660") looks like it might be related...  going to see if I can disable one core.

I've just spent a few hours trying to get Ubuntu and Kubuntu working on my system.   I looked on Launchpad and here but couldn't find a solution... 

The LiveCD installer bombs out at 78% when it begins generating locales, I flipped over to the console and tail -f /var/log/dmesg and saw the kernel die with some message about not syncing Aieee after which the kernel panics (caps and scroll lock keys blink, nothing else happens).

The installer freezes at the exact same spot on both Ubuntu and Kubuntu 7.10 AMD64 discs.

I eventually got onto the drive chrooting from the liveCD and manually configuring grub.

Once I got the system booted from the HDD to Kubuntu, I ran dpkg-reconfigure --all to complete the install...  when it hit the locales, I got seg fault (core dump), seg fault, then a general protection fault on SMP #1 and finally it fried the second CPU...   This is reproducible by also running dpkg-reconfigure locales.   It randomly segfaults on about 50% of the locales, but it takes less the 6 to nuke the kernel every time. 

Has anyone seen this before / know of a fix?   Also is there a way to reduce the number of locales that must be generated via a config change or removing some files/dirs?  

I seem to remember dpkg-reconfigure locales would pop up a dialog asking which locales to config... 

Here's the system
AMD64 X2 3800+ (dual core)
1GB DDR Ram
Nvidia 6800GTS 256MB
NForce4 mobo
160GB Sata drive

Any suggestions would be appreciated...

-G

---

### Post by ganryumvp on 2008-01-10
Just wanted to bump this as I've got exactly the same problem. AMD64 crashes generating locales every time on livecd and alternate since I first tryed on 6.06 to now with 7.10. CDs are fine. i386 installs and runs without a problem.

My system:
AMD64 3200+
1GB DDR Ram
Nvidia 6600GT
DFI SLI-DR NForce4 mobo
Sata drives

My system has a lot of similiarities with this guy with the same problem [Server Install Hangs at Locales Generation]("http://ubuntuforums.org/showthread.php?t=187372"). So maybe something in the DFI boards? We both have nForce SATA, nForce LAN and also a Marvel Yukon LAN.

64bit only runs for me on Fedora-64 and Windows-64. Ubuntu, Debian and Gentoo all segfault when generating locales in 64bit.

If anyone can think of what could be causing this please let us know.

---

### Post by p_murinus on 2008-03-24
I also encountered this, installing from xubuntu-7.10-alternate-amd64.iso

However, I got the installation to complete successfully by doing the following:
[LIST=1]
[*]Open Synaptic Package Manager
[*]Search for **language-pack**
[*]De-select / Completely Remove any **language-pack-*xx*** you don't need (I only left -en selected)
[*]Search for **language-support**
[*]De-select / Completely Remove any **language-support-*xx*** you don't need .
[*]Apply, then run the Installer. (Don't reboot!)
[/LIST]
It's labor-intensive, but it worked for the 3 AMD64 systems I tried it on.

---

