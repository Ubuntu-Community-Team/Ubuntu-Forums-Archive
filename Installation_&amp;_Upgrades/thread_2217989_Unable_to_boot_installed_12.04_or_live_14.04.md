---
title: "Unable to boot installed 12.04 or live 14.04"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by philip10 on 2014-04-19
CPU: AMD FX-8350
MOBO: M4A89TD PRO/USB3
GFX: ATI Radeon HD 7850
Storage: 4x HDD in RAID0 dual booting Win 7

Last year I upgraded from an AMD phenom II x3 720 BE to an AMD FX-8350. After this upgrade I was no longer able to boot into my Ubuntu 12.04 partition. The last thing that shows up in the console is "Freeing initrd memory: 14108k freed".
- If i press e in the grub menu and add "nomodeset apci=off" to the end of the linux line and then press ctrl+x, it removes some ACPI entries but still gets stuck on "Freeing initrd memory:"
- Unplugging all USB devices including the keyboard doesn't help either.

Now I have decided to install ubuntu 14.04 but I'm having problems with that as well. The only thing I see in the top left corner of the screen is a white flashing cursor. Keyboard doesn't seem to respond either.
I have tried the following:
- Unplugged all USB devices including the keyboard | no difference
- Pressed any key as soon as the purple screen with keyboard icon appears, disabled lapci, apci, and checked nomodeset. | now I see a low res purple ubuntu screen with dots that change colour to form a loading bar. Keyboard is responding but the purple loading screen never disappears.
- Removed all instances of "quiet splash" from isolinux\txt.cfg | no difference
- Played around with various bios options including PnPOS, ACPI, and resetting to factory settings | no difference

I have also tried to setup a virtual box to ensure my DVD is ok. I'm unable to create a 64bit guest though.
- Changed the bios option "Secure Visualization" to enabled and disabled | no difference.
- Unable to find *.vbox-prev in my virtual box install directory.

Any advice for getting Ubuntu 14.04 up and running would be appreciated.

---

### Post by philip10 on 2014-04-20
[COLOR=#ff0000]Bottom line: 
- Download ubuntu server 14.04 x64.
- Boot up the iso
- Press F6 and check "nolapic"
- Install ubuntu server
- Login and type "sudo apt-get install ubuntu-desktop"
- Restart the computer.
[/COLOR]
Ok I figured it out :D [COLOR=#ff0000](solution above)

[/COLOR]The option I needed to add in order to boot my existing 12.04 installation was "nolapic". This option can be set by pressing e on the grub menu and typing "nolapic" without quotations at the end of the line that starts "linux ..."

I was still unable to boot the ubuntu desktop dvd for some reason even though It seems to work in a friends computer. The solution for that is to install ubuntu server and then desktop on top of that.[COLOR=#ff0000]

[/COLOR]So far 14.04 appears to be extremely snappy and tidy. Nice work.[COLOR=#ff0000]
[/COLOR]

---

