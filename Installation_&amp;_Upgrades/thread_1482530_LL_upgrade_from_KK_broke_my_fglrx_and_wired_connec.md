---
title: "LL upgrade from KK broke my fglrx and wired connection?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by gnunub on 2010-05-13
TL/DR: reboot on upgrade has no gui, fglrx not working, also my wired connection is no longer detected by ubuntu or other distros live cds since upgrade

Before installing KK a few weeks ago I booted from live CD w/o issues. Also booted a few other distros that way and all detected my wired ethernet connection.

So, 64 bit... On reboot after upgrading from within KK to LL...

Monitor via DVI cable loses video signal aften displaying BIOS and GRUB-- 
It goes black and reports "No Signal" and enters sleep mode.
When I boot into Recovery Mode from GRUB and select failsafeX (safe graphics mode) it loads the GUI but fglrx isn't working.

Update Manager tells me there is a distribution update: fglrx (New install). Clicking Install Updates presents errors...
1. I have 3 broken packages.
2. "E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1"
3. Errors were encountered while processing:
xorg-driver-fglrx
fglrx-kernel-source
fglrx-amdcccle

I'm plugged into internet via etherent cable but the 'Wired Network is disconnected' in the system tray notification. When I boot into live CDs of other distros my ethernet connection is no longer detected! My router doesn't show a light above the port it's connected to like it should. I haven't made any other changes to the system or router recently. I've tried another ethernet cable and a diff port. None detected by system or confirmed by router...


sudo apt-get upgrade:
The following packages have unmet dependencies:
fglrx-amdcccle: Depends: fglrx but it is not installed
fglrx-kernel-source: Depends: fglrx but it is not installed
xorg-driver-fglrx: Depends: fglrx but it is not installed
E: Unmet dependencies. Try using -f.


sudo apt-get -f install, i get an equivelant of:
"E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1"


sudo apt-get update
W: Failed to fetch xxx Could not resovle 'xxx.ubuntu.com'
over and over and over
W: Some index files failed to download, they have been ignored, or old ones used instead.


I tried fixing the broken packages from the option in Recovery mode but that didn't work either. I think if I can get my ethernet wired connection back I should be able to fix the fglrx...

Please help a noob out!

---

### Post by gnunub on 2010-05-14
Didn't find answers in the search engine or anything. Unfortunately, this computer can't go without internet for longer, so I'm going to swtich back to Windows. No point in using linux when things stop working or go undetected on upgrade. I'd rather have a working OS. I'll check back in a few years and see if linux works then.

---

