---
title: "Can't install Lubuntu due to boot/BIOS issue"
date: 2019-02-07
forum: Installation &amp; Upgrades
---

### Post by johandeboer on 2019-02-07
I have an old HD with on it Ubuntu 12.04. It never was updated further due to hardware limitations and as it worked perfectly. When the hardware finally became terminally I took out the HD and placed it in a same-like PC, only to discover that the hardware was of a lower standard (processor, RAM). The PC works, but it is so slow that you just know it is too much for him to cope with. So I decided to first save all data (done) and then install a newer yet much lighter Linux/Ubuntu distro.
So I made a bootable USB stick with Lubuntu 18.10 32bit on it. Unfortunately, when I tried to enter the BIOS/boot menu I discovered that it is protected by a password, so I cann't let it boot from the USB stick.
I so far have tried 2 ways to solve the problem:
1) try to find out how to get around the password. Failed as my Ubuntu and Linux knowledge is too limited, as I don't want screw around in my hardware, and as it all was simply too complicated: I am a user, not a knowledge expert.....
2) try to find a way to install Lubuntu directly through a so-called netboot: so install the whole thing directly from a download. Failed as I could not find such, only more heavy Ubuntu distro's were found for a netboot.

So my question is simple: is there anybody who can tell me how to install Lubunto 18.10 32bit (or 18.04 32bit if you think that will work better), without access to BIOB/boot menu ?

---

### Post by yancek on 2019-02-07
A password in the BIOS has nothing to do with Ubuntu or your operating system but is on the system board.  Someone had to have created the password.  You might post what hardware you have (manufacturer?) or do an online search for changing the password in the BIOS of that specific machine.

---

### Post by CatKiller on 2019-02-07
> **johandeboer said:**
> Unfortunately, when I tried to enter the BIOS/boot menu I discovered that it is protected by a password, so I cann't let it boot from the USB stick.

That has nothing to do with the operating system that's installed.

If you're lucky you'll have a BIOS reset button that will reset the BIOS to defaults, including the password. If you're less lucky you'll have a jumper you can set to do the same thing.

Otherwise you'll need to unplug it, find the watch battery that maintains the settings when there's no power and remove that, and then press the power button to discharge it. Then put the battery back and plug it in again.

---

