---
title: "Unable to boot nor see grub after installing Nvidia drivers and lowlatency kernel"
date: 2021-09-19
forum: Installation &amp; Upgrades
---

### Post by canhoto on 2021-09-19
Hi
I did a clean installation of Ubuntu (Cinnamon Remix) on my brand new Acer laptop. It all went well and I was able to boot to the system and begin configuring it to my needs.
However, this configuration implied installing all the components of Ubuntustudio (including the lowlatency kernel) and also the Nvidia 470 proprietary driver (since the computer has a dedicated GTX 1650 GPU).
I guess that, because of one this reasons (most probably Nvidia driver), I can't boot to the system. I get stuck on the "Acer" logo. I can't even access the grub menu. 
I tried to figure how to remove installed software using the USB stick that I used to install the system, but I can't. Is there a way to remove installed software (in this case, Nvidia drivers or lowlatency kernel) without booting into the system (which I can't)?

---

### Post by canhoto on 2021-09-19
Well, I managed to get into the system by getting into the grub menu after pressing Esc a few times during he initial boot. Now I'm going to see if I can find what the problem is.

---

### Post by MAFoElffen on 2021-09-19
Between your two posts, you say both NVidia 1650 and 1050 ti... ?

Mine is NVidia GTX 1650 ti and as such runs best on Kernel 5.11.1, Gnome XServer DE, and the NVidia 760 Server driver. Just saying...

---

