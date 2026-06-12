---
title: "Safe to upgrade kernel yet?"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by shadowfx78 on 2007-02-20
Have any other bugs been worked out of the newest kernel for Kubuntu Edgy?  i know alot of people were experiencing video issues and I myself experienced sound issues.

---

### Post by Kateikyoushi on 2007-02-20
I doubt it is going to change so you can check the threads how to make your soundcard work after the upgrade or do not upgrade at all, I do not find it crucial.

---

### Post by esaym on 2007-02-20
I have updated 5 kubuntu's.  Haven't had a problem.

---

### Post by undertakingyou on 2007-02-20
I installed the new kernel with reluctance just the other day and didn't have a hickup at all.

The one thread was saying that I'd have to recompile and modules, but I didn't end up having to.

---

### Post by Kateikyoushi on 2007-02-20
That is very hardware dependent and he already stated the problems with his sound.

---

### Post by geira on 2007-02-22
> **shadowfx78 said:**
> Have any other bugs been worked out of the newest kernel for Kubuntu Edgy?  i know alot of people were experiencing video issues and I myself experienced sound issues.

Not as far as I can tell. Two days ago my Thinkpad T60p was functioning almost perfectly (no power saving and Bluetooth). After yesterday's "security update" it's more or less broken. The WiFi card is gone. USB devices (including my mouse) aren't recognized. Sound hangs, causing a chopping noise like a defective CD. And I'm pretty sure the boot error message about my BIOS not supporting PNP wasn't there before. Booting from an older kernel doesn't help, and neither did upgrading the BIOS.

In the "trouble in paradise" sidenote of the otherwise glowing review of Ubuntu in the latest Linux Magazine US it is stated that "Ubuntu has re-doubled its quality control to ensure that such obvious mishaps don't happen again". Guess a re-re-doubling would be in order.

Seriously considering switching back to SuSE, despite the politics.

---

### Post by Xanatus on 2007-02-23
what sound problems are you having ?

---

### Post by geira on 2007-02-27
> **Xanatus said:**
> what sound problems are you having ?

Any sound generated a continous loop of about 10 bleeps per second until I killed ESD.

However I found out all my problems were related to ACPI. As i could never get power saving to work I had disabled ACPI in favor of APM, but apparently ACPI is now more or less mandatory. Re-enabling ACPI fixed the sound and network problems, although suspend and hibernate still causes a system hang on my Thinkpad T60p.

(Note: Suspend and hibernate is apparently supported for this laptop under SLES 10.)

---

