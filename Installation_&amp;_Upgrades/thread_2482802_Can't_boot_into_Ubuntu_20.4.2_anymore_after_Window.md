---
title: "Can't boot into Ubuntu 20.4.2 anymore after Windows 10 Updates over the last 2 years"
date: 2023-01-11
forum: Installation &amp; Upgrades
---

### Post by xaodhjksa on 2023-01-11
Hello everybody,

I hope this is the right sub-forum for this. Please tell me if I should use an other one instead.

I have problems booting into Ubuntu 20.04.2 after 2 years of doing Windows updates without thinking about my Ubuntu partition.
Log files from boot-repair (also tried running it with default settings, didn't help to fix the problem): [https://paste.ubuntu.com/p/V3qZbCGtDG/](https://paste.ubuntu.com/p/V3qZbCGtDG/)

I think the problem lies in the fact I have two EFI partitions and maybe that got messed up by multiple Windows Updates over the last years (I didn't touch the Linux partition for like 2 years before investigating this issue).
 
UEFI is configured to boot on ESP of the HDD with Grub, and in the Grub Menu I have an item for the Windows Boot Manager, which is probably chainloading the ESP of the SSD. I think this should be visible in the pastebin.

Best regards,
Martin

---

### Post by tea for one on 2023-01-11
Line 89 - Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (sdb2/efi/ubuntu/grubx64.efi file) !
Line 90 - If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware

Did you try to boot your sdb disk via the PC boot menu (i.e. using the dedicated key F10 or F12 etc)?

---

### Post by xaodhjksa on 2023-01-11
> [COLOR=#000000]Line 89 - Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (sdb2/efi/ubuntu/grubx64.efi file) ![/COLOR]
How do I make sure, that UEFI firmware is booting on the right entry? I can just overwrite boot order or specifically boot into disk.

[COLOR=#000000]> Line 90 - If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware
[/COLOR]This is working fine, grub is showing up with ubuntu and windows to select

[COLOR=#000000]> Did you try to boot your sdb disk via the PC boot menu (i.e. using the dedicated key F10 or F12 etc)?
[/COLOR]Yes, I tried to boot directly into my sdb disk by overriding the boot order temporarily. Unfortunately Ubuntu won't start, it is freezing directly at the boot process where this loading animation is played.

---

### Post by tea for one on 2023-01-11
When you reach Grub, can you select Advanced Options > Recovery?

---

### Post by xaodhjksa on 2023-01-11
Yes, I can select Recovery-Mode for two kernel versions. (5.8.0-53/55-generic).

I will try to boot in recovery mode - maybe that works. How should I continue then?

Edit: I tried to boot into recovery mode for the  x.55 kernel and got the following error: `Bluethooth: hci0: unexpected event for opcode 0xfc2f`

Picture: [https://imgur.com/a/nZaumkg](https://imgur.com/a/nZaumkg) (sorry, Imgur compresses it alot - I can also upload it somewhere else.) Boot process freezes right after this error.[IMG]https://imgur.com/a/nZaumkg[/IMG]

---

### Post by xaodhjksa on 2023-01-11
Strangely, I can actually boot into recovery mode on x.53 kernel.

Edit: When I boot into recovery mode on kernel 53, then click on resume, I can actually boot into Ubuntu, but I guess graphic drivers are not loaded correctly and maybe they are the problem? But why do I get Bluetooth errors then?

---

### Post by tea for one on 2023-01-11
Some progress made now.
Can you boot into Ubuntu using kernel 5.8.0-53 without recovery mode?

---

### Post by xaodhjksa on 2023-01-11
Thank you very much for the help.
 
That worked and I was able to update Ubuntu there and this fixed all the issues. Now I can use the default Ubuntu grub entry again.

How can I close this? Nvm, found it.

---

