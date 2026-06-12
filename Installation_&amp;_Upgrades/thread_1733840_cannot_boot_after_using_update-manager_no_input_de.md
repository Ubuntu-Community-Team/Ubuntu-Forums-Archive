---
title: "cannot boot after using update-manager: no input detected"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by alex86 on 2011-04-19
I am new to Ubuntu, using a rather incompatible laptop (Gateway ID49C) with 10.04; by this I mean that I have problems with sound output, brightness control, keypad functionality, occasional freezes, etc.

Anyway, the Update Manager popped-up last night, proposing me to download some 400 Mbs of "updates" to installed programs, I presume. I told him to go ahead. After downloading, it proceeded to install the updates, and I left the computer unattended. Hours later, I came back to find the computer hibernating: it woke up to show me update manager freezed on some grub update, to my horror.

I shut it down. Now, whenever I try to boot, I find a very low quality 10.04 text with four white dots that "fill up" as it boots (instead of the fancy logo), then the user selection thing pops-up. No response from keyboard or keypad. Howver, the system is NOT frozen, since the visible clock actually works. 

I can access GRUB (I have a dual boot) but the recovery mode does not work: it freezes at some point.

I don't even know how to get started...Any help appreciated.

Thanks in advance guys

---

### Post by Dutch70 on 2011-04-19
Do you get a grub menu? I can't remember for sure, but I think it's the shift key to bring it up if you only have Ubuntu installed. Try to bring it up and choose an older kernel to log in to.

---

### Post by alex86 on 2011-04-20
Yes, I do get the GRUB menu, but then what? The options I get are for memtest, Windows, Ubuntu, and Ubuntu Recovery. My guess is that I should edit some boot parameters, since its my only way to communicate with the system, but I really don't know what I am supposed to edit. Or how. I know that pressing the "e" key lets me edit some stuff, but that's as far as I go.

I don't have an "older" kernel...or maybe I'm not understanding you.

---

### Post by Dutch70 on 2011-04-20
Maybe this will help.
[[COLOR="RoyalBlue"]How to set NOMODESET and other kernel boot options in grub2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by alex86 on 2011-04-21
It did not, thanks anyway. Nomodeset caused a blank screen, noapic and nolapic caused white squares to appear in a corner of the screen and in place of the login screen, acpi_osi and acpi=off changed nothing.

Do you think recovery mode is useful? When I boot on it, I get a long list of echoes of stuff happening, and then it stops in one of either two possible scenarios, the difference being that in one of them, there are additional lines, which I put in italic. The last lines are

[I]
[     4.646511] EXT4-fs(sda5): INFO: recovery required on readonly filesystem
[   4.646566] EXT4-fs(sda5): write access will be enabled during recovery
[     4.646537] EXT4-fs(sda5): recovery complete [/I]
[     4.646893] EXT4-fs(sda5): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ...
Done
Done
Begin: Running /scripts/init-bottom
Done
_(blinking cursor)

The numbers may not be accurate. Then nothing happens, I cannot input anything, however ALT+CTRL+DEL works just fine and reboots smoothly.

Any other ideas?  Thanks

---

### Post by Dutch70 on 2011-04-21
I'm just about out of ideas. :)

Can you boot to the live cd/usb environment & does it work well?

Not sure if this makes a difference at this point, but did you check the cd/usb for defects?

Another less likely thing could be the md5sum of the downloaded .iso. Although I don't think you would have gotten far if it didn't match perfectly, it may be worth checking.

---

### Post by alex86 on 2011-04-26
I have not yet tried the live cd, because I don't have one and have problems burning one. I will let you know as soon as I give it a try. I am hoping to be able to boot with it and complete the updates, that might fix the problems...

---

### Post by alex86 on 2011-04-28
Ok, problem fixed! I simply attached a USB keyboard when at the login screen, and even though the display was terrible and the performance poor, I executed 

```
sudo apt-get -f install
```

which settled the matter definitely.

Thanks!

---

### Post by Dutch70 on 2011-04-28
Nice work!

---

