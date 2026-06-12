---
title: "Update/check stops MD RAID10?"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by David Stodolsky on 2010-05-21
Yesterday, upon boot, machine spends some time checking the 2 RAID10 devices. It then started normally.

Today (this is all before GUI appears):

On boot 10.04 says a disk of a RAID10 dev can't be found. Waits for response and then proceeds, but drops into Busy Box. 

After trying a couple of commands, I hit the reset button and the select the Recovery Mode in GRUB. This halts with a blinking cursor on a blank screen, after some Console outputs to display. (Noted that all RAID disks were available according to the BIOS listing to the display.)

Powered down machine and restarted after a few minutes. This led to completely normal GUI.

Ubuntu, with Linux 2.6.32-22-generic was in GRUB after this, so I am not sure whether the check of MD RAID or the update caused the problem.

---

