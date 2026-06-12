---
title: "ubuntu only boots from my flash drive"
date: 2024-07-06
forum: Installation &amp; Upgrades
---

### Post by ultro404 on 2024-07-06
hello im new to linux and i feel like this is a very basic issue but i wasent able to figure out what it was. i want to install linux on my ssd, i tried installing mint first, i got the bootable usb and mint opened into a live session fine but when i tried installing it onto my ssd it said it was done but couldnt boot without the usb plugged in.
i went online and until now ive tried going into the bios and rearanging the boot order and deactivating secure boot, in both mint and ubuntu i went in the terminal and typed lsblk which told me that /cdrom (which was the only thing in mountpoint so i think its linux) was mounted to sda1 which im pretty sure is the flash drive, ive also tried a few other things in the terminal that i found online but i cant remember exactly what.
i also went in the lenovo diagnostics tool and made sure id installed my ssd correctly since i got a used thinkpad t480s off ebay and it didnt come with one
i also went in boot repair and got a boot info diagnosis
[https://paste.ubuntu.com/p/bp3xwQCrKN/](https://paste.ubuntu.com/p/bp3xwQCrKN/)
im not to sure what other information im supposed to put but im on a live session of ubuntu so i can try whatever is needed
another thing is that this is my first personal computer but ive been programming on my school laptop for a while and using the terminal sounds nice but im not to sure where to start so any help on that would be good
thank you

---

### Post by yancek on 2024-07-06
You don't mention it so did you in fact, set the SSD to first boot priority in the BIOS after the install?
You have a drive with a GPT partition table and you have installed in Legacy mode.  Generally it is better to do an EFI install on a GPT drive and in order to do that, you need to boot in EFI mode to install in EFI mode.  THe BIOS_boot partition shown (first partition on the SD) should be unformatted but that is not indicated in boot repair although it may be the case.  If you have done this it should boot as long as it is set to first boot priority but I would suggest reinstalling in UEFI mode as the Legacy BIOS dates from the 1970's before things like microsoft and windows existed.

---

### Post by ultro404 on 2024-07-06
IT WORKED
thank you so much i thought i had already tried that although it only worked when i deactivated csm do you know why
also im supposed to mark this as solved using the prefix right

---

### Post by #&amp;thj^% on 2024-07-06
> **ultro404 said:**
> IT WORKED
also im supposed to mark this as solved using the prefix right
Mark as Solved in yor first thread>> Top Right>> Thread Tools

---

### Post by ultro404 on 2024-07-06
thank you

---

### Post by yancek on 2024-07-07
>  thank you so much i thought i had already tried that although it only worked when i deactivated csm do you know why

No, I don't know why because I don't know what the 'It' is that you are referring to.  Did you just change the drive boot priority in the BIOS or reinstall in EFI mode?  Most computers will give temporary boot options on boot and will allow you to select to boot a device (a live usb for example) on boot and do it in either UEFI or Legacy mode.  For several years now, some computers do not have the option and only allow UEFI boot.

---

