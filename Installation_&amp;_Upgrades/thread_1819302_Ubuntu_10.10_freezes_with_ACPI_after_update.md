---
title: "Ubuntu 10.10 freezes with ACPI after update"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by voilsb on 2011-08-05
I updated my system today (a simple "mark all upgrades" then apply in synaptic) and when I booted it up later, it stops after > isapnp: No Plug & Play device found

I can't even use the magic sysrq keys to stop or reboot the system, so I hard power it off and turn it back on. In Grub I add "acpi=off" to the end of my linux boot line, and it boots up. Only now ACPI is off, so it doesn't give me battery status updates and only recognizes one of the CPU cores.

These were the upgraded packages, which were the only changes made to the system:> chromium-browser (12.0.742.112~r90304-0ubuntu0.10.10.1) to 13.0.782.107~r94237-0ubuntu0.10.10.1
chromium-browser-inspector (12.0.742.112~r90304-0ubuntu0.10.10.1) to 13.0.782.107~r94237-0ubuntu0.10.10.1
chromium-browser-l10n (12.0.742.112~r90304-0ubuntu0.10.10.1) to 13.0.782.107~r94237-0ubuntu0.10.10.1
chromium-codecs-ffmpeg (12.0.742.112~r90304-0ubuntu0.10.10.1) to 13.0.782.107~r94237-0ubuntu0.10.10.1
libsmbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
libwbclient0 (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
samba-common (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
samba-common-bin (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
smbclient (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5
winbind (2:3.5.4~dfsg-1ubuntu8.4) to 2:3.5.4~dfsg-1ubuntu8.5

Here's the output of 'uname -a'
> Linux MrBurns 2.6.35-30-generic-pae #56-Ubuntu SMP Mon Jul 11 21:51:12 UTC 2011 i686 GNU/Linux

I can't find any system logs of the freeze, all my logs are from before the updates or when booted with acpi=off

I've attached a screenshot of the console during the freeze.

Any ideas how I can fix this? If I can't figure something out by the end of the weekend I may just backup my data and do a fresh install 11.04.

---

