---
title: "Installing on SD Card"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by AndrewD2 on 2009-11-27
I've had a crazy idea recently, not wanting to change too much on mine and my wife's shared laptop I was thinking about trying to install Ubuntu onto a spare 8GB SD Card I have.  Setup Grub on the MBR of the primary hard drive and have Windows set as the primary loading OS and have the option of selecting Ubuntu from the menu and just insert the SD card when I want to use it.

I guess the major question being is there any reason this wouldn't work?

Thanks,
Andrew

PS
Sorry I wasn't sure if this fit in hardware or installation so I went with posting here..

---

### Post by snowpine on 2009-11-27
It will work fine. I have done it many times.

Personally, I prefer to install Grub on the SD card (via the Advanced button on the last step of the installer). That way, the internal drive is completely unmodified. To boot, I press Esc (on my eee; the specific key you press depends on the bios) and choose the SD card or the internal drive, depending on whether I want Ubuntu or Windows. That is just a preference, though... you could put Grub on the internal drive if you prefer.

Just be forewarned, it will be slower than a regular hard drive install.

---

### Post by AndrewD2 on 2009-11-27
The only reason I wasn't considering putting grub on the SD Card is that the bios do not appear to find the sd card slot as a boot option.  I had tried it with a live setup on the SD card and it would run fine off of the USB (it's a SD/USB card where you can fold the end back and it has a USB plug built into the card) it just wasn't seen as SD so I figured grub would be able to tell it to look at 'sdb' which is where the card showed up when mounted in a live cd.

Although now I'm considering just resizing the windows partition when I do a reinstall.  But I am trying to figure this out for a future endeavor still.

---

