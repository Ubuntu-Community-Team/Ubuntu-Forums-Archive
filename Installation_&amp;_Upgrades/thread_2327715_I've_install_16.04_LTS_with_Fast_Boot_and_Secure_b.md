---
title: "I've install 16.04 LTS with Fast Boot and Secure boot enabled. Question..."
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by hydn79 on 2016-06-13
Excerpt from here: [https://help.ubuntu.com/16.04/installation-guide/amd64/ch03s06.html#disable-fast-boot](https://help.ubuntu.com/16.04/installation-guide/amd64/ch03s06.html#disable-fast-boot)

[I]"3.6.4. Disabling the Windows 8 &#8220;fast boot&#8221; feature - [COLOR=#000000][FONT=liberation sans]Windows 8 offers a feature called &#8220;fast boot&#8221; to cut down system startup time. Technically, when this feature is enabled, Windows 8 does not do a real shutdown and a real cold boot afterwards when ordered to shut down, but instead does something resembling a partial suspend to disk to reduce the &#8220;boot&#8221;time. As long as Windows 8 is the only operating system on the machine, this is unproblematic, but it can result in problems and data loss when you have a dual boot setup in which another operating system accesses the same filesystems as Windows 8 does. In that case the real state of the filesystem can be different from what Windows 8 believes it to be after the &#8220;boot&#8221; and this could cause filesystem corruption upon further write accesses to the filesystem. Therefore in a dual boot setup, to avoid filesystem corruption the &#8220;fast boot&#8221; feature has to be disabled within Windows. [/FONT][/COLOR][COLOR=#000000][FONT=liberation sans]It may also be necessary to disable &#8220;fast boot&#8221; to even allow access to UEFI setup to choose to boot another operating system or debian-installer. On some UEFI systems, the firmware will reduce &#8220;boot&#8221; time by not initialising the keyboard controller or USB hardware; in these cases, it is necessary to boot into Windows and disable this feature to allow for a change of boot order."[/FONT]

[/COLOR][/I][COLOR=#000000][FONT=liberation sans]So my question, I have Ubuntu 16.04 as the single OS installed on my laptop. I kept fast boot and secure boot enabled. Are there still risk? Is there any benefits to fast boot for Ubuntu only intall?

[/FONT]Thanks![/COLOR][I][COLOR=#000000]
[/COLOR][/I]

---

### Post by oldfred on 2016-06-13
There are two different settings. Windows & UEFI.

Windows has its fast start up or always on hibernation. If you only have Ubuntu that does not matter.

But UEFI has fast boot which is not related to Windows fast start up.
UEFI fast boot assumes system is configured exactly as it was before rebooting. It can speed boot for both Ubuntu & Windows. But if hardware or configuration otherwise changes, then you may need to go into UEFI to change settings. And it can be so quick you have no time to press del for f2 key to get into UEFI.

Often cold boot uses normal not fast boot.
With my motherboard, I had fast boot on/off settings for both cold boot & warm (reboot). And a setting for delay. I set delay to 3 seconds so if quick I can get into UEFI.
If system boots to grub, last entry in grub menu should also take you to UEFI. 'System setup'

If no issues booting with Secure Boot on, then it is fine. Grub does not normally let you boot Windows from grub menu if Secure boot is on. But if no Windows not an issue. Some systems also are not friendly to anything other than Windows and they may need secure boot off.

---

### Post by hydn79 on 2016-06-13
Thanks. It a 2013 Alienware 14. I would have to reboot an had a look. But I'm 95% sure its labeled "Windows 8 Fast boot" so probably pointless to keep enabled? What I have noticed is when enabled the Alienware bios splash screen or time it takes to begin loading the OS is greatly reduced. So not sure.

---

### Post by oldfred on 2016-06-13
It was Microsoft that required vendors to include that UEFI option. If yours calls it Windows that may be why?

Windows was/is so slow booting, the have to have UEFI settings & hibernation to make it seem like it boots faster. But those are work arounds and do reduce start up time for most users.

---

### Post by hydn79 on 2016-06-13
I'll update here/close thread after a week or two of reboots. (if thats ok) Happy to be completely free of Windows. Linux and especially Ubuntu has come a long way! I'm running 2 extended desktop external monitors + Corsair keyboard with no issues. Plug and play pretty much. 

Thanks again!

---

### Post by yoshii on 2016-06-15
If you ever need to use Legacy/MBR-BIOS boot in the future, you will possibly need to disable Secure Boot to be able to enable Legacy/MBR-BIOS booting.  
This was the situation on my HP ENVY desktop.

---

