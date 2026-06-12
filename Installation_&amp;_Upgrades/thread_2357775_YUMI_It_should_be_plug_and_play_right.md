---
title: "YUMI: It should be plug and play right?"
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by kylona on 2017-04-05
I'm not sure if this is the right place to ask, but I wasn't sure where to go.

I'm trying to live boot Ubuntu Studio so I can use Aurdor. I've used YUMI before and I really liked it. No problems whatsoever. Download the .iso let it do its magic select the option from the boot menu and ta da! This time has been a mess.

My system is an ACER with a AMD FX 7th gen 64 bit processor. 

I know my iso is good because it successfully boots in a virtual machine, but the latency for audio recording is just too much.


After trying several things including switching flash drives I've hit this dead end. I think YUMI did it right this time, except that the OS is not showing up in the menu. I tried uninstalling and re-installing with no luck. Still not showing up in the menu..... 


Is there a way to manually add it to the menu?


I honestly don't know what I should include here. Sorry I'm a noob.

---

### Post by TheFu on 2017-04-06
Welcome to the forums.

Is ubuntu studio in the list of Yumi distros?  I don't recall and can't get to a Windows PC for a few hours.  If not, you'll want to change the ISO name so that it looks like one of the other Ubuntu ISOs.  Make the mask match a pattern used by some other Ubuntu flavor.

Also, there is always a chance that a specific USB drive won't work with a specific computer.  Try a different flash drive, try a different port, and try putting a normal lubuntu/xubuntu onto the yumi multi-boot flash too.

Also, be certain the computer is set to boot off USB.  This is in the BIOS.  Often different vendors have a "boot menu" that can be used to pick a boot device. F2 or F12 are commonly used, IME.

BTW, running off a flash drive will be slower than when installed. USB2 will feel much slower. Best to carve out 25G of space (and 2 empty partitions) and actually install onto the HDD.

---

### Post by Autodave on 2017-04-06
What OS are you running? I believe that Ardour is available for all OSs. Why are you trying to run it from a USB?

---

### Post by kylona on 2017-04-06
> **Autodave said:**
> What OS are you running? I believe that Ardour is available for all OSs. Why are you trying to run it from a USB?

I'm running windows.

Yes Ardour is available for windows but only if you make a donation of at least a dollar. I like to avoid using a credit card on the internet as much as possible. Call me paranoid. Not to mention Ubuntu studio has a lot of other useful software out of the box like JACK and different mixers and such. 




> **TheFu said:**
> 

Is ubuntu studio in the list of Yumi distros?  I don't recall and can't get to a Windows PC for a few hours.  If not, you'll want to change the ISO name so that it looks like one of the other Ubuntu ISOs.  Make the mask match a pattern used by some other Ubuntu flavor.

Also, there is always a chance that a specific USB drive won't work with a specific computer.  Try a different flash drive, try a different port, and try putting a normal lubuntu/xubuntu onto the yumi multi-boot flash too.

Also, be certain the computer is set to boot off USB.  This is in the BIOS.  Often different vendors have a "boot menu" that can be used to pick a boot device. F2 or F12 are commonly used, IME.

BTW, running off a flash drive will be slower than when installed. USB2 will feel much slower. Best to carve out 25G of space (and 2 empty partitions) and actually install onto the HDD.


Yeah it is on the list. YUMI says its added the OS to the menu but its not showing up. It might be because I first used the UEFI installer that is still in BETA first. It failed to boot using the UEFI because the kernel failed to sync, which as I understand it means it could not find a proper place for its root directory correct? So I downloaded the Legacy boot version and uninstalled Ubuntu studio and reinstalled. (This might have been where things got messed up)

I just bought a new USB drive and its a SanDisk which is the same brand as the USB drives YUMI recommends. Thanks for the advice I'll try lUbuntu and see what happens.

---

### Post by kylona on 2017-04-06
So I installed lubuntu and it also didn't show up. So I deleted all the files put on by YUMI (BOOT, EFI, MULTIBOOT ect) and reinstalled Ubuntu studio and it showed up in the menu! Progress! But it still failed to boot. It said "squashfs error data probably corrupt" 

Do you think it would install properly? If I were to make a partition for it to go in like TheFu suggested?

---

### Post by TheFu on 2017-04-06
I've never used UEFI anywhere.  Only have 1 system where it might work, but didn't want to screw around with it.
I've had issues with name brand flash drives in certain systems. 

I should mention, I use Yumi all the time too. It is my primary Windows --> multiboot tool.

You'll need 2 partitions, minimal. Those are / and swap. Perhaps more will be needed depending on selections made during installation - LVM, encryption, etc. Those choices demand more partitions.

If you have 25G of storage on a real disk (SSD/HDD) and can support at least 2 more partitions (if you are using GPT, that isn't an issue), Just make some free, unallocated, space on the existing disk drive, backup everything you can't afford to lose (stupid mistakes happen all the time), and install.  When I say backup, I mean **everything on the disk**. EVERYTHING.

---

### Post by kylona on 2017-04-06
Sounds like a plan. My computer has a solid state drive which currently has Windows and such on it and a TB HDD that is almost empty. I think I will try to install on the HDD (it will be fast enough). 

Usually when I decide to install a distro I just select the install option from my live booting USB, but that's not seeming like it will work. What are the options to directly install?

---

### Post by kylona on 2017-04-07
Just an update. I can't even get it to install from the usb. However I had the chance to try it on another computer and it booted in less than 60 seconds. So I guess my computer is not happy to boot from a USB. Sad day.

---

### Post by TheFu on 2017-04-07
As mentioned in #2 above:
* Try a different flash drive.
* Try a different USB2 port. Do not use hubs or USB3.
* Ensure that the BIOS allows booting from a USB device.

---

### Post by kylona on 2017-04-08
Ok. Weird story.

My system is for sure a 64 bit system. It runs 64 bit windows 10 usually. I just downloaded a 32 bit iso for KXStudio and ran it through YUMI. I boot it and Ta Daaaa! Boots not problems. I hope this will work for someone else some day too.

---

