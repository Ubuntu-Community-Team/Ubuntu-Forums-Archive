---
title: "Unable to Access BIOS on Lenovo P3 Tower Despite Multiple Attempts (BIOS Accessible a"
date: 2024-08-14
forum: Installation &amp; Upgrades
---

### Post by leonardosalim on 2024-08-14
Hello everyone,
I'm facing a frustrating issue with my Lenovo P3 Tower, and I'm hoping someone here can help.
[h=3]**System Details:**[/h]
[LIST]
[*]**Model:** Lenovo P3 Tower
[*]**GPU:** NVIDIA T400 4 GB
[*]**Current OS:** Ubuntu 22.10 (Kinetic Kudu)
[/LIST]
[h=3]**The Issue:**[/h]I recently got my computer back from a repair center, and they informed me that the drivers were installed correctly. However, I'm now trying to access the BIOS to make some changes, but I can't seem to enter it, no matter how many times I try.
**What I've Tried:**

[LIST]
[*]Pressing the usual keys (F1,F2, F12, Esc, Del, etc.) repeatedly during startup—I've tried this over 100 times with no success.
[*]Using a different keyboard and switching USB ports.
[*]Attempting to access the BIOS from within Ubuntu using sudo systemctl reboot --firmware-setup.
[*]Disabling Fast Boot and Secure Boot (if they were enabled) via Ubuntu.
[*]The repair center sent me a picture showing that they were able to access the BIOS, so I know it's possible, but I just can't seem to get it to work on my end.
[/LIST]
[h=3]**What I Need Help With:**[/h]
[LIST=1]
[*]**Why might I be unable to access the BIOS even though the repair center could?**
[*]**Are there any specific tricks or less common methods I can try to enter the BIOS on a Lenovo P3 Tower?**
[*]**Could this be related to the installed drivers or any other software issue?**
[*]**Is there a way to reset or force entry into the BIOS using hardware (e.g., a specific jumper or button on the motherboard)?**
[/LIST]
I’m trying to upgrade (or rather, downgrade) my OS from Ubuntu 22.10 to Ubuntu 22.04 LTS for stability reasons, but I can't do that without accessing the BIOS to boot from a USB drive.
Any advice or suggestions would be greatly appreciated! Thank you in advance.

---

### Post by currentshaft on 2024-08-14
cf

---

### Post by tea for one on 2024-08-14
(a) Contact the repair centre and ask them how they accessed the UEFI Settings (BIOS)
(b) Remove all disks - some PCs will then automatically jump into the UEFI Settings (BIOS)
(c) Remove your internal disk(s) and leave the bootable usb attached - the usb may boot
    (A bootable usb will show Grub, which also has a menu entry for UEFI Firmware Settings)
(d) Install rEFInd on a USB stick 
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File
rEFInd has options to boot into UEFI firmware or start an EFI shell
You can boot an external device via an EFI shell (although it's a bit fiddly)

---

### Post by leonardosalim on 2024-08-14
I will try these methods. Thank you for your replay.

---

### Post by leonardosalim on 2024-08-14
Thank you for your replay. I've tried this but the issue still unfortunately not solved.

---

### Post by bobunderwood99 on 2024-08-14
According to the manual
[https://download.lenovo.com/pccbbs/thinkcentre_pdf/p3_tw_linux_ug.pdf](https://download.lenovo.com/pccbbs/thinkcentre_pdf/p3_tw_linux_ug.pdf) 
you may need to use Fn+F1.

---

### Post by currentshaft on 2024-08-14
""

---

