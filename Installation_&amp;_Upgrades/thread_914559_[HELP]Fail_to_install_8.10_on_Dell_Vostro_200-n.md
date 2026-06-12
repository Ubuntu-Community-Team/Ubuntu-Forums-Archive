---
title: "[HELP]Fail to install 8.10 on Dell Vostro 200-n"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by HHJJ on 2008-09-08
:( As the title, I failed to install. My CD is 8.10 Alpha5 alternate because 8.04 didnt work either.

I searched lot of solutions and tried them but none of them worked. I will show you the error messages below.

[COLOR="DarkGreen"]//with no additional boot options[/COLOR]
the screen was full of something like
[COLOR="DarkRed"][0000][00000000000000]some mount behavior or some other behavior I donot know.[/COLOR]

[COLOR="DarkGreen"]//I pressed F6 and added each of these: splash=silent,acpi=off,noapic[/COLOR]
Kernel alive
Kernel really alive
PANIC: early exception 0d rip 10:ffffffff8044dfba error 0 cr2 0

//I pressed F6 and added vga=788
the screen turned black. It was not a "#000000" black but a "#111111" black.

I'm in China and Dell sold me this pc with a free Red Flag Linux 6. I tried it and the install process was too smooth to describe. I searched some related websites and found out that Dell sold this pc in the US with ubuntu, so I should have been able to install it!

The option of booting the Red Flag Linux is like below:
[COLOR="DarkRed"]Kernel /boot/wmlinuz-2.6.22.1-9 ro root=LABEL=/ vga=788 splash=silent initrd /boot/initrd-2.6.22.1-9.img[/COLOR]

And these are the things of my pc:
Dell Vostro 200-n
Graphic: Intel GMA 3100
Driver: 160G,SATA II,3.0Gb/s,no Raid
RAM: 1*1GB, NECC DDR2 667MHz,SDRAM
Intel Pentium Dual Core E2160
chips: Intel G33
BIOS: Dell inc,1.0.15
Dell USB keyboard(English), and I have no ps2 on the back of my pc.
Screen: ACER AL1716, 17'

I really hope someone may help me out](*,)

---

### Post by Partyboi2 on 2008-09-08
Intrepid 8.10 alpha5 is in development still, I would suggest trying to install hardy 8.04 (current stable release) and see how you go. You can download it from [here]("http://releases.ubuntu.com/8.04.1/")

---

### Post by HHJJ on 2008-09-09
> **Partyboi2 said:**
> Intrepid 8.10 alpha5 is in development still, I would suggest trying to install hardy 8.04 (current stable release) and see how you go. You can download it from [here]("http://releases.ubuntu.com/8.04.1/")

I turn to 8.10 because 8.04 didnot work. The same symptoms. So I tried the newest version.

---

