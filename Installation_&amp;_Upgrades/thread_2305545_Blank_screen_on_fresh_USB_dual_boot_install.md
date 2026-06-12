---
title: "Blank screen on fresh USB dual boot install"
date: 2015-12-06
forum: Installation &amp; Upgrades
---

### Post by Abhishek_Madhyasth on 2015-12-06
I'm trying to install Ubuntu 14.04 LTS edition via a bootable USB alongside Windows 8 on my Intel core i3 pc. I manage to get to the stage where I'm asked to select a boot location & I correspondingly select the respective USB drive. That's it. All I get is an empty black screen with absolutely no options. I've waited for almost 40 mins & nothing. I've tried Universal USB installer, Rufus & many others & get the exact same result. The iso itself isn't corrupt though as I've managed to install using Wubi. It's just that the bootable USB just simply won't even start. Could someone help me out here?

Regards,
Abhishek

---

### Post by Bucky Ball on 2015-12-06
Well, it sounds like you are trying to install Ubuntu to the USB you are trying to install Ubuntu from! Where do you want it to end up? On the hard drive? When you say you are asked to choose a boot location, what do you mean? Where to install grub? Where to put the /boot partition (I'd avoid having one). :-k

You don't want to be pointing anything to install to the USB. That is already install media to install Ubuntu to *somewhere other than itself*.

---

### Post by Abhishek_Madhyasth on 2015-12-06
Of course I'm not trying to install it into the USB!8-[ In fact, I'm not even able to reach the point where I can specify an install location.
I was referring to the boot options that you get on pressing F12 at the time of start up(guess I should have been a bit more specific). That's the point where it hangs! I don't even reach the Ubuntu screen. The moment I select USB from the boot options, the blank/black screen pops up & that's it.

---

### Post by Bucky Ball on 2015-12-06
Ah, sorry about the confusion. Wasn't clear, at least to me. :)

Have you tried [UNetbootin]("http://unetbootin.sourceforge.net")? Are you completely wiping the USB by formatting it to FAT32 prior to writing the installer to it?

PS: Don't go near Wubi. It is no longer supported by Canonical or these forums and you will get little to no help with it if you have issues (and whatever you find online will probably be seriously outdated). In this case, though, it does show that the USB seems to be ok.

---

### Post by Abhishek_Madhyasth on 2015-12-07
Yes I have. I make a clean wipe every time. Just as a check, I flashed a version of Linux Mint on the same USB using the same tools & it booted perfectly. I wiped it again & flashed Ubuntu but no luck. It just gets stuck at the boot screen.

The use of Wubi was just to test the package itself & verify that it's not corrupt. I certainly have no intention of installing any version of Ubuntu using it!:)

---

### Post by Bucky Ball on 2015-12-07
Hmm. Very strange. Could you perhaps try creating a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") USB, boot from that and see if you get any further. Just see if the install screen pops up and report back. We can take it from there. :)

If you get through a minimal install, when you reboot, you will be at a CLI with a cursor to login. Simply login and 

> sudo apt-get install ubuntu-desktop

Reboot and you are running Ubuntu. :)

Take note that the minimal MUST be done with an online ethernet cable, not wireless.

---

### Post by Abhishek_Madhyasth on 2015-12-07
I found a rather weird solution to get further. I repeatedly clicked Enter and/or Esc after selecting USB for booting. I got an error message related to ACPI (I couldn't read it as it was displayed only for a brief moment) & then the Ubuntu screen popped up. Now, there's a different problem. When I shut down the live version, the system hangs at the ubuntu logo making me to do a forcible shut down by holding down the power button.

---

