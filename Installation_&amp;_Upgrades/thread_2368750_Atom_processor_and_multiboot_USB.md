---
title: "Atom processor and multiboot USB?"
date: 2017-08-14
forum: Installation &amp; Upgrades
---

### Post by grandkodiak2 on 2017-08-14
Hello,


I have used multiboot for a long time now, very convenient to have gparted, ubuntu, mint, kali etc all on one usb handy. I have also used it to install linux on many older machines to get extra life out of them. Today I purchased an Asus "2 in 1" t102ha model that has the Atom processor, and 64 bit windows 10 loaded. For some reason, it will not use multiboot.. it will ignore the boot and go to windows boot loader, or if disabled, will try the usb then boot back into the bios. I was reading that even though Atom processors can run 64 bit OS's such as the ubuntu I'd like to put on it, that it uses a 32 bit loader. 


I found on the forums some related type explinations from older models and other Atom based computers that refer to the boot loader being either 32 or 64 bit, and Atom using only 32 bits. I'm assuming that multiboot is a 64bit loader then? Is there a way to install it in 32 bit to install a 64 image of ubunutu (or whatever)? I have both 32 and 64 images of the releases already on the usb already using multiboot as I put 32 on some older machines here and again...but it wont even get to multuboot menu to choose an image to load, it never even gets that far.


If not, is there another live usb program that I should try with it? I also have Yumi but I get the same result. I also do not have an external cd/dvd handy, not in years lol.

Thanks!

ps. hardware is[COLOR=#494949][FONT=Arial]  quadcore 1.44ghz Atom x5-Z8350 w/4gb ram, and I'm assuming the board is asus of some sort since they make it lol[/FONT][/COLOR]

---

### Post by Autodave on 2017-08-14
Have you tried disabling *secure boot *in the BIOS?

---

### Post by grandkodiak2 on 2017-08-15
Secure boot is disabled, quick boot is disabled.

Update:
I formatted the USB stick and tried unetbootin with mint 64 which worked live. docking keyboard, wireless, bluetooth, and sound worked but the pen touch would not realign with the screen going from tablet to landscape, but I can figure that out later. issue is now, it made the partitions ok, went through the entire install ok, but on reboot, no grub and goes right to windows. the partitions are there and have volume data on there that would show mint is sitting there, but no grub.

I tried a random command I found on the interwebs but it didnt help in the windows command line,. "bcdedit /set [bootmgr] path \EFI\ubuntu\grubx64.efi" 
should i rename the ubunutu path to mint? ive never looked at the mint filing system to see what its nomenclature is.

thanks!

---

### Post by grandkodiak2 on 2017-08-16
Resolved:

I tried multiboot and unetbootin with the same results, however when I tried using rufus to create the live cd, the install work and an option was created in the bios that listed "ubuntu efi" as a boot option along with "windows boot manager" (which is listed twice now for some reason) but it will boot to grub which can boot successfully boot into both mint and windows 10.

the only issue remaining is that the sound does not work in linux, and the touch alignment does not rotate with the desktop, nor does it automatically switch from landscape to portrait using the motion sensor but we'll figure out that in another thread. 

thanks all

---

