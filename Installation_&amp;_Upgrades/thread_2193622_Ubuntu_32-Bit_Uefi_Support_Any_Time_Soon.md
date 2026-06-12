---
title: "Ubuntu 32-Bit Uefi Support Any Time Soon?"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by JasonMRaub on 2013-12-13
I have a device with 32-Bit Uefi & currently no Linux distro supports 32-Bit Uefi. Will Ubuntu start supporting 32-Bit Uefi in future releases? I hope it does. I currently have no work around in Uefi to support non Uefi 32-Bit distros & my device will not run a 64-Bit operating system due to the 32-Bit Uefi. Thanks for any pointers. I'm really just curious why all these Linux distros lack support for 32-Bit Uefi, obviously because I want to run Linux on my device, Ubuntu preferably.

---

### Post by ubfan1 on 2013-12-13
M. Garrett discusses this issue:
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Not that it's impossible, just too many setups needed.

---

### Post by JasonMRaub on 2013-12-13
I'm about to break my device due to Windows 8.1 deleting both my well thought out text entries on this reply. I read you're linked web page, thanks, it makes sense. This is exactly why I want Linux support on my device, I'm about to break it in half due to Windows 8.1 frustrations. I requested legacy boot mode from my device manufacturer in there support forums, after two bios updates there is still no legacy boot option. I hope we can talk about this more, thanks. If you would like to know the device I am using I will share but I think it takes away from the discussion. It would be great to run Ubuntu on this device, I would be so happy.

---

### Post by oldfred on 2013-12-13
I think your device is intended to be more like the totally locked down iPad type devices. 

It is one of the first with the 32 bit UEFI and no BIOS boot support and they know Linux does not have any of that available. And since it is very new, I would not expect much help soon.

If enough new devices are sold someone will recompile and make some distribution work.

 New Intel Atom - Nov 2013 x86 secure boot can be turned off, but only 32 bit UEFI which no one else has.
 Intel Atom SoC systems that ship with Windows 8/8.1 32-bit provide 32-bit UEFI-only firmware with no BIOS compatibility option (no CSM). In UEFI terms these systems are called Class 3 systems (this term is not specific to 32-bit), ie. UEFI-only with no BIOS CSM.
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)

---

### Post by JasonMRaub on 2013-12-13
I think you're right about them locking the device down, its a shame they do it but understandable, imagine users installing Linux then deciding they want windows back but can't cause its windows 8.1 OEM and that product key from OEM won't work so they send it back to the manufacturer, so the manufacturer kind of gets ripped off. I'm not trying to rip any one off though, if I mess up my device trying a different operating system its my own fault, not likely it will get messed up though. I just want to run Linux on a product I spent my money on, fair enough? I believe. Thanks again for the reply.

---

### Post by JasonMRaub on 2013-12-14
I see what you're saying. Class 3 devices have no bios support? That's kind of scary to me.

---

### Post by JasonMRaub on 2013-12-14
I've been trying to get the bios rom file for this device from the bios chip manufacturer rather than the OEM to flash with a software tool to see if it's not locking me out like the OEM version is, I've had not luck so far but I will share the bios chip so may be some one reading this can find the rom for the chip. I'm thinking it has to be device specific flashed onto the chip? if that's the case then I'm out of luck for now. Bios Chip Name: Winbond 25X/Q Series . Firmware ID: 1AGREE026 . Firmware GUID: 49241ea6-b2ec-475c-a0cd9f1dc1d17344 . It's American Megatrends Aptio Motherboard? Or bios I'm not sure, that's what it says when I start the bios> Aptio American Megatrends. Thanks Again.

---

### Post by oldfred on 2013-12-14
I do not think there will be a BIOS chip. 
I did see one user who was attempting to recompile grub2 himself in a 32bit enviroment.
There are other boot loaders for UEFI than grub.

This says HP had a 32 bit elilo.
[http://en.wikipedia.org/wiki/LILO_%28boot_loader%29](http://en.wikipedia.org/wiki/LILO_%28boot_loader%29)

Or perhaps the efistub and put kernel in efi partition. May need kernel that is compiled to work with that and I am not sure if 32 bit Ubuntu is, but then you may only need to recompile 32 bit kernel with correct switches.
[https://wiki.archlinux.org/index.php/Boot_Loaders](https://wiki.archlinux.org/index.php/Boot_Loaders)

---

### Post by JasonMRaub on 2013-12-14
Thanks. I'll look into those two links you shared some time soon. I know some stuff about Linux, enough to tinker around and get it working how I want pretty much, so some things you're saying go over my head but if I tinker around more i'll know what you mean. I grew up with Windows so learning another operating system takes a while for me, but I'm learning. If any one has more to say on this topic that's great, if it needs closed? That's fine too, I'm kinda new to these forums and should read the rules. Thanks.

---

### Post by oldfred on 2013-12-15
I have never complied a kernel. 
Last time I did a lot of compiling was 1965 when learning Fortran and assembly language. 

But there are instructions some where. But with the kernel I gather there are many switches. Some use that to optimize so kernel only has parts needed for their system. Most distributions have the parts needed for x86 either 32 bit or 64 bit standard server or desktop systems.

---

