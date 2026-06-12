---
title: "Stuck at &quot;Starting Windows&quot; after installing Ubuntu"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by AdrenaLiNv1 on 2012-06-11
So, here's my situation:

This afternoon I decided to try out BackTrack 5, installed it, all worked fine but it wasn't so friendly so I decided to go with Ubuntu. In the installation process I accidentally set to install the boot manager (GRUB) only on the partition in which I was about to install Ubuntu, I realized that only after being stuck in the "grub rescue" limbo for a while. I reinstalled the whole thing correctly this time, I boot into it and every thing works fine.

When I decided to get back to my Windows 7, for some reason it loads only to a certain point and then stops all of a sudden ( I can tell because the red dot under the power button on the case stops flashing). I've checked the forums, I tried the "Boot-repair-disk" too as it was suggested by someone, I tried running Windows in any alternative mode possible, nothing.

I have a Windows 7 installation DVD but unfortunately it's not the same version as the one I have installed right now, so the repair utilities won't work. I've spend hours trying to solve this, the shops are closed right now (11 pm here), I've downloaded a "repair disk" iso that would work but I don't have blank dvd, that's why I mentioned the closed shops. I've tried using UNetbootin but it doesn't support nfts formats so I can't burn it unto a USB and boot it.

I am desperate, I don't want to install Windows again unless it's my only option.

---

### Post by darkod on 2012-06-11
Did you mentioned unetbootin for creating bootlable usb stick with the win7 rescue cd? You can format the stick as FAT32, it should work out. You don't need the stick as NTFS, if that is the issue.

On another note, after you select win7 from the grub2 boot menu, if you hit F8 does it load the advanced options? Can you try booting in safe mode? Or Last Known Good configuration if it offers that option?

Also, when you try to load win7 as normal, does it give any particular error or it just stops loading? What happens if you wait longer?

---

### Post by AdrenaLiNv1 on 2012-06-11
Thank you for replying.  I tried booting with the USB in FAT32 format, but at the boot menu the only option is "Default" and after selecting it nothing happenes, it just blinks for 0.1 seconds and returns there, if I hit enter again the same thing happenes. I saw somewhere on the forums that a previous version of UNetbootin (495 I think) supported the "Show all devices" option, enableing the selection of nfts devices as well. And yes, as I said, I tried every loading option, those available if the F8 key is hit as well.  While waiting for Windows to load there is no error message or anything alike, all I see is the animation loop of the logo. I've waited for almost an entire hour, but nothing changed.

---

