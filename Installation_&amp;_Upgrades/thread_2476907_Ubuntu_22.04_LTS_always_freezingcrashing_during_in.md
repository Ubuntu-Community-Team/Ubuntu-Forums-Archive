---
title: "Ubuntu 22.04 LTS always freezing/crashing during installation (Win10 Dual boot)"
date: 2022-07-11
forum: Installation &amp; Upgrades
---

### Post by nickdv99 on 2022-07-11
I've been trying my bloody hardest to get Ubuntu 22.04 LTS installed on my system alongside Windows 10, and failing every single time. I'm completely out of ideas and hoping someone here can help me. Let's start with system specs:


[TABLE="width: 500"]
[TR]
[TD]**Component**[/TD]
[TD]**Name**[/TD]
[/TR]
[TR]
[TD]CPU[/TD]
[TD]AMD Ryzen 9 3900x[/TD]
[/TR]
[TR]
[TD]Motherboard[/TD]
[TD]MSI MPG B550i Gaming Edge WiFi[/TD]
[/TR]
[TR]
[TD]SSD (Primary)[/TD]
[TD]Sabrent Rocket 4.0 1TB NVME[/TD]
[/TR]
[TR]
[TD]SSD (Additional Storage)[/TD]
[TD]Crucial P2 1TB NVME[/TD]
[/TR]
[TR]
[TD]Graphics card[/TD]
[TD]Nvidia GeForce RTX 3070 Founders Edition[/TD]
[/TR]
[TR]
[TD]Memory[/TD]
[TD]Klevv Bolt X 32GB (2x16GB) DDR4-3200 CL16[/TD]
[/TR]
[/TABLE]

My attempted method at installing:
[LIST=1]
[*]Prerequisites:
[LIST=1]
[*]Ensure secure boot and fast start-up are disabled
[*]Set BIOS to UEFI-only mode and set partition table to GPT
[*]Shrink my Windows 10 partition by 100GB to ensure there is enough space available on my primary SSD
[*]Disconnect my additional SSD
[/LIST]

[*]Flashing a USB:
[LIST=1]
[*]Flash Ventoy to a brand new 8GB USB stick
[*]Drop the Ubuntu 22.04 LTS ISO onto it (hash checked)
[/LIST]

[*]Boot my system from the USB stick
[*]Select the Ubuntu ISO in the Ventoy splash screen
[*]Select "Safe graphics mode" (note: I have also tried using the default graphics mode)
[/LIST]

Now, usually one of the following will happen:
[LIST=1]
[*]Infinite loading spinner on the Ubuntu splash screen
[*]Splash screen freezes with loading spinner
[*]Splash screen freezes after loading spinner disappears
[*]Installation crashes with command line output mentioning kernel panic ([example]("https://photos.app.goo.gl/Porx2XSHoUUFCSTr7"))
[*]Installation crashes with command line output mentioning soft lockups with CPU cores getting stuck ([example]("https://photos.app.goo.gl/LSQS799uuyUuMqeV9"))
[*]Desktop loads and lets me get part way through the installer before freezing
[*]Desktop loads and lets me get almost to the end of installing (status bar nearly full) before freezing ([example on 20.04]("https://photos.app.goo.gl/NJbNbfqXR4YqsY4BA") but this has happened on 22.04 in an identical fashion)
[*]Splash screen disappears and cursor appears, but freezes entirely
[/LIST]

I have tried everything I can think of. I've ensured I have only one monitor plugged in. I've unplugged every single USB device except for my mouse, keyboard, and Ubuntu USB stick. I've tried running it on my girlfriend's PC (i3 9100F and Nvidia GeForce GT 1030 with 8GB RAM) and it worked flawlessly.

I am completely at a loss. Can anyone help me figure this out?

---

### Post by ubfan1 on 2022-07-11
Have you checked the vendor for any BIOS/firmware updates?  Those can solve many problems.

---

### Post by nickdv99 on 2022-08-04
Updated the BIOS and that fixed it. Typing this from my fresh new Ubuntu install. Thank you so much for your help!

---

