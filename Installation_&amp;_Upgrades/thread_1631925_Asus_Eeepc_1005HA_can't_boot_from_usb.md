---
title: "Asus Eeepc 1005HA can't boot from usb"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2010-11-27
Hi, this has been an issue with me for a long long time, I can't get my Asus Eeepc 1005HA to boot from usb so as to re install Ubuntu. I did it right once - obviously -  and now have a malfunctioning dual boot partition. My memory is of having to hit a function key repeatedly once I'd changed the BIOS and restarted the computer. Asus forums all repeatedly give me the same advice - F2 for BIOS, F10 to save settings then it should boot up, but --- nothing --- works. 

So. Any additional or creative advice? The computer doesn't have a CD drive. My thumb drive is a Delkin 4gig... are there thumb drives known to work for this operation? thanks...

---

### Post by gordintoronto on 2010-11-27
Almost all thumb drives are OK. Some thumb drives come with backup or encryption software which interferes with "proper operation."

Have you tried Del or Esc or F11 or F12 at boot time?

I leave my computer set to boot from, first, a thumb drive, then from CD/DVD, then from the hard drive. If the first two aren't present, it boots normally.

---

### Post by onekama_michigan on 2011-04-28
> **arnicainthemembrane said:**
> Hi, this has been an issue with me for a long long time, I can't get my Asus Eeepc 1005HA to boot from usb so as to re install Ubuntu. I did it right once - obviously -  and now have a malfunctioning dual boot partition. My memory is of having to hit a function key repeatedly once I'd changed the BIOS and restarted the computer. Asus forums all repeatedly give me the same advice - F2 for BIOS, F10 to save settings then it should boot up, but --- nothing --- works. 

So. Any additional or creative advice? The computer doesn't have a CD drive. My thumb drive is a Delkin 4gig... are there thumb drives known to work for this operation? thanks...

you need to disconnect power and disconnect battery.  then, put battery back in and restart while pressing F2.  For some reason, due to quickboot the eee doesn't recognize you pressing F2.  Turn quickboot to disabled and you won't have the problem again.

I had same problem and found the answer above on other forums.

Now I wish I could get the eee pc to recognize the usb CD drive so I can reinstall ubuntu.  Every time I do this I need to use an SD card to rebuild the machine rather than an external USB CD drive.  The USB never seems to show up on the boot order menu, even if I press ESC to pick an alternate boot method.

---

