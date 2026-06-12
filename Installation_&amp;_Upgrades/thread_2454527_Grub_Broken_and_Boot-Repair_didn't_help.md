---
title: "Grub Broken and Boot-Repair didn't help"
date: 2020-12-01
forum: Installation &amp; Upgrades
---

### Post by hex25 on 2020-12-01
Hi,

I'm using Ubuntu 20.04 alongside Windows 10 and suddenly, after a Windows 10 or Ubuntu update, Grub is broken and the system boots directly to Windows 10.
Below you can find the error message that is shown prior to Windows boot.

```

Failed to open \EFI\UBUNTU\BOOT\grubx64.efi - Not Found  
Failed to load image \EFI\UBUNTU\BOOT\grubx64.efi: Not Found    
start_image() returned Not Found  
```

I tried to fix the error with Boot-Repair with no success.
In this [pastebin ]("http://paste.ubuntu.com/p/CTffMrWjky/")you can see the output
[http://paste.ubuntu.com/p/CTffMrWjky/](http://paste.ubuntu.com/p/CTffMrWjky/)

Thank you very much!

---

### Post by yancek on 2020-12-01
The reason for this is explained on lines 95 & 96 of boot repair.  You need to go into the BIOS firmware for EFI boot options and select Boot 0002, shown on line 68 of boot repair.

---

### Post by tea for one on 2020-12-01
I don't think grub is broken.

Have a look at line 7 of your report - Windows is hibernated.

Boot into Windows, turn off Fast Start Up and shut down Windows without hibernation.

---

### Post by hex25 on 2020-12-01
Thank you for your help!
I managed to boot Ubuntu by changing the boot order in EFI boot options.
I didn't consider this solution because I used the system in this configuration for about 1 year without the need to touch the boot order or Fast Start-up options in Windows.
Before that, I disabled Fast Start Up, reinstalled Grub and other solutions, and to me it's weird that somehow the boot was messed like this.

---

### Post by oldfred on 2020-12-01
Windows updates turn Windows fast start up back on.
The also can run UEFI updates which may change some UEFI settings to defaults.

Back in BIOS days all settings were changed to defaults, with UEFI only some are. 
But I keep a list, so I know what settings I change and then after I do a UEFI update I can check if settings are still correct.
I do not have Windows, so know when UEFI is being updated. Windows may not tell you that is one of the updates it is doing.
A few newer systems also support UEFI update from Ubuntu with fwupd. Again you may not know it is done, unless you monitor updates.

---

### Post by hex25 on 2020-12-01
> **oldfred said:**
> Windows updates turn Windows fast start up back on.
The also can run UEFI updates which may change some UEFI settings to defaults.

Back in BIOS days all settings were changed to defaults, with UEFI only some are. 
But I keep a list, so I know what settings I change and then after I do a UEFI update I can check if settings are still correct.
I do not have Windows, so know when UEFI is being updated. Windows may not tell you that is one of the updates it is doing.
A few newer systems also support UEFI update from Ubuntu with fwupd. Again you may not know it is done, unless you monitor updates.

Thanks, good to know, I will consider that in the future.

---

