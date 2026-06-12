---
title: "Live CD won't start, Installation won't boot"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by S1Drano on 2010-10-13
Hi, I downloaded Ubuntu 10.10 2 days ago and tried to instal it on my:
HP EliteBook 8540w
Intel Core i7 740QM
Intel QM57 Express
8GB RAM
nVidia Quadro FX 1800 with CUDA (1GB)

Of course I went 64bit, but the Live CD wouldn't start. Instead I get some weird artifacts on my screen.
I can see bits of my Windows-background with taskbar and some of the windows I was using earlier before restarting, like the download manager. If cold boot my PC I see black and white boxes with coloured dots on them.
Thus I thought of an issue with the 64bit architecture and possibly the grafics card too (the artifacts are clearly remnants of data from the VRAM)

I tried the same with the 32bit version and got the same issue (indicating NO issue with 64bit, at least not directly).

In the end, I installed Ubuntu from the alternate 64bit CD and now am stuck with a non-working installation of Ubuntu.
I get some kind of error concerning pcieport (probably PCI Express).


When I install Ubuntu on Virtualbox through Windows 7 however, I don't get any kind of issue (I'd still like to be able to run Ubuntu natively)




Any idea on how to fix the problem?

PS: I'm not very experienced with Linux, so if you ask me to go into console mode, please be detailed on what command I should input.


I'm very grateful to anyone who took his (or her) time reading my post trying to help me.

---

### Post by kansasnoob on 2010-10-13
It sounds like the Nouveau Drivers aren't working well with your nVidia Quadro FX 1800. It may ultimately be necessary to change to the Nvidia drivers but I'm unsure how to do that via CLI :(

You might find the following helpful to troubleshoot Nouveau:

[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

Otherwise I'm sure someone more experienced with Nvidia GPU's can help you further.

---

### Post by S1Drano on 2010-10-13
It worked perfectly, thank you very much.

Now my grafics are a little messed up (especially the resolution), but I think I'll be able to find a solution to that myself.

I used:
> Disabling nouveau

Sometimes it can be useful to disable nouveau to see if the computer boots correctly without it.

During boot hold down the shift key to get to the grub menu. Press the 'e' key to edit the boot command, and go down to the "kernel" line. Add "nouveau.modeset=0" to the end of the line containing "quiet splash", then press Ctrl+x to boot. Nouveau will be disabled for this boot.

Edit: After activating the nVidia proprietary drivers, I don't need to disable nouveau on startup anymore and my grafics have become just perfect.

---

