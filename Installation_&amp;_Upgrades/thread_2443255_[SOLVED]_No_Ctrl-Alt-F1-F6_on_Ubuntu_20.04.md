---
title: "[SOLVED] No Ctrl-Alt-F1-F6 on Ubuntu 20.04"
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by lcs_europe on 2020-05-13
Since I installed Ubuntu 20.04 on my PC I can not get Ctrl+Alt+F1 to F6 working. Here are my config:

[LIST]
[*]OS: Ubuntu x86_64 (5.4.0-29-generic)
[*]Motherboard: msi B450M MORTAR MAX, MS-7B89 1.0, 32 GB RAM
[*]CPU: AMD Ryzen 5 3600 (12) @ 3.600GHz
[*]GPU: NVIDIA GeForce GTX 1050 Ti
[*]GPU Driver: NVIDIA 440.64
[*]Resolution: 2560x1440 @ 59.95Hz
[/LIST]

I have tried different solutions published here, with no success:
[LIST]
[*][How to launch GUI app in Ctrl+Alt+F7 from tty Ctrl+Alt+F1-F6]("https://askubuntu.com/questions/541438/how-to-launch-gui-app-in-ctrlaltf7-from-tty-ctrlaltf1-f6")
[*][Using Ctrl-Alt-F1]("https://askubuntu.com/questions/115709/using-ctrl-alt-f1")
[*][Cannot do Ctrl+Alt+F1 after login]("https://askubuntu.com/questions/858647/cannot-do-ctrlaltf1-after-login")
[*][Enable Ctrl+Alt+F1 Virtual Consoles in GNOME Ubuntu 17.04+]("https://askubuntu.com/questions/911560/enable-ctrlaltf1-virtual-consoles-in-gnome-ubuntu-17-04")
[/LIST]

Does anyone have a solution?

Thank you in advance, Laszlo

---

### Post by CatKiller on 2020-05-13
> **lcs_europe said:**
> Since I installed Ubuntu 20.04 on my PC I can not get Ctrl+Alt+F1 to F6 working. 

It's an nvidia thing. It does work if you get the nvidia driver working with Kernel Mode Setting (which I *think* requires UEFI rather than Legacy/CSM).

---

### Post by CelticWarrior on 2020-05-13
> ... which I *think* requires UEFI rather than Legacy/CSM ...

Yes, indeed.
And any AMD Ryzen based PC has UEFI and really really begs for UEFI mode. I don't understand why people still insist in Legacy/CSM... I mean, I could understand if we were still in 2012 but now with all the new hardware depending on UEFI's advanced hardware initialization features, insisting on Legacy/CSM is shooting one's own feet.

---

### Post by lcs_europe on 2020-05-13
> **CatKiller said:**
> It's an nvidia thing. It does work if you get the nvidia driver working with Kernel Mode Setting (which I *think* requires UEFI rather than Legacy/CSM).

I can't imagine it's a graphics driver issue. My notebook has an Intel HD Graphics 620 card. The other desktop also has an Intel HD Graphics 620 card. The key combinations Ctrl-Alt-F1 to F6 do not work on both machines.

---

### Post by CelticWarrior on 2020-05-13
> **lcs_europe said:**
> I can't imagine it's a graphics driver issue. My notebook has an Intel HD Graphics 620 card. The other desktop also has an Intel HD Graphics 620 card. The key combinations Ctrl-Alt-F1 to F6 do not work on both machines.

Are all installed in UEFI mode?

---

### Post by lcs_europe on 2020-05-13
Hey Guys. The problem is solved. It is the Keyboard (Microsoft Wireless ComfordKeyboard 5000). With a wired Keyboard the Keystorkes are working :lolflag:

---

### Post by lcs_europe on 2020-05-13
On my Microsoft Wireless ComfortKeyboard 5000 was the F-LOCK Key activated ;-)

---

