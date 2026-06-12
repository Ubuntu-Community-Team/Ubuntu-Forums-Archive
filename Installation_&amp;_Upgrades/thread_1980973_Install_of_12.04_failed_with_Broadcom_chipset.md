---
title: "Install of 12.04 failed with Broadcom chipset"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Bob Henson on 2012-05-16
I previously had Ubuntu 11.10 running just on my old laptop, but for reasons I need not go into, required a re-install. I tried, more than once, to install 12.04, but hit a problem immediately I tried to boot from the DVD I had burnt. The installer paused with an error relating to the Broadcom B43 WiFi  setup, and then quickly cleared the screen before I could note the exact details, printed one more screen of writing (not related) and then hung totally. I had to hold down the power button to get out of the crash.

I realise I can re-install 11.10 and then upgrade, but I thought that if the devs were reading this they might find the information useful, and thought that someone might have an explanation.

Now, here's the strange thing - exactly the same happened with Linux Mint Debian's latest version - exactly the same point in the install. The earlier LMDE .iso had worked just fine, so I re-installed that one and upgraded. You will gather I'm new to Linux and not at all technical, but there has to be a clue here as to why both Ubuntu and Debian installers should fail when confronted with an older Wifi chipset. Is it to do with Grub? Or is it a newer installer, similar in both distros? Or is it releted to the newer kernels?

Regards,

Bob

---

### Post by darkod on 2012-05-16
Looks like you are affected by this bug:
[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

As explained there, you need to temporary blacklist the b43 and after you install ubuntu you will install the correct driver.

---

### Post by Bob Henson on 2012-05-16
> **darkod said:**
> Looks like you are affected by this bug:
[http://ubuntuforums.org/showpost.php?p=11883375&postcount=6](http://ubuntuforums.org/showpost.php?p=11883375&postcount=6)

As explained there, you need to temporary blacklist the b43 and after you install ubuntu you will install the correct driver.

Thanks very much - that did it. I did a bit of searching but I obviously didn't look far enough! As it's a known problem I'll mark this solved, as it obviously soon will be.

Thank you,
Regards,

Bob

---

