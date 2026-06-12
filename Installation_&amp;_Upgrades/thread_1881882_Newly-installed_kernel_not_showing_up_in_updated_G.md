---
title: "Newly-installed kernel not showing up in updated Grub"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by Rhaumces on 2011-11-16
Hello,

I am quite the beginner in Ubuntu, and I already need help.

I use a PC with a dual-boot Windows 7 / Ubuntu 9.10. In order to use my computer for MIDI applications, I need to install a realtime kernel. So i've tried that using Synaptics : i've downloaded and installed linux-headers and linux-image for version 2.6.28-3.

Then, I opened the terminal and used the command "sudo update-grub".

The newly installed rt kernel appears during the updating process. But it won't show up on the bootloader once i reboot.

Can anyone help ? Thank you for your time.

---

### Post by raja.genupula on 2011-11-16
look my signature for grub customizer and from that you can easily manage what are the kernels to be on boot time in grub.

---

### Post by gordintoronto on 2011-11-16
That version of Ubuntu is too old. Can you install 10.04 or 11.10?

Is your computer very slow, that you need a real-time kernel?

---

### Post by Rhaumces on 2011-11-17
Thanks for you help !

I have installed grub customizer as you suggested, but the problem remains the same : the realtime kernel was detected without trouble, but still wouldn't exist in the bootloader...

Actually, i've spoken with a colleague about it : he never encountered such an issue installing a realtime kernel, but he never tried this on a dual-boot PC.

Could this issue be related to the dual boot ? Or could the realtime kernel version be incompatible with ubuntu 9.10 ?

Anyway, thank you both for your quick answers !

---

### Post by unadulterated on 2011-12-25
I am having the same problem with seeing the latest kernel update (3.0.014, 15).. but in the grub menu I see only the 3.0.0.12. Any suggestions. I am using 11.10

---

### Post by gordintoronto on 2011-12-25
Rhaumces: did you also install linux-headers(version)-generic? A kernel update includes three files.

unadulterated: did you get the new kernel from system update? Is your computer multi-boot, if so what and what?

---

