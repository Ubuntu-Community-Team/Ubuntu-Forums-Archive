---
title: "Unable to boot linux with USB drives connected"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Gianvacca on 2008-02-21
My laptop DVD drive is not working very well anymore, and booting is sometimes a pain, especially installing (it takes a very long time when it doesn't fail). So I would like to use my perfectly fine USB DVD drive.

However, as soon as it loads the kernel the system freezes in a very depressing full black screen. The same thing happens if I boot from the internal hard disk with any plugged USB drive (pendrive, 300 GB USB hard disk or the metioned above USB DVD writer). It's not a problem of boot priority. I get the splash screen and the multiple choice menu, but as soon as it finishes to load the kernel, I get a black screen of death. I can only switch off and on again unplugging all the USB drives (not any general USB device, only drives).


It's a general Linux problem. I get the same outcome also with other distros, but I don't get it when booting into Windows or DOS.

My motherboard is Uniwill 755IA5. My laptop is a Fujitsu-Siemens Amilo D 7830.

I hope someone can help. Are there any parameters I can pass to the kernel?

---

### Post by dstew on 2008-02-21
I agree this seems to be a problem with the kernel interacting with the USB hardware on your system. Since USB support is compiled into the generic kernel, I don't think there are any kernel parameters that could or need to be used. A couple of thoughts: What kernel are you using? If it is a custom kernel, then it might be fixable. If it is the standard generic kernel, then probably it is not fixable. Are you sure you have the correct kernel for your hardware?

Another possibility is that you are using a kernel parameter that interferes with the boot when USB drives are present. Do you have any parameters on your kernel line, other than the usual quiet nosplash?

You could try some other kernel parameters. Maybe the problem is with other systems that indirectly affect the USB system. Other kernel parameters to try are noapic nolapic acpi=off irqpoll

---

### Post by petteriIII on 2008-02-21
Is there 'legacy USB support' in Amilo ? Try and disable it.

---

### Post by Gianvacca on 2008-02-21
I tried to append some parameters to the kernel but it didn't work.

I never tried to disable the legacy support. I'll let you know.

---

### Post by Gianvacca on 2008-02-21
PetteriIII, you are a star!

THANK YOU! That was the problem! The legacy has to be disabled!

---

