---
title: "Issue with Ubuntu Installation?"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Luke11 on 2011-05-19
Ok, my first post and I'm thinking this is the most logical place for it. I am running Ubuntu 11.04 along side Windows Vista Home Premium (64-bit) on my Toshiba laptop, model, Satellite E105-S1402. The system is about 2.5 years old and the hard drive is about 4 months old. Vista is in the first primary partition and Ubuntu is in the second.

I had just rebooted into Vista after installing a couple of drivers because I had no internet connectivity (in Vista). I then restarted the machine and things seemed to be fine. The system was probably running a good five minutes. 

Drivers installed: Wireless LAN_Intel_13.0.0.107_W7x64W7x86_A
motherboard_driver_lan_realtek_8111_vista

I was entering some text (actually updating my vista product key!) and the system suddenly powered down, not completely but to what looked like a sleep state because the screen was blank. When I try to reboot by pressing the power key, the system powers on and then nothing, no hard drive activity, no BIOS info to the screen, just power and a blank screen. If I attempt to boot from CD (stuck the Vista disk in again), the drive will spin and then just spin down again, still showing nothing on the screen.

I was thinking the drive just went bad, but then why won't the machine POST? Did the BIOS info somehow get erased? If so, how to replace it since the machine doesn't see the optical drive?

Any advice would be appreciated.

---

### Post by jerrrys on 2011-05-20
what did you use to create a partition for your ubuntu install? vista (and only vista) cannot be partitioned with ubuntu (gparted).  it will bork your vista install.  vista must be partitioned with window tools only.

---

