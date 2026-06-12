---
title: "GFX Card install - Nvidia GTX550 ti"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Taboo Tongue on 2012-05-30
Ey, I'm upgrading from an ATI card (using the default\open source drivers) to an nVidia GeForce GTX550 Ti.
I have enough power plugged in to it
And I am using the VGA to DVI converter that came with the card.

I'm running Ubuntu Studio on a 64bit system in the XFCE desktop enviroment.

**I tried just swapping out the hardware and it gave me a blank screen with a [fast] flashing underscore _ . Where it hangs up after the GRUB menu.**
I tried installing the propreitary nVidia drivers with my old ATI card in, and was informed that I didn't have a compatible nVidia card plugged in (which is of course true).
I couldn't figure out how to install the Nouveau drivers, but seeing as how I want to play Diablo III, I think I will need the proprietary ones anyhow.

Thank you! =)

---

### Post by bogan on 2012-05-30
Hi!, **Taboo Tongue,**

With The nvidia card installed, select the ubuntu entry you want - presumably 12.04 - and press the 'E' key to get into script editing mode.

Use the arrow keys to move to the line beginning with 'Linux', and along it to " ro ", insert "nomodeset" - with a space each side of it. The rest of the line will probably read " quiet splash".

Then press 'Ctrl+x' to boot up.

If this works it can be made permanent by editing the /etc/default/grub file and altering the line: GRUB_CMDLINE_LINUX="" to read: GRUB_CMDLINE_LINUX=" nomodeset" ```
gksu gedit /etc/default/grub
``` And, after saving , running: ```
sudo update-grub
```Chao!,** bogan**.

---

