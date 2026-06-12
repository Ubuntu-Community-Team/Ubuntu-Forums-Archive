---
title: "Ubuntu 9.10 Will Not Boot"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by Jinseru on 2010-04-02
Hey everyone, I'm fairly new to Linux but am not a stranger to computers at all so I guess be a little easy on me. I recently installed 9.10 on my P4 HT 3.2ghz processor on a D915GEV motherboard. Problem is, the program will not run from disc or from the hard drive. I had no problems installing but once it's done it got stuck on a screen where everything was mixed up and distorted and when I restarted the computer and tried to boot it simply sat at the DOS screen and did nothing. When I tried to run it from the disc it loads up and everything but once the loading screen (equivalent to the windows loading screen before login) is done it brings up a black screen. I can see my mouse and the thinking icon for it, but that's it. Any advice? I can get more information from it if needed.

---

### Post by oldfred on 2010-04-02
Welcome to the forums.

It sounds like a video issue. From the liveCD f6 gives some of the options for booting. See if any of these work and then we can add those to your boot that your installed.

---

### Post by dsb1225 on 2010-04-24
I am new to Ubuntu also and installed 9.10 recently for my autistic son. I had the problem at one point where the OS would not boot or would take a long time to boot. None of the on-line helps actually found the problem, but I figured it out. My son had left a CD in the CDRW drive and the computer BIOS was still set to boot from CD first. Rather than UBUNTU 9.10 recognizing that this was not a boot disk, it ran fsck on the CDROM. Eventually the OS booted, but would take an hour or so. My simple fix was to change the BIOS boot sequence so it boots from the HDD first.
 
Since then I have met with a whole host of other issues which are related to my novice status. But there are so many helpful users out there that I found fixes for those problems:
 
For example: If you install dansguardian using the webcontentcontrol steps which install also firehol, and you find you cannot configure it in 9.10, use google to look for "DANSGUARDIAN GUI Ubuntu 9.10" and there are some steps which will guide you to install the GUI. Don't do what I did and uninstall dansguardian only to find the WEB does not work at all even if you do connect to your router due to firehol still running. I did a complete OS reinstall then, had the problem repeat later and finally found some helpful sole who said how to kill and remove firehol if you get rid of dansguardian so it will still have internet connectivity. Later I reinstalled and added the GUI and was fine.
 
Anyway, hopefully some of this is helpful:)

---

