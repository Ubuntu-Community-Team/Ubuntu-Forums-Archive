---
title: "Installation of Ubuntu 12.04 LTS on Asus Notebook fails"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by FlipsenRE on 2014-04-10
Hi!

I am trying to install Ubuntu 12.04 LTS on my Asus Notebook ([specifications]("http://www.asus.com/Notebooks_Ultrabooks/F50Sv/specifications/")). I am booting from an usb drive which was arranged by LinuxLive USB Creater.
After some time the installation stops and freezes at the outputline "AppArmor: AppArmor sha1 policy hashing enabled".
The process stops at this point and the machine switches off after a while.
It is also not possible to run the system via usb without installation.

I googled that problem and found some threats with a similar issue, but there was no propper workaround for that.
I had this problem before and couldn't find any solution (even tried to install from CD but didn't work). The same thing happend with other linux distributions. I am using the Windows bootloader and BIOS v02.61 (shoudn't play a role). The only distro that finally worked was "Sabayon" - no clue why... But since I am tired of working with Sabayon I am trying to install Ubuntu. 

Does anyone know how to solve that?

Cheers
Philipp

---

### Post by FlipsenRE on 2014-04-11
Nobody with an idea? I am wondering if the BIOS Version could cause the problem? Would it make sence to have a try with UEFI?

---

### Post by sudodus on 2014-04-11
A. Does it work to 'try Ubuntu', to run it live from the install CD/DVD/USB drive without installing?

B. Maybe you have problems with the nvidia graphics chip. Otherwise I think your computer should work with Ubuntu.

Try the boot option nomodeset according to this link. It that does not help, try (in Windows) to find out the following specs

1. CPU
2. RAM (size)
3. graphics chip/card (exactly which model it is)
4. wifi chip/card

It helps us help to know those details about your computer.

---

### Post by FlipsenRE on 2014-04-11
Hi sudodus,

first of all, thanks for your answer! According to your notes:

A. Neither the Live-Mode nor the Persistent mode work. I got the same Problem: The process stops at "[#]AppArmor: AppArmor sha1 policy hashing enabled"

It doesn't change if I use the nomodeset option.

The specs for my machine are:
1.CPU: Intel(R) Core(TM)2 Duo CPU T5850 @ 2.16GHz 2.17 GHz
2.RAM: 4,00 GB
3.Graphic Chip: NVIDIA GeForce GT 120M
4.Wifi chip: Atheros AR928X Wireless Network Adapter

Cheers
Philipp

---

### Post by sudodus on 2014-04-11
OK, we know more now, and I think you will soon have Ubuntu working in that computer.

- I think you will get some more tips soon. The best thing would be if someone with the same or very similar computer will tell us how to make Ubuntu work.

- Have you tried the USB boot drive in another computer - that it can run live 'trying Ubuntu'? If it does not work there either, use another tool to create the USB boot drive (to flash the iso file into the drive).

- You can also try other boot options, not only nomodeset.

- You can download Ubuntu 13.10 and use that iso file to make the USB boot drive.

For more details about booting from USB, see this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by FlipsenRE on 2014-04-11
Hi!

Thanks for your advice! The problem has been solved.
I tried out several other boot options and it finally worked with choosing "nolapic".

I have no idea why, but I can imagine that the CPU caused the problem in some way since nolapic turns off the local APIC (but I am no expert, nor do I have any idea what a local APIC realy is... :D)

So for everyone with a similar problem: Give the boot option "nolapic" a try!

Cheers
Philipp

---

### Post by sudodus on 2014-04-12
Congratulations :KS

Please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

