---
title: "kernel is pointing to the wrong headers."
date: 2023-08-28
forum: Installation &amp; Upgrades
---

### Post by eje2112 on 2023-08-28
I updated... something. There were some modules that required manual fixing because they were not part of [FONT=courier new]dkms[/FONT], so I did that. It all looked very minor.  I installed [FONT=courier new]linux-headers-6.2.0-24-generic[/FONT] over [FONT=courier new]linux-headers-6.2.0-20-generic[/FONT]. While I was at it, I also upgraded the nVidia graphics drivers and lost my graphics. (That's not what I'm writing about here though.)

When I rebooted, I had no network. It turns out that the module for my ethernet device, [FONT=courier new]igc[/FONT], is in [FONT=courier new]linux-headers-6.2.0-20-generic[/FONT] but *not* in [FONT=courier new]linux-headers-6.2.0-24-generic[/FONT]. What's up with that? The problem is that I can't figure out how to get Ubuntu to go back to using [FONT=courier new]linux-headers-6.2.0-20-generic[/FONT]. I tried [FONT=courier new]apt install --reinstall linux-headers-6.2.0-20-generic[/FONT]. It did not work. I could put a softlink from [FONT=courier new]linux-headers-6.2.0-24-generic[/FONT] to [FONT=courier new]linux-headers-6.2.0-20-generic[/FONT] but sounds like begging for big trouble.

Is there a clean, official way of doing this? I looked and I couldn't find anything.

For the [FONT=courier new].deb[/FONT] files, I'm moving them from my laptop to my desktop with a USB stick.

---

### Post by MAFoElffen on 2023-08-28
I don't understand what you did that for and why(???) Up until today, the current HWE kernel was 6.2.0-26, which had a few challenges that were fixed in today's kernel update, which is now 6.2.0-31...

What you just posted doesn't match any of those.

To top that off, the installed kernel header file needs to match the version of linux-generic, linux-modules and linux-modules-extra

---

### Post by eje2112 on 2023-08-29
I figured it out. All I had to do was go to the "advanced" part of the boot menu and select the correct kernel version there.

---

### Post by ajgreeny on 2023-08-29
And which version was that?

What you've said doesn't quite make sense as grub normally chooses the correct most recent kernel,  and that version would pull in the correct header packages as dependencies.

---

