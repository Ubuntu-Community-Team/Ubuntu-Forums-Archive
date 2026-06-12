---
title: "Problem installing Ubuntu Server 16.04 LTS on Quanmax Qbox-100s"
date: 2016-07-13
forum: Installation &amp; Upgrades
---

### Post by hiphil on 2016-07-13
Hi,

I've installed Ubuntu on a qbox-100s, and everything worked fine until the final reboot. The system will start booting, a couple of text lines flash by really fast, and then the screen goes black and the monitor enters standby. I've tried switching from HDMI to VGA but it doesnt make any difference. Any help would be appreciated.

Br,
Phil

---

### Post by hiphil on 2016-07-13
I've tried so far: 
1) booting into recovery mode (same error)
2) changing the boot params from
linux /boot/vmlinuz-4.4.0-21-generic.efi.signed root=UUID=377584a5-46a2-40a8-9dcs-337359009149 ro
to
linux /boot/vmlinuz-4.4.0-21-generic.efi.signed root=UUID=377584a5-46a2-40a8-9dcs-337359009149 ro nomodeset
but same error happens

---

### Post by hiphil on 2016-07-19
Okay, i managed to make the screen stop dissapearing, edited boot params i added this: (...) [COLOR=#111111][FONT=Consolas]quiet splash acpi=off nolapic nomodeset (...)
Not it boots until it gets to "Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000009

Kernel offset: disabled
End Kernelpanic

then it hangs. It's a fresh install i did not change any libs etc. what might be causing this?[/FONT][/COLOR]

---

