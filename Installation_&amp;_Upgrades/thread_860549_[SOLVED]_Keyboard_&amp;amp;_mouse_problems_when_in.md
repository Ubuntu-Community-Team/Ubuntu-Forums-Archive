---
title: "[SOLVED] Keyboard &amp;amp; mouse problems when installing Ubuntu 8.04"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by ivancaa on 2008-07-15
I recently bought a new Acer Aspire M3640 with the following components:

Processor: Intel Core 2 Quad
Q9300 @ 2.50GHz
RAM: 4GB
OS 32 bits
Graphics card: ATI Radeon HD 3450
Keyboard & Mouse: Standard PS/2

I tried to install Ubuntu 8.04 and couldn't. Everything seems to work fine when I insert the LiveCD, the splash screen shows where I can select installation language normally, and then the next screen shows where I can choose installing Ubuntu or running it from the LiveCD. Everything runs smooth until that moment, but when I select any of the two options (installing Ubuntu or running it from the LiveCD) it all freezes in the "Loading Bluetooth" line and then the following error messages begin to show:

(150.311385) usb 1-9 device not accepting address 6 error -110

Four messages like this one appear and then, the system seems to run correctly but, when finally Ubuntu Desktop loads (this only happens when I run Ubuntu from the LiveCD, not when I install it), the keyboard and mouse do not answer anymore and there is nothing else that I can do. It looks like the problem is exclusively with the keyboard & mouse, because everything else seems to work fine. At that point, with keyboard & mouse not responding, the only thing that I can do is shut the PC down pushing the Power button, and then the tray ejects and a message shows telling me to take the CD out, close the tray and press Enter. Not even at that point the keyboard seems to respond, because when I press Enter nothing happens.
It is a strange thing because, as I said, the keyboard seems to work fine in the first two screens, where I can select language and install type, but after those screens the keyboard & mouse do not work any more.

Keyboard & mouse are standard PS/2 and work fine in Vista.

Thanks

---

### Post by ivancaa on 2008-07-18
I managed to solve the problem and now I have Ubuntu correctly installed in my machine. Here's what I did:

In the initial LiveCD screen, I pressed F4 and selected **Safe Graphics mode**.
In that same screen, I pressed F6 to edit boot options and added **acpi=off** at the end of the line.
After that, I selected Install Ubuntu, and everything was OK.

---

### Post by Wizzykin on 2008-07-18
I'm going to give this a shot - thanks. I've been having the same problem and no one has been able to help me yet (and most posts go unanswered even... No wonder people are shy about moving to linux, you get an error and not even the official developer board will help you out...)

edit: still not working. Ah well, thanks for posting what fixed it for you. That's better than what most people have done so far with this issue. This OS is seeming less and less worth the hassle. I'll just stick with one I can actually install. I really wanted to try Cinellera, though :\

---

