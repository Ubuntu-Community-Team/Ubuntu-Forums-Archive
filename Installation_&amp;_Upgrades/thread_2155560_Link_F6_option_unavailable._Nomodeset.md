---
title: "Link? F6 option unavailable. Nomodeset"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by Cocolate on 2013-06-18
Usb installation 10.04
Install ubuntu
Loading screen / start up
. . . . Ubuntu . . . .

Blank black screen.

Hold shift on splash
No keyboard logo
Goes straight from BIOS to "install or run ubuntu"

Hit F6
<boot>:

Graphics card: AMD Radeon HD 6320 Discrete-Class Graphics Supports DVI with max. resolution up to 1920 x 1200 @60Hz 

CPU: AMD Dual-Core processor E-450 with AMD Radeon HD 6320 

Chipset: AMD FCH A50M (Hudson M1)


My recources for Internet usage is horrible right now. Is it possible anyone can link me or advise me on the method to get this to run? I believe I need nomodeset but I am not given the option to hold shift? Any gelp please?

---

### Post by Bashing-om on 2013-06-18
[COLOR=#000000]Cocolate; Hi ! Welcome to the forum .

Think we need a separation between booting in the liveUSB environment and the real install environment understanding.

liveUSB to get boot options menu: In bios set usb as the 1st boot priority -> boot the usb drive and as soon as the bios screen clears, depress and hold the shift key -> language screen, escape to accept the default -> boot options screen -> f6 key for the preset boot options.

installed system: hard drive set as 1st boot priority in bios, when bios screen clears depress and hold shift key -> grub boot menu -> "e" key for edit mode , -> booting parameters screen -> arrow down to the line similar to this " [/COLOR]linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" -> arrow across to the term "quiet splash" and insert the term "nomodeset" -> ctl + X to continue the boot process to your installed desk top.
[COLOR=#000000]
If you are successful in getting to your GUI desktop using the "nomodeset" option then it may prove real difficult to get you a "woking" graphics driver as 10.04 version is no longer supported... and do not know what will be the result of attempting to find/install a graphics driver.

There are any number of alternatives in current supported versions. Just asking, Why do you want to install something that is no longer supported ? [INDENT=3]

hope this helps [/INDENT]

[/COLOR]

---

### Post by Cocolate on 2013-06-19
Hi Bashing :)

A very big thank you for the response. Im in somewhat of a doozy perdicament in regards to Internet connection and compatibile devices: New apartment, new hardware.

OT: thats exactly the trouble Im experiencing. Depressing SHIFT>esc>F6 isnt computing. There is no screen flash between Bios load screen, and Ubuntu load screen. It goes immediately from Bios>Ubuntu =thus no "keyboard/little man" logo (flash screen. Is that called Splash screen?)

Anyhow, my motherboard has a UEFI asus Bios  idk  that may have some direct result of my problem.

Also I prefer Ubuntu 10.04 layout. *sigh* Ive installed it a dozen times a few years back no problem. I thought if anything I would be able to run liveUSB and fix these issues myself, but here I am stuck at load screen. 

Thanks for your advisement.

Frustrated booboo,

Cocolate

---

### Post by Cocolate on 2013-06-19
UEFI asus Bios boot loader 1st 2min [https://www.youtube.com/watch?v=9u8sJ8zS4C8&feature=youtube_gdata_player](https://www.youtube.com/watch?v=9u8sJ8zS4C8&feature=youtube_gdata_player)

---

### Post by arpanaut on 2013-06-19
10.04 does not have support for uefi built in you will need to use 12.04.2 12.10 or 13.04 64 bit to get uefi support.

---

### Post by Cocolate on 2013-06-19
Solved...........^^^^^

---

