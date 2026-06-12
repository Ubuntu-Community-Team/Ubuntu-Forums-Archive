---
title: "Can't fully boot Ubuntu."
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by drew31 on 2015-06-11
Installed Ubuntu today (twice, first time I didn't get passed a purple screen). Now I can boot up until it asks for me to "enter passphrase" but the problem is whenever this prompt activates, my keyboard and mouse stop functioning... Every time. Same problem happens when I enter recovery mode. Help!

---

### Post by v3.xx on 2015-06-11
This an older computer?  Using a usb keyboard/mouse?  Look for a BIOS setting for the keyboard if this is so.  Called something like 'Legacy USB Devices'.

---

### Post by drew31 on 2015-06-22
No, the computer is brand new with USB keyboard and mouse, I also tried switching around the legacy/ UEFI settings in bios but it dosent seem to help anything.

---

### Post by Bashing-om on 2015-06-22
drew31; And 

Additional thought ; in bios enable "plug and play" . My system's bios - Phoenix - has this setting, and I must enable it for USB mouse .

[INDENT][INDENT]it all begins in bios 
[/INDENT][/INDENT] .

---

### Post by Geoffrey_Arndt on 2015-06-23
A candidate for nomodeset boot parameter?    What are hardware specs especially graphics info?

---

### Post by Bucky Ball on 2015-06-24
> **Geoffrey_Arndt said:**
> A candidate for nomodeset boot parameter?

Yes, it is, so let's try that.

When you boot to the list of kernels, highlight the one you want to boot and hit 'e' to edit. Find the line that ends:

```
quiet splash
```

Or any one or combination of those two words. At the end, add 'nomodeset', so the end of that line looks like:

```
quiet splash nomodeset
```

Follow the instructions at the bottom of the screen to save and reboot. Any luck?

This is not a permanent change. Once you reboot the 'nomodeset' option will be gone, so if it does work, let us know and we can show you how to make the nomodeset option permanent.

---

