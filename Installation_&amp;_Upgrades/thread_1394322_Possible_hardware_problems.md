---
title: "Possible hardware problems?"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by videoismylife on 2010-01-30
Hi, all; new to the forum and to Ubuntu;  I have a question for the more experienced.... 

Sorry for the long post; here's the executive summary: 

Is there an issue with the new Intel i-series processors and associated chipsets that is causing problems with Ubuntu 9.10? What am I doing wrong? 

Longer version:

Hardware: (new build)
- Gigabyte GA-H55M-UD2H - H55 Express Northbridge, using on-chip Intel graphics. Set to "Safe" settings in the BIOS, rather than "Optimized". Realtek ALC889 audio. Realtek 8111 LAN. 
- Intel i5-650 processor
- OCZ PC1600 DDR3 RAM; 4GB in 2 sticks.
- Encore ENLWI-G(2) PCI wireless card - Realtek 8081 chipset.
- Windows 7 Pro 64-bit.
- Logitech cordless EX 100 mouse and keyboard. 

That's it, a basic workstation. Had some[FONT=Franklin Gothic Medium][SIZE=2] i[/SIZE][/FONT]ssues with the Realtek 8081 wireless card that I solved by installing the XP driver and wireless utility rather than allowing Windows 7 to choose; but now working fine.

I've downloaded the Ubuntu 9.10 desktop version and burned a CD; the CD demo works on an older XP computer (Core 2 Duo 8400, P45 chipset, Radeon HD 3450). 

However, I can't get the CD to boot completely on the new build - it seems to be going ok and then hangs with the desktop background in place but no icons or task bar. I can't move the mouse cursor, can't "vulcan neck pinch" or "ctrl-C" my way out of it; have to hit the power button and reboot. 

I also tried installing 9.10 under Windows 7 Pro 64 bit; it seems to install fine but when I reboot to Ubuntu it hangs in the same place as the CD-boot.

So, I'm thinking it's a hardware incompatibility, but I have no idea where to go from here. Any ideas? 

Thanks for any help.

---

### Post by iskarion on 2010-01-31
The Realtek ALC889 audio chipset as well as the Realtek 8111 Ethernet chipset included on the board are supported by Ubuntu 9.10. So I guess your problem is related to the new Intel H55 northbridge.

Therefore the solution described here
[https://wiki.ubuntu.com/Intel_DH55TC](https://wiki.ubuntu.com/Intel_DH55TC)
should also be applicable to your problem.

Boot with the kernel parameter ACPI=off to get Ubuntu stable during installation. Once Ubutnu is installed, install the most recent kernel 2.6.33-rc6 and reboot with this kernel.

Seems like neither the kernel 2.6.31 included in Ubuntnu 9.10, nor the kernel 2.6.32 which will be part of the upcoming Ubuntu 10.04 properly supports the H55 chipset.

---

### Post by videoismylife on 2010-02-02
> **iskarion said:**
> The Realtek ALC889 audio chipset as well as the Realtek 8111 Ethernet chipset included on the board are supported by Ubuntu 9.10. So I guess your problem is related to the new Intel H55 northbridge.

Therefore the solution described here
[https://wiki.ubuntu.com/Intel_DH55TC](https://wiki.ubuntu.com/Intel_DH55TC)
should also be applicable to your problem.

Boot with the kernel parameter ACPI=off to get Ubuntu stable during installation. Once Ubutnu is installed, install the most recent kernel 2.6.33-rc6 and reboot with this kernel.

Seems like neither the kernel 2.6.31 included in Ubuntnu 9.10, nor the kernel 2.6.32 which will be part of the upcoming Ubuntu 10.04 properly supports the H55 chipset.


Thanks for the reply - I gave the "ACPI=OFF" option a try and it finally booted to the GNOME desktop; but it still froze completely requiring a hard reboot when I tried to open one of the items on the upper task bar. 

Is there any interest in a debug log? I haven't tried it but I noted that it's an option on the boot screen - I could post it if it would be useful.

In an unusual twist, I was trying to install Ubuntu because Windows doesn't support my hardware - I have an HP printer that was abandoned when Vista came out, and I can't install it in Win 7 Pro.

Oh well - I'm no computer whiz so I'm stuck on the sidelines for now, until the next itieration of Ubuntu or so. I'll install on my older P45/Core 2 Duo based computer and use it there instead.

---

### Post by iskarion on 2010-02-04
> **videoismylife said:**
> Thanks for the reply - I gave the "ACPI=OFF" option a try and it finally booted to the GNOME desktop; but it still froze completely requiring a hard reboot when I tried to open one of the items on the upper task bar. 

If starting Gnome/X Server freezes your computer, it might be worth a try to just boot to the terminal, install the 2.6.33-rc6 kernel from there, reboot with this new kernel and only then go into Gnome.

---

### Post by alexmstevens on 2010-02-05
I had no luck with the 2.6.33 kernel but I am able to get it working just fine by selecting the recovery mode for the kernel at boot, logging on in terminal mode and then running startx. At tha point Gnome comes up fine and everything works (well, almost everything). there are no freezes and/or crashes. 
 
I'm guessing that something in the sequence of events when booting directly into Gnome is related to the problem, and it doesn't happen if you complete the boot process in text mode. I am too old and lazy to research the boot logic, but maybe someone enterprising might be willing to give it a try.
 
BTW: the ACPI option is not a problem with my setup.
 
Here's the hardware basics:
 
ASUS P7H55M-Pro MB
Intel I5 650 cpu
4 GB DDR3-1600 ram
1Sata HD, 1 Sata DVD-RW
 
Good Luck,
 
Alex Stevens
alexmstevens

---

### Post by alexmstevens on 2010-02-05
Further testing seems to indicate that the problem is with GNOME, not linux. I added the Kubuntu desktop to the installation, rebooted into Kubuntu, made it the default and now everything works fine. If you're having trouble with a H55 chipset give it a try.

Alex Stevens
alexmstevens:D

---

### Post by videoismylife on 2010-02-08
> **alexmstevens said:**
> Further testing seems to indicate that the problem is with GNOME, not linux. I added the Kubuntu desktop to the installation, rebooted into Kubuntu, made it the default and now everything works fine. If you're having trouble with a H55 chipset give it a try.

Alex Stevens
alexmstevens:D

Thanks, I'll give that a try. One of the perks to being a complete newb is there's no "good ol' days" to compare to and wish for.... ;)

---

### Post by pcbuilder on 2010-03-02
I have run into this same lock up problem with Ubuntu 9.10. I'm using a Gigabyte H55M UD2H with a Core i5-650. The lock up occurred both after a full install and with the live CD.

After I saw a previous post regarding Kubuntu, I installed Kubuntu 9.10 and have not encountered the lock up problem anymore.

---

### Post by RJARRRPCGP on 2010-03-02
Can you run ```
mprime
``` for 12 hours without a lock up? 

That test will determine how your CPU and motherboard are doing.

---

