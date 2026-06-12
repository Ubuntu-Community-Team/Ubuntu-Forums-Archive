---
title: "System won't install, live cd doesn't work...Experiencing freeze"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by warchild on 2015-03-01
Hey peeps,

Finally I decided to make the transition from Windows to Linux but I've been battling with this frustrating issue since morning and I've tried almost everything to solve it but still no go. 

First things first, I have a high-end gaming laptop and here's the specs:

i7 4710QM
16GB RAM
2x250 GB Samsung 840 Evo mSATA SSD (Been using these as RAID0 array in Windows, planning to do the same in Ubuntu, care to help?)
1TB 7200RPM HDD
NVIDIA GTX 880M 8GB
1080p monitör

I downloaded the ISO file (First Ubuntu 14.10 and then Ubuntu MATE 15.04) and burned it to a DVD. Booted using the DVD and choose Live CD & Install options from the welcome screen but neither of them are working. I see the Ubuntu loading screen and it won't go any further than that. I see the animation going but nothing happens... When I press F1, I see some text on the screen: [ATTACH=CONFIG]260362[/ATTACH][ATTACH=CONFIG]260363[/ATTACH]

I tried with UEFI and Legacy boot options, plugged & unplugged my Ethernet cable still no go.

---

### Post by jacobpratt909 on 2015-03-01
The first picture seems to have interesting info, while the second is normal. The second picture says it found CPU stalls (?), so that might be of some use.

---

### Post by warchild on 2015-03-01
> **jacobpratt909 said:**
> The first picture seems to have interesting info, while the second is normal. The second picture says it found CPU stalls (?), so that might be of some use.

Uhm yeah so is it about my hardware's being incompatible with Ubuntu?

By the way I just disabled AHCI in bios and tried with IDE, still no go.

Also played with some options such as acpi=off etc.. and now it says something about Nouveau [DRM].

I'll upload more screenshots.

EDIT: Switched to USB stick installation method now, then chosed nomodeset in options before I begin Install. Here's the text on the screen:

---

### Post by jacobpratt909 on 2015-03-01
I'm not professional enough to figure out what happened, I was just pointing it out for a pro. Sorry :/

---

### Post by gifford on 2015-03-01
Sorry about the issues you are having. The Nouveau is the open source driver for you Nvidia graphics card.
My recommendation is that you install Ubuntu 14.04.2 which should work fine with your hardware. If not,
use Ubuntu 14.04 which has the 3.13.XX kernel as opposed to the 3.16 you have been attempting to install.

---

### Post by warchild on 2015-03-01
I figured the problem out. Looks like it's a known bug and there's no solution to it...

Really disappointed by all this. I feel like I'm in 2000 again when I was a kid. My dad just purchased me a computer for the first time.

I decided to give Linux a try back then. There was a Mandrake distro I downloaded using the dial-up connection... 

But in the end, none of my drivers were recognized. No graphics card, no printer, no fax modem, no sound card, no tv card... nothing. All I had was some crappy arcade games and players that could not open any files. So I really hated Linux back then.

Today, 15 years later. Seeing all the hype about Linux, I decided to give another go and BAM! My top of the line, modern graphics card is not recognized. Kinda brings back memories lol...

It's not like this is a rare issue or something. I checked this thread ([https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1097178](https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1097178)) where people experience my issue and it has been present since 2013. Everybody's complaining about it. Yet no fixes available and bug report is closed.

> **gifford said:**
> Sorry about the issues you are having. The Nouveau is the open source driver for you Nvidia graphics card.
My recommendation is that you install Ubuntu 14.04.2 which should work fine with your hardware. If not,
use Ubuntu 14.04 which has the 3.13.XX kernel as opposed to the 3.16 you have been attempting to install.

Thanks gifford,

Will try.

---

### Post by warchild on 2015-03-01
Tried 14.04 but it's worse: black screen of death.

SuSe Linux installation finishes successfully but it freezes on the desktop environment.

Isn't there a way to disable or remove Nouveau from the installation medium and replace it with official Nvidia driver?

---

### Post by warchild on 2015-03-01
OK. Good news is I managed to get past to installation screen. I applied "nouveau.blacklist=1" right before the quiet splash and it worked.

the bad news is I cannot enable software raid in ubuntu partition manager. How do I do that?

---

### Post by gifford on 2015-03-02
Glad you got the installation screen to work. Are you trying to enable the raid when you are installing? 
Or have you installed and are using GParted?

---

### Post by The Big Head One on 2015-08-04
> **warchild said:**
> OK. Good news is I managed to get past to installation screen. I applied "nouveau.blacklist=1" right before the quiet splash and it worked.

the bad news is I cannot enable software raid in ubuntu partition manager. How do I do that?

I'm having the same problem and my notebook is really similar to yours (a high end gaming notebook with nvidia gpu). Where exactly did you apply the nouveau.blacklist=1? Did you press ESC after choosing to install or during the screen to select whether to install or try withotu installing?

I'm already running 14.04 and I really want to use the new distro. Installing a old distro just because of such a bug really sux.

---

