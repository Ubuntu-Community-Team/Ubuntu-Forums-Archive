---
title: "Tough installation"
date: 2021-03-27
forum: Installation &amp; Upgrades
---

### Post by superredcomet on 2021-03-27
I am trying to install ubuntu server on my Lenovo 100s which does not support boot from usb, I have tried unetbootin which failed to boot

---

### Post by CelticWarrior on 2021-03-28
Welcome.

"Lenovo 100s" doesn't say much. Please always post the actual hardware specifications. 
The above notwithstanding, any model that google showed definitely support USB boot. It would have to be a very old machine (like 20 years old) to not support USB boot, really. So, that's unlikely to be the problem. And Unetbootin isn't a solution, especially because it seems you don't know what you're doing and are making wild assumptions.
How exactly have you tried to boot the installation media and how did you do it?

---

### Post by yancek on 2021-03-28
Were you attempting to do a frugal install to boot the Ubuntu installer from the hard drive as explained at the link below?  If it didn't work for you, you will need to explain in some detail what you did and whatthe results were as this method has been successful for many for years.

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by TheFu on 2021-03-28
A few years ago, "Lenovo 100s" laptops were $99 new and came with ChomeOS. A friend had one and he worked for months to get any Linux to work on it.  Lenovo had a $50 settlement for the battery/power cord recall (I don't recall which), so he was very happy that the device only was $50 total, after the settlement check cleared.  I don't recall whether he ever go any Linux working. Sorry.  

Seemed like it was built for ChromeOS and only ChromeOS. The internal storage was eMMC, soldiered onto the board. [https://wiki.mrchromebox.tech/Supported_Devices](https://wiki.mrchromebox.tech/Supported_Devices) says the name is "Lenovo Ideapad 100S Chromebook 	ORCO " and that the write protect screw needs to be removed to load the firmware, then other OSes.

Or I could be completely confused and this has nothing to do at all with the OPs laptop.

---

### Post by rsteinmetz70112 on 2021-03-29
Have you tried old school a DVD in a USB drive?

---

### Post by superredcomet on 2021-03-29
I may be new but I'm not an idiot I know my laptop doesn't support USB boot on the BIOS and is booting from EFI as opposed to UEFI which according to Easy BCD means I can't install plop (I have tried a manual installation as well which errored).
My laptop specifically is an intel Atom 1.33GHz 4 core 64 bit CPU (though I think it's a wierd CPU which only runs partially 64 bit which is why I'm trying to run the 32 bit version as that was what came pre installed in terms of Windows), 2GB of RAM, 30 GB SSD
I have tried through multiple routes to boot the media:
- Boot options only want to run windows boot manager
- Bios settings have not options to switch on USB boot or anything similar
- Windows boot manager will try to get the computer to boot from my USB but then says that it's not supported

---

### Post by superredcomet on 2021-03-29
> **rsteinmetz70112 said:**
> Have you tried old school a DVD in a USB drive? Considered it but I don't have an external drive anymore and am slightly worried my PC won't boot from any external media (atleast not through the USB port), I'll probably buy one if I can't work out another way

---

### Post by superredcomet on 2021-03-29
> **TheFu said:**
> A few years ago, "Lenovo 100s" laptops were $99 new and came with ChomeOS. A friend had one and he worked for months to get any Linux to work on it.  Lenovo had a $50 settlement for the battery/power cord recall (I don't recall which), so he was very happy that the device only was $50 total, after the settlement check cleared.  I don't recall whether he ever go any Linux working. Sorry.  

Seemed like it was built for ChromeOS and only ChromeOS. The internal storage was eMMC, soldiered onto the board. [https://wiki.mrchromebox.tech/Supported_Devices](https://wiki.mrchromebox.tech/Supported_Devices) says the name is "Lenovo Ideapad 100S Chromebook 	ORCO " and that the write protect screw needs to be removed to load the firmware, then other OSes.

Or I could be completely confused and this has nothing to do at all with the OPs laptop.
I think they sold in two runs, once with windows and once as a chromebook, I have the windows version, it's not a very good laptop but it was only like £150 and came with windows and office, it's also very light (even compared to a modern ultrabook or tablet) and even had a magnesium plate to keep it light and rigid (found out while replacing the keyboard (which is mechanical)) it's not really powerful enough to run Windows but offers a good enough user experience for me to want to use it to code on the go, hence linux

I agree that it doesn't seem the laptop was really designed to run anything it wasn't shipped with, the bios is utterly featureless and it doesn't seem to support any kind of non standard boot

---

### Post by CelticWarrior on 2021-03-29
> [COLOR=#000000]My laptop specifically is an intel Atom 1.33GHz 4 core 64 bit CPU (though I think it's a wierd CPU which only runs partially 64 bit which is why I'm trying to run the 32 bit version as that was what came pre installed in terms of Windows), 2GB of RAM, 30 GB SSD[/COLOR]
It's one of the infamous "Bay Trail" or "Cherry Tail" families.
You got it almost right. It's a 64-bit CPU paired with a 32-bit UEFI, a total freak show, the only redemptive characteristic is/was its very low price. In a way it can be said you got what you payed for.
Here's the advice I give to all owners of such hardware: Use Windows. It's very hard to make any Linux distro work decently and in most cases [a special respinned ISO]("http://www.linuxium.com.au/isos") is needed. Now, FYI, **it's 64-bit and ONLY 64-bit is supported.** Assuming that 32-bit is needed because it came with 32-bit Windows is incorrect and actually it can't boot any 32-bit Linux distro as you found out already. And Ubuntu dropped 32-bit some time ago so there's that also. Again, new 64-bit releases may boot on its own but in may cases it's better to use the respin above that contains a special "bootia32" file that handles the crippling 32-bit UEFI.

The problem then is, even if you manage to boot and install Ubuntu, some hardware won't work: WIFi, Ethernet, integrated audio, graphics in any combination depending on the actual hardware. This is the main reason for the suggestion to use Windows. 

> [COLOR=#000000]I know my laptop doesn't support USB boot on the BIOS and is booting from EFI as opposed to UEFI which according to Easy BCD means I can't install plop (I have tried a manual installation as well which errored).[/COLOR]
BIOS and UEFI are firmwares. If you have one you don't have the other. Surely many people and manufacturers insist on using the wrong terminology, calling "BIOS" to what is UEFI or even "UEFI BIOS". Calling a horse carriage a (motor)car doesn't make the the horse run on petrol though.
FYI, EasyBCD is for BIOS. For UEFI there's EasyUEFI and PLoP's main usage is for very old computers that can't boot from USB media and so a PLoP bootable CD takes care of the first stage and then chainloads to the USB installation media. Definitely not applicable in your case because **yours boots from USB media and can only boot from 64-bit USB media**.
Finally, saying "[COLOR=#000000]booting from EFI as opposed to UEFI" sort of negates what so enthusiastically/confidently preceded it. So, another advice is to look at the post count of the people trying to help you. An high number usually means something.

Good luck.[/COLOR]

---

### Post by superredcomet on 2021-04-01
> **CelticWarrior said:**
> It's one of the infamous "Bay Trail" or "Cherry Tail" families.
You got it almost right. It's a 64-bit CPU paired with a 32-bit UEFI, a total freak show, the only redemptive characteristic is/was its very low price. In a way it can be said you got what you payed for.
Here's the advice I give to all owners of such hardware: Use Windows. It's very hard to make any Linux distro work decently and in most cases [a special respinned ISO]("http://www.linuxium.com.au/isos") is needed. Now, FYI, **it's 64-bit and ONLY 64-bit is supported.** Assuming that 32-bit is needed because it came with 32-bit Windows is incorrect and actually it can't boot any 32-bit Linux distro as you found out already. And Ubuntu dropped 32-bit some time ago so there's that also. Again, new 64-bit releases may boot on its own but in may cases it's better to use the respin above that contains a special "bootia32" file that handles the crippling 32-bit UEFI.

The problem then is, even if you manage to boot and install Ubuntu, some hardware won't work: WIFi, Ethernet, integrated audio, graphics in any combination depending on the actual hardware. This is the main reason for the suggestion to use Windows. 


BIOS and UEFI are firmwares. If you have one you don't have the other. Surely many people and manufacturers insist on using the wrong terminology, calling "BIOS" to what is UEFI or even "UEFI BIOS". Calling a horse carriage a (motor)car doesn't make the the horse run on petrol though.
FYI, EasyBCD is for BIOS. For UEFI there's EasyUEFI and PLoP's main usage is for very old computers that can't boot from USB media and so a PLoP bootable CD takes care of the first stage and then chainloads to the USB installation media. Definitely not applicable in your case because **yours boots from USB media and can only boot from 64-bit USB media**.
Finally, saying "[COLOR=#000000]booting from EFI as opposed to UEFI" sort of negates what so enthusiastically/confidently preceded it. So, another advice is to look at the post count of the people trying to help you. An high number usually means something.

Good luck.[/COLOR]

Yeah sorry I'm well aware of the UEFI I was just using BIOS as a coloquial and because that is what it is refered to on startup (although the settings do correctly refer to the boot as UEFI even if BIOS is the menu name) seems like a lost cause unfortunately but I will continue to tinker, I don't think my issue was with the kernel as opposed to even being able to attempt the boot so I've got a number of issues to sort, hopefully I can get the laptop to boot linux eventually as this has been a on and off thing for a couple of years but I will probably transition my usb stick to a standard am64 build since that will boot on my PC even if my laptop will never run from external media

---

### Post by CelticWarrior on 2021-04-01
The aforementioned Linuxium respin is your best chance for hardware support.

---

