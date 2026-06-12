---
title: "no sound"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by sparky100 on 2005-11-13
i have upgraded from hoary to breezy.  my sound card is no longer recognised (Ensoniq 5880 AudioPCI (rev 02) :( .  sound worked perfectly under hoary.  

any sugestions thanks simon

---

### Post by majed on 2005-11-13
sound card not recognized, or sound not working? It's different..

i get this all the time, do a mute and unmute or adjust volume and then it should work if u have the same problem i have :)

---

### Post by sparky100 on 2005-11-13
No sound because card not found.

Simon

---

### Post by opera on 2005-11-13
This did it for my sound:

Go to Video and Sound, posting the Sound of silence, and follow the suggestions by Teaker1s

---

### Post by sparky100 on 2005-11-13
Ok... 

This is what I can't understand

lspci

0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
0000:00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
0000:00:08.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
0000:00:09.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:05.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

modprobe indicates that the sound module is installed.

any suggestions..

Simon

---

