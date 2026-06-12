---
title: "Installing Ubuntu on MSI Laptop"
date: 2022-07-24
forum: Installation &amp; Upgrades
---

### Post by laryea73 on 2022-07-24
Hello there,

As above topic i would like to hear opinions regarding installing Ubuntu on MSI GV72 8RE.
Would it work without any problems?
I am very tired of this pre installed Windows 10 in all matters. 
Especially when it comes to storage issues...

Thus i want to get totally rid of the Microsoft pre installations and so on. Virtual machine is nothing i would want to use.
Below is a link of this laptops specs.
[https://www.msi.com/Laptop/GV72-8RE/Specification](https://www.msi.com/Laptop/GV72-8RE/Specification)

Thank you in advance

regards from
Bob Laryea

---

### Post by tea for one on 2022-07-24
> **laryea73 said:**
> As above topic i would like to hear opinions regarding installing Ubuntu on MSI GV72 8RE.
Would it work without any problems?
First of all, create a bootable USB with Ubuntu 22.04 and explore a live session?
Test your wifi, sound, graphics etc.

---

### Post by Impavidus on 2022-07-24
Nvidia graphics may need proprietary drivers. The installer can automatically find the correct drivers for your system and install them, or you can do it later from your installed system. Don't try to do it manually; that's the hard way. Before you've installed proprietary drivers, you may need safe graphics mode. Not sure what it's called right now; I never needed it myself.

It says maximum of 32GiB memory, but doesn' say how much is currently/by default installed. I assume at least 8GiB, which is more than enough.

I don't expect real problems on that hardware. Try a recent release of Ubuntu, like 22.04 LTS.

Have you got some Linux experience already? You joined the forum 4 years ago, but your bean count is at one. If you're new, keep in mind that Ubuntu is not a drop-in replacement for Windows.

---

### Post by ubfan1 on 2022-07-24
Ubuntu 22.04 installed easily on an MSI GP66 with Nvidia hardware.  Everything worked, did the proprietary video drivers after the install.  DEL to get into the UEFI settings, double click on the boot item to change the order.

---

### Post by mIk3_08 on 2022-07-26
> **laryea73 said:**
> Hello there,

As above topic i would like to hear opinions regarding installing Ubuntu on MSI GV72 8RE.
Would it work without any problems?
I am very tired of this pre installed Windows 10 in all matters. 
Especially when it comes to storage issues...

Thus i want to get totally rid of the Microsoft pre installations and so on. Virtual machine is nothing i would want to use.
Below is a link of this laptops specs.
[https://www.msi.com/Laptop/GV72-8RE/Specification](https://www.msi.com/Laptop/GV72-8RE/Specification)

Thank you in advance

regards from
Bob Laryea

Actually, This is good enough specification of laptop hardware for Linux Ubuntu Operating System. You can go then install Linux Ubuntu. But I prefer to use AMD graphics than Nvidia because you might experience a problem when the installer can't automatically find the correct proprietary drivers for your laptop graphics. Maybe you might be having some difficulty when you encounter this. Good Luck. Regards and cheers.

---

