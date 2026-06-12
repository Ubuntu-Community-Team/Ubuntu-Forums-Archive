---
title: "Ubuntu 18.04 installation issue"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by omaralam on 2020-03-31
Hello,
while trying to install Ubuntu 18.04 from a live USB (the system was previously Windows and I opted to erase Windows) I encountered the issue described in [this]("https://askubuntu.com/questions/771899/pcie-bus-error-severity-corrected") post. As instructed in that post, I inserted the line "pci=noaer" into the GRUB and managed to finally install Ubuntu. The issue is that it only allowed me install it in OEM installation mode. I would really like to have a traditional install route, and understand what exactly was initially causing me this install issue. Is there anything I can do now that I have installed Ubuntu on my system (albeit in OEM mode) to reverse engineer what was causing the issues in the first place, that would then allow me to fix the installation issues and install Ubuntu normally ? I have no issue doing a fresh install (I haven't used the new Ubuntu install yet).

---

### Post by Autodave on 2020-04-01
Please give us some info on your equipment.

---

### Post by VeloxNeb on 2020-04-01
to remove the oem user:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)


to help you find out exactly what went wrong:

it's usually best to "try ubuntu" (live-session) before actually choosing "install" and see if everything works out of the box; graphics, sound, internet... if you have an internet connection you can update your (live-)system and/ or the installer and see if this already fixes your problem (newer kernel).  comprehensive guide: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

in a nutshell it seems your kernel is complaining about hardware compatibility issues. adding noaer suppresses the error messages. more on this here: [https://itsfoss.com/pcie-bus-error-severity-corrected/](https://itsfoss.com/pcie-bus-error-severity-corrected/)
  
is the hardware mentioned in the askubuntu thread you linked to exactly your machine? 
if so, the bug report incl workaround is in that same thread.
to find out about your hardware hit ctrl+alt+T to open a terminal and type sudo lshw.

---

### Post by slickymaster on 2020-04-01
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by mell652 on 2020-04-02
I also decided to install Ubuntu and it also got up in OEM mode and what is the problem I did not figure out and sat back on windows[COLOR=#1155cc][FONT=Arial][/FONT][/COLOR]

---

