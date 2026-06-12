---
title: "GRUB2 bootloader not showing after firmware update"
date: 2020-07-07
forum: Installation &amp; Upgrades
---

### Post by ndawson on 2020-07-07
Hi

I recently installed BIOS firmware updates on my Lenovo X1-Carbon, subsequent boot goes straight into a old Windows install i dont use at all (it came with the laptop)

I managed to get back into my Ubuntu install using recovery disk and grub and have tried to grub-mkconfig and grub-install to reinstall GRUB bootloader , 
it says it completes OK with but does not work when you reboot the machine (straight back into windows)

i have also tried using Boot-Repair to fix this but it just tells me to "*Please create a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag)*" even though the first partition is a ESP (output of Boot-Repair here [http://paste.ubuntu.com/p/KnRfgF9Bgm/](http://paste.ubuntu.com/p/KnRfgF9Bgm/))

As it stands, i can get into my Ubuntu install but i have to do it via manually typing grub commands every time

id be happy to loose the windows install (and also the Ubuntu 20.04 install which is just for testing) the 18.04 is the important one

id appreciate any and all help on this

Thanks

N

---

### Post by CelticWarrior on 2020-07-07
Boot Windows and disable "Fast Startup".
Then reboot to UEFI (the firmware you call "BIOS" but isn't) and go to the Boot menu and put "Ubuntu" again as the first boot priority.

---

### Post by ndawson on 2020-07-07
brilliant, thank you so much, works perfectly now

---

