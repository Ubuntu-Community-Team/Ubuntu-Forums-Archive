---
title: "Ubuntu freezes at start of installation"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by mrwooster on 2007-01-15
I am having trouble installing ubuntu on a dell inspiron 9400 - I have created the install disk with the latest version of ubuntu and checked the disk, when I boot up the install it shows a screen with the ubuntui logo and an orange status bar at the bottom, the bar moves for about 1 minute and then freezes, then the cd stops turning. Anyone know how to resolve this? Thanks

---

### Post by mrwooster on 2007-01-15
Have done a bit of research - I know there are issues with the core 2 duo, though not sure exactly what the problem is as there is no error message and it freezes within about 1 minute of starting to install.

Thanks

Guy

---

### Post by wysbf2 on 2007-01-15
I have the same issue. I inherited an old P3 machine (without HDD but with plenty of memory) from a friend; installed a new HDD this evening and was able to recognise the new drive and then boot from the Ubuntu CD....but then have exactly the same issue as you when starting the Ubuntu installation. I know from running Knoppix previously that when using a TFT monitor (as I am) you may need to switch the video framebuffer off - so I added fb=false to the boot options, but to no avail.

SB

---

### Post by mrwooster on 2007-01-15
I have used knoppix with no problem, it worked fine (minus a few issues such as the wireless card not working), it booted up correctly with no problems, but ubuntu just freezes with no error message and so am really stuck. If I can't resolve the issue I think I will attempt to install Debian directly.

Any help would be great - thanks

Guy

---

### Post by Pobega on 2007-01-16
> **mrwooster said:**
> Have done a bit of research - I know there are issues with the core 2 duo, though not sure exactly what the problem is as there is no error message and it freezes within about 1 minute of starting to install.

Thanks

Guy

I'm running Core 2 Duo right now, works fine.

Have you tried the alternate install disc yet?

---

### Post by wysbf2 on 2007-01-16
My problem was resolved by attempting a desktop install of Dapper (6.06) rather than Edgy (6.10). The installation tool for Edgy just didn't want to play, no matter what combinations of acpi=off, noapic, nolapic etc I tried.

I was able to boot OK from the Dapper LiveCD, and then to complete the installation to my new HDD. Before attempting the installation to HDD, I wiped some partitions that I had previously created (unwisely) on the drive using Western Digital's provided software.

Now up and running OK....can't wait to explore.

SB

---

### Post by mrwooster on 2007-01-16
Downloading Dapper now - will let you know how it goes. Thanks

---

### Post by mrwooster on 2007-01-16
The dapper cd works fine - I guess thats why 6.10 is called Edgy. The only thing which did not look so good was the resolution. I have an ATI (X1400 i think) card, in the device manager of ubuntu, it recognises it but only just. Do I need to install drivers for ATI to get the correct screen resolution?

Thanks

Guy

---

