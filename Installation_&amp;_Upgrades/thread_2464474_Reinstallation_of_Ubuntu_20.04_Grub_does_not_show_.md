---
title: "Reinstallation of Ubuntu 20.04 Grub does not show option for my dual boot Windows 10"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2021-07-02
For the second time, Ubuntu stopped allowing me to boot it up.  I tried recover options from Advanced Options, Fdsk on my ubuntu drive, all  to no avail.  Finally, I chose to reinstall from my USB stick.  Installed to the existing Ubuntu partitions, but upon boot, Grub no longer gives me an option to select Windows 10.  If anyone can offer suggestions, I would be most appreciative.  Windows directory still resides on my hard drive.

Thanks.

Caruso

---

### Post by Impavidus on 2021-07-03
UEFI or bios/legacy? If UEFI (most likely), use the UEFI menu to select the Windows bootloader. That should start Windows directly, bypassing grub. Then make sure Windows Fast Startup is disabled. If it's enabled, update-grub cannot detect Windows and doesn't put it in the menu. Windows can automatically enable Fast Startup. When disabled, update-grub on Ubuntu should detect Windows and put it back on the menu.

If bios/legacy, you need a Windows repair disk.

---

### Post by carusoswi on 2021-07-03
> **Impavidus said:**
> UEFI or bios/legacy? If UEFI (most likely), use the UEFI menu to select the Windows bootloader. That should start Windows directly, bypassing grub. Then make sure Windows Fast Startup is disabled. If it's enabled, update-grub cannot detect Windows and doesn't put it in the menu. Windows can automatically enable Fast Startup. When disabled, update-grub on Ubuntu should detect Windows and put it back on the menu.

If bios/legacy, you need a Windows repair disk.

Thank you for the reply.  In my bios, I can enable/disable UEFI, but I don't see how that enables me to boot into Windows.  When enabled, I get no Grub menu at all, when disabled, Grub appears with only an option for Ubuntu.  What am I missing?



Thanks.


Caruso

---

### Post by grahammechanical on 2021-07-03
What is your reply to this statement?

> Then make sure Windows Fast Startup is disabled. If it's enabled,  update-grub cannot detect Windows and doesn't put it in the menu.

Also, if Ubuntu is installed in BIOS/Legacy mode then it cannot boot Windows 10 which is installed in UEFI mode. If we load the Ubuntu live session (USB stick) in UEFI mode then Ubuntu will install in UEFI mode and the Grub bootloader should put Windows 10 as a boot option. Provided, of course, that Windows 10 does not have Fast Startup enabled. 

As I do not have a UEFI motherboard I cannot direct you how to use the UEFI menu to boot Windows 10. But apparently the UEFI menu can allow you to boot Windows 10. On the other hand, disabling UEFI and enabling BIOS/Legacy will prevent Windows 10 from loading. That is my understanding.

We are trying to get information from you about your installation. Without that information we cannot advise you accurately. So, we ask, is Ubuntu installed in UEFI mode or BIOS/Legacy mode? Is Windows 10 Fast startup disabled. 

Regards

---

### Post by Impavidus on 2021-07-03
> **carusoswi said:**
> 

Thank you for the reply.  In my bios, I can enable/disable UEFI, but I don't see how that enables me to boot into Windows.  When enabled, I get no Grub menu at all, when disabled, Grub appears with only an option for Ubuntu.  What am I missing?



Thanks.


Caruso
This suggests you installed Ubuntu in legacy mode. Dual booting Windows 10 and Ubuntu in legacy mode isn't such a good idea. Did you have a legacy system before or was it an UEFI system, and you accidentally reinstalled Ubuntu in legacy mode?

I assume you've still got your live usb at hand. Try [boot repair]("https://help.ubuntu.com/community/Boot-Repair") and create a boot info summary. That should tell us most of the details.

---

### Post by carusoswi on 2021-07-05
> **grahammechanical said:**
> What is your reply to this statement?



Also, if Ubuntu is installed in BIOS/Legacy mode then it cannot boot Windows 10 which is installed in UEFI mode. If we load the Ubuntu live session (USB stick) in UEFI mode then Ubuntu will install in UEFI mode and the Grub bootloader should put Windows 10 as a boot option. Provided, of course, that Windows 10 does not have Fast Startup enabled. 

As I do not have a UEFI motherboard I cannot direct you how to use the UEFI menu to boot Windows 10. But apparently the UEFI menu can allow you to boot Windows 10. On the other hand, disabling UEFI and enabling BIOS/Legacy will prevent Windows 10 from loading. That is my understanding.

We are trying to get information from you about your installation. Without that information we cannot advise you accurately. So, we ask, is Ubuntu installed in UEFI mode or BIOS/Legacy mode? Is Windows 10 Fast startup disabled. 

Regards

UEFI was enabled in my bios when I installed Ubuntu.  I do not know how to tell if my Windows 10 was installed in UEFI mode or Legacy mode.  Would it helped if I installed Ubuntu again in Bios/Legacy mode?

Thanks.

Caruso

---

### Post by Impavidus on 2021-07-05
Can you create the boot info summary I mentioned above? That would give us some facts.

---

### Post by tea for one on 2021-07-05
> **carusoswi said:**
> UEFI was enabled in my bios when I installed Ubuntu.  I do not know how to tell if my Windows 10 was installed in UEFI mode or Legacy mode.  Would it helped if I installed Ubuntu again in Bios/Legacy mode?


Even if UEFI and Legacy were enabled in your firmware, it depends on how you booted the USB installation device.

Boot in UEFI mode = Install in UEFI mode
Boot in Legacy mode = Install in Legacy mode

To check how Windows is installed:-
System Information > System Summary > BIOS mode > UEFI or Legacy

To check how Ubuntu is installed, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Anyway, please run the boot-repair report as requested by [COLOR="#0000FF"]Impavidus[/COLOR].
The information in the report will provide concise details about the status of each OS on your PC.

---

### Post by carusoswi on 2021-07-09
Thanks for the replies.  My cleaning lady mislaid my USB stick, so I will have to get another in order to have a live Ubuntu "CD". Will try your suggestions and let you know what ijnfo shows up.
Caruso

---

