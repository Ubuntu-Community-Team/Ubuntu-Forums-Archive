---
title: "Live CD won't boot"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by MonteO on 2004-12-03
I've been trying to get a computer running.  It is based on a Gigabyte 7N400 Pro motherboard (AMD 3000+ chip) with an Nvidia GForce 2 video controller, 512 DDR Ram (dual channel), and by now, one CD and no hard drive connected.  The onboard SATA and RAID are disabled in BIOS. I'm using a 450W Diablo power supply. This configuration was arrived at after Win98, Win2K, and Mandrake all froze during the installation process.

Ubuntu Linux in failsafe mode gives the following abnormal information:
MP-Bios bug: 8254 timer not connected to IO-APIC audit (1102111381.664:0):initialized

Unable to handle kernel paging request at virtual address 08010800 printing eip:08010800

*pde=00000000

Oops: 0000[#1]

[<c0104269>] kernel_thread_helper +0x5/0xc
Code: bad EIP value
<0> kernel panic: attempted to kill init!

Can anyone tell me where to go from here?

---

### Post by Marauder1 on 2004-12-04
What happens in the normal booting mode ?
Maybe it could help you to know if somebody
had the same error.

Just curious   :wink:

---

### Post by MonteO on 2004-12-04
[QUOTE=Marauder1]What happens in the normal booting mode ?
Maybe it could help you to know if somebody
had the same error.

Just curious   :wink:[/QUOTE]
 Ubuntu freezes during normal boot mode to a blank screen with no information at all, just like Mandrake and Windows....

---

### Post by deception on 2004-12-04
[QUOTE=MonteO]Ubuntu freezes during normal boot mode to a blank screen with no information at all, just like Mandrake and Windows....[/QUOTE]

Check your memory sticks are placed in your MB correctly.

---

### Post by MonteO on 2004-12-04
Memory sticks have been checked and rechecked (there are two 256 sticks on the dual DDR RAM board)

Also, the power supply is good, as the board has been checked with a known good supply, and gets the same results.

---

### Post by Marauder1 on 2004-12-05
Maybe you could try to add in the normal boot the switch

ide=nodma

just add it to the line showing down.

---

### Post by randy on 2004-12-05
Also turn off acpi support.

---

### Post by MonteO on 2004-12-05
OK, but how do I add a switch to the boot process (yes, I'm quite inexperienced at Linux in general), and I presume ACPI can be turned off in the BIOS?

---

### Post by Marauder1 on 2004-12-06
Just add any new arguments in the boot line on the bottom
of the screen. As you scroll down the menu, you can see it
change.Press any direction keys to prevent the cd to autoboot
then select the option in the menu with the up and down keys
then anything you type will add up to the line on the bottom.
Hope i'm clear !!!!

---

### Post by XXFCTEXX on 2006-06-10
I had this problem as well why trying to boot it would go to text and then freeze loading drivers. After swapping hard drives, memory, and even running the text version the problem still existed. I found that the problem was that my motherboard had onboard Intel Graphics as well as an AGP slot. I had disabled the onboard graphics and put in a Nvidia 5200FX. For some reason Linux was trying to recognize and use the onboard graphics anyway, even after being disabled in the BIOS. By reactivating the onboard graphics and removing the Nvidia card I restarted with zero problems. Booted right up and installed incredibly fast, I've had no problems since. Luckily I don't do anything graphic intensive so the onboard Intel Graphics are fine for this box.

---

