---
title: "How to verify 7.10 upgraded properly following crash during process?"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by milkyspit on 2007-11-02
Hi all, please be patient with me, I need some help... have been a software developer most of career but am new to Ubuntu. My problem...

I used Upgrade Manager to upgrade my Sony Vaio PCG-SR17K notebook from 7.04 to 7.10... packages seemed to download fine but partway through the upgrade process the upgrade hung... after a few hours (to make sure it wasn't just slow) I rebooted the system.

Couldn't get the system to log into Gnome, it would hang with a generic backgound and active mouse pointer, but nothing else... so I had to power cycle the laptop and log into Failsafe Gnome session.

HAL didn't work... Cardbus ethernet card (wired) didn't work... Upgrade Manager told me to run 'dpkg --configure -a' or something along those lines from terminal... I did so as root, it completed after quite some time, looked like it did a lot, but also reported a handful of packages that didn't configure properly.

System froze on attempted reboot, never shutdown properly, just hung... power cycled the hardware, went back to Failsafe Gnome, used Upgrade Manager to grab another 5 or so things it reported as needing updating.

Now I've got a system that kinda sorta works, but I really have no confidence the upgrade to 7.10 finished and is configured properly.

How can I check that 7.10 is installed properly... is there a way? Or... how can I force the system to repeat the 7.10 upgrade, perhaps correcting steps it might have missed or bungled the last time?

Thank you... I could use the help! Just want some peace of mind that my laptop is now running a complete, stable copy of 7.10, and not some weird patchwork of newer and older elements.
:popcorn:

---

### Post by dantrevino on 2007-11-03
There are a few ways to do this.

"sudo update-manager -c" will attempt a dist-upgrade, which should upgrade everything if necessary.  If you wanna double check, go look at /etc/apt/sources.list and make sure there are no lines with "feisty".  If so, change them to "gutsy".  "sudo apt-get install -f" will fix any broken/partial installations.

dan

---

### Post by fausto1980 on 2007-11-04
I had the same problem with my Vaio SR-17K but it seems like I have everything running normally now.  I had to do a partial upgrade but that didn't work the first time.  I kept getting an error about acpid but I was able to fix that now everything seems to be up to date.  Do you know if desktop effects works on the Vaio SR-17k?

---

