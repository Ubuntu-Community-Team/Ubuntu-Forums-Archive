---
title: "Wont boot to USB"
date: 2019-09-12
forum: Installation &amp; Upgrades
---

### Post by scott_2 on 2019-09-12
I have an ASUS computer running windows 10. 
I want to install Ubuntu onto this machine, so I created a Ubuntu bootable USB, but no matter what I do, when I restart my computer, it will not boot into to live USB, it just goes straight into Windows. I have tried all of the USB ports on my computer. I have tried different USBs. I have disabled secure boot and fast boot and enabled CSM. 
The USB doesnt even show up in the BIOS as something that can be booted to. 
I've googled this issue and followed the suggestions of dozens of different sites, but no matter what I do, it still goes straight into Windows.

Can anybody help me please?

Thanks

---

### Post by ubfan1 on 2019-09-12
Assuming your USB install media is good (hashcheck the downloaded ISO, run a media check on the newly created USB, boot on another machine), you might have a problem with the Windows Power option "fast boot" (not the BIOS setup fastboot which just gives you a few seconds to type a function key).  Ensure no "shutdown" results in hibernation, and that fastboot is off.  Another possible problem is with ASUS resetting the boot order when the USB device is not present.  You should be able to see it, and set it to first in the boot order, but it may take a few boots with the device present before it shows up. You want Windows and Ubuntu installed in the same mode, probably UEFI, so disable all the legacy CSM stuff you set.  Leave fastboot disabled in the BIOS, secure boot should not matter much these days unless you have proprietary drivers for things like video (Nvidia,...).  Definitely turn if off in that case.

---

### Post by pcfan1234 on 2019-09-13
If you have installed Windows in EFI mode do not install Ubuntu in CSM mode. Disable it.
Make sure Fastboot is disabled in windows.
Then restart from windows. GO into the BIOS and make sure you boot the usb device with UEFI not Legacy/CSM.

---

### Post by yancek on 2019-09-13
If you haven't resolved this issue, it would be a good idea to read the Ubuntu documentation on dual booting with windows 10 at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

