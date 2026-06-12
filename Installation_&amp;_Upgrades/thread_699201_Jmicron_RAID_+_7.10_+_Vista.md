---
title: "Jmicron RAID + 7.10 + Vista"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by gamiao on 2008-02-17
Hello!

After several unsuccessful attemts to install gutsy along with vista on my raid0 setup (using Jmicron 363 controller on Gigabyte P965-DS3) I decided to install a separate disk just for Ubuntu.
So I put on an additional SATA drive on the Intel ICH8 sata controller, unplug the other sata drives so that ubuntu doesn't mess up the raid0 and I proceed with install.

Installation was fine, and I could log in to Gutsy.

I then re-plug the raid0 drives and reboot. I choose the Intel Sata as 1st boot device -> Ubuntu boots normally.

But when I restart the PC, the raid0 setup (as seen in the message screen of the controller during boot) is lost and of course I can't boot into windows! (I would do it by resetting raid0 (scsi1) as 1st boot device).
If the pc is turned off and on (no cold reset, only power off) the raid0 comes back.

Is there anyway of avoiding this problem? If this is sloved I guess I could use a boot manager like boot magic to setup the dual boot (because grub will fail on the jmicron).
I have updated the kernel to 2.6.22.14 but no good.

Any help would be appreciated, I just don't want to mess the windows set up at no cost!

---

