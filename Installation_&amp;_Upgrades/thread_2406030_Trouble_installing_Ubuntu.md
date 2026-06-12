---
title: "Trouble installing Ubuntu"
date: 2018-11-14
forum: Installation &amp; Upgrades
---

### Post by champe on 2018-11-14
Hello all,

I've had no problems using a USB to install Ubuntu on my laptop, but it seems there is no easy way to do it with my desktop. Even with the same USB I used for my laptop, I either get black screens or it hangs up on the purple screen with the Ubuntu logo

What I've tried so far:
[LIST]
[*]Upgrading to the latest BIOS
[*]Disabling fastboot
[*]Different USB sticks
[*]Verifying integrity of the download(s)
[*]Attempting with 16.04 and 18.04
[*]"Try Ubuntu" instead of jumping straight to installation
[*]Nomodeset
[*]Replacing my PSU (seemed to work for someone else)
[/LIST]

Now I'm going to attempt to Install Ubuntu externally to my SSD from my Laptop cause I'm not really sure what else to do. I would great appreciate any other suggestions on what to do. 

Motherboard: GA-Z170-HD3
CPU: i7-6700k 4 GHz
Graphics card: GTX 1050Ti 4GB
Memory: Crucial 16GB (2 x 8) DDR4-2133

---

### Post by kc1di on 2018-11-15
The problem is the Nvidia gtx1050Ti card in that machine.
you need to append nomodeset to the boot line of the grub menu.
see [this page. ]("https://medium.com/@sh.tsang/geforce-gtx-1080ti-gpu-nvidia-driver-installation-in-ubuntu-18-04-1d3407ecfd5e")

---

### Post by champe on 2018-11-15
[FONT=arial]Appending nomodeset to the end of the linux line keeps bringing me to the purple screen. I found another suggestion that said to add "nouveau.modeset=0", but that just leads me to a black screen again. [/FONT]Is it common for the purple screen to just take a long time sometimes? If I keep it running for an hour or so will it eventually bring me to the install prompt? Could a hardware issue possibly be causing this? My hardware isn't that old though, just a few months to a little under 2 years old. For what it's worth, I also tried installing a windows 10 USB and I got a BSOD


Update: Looks like it was indeed a hardware issue :( ! After swapping out my CPU I was able to proceed through the installation and install the drivers just fine after adding nomodeset. This thread can be locked

---

### Post by kc1di on 2018-11-15
Glad you found the problem and have it working, you can mark this thread as solved.

---

