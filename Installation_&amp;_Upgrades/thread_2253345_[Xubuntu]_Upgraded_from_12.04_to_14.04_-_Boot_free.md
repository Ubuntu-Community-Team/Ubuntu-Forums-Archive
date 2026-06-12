---
title: "[Xubuntu] Upgraded from 12.04 to 14.04 - Boot freezes on loading CUPS"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by Mallgur on 2014-11-19
Hi,

I have an ASUS F5GL running 12.04 fine.

I was running out of space on the partition I had so I decided to buy a new drive.
A brand new installation of Xubuntu 14.04 fails due to problems with nouveau drivers. I even tried another variant (LXLE) that would boot on VESA but the install also failed with nouveau drivers problems. I then gave up and simply moved the installation to the new bigger drive to upgrade (best option for this was Clonezilla).

So, after I got the installation onto the new drive, it was working ok. So I proceeded to the upgrade process.

First I installed the updates that were pending. All went well. The system booted fine.

Then I opted for the Upgrade to 14.04. I was warned that it would be a partial upgrade, no details on exactly why, but I did not care and proceeded.

The upgrade completed with no errors reported but now the systems freezes during boot.

Pressing ESC during the splash screen shows me messages up to a point where it is loading CUPS. Then everything stops and the systems is frozen.

I tried booting in rescue mode to try and fix it but am not an expert so I could not manage it. I tried to unsinstall CUPS (I rarely print anyhting anyway) but in rescue mode the systems is mounted as read-only and apt-get can't work to remove CUPS.

Any idea on how to get the system back to running condition?

I can always redo the Clonezilla process and the updates but it seems kind of silly and reminds me too much of how things used to be on Windows...

Thanks for any help.

---

### Post by Mallgur on 2014-12-15
Update:

Gave up on upgrading to 14.04. It simply will not work.

I did manage to get further from the CUPS part and even got to have a desktop working. However, it was somehow impossible to get a decent resolution. Trying any of the NVIDIA drivers resulted in black screens, using the nouveau drivers gave me no option above 640x480 (:sad:)...

So, I'll just keep it at 12.04 until the PC dies. I have little hope that any newer version will work.

---

