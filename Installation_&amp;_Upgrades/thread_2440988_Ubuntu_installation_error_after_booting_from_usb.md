---
title: "Ubuntu installation error after booting from usb"
date: 2020-04-17
forum: Installation &amp; Upgrades
---

### Post by gerrit20 on 2020-04-17
Hi! I'm trying to install ubuntu but i'm definitely not a computer expert. So far i've succeeded to make my usb bootable. But i got stuck when i try to boot from my usb. First i got the ubuntu loading screen, but after that my screen only shows code, which seems very weird (i attached a picture of the code). After this, my screens stays black with the only code "please remove the installation medium, then reboot". The only thing i can do, is to turn off my laptop with the power button. I'm kinda scared i did something wrong, i only followed a youtube video and i have no idea what to do next or how to fix this. Hope anyone can help, thanks in advance for your reaction! :)

---

### Post by dino99 on 2020-04-17
You seems have well donre the installation on the usb. The installer (aka ubiquity) tells you then to remove it before rebooting (this is the usual comment).

Next step is :
- reboot with the usb plugged again (as ubuntu is installed on it), and quickly at the early booting time open your bios to tell him you want to boot from usb (via F2 usually, can be something else for you depending on your system mobo)
- from the bios / uefi boot option, select the usb device, validate, and let the process continuing.

Voila ):P

---

### Post by gerrit20 on 2020-04-20
Thank you for your reaction!! :) 

I tried it two ways, via direct install and try ubuntu. In both ways, the installation screen opens but after a fews seconds, the screen changes to black with the error as seen in the picture i attached. I also tried to disable the secure boot setting but i gives the same problem. Do know what might be a solution for this?

---

