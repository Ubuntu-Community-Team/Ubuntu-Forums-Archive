---
title: "Edgy Upgrade Issues"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Digicrat on 2006-12-01
I just completed running the upgrade from Dapper to Edgy on my laptop, and I'm having several annoying issues.  I'd appreciate any help.  (FYI: I've had Linux installed on my laptop for over a year, and have been using Gentoo on my desktop for even longer).

Going in the order I've encountered these issues . . . [ok, this is also a half-rant on Ubuntu upgrade problems, sorry about that, but I'd still appreciate some help - feel free to skip over the background/rant paragraphs]

**1. Grub Configuration**
It seems that Ubuntu does not like to play nice with other operating systems.  I originally installed Ubuntu to replace Fedora in a dual boot with Windows.  During that initial install Ubuntu automatically re-installed grub to the boot partition (which I did not want, as Windows was nicely booting into the grub launcher, and having the windows boot menu on the MBR simplifies a lot of things) - I never did get around to restoring the Windows MBR.

Now with the upgrade, Ubuntu is again playing with my boot settings.  After the upgrade, despite the grub.conf files being unchanged, all modifications to the boot options have dissapeared, meaning I no longer have the option to boot into Windows.  How can I get Grub to show the Windows boot options again without losing Ubuntu's automatically updated boot options?

**2. Strange Boot Issues.**
On Boot, the splash screen is no longer showing the system status.  There is the Ubuntu logo and a progress bar, but the details (checking disks, starting networking, etc.) are no longer visible.  

Additionally, when it transitions into loading the desktop there are some brief, but weird, graphical glitches.  Kind of like frozen static on the screen for a second.  

Any ideas?  Particularly with the laptop, I want to see the progress of what it's doing when it boots, and the graphical glitches are just annoying.

**3. Wi-Fi**
Wi-Fi worked perfectly well (or at least it was always detected) before/during the upgrade, however now it no longer detects my wireless card (A Dell-branded 802.11b/g card, I don't recall the model offhand).  It seems that for some reason it completely uninstalled ndiswrapper during the upgrade process without telling me?  

What happened to Ubuntu's acclaimed improved support for wireless network devices?  I believe the original LiveCD correctly detected the card without much configuration (actually, I don't remember whether or not I was using ndiswrapper with this installation or not, all I know is that ndiwrapper is not installed now and it is not detecting the wireless card)

WiFi has never worked relatively reliably for me in Ubuntu - it's always a matter of trial and error before it successfully connects to the network and retrieves DHCP information.  Command-line utilities required a waiting game until DHCP connected, while the GUI configuration utilities worked maybe 1/2 of the time at most.  Once I managed to get it to work reliably in Ubuntu on my home network between boots, only to lose it when I try connecting to the network on campus.  I've been resorting to command-line options and a regular routine of waiting anywhere between 1-5 minutes (as much as 10 when the campus wi-fi is being slow) before it connects successfully.

This brings me to my next issue, the 
**4. Package Manager**
Is there a reason why the "Advanced" view option in the package manager (Add/Remove Programs) is no longer present?  A number of applications, including ndiswrapper, will typically only show up in the advanced view which I can no longer seem to access. I could of course always use the manual apt-get, but I have enough of manual commands when maintaining my Gentoo install - I'd rather use a GUI on the laptop, I chose Ubuntu as a low-maintenance distro.



Any suggestions on any of these issues?  

I really don't feel like digging up an extra ethernet cable (to get a wired connection so that I can re-configure the wireless yet again) and/or my original XP CD in order to fix the MBR [the Windows boot loader can load Grub . ..but this Ubuntu upgrade seems to have told Grub that it can't load Windows anymore!]

Thanks

---

### Post by lemonsCC on 2006-12-01
4)  there is no more advanced as far as i know.  its either add/remove of synaptic.  just run synaptic from system > administration

---

### Post by Digicrat on 2006-12-02
I've been trying to fix some of these issues, but haven't been making much progress:

**Wi-Fi:**
I just plugged in the old 6.06 LiveCD, and in that CD Ubuntu does successfully detect my (Broadcom) wireless network card without using ndiswrapper.  Of course, getting it to connect to my security-enabled wireless network successfully is another story.  This just adds to my confusion of why after upgrading Ubuntu no longer detects my wireless card!

**Boot Issues:**
I still can't figure out why the Windows option, despite being in the grub.conf files, no longer appears on the grub boot menu.  

I just used the Windows boot disk to fix the MBR, however now I can't boot into Linux.  Prior to the Ubuntu upgrade, the boot-loaders were successfully chained (although Grub was still in the MBR)-- the Windows Boot loader could load Grub, and Grub the Windows loader.  Now for some reason, with the only change being the fixmbr and Ubuntu upgrade, this is no longer working.  I tried regenerating the linux.bin file used by the Windows boot loader, however there's no difference, it just freezes at the "GRUB" text message.  

Any ideas?

---

### Post by ciscosurfer on 2006-12-02
You won't have as many issues if you do a fresh, clean install from a disc.  More people have trouble upgrading than fresh installing.

Fresh install, fresh install.

---

### Post by Digicrat on 2006-12-02
Fresh installs take more time and effort though, particularly in backing up settings and reinstalling a lot of non-standard applications and utilities I've installed.  At this rate though, I might not have a choice (I knew I should have waited until I actually have time to try the upgrade)

---

### Post by ciscosurfer on 2006-12-02
When all is said and done, you'll be glad you did a fresh install over upgrading.  Trust me.

---

### Post by dsapoki on 2006-12-02
Wifi problem

hello,
I had a same problem. don't worry. just type in terminal or proceed by synaptic ndiswrapper 1.8 and ndsiwrapper-common
hope this helps

---

