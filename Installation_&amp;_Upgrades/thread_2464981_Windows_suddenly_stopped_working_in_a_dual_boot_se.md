---
title: "Windows suddenly stopped working in a dual boot setup with Ubuntu 20.04"
date: 2021-07-18
forum: Installation &amp; Upgrades
---

### Post by ankursharma309 on 2021-07-18
Hi, I had a nicely working dual boot setup with the factory Windows 10 that came with my computer and Ubuntu 20.04.
However, suddenly the Windows stopped working with this error:

Error: file /efi/microsoft/boot/bootmgfw.efi not found

And then I tried to boot-repair on a usb disk and tried the recommended repair and got this message :

[COLOR=#AFA99E][FONT=-apple-system]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
[/FONT][/COLOR]
I am not sure how to proceed because I have no understanding of grub, uefi etc so I would appreciate someone's help before I mess up my system completely.
Here is the full boot info log:
[https://pastebin.ubuntu.com/p/JdtqYDf5HV/](https://pastebin.ubuntu.com/p/JdtqYDf5HV/)

---

### Post by tea for one on 2021-07-18
> **ankursharma309 said:**
> Hi, I had a nicely working dual boot setup with the factory Windows 10 that came with my computer and Ubuntu 20.04.
However, suddenly the Windows stopped working with this error:

You mentioned Windows 10 yet:-

[COLOR="#0000FF"]Line 60[/COLOR] - OS#2:   [COLOR="#FF0000"]Windows XP[/COLOR] on nvme0n1p3
[COLOR="#0000FF"]Line 368[/COLOR] - Grub-efi would not be selected by default because: legacy-win no-win-efi 

You have Ubuntu in UEFI mode and Windows in Legacy mode.

For dual booting, you need both installations in the same mode, here is some more info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The best solution is to back up all your data (both Windows and Ubuntu) and re-install both systems in UEFI mode with GPT.

You could try to only re-install Windows 10 in UEFI mode but that will probably over-ride the existing grub?

---

### Post by yancek on 2021-07-18
The boot repair output shows you have a GPT drive.  Microsoft requires an EFI install on a GPT drive.  Boot repair does not show the existence of the file required by windows to boot in UEFI mode (bootmgfw.efi ).  If you had been booting windows 10 on a GPT partition, you would have needed that file.  That cannot be replaced or repaired by Linux/Ubuntu or boot repair.  Not sure what happened to that file or the other windows EFI files?

You would not have been able to boot windows in Legacy mode either as there is no windows boot code in the MBR which would be necessary for a Legacy/CSM install.

If you have a windows install device, you might be able to repair/replace that file but you will likely need to go to the microsoft site or some windows forum to get the procedure.  

Boot repair is designed primarily to repair Linux boot problems.  It can do some things with windows such as adding a windows boot entry but it can't replace required windows efi boot files which are missing on your device.

Probably the simplest solution is a reinstall suggested above after a backup.

---

### Post by ankursharma309 on 2021-07-18
Thanks both of you, I think there was probably some Windows updates which messed up the EFI file and converted the windows into a legacy install. Not sure if that is even possible but thats my guess. Also, not sure why it detected the windows OS as WindowsXP, I am assuming that is a bug in the boot info software.

I will do as you suggested and will backup files from Windows and just reinstall Windows in EFI mode. Thanks for the help :)

---

### Post by tea for one on 2021-07-18
Boot-repair stated [COLOR="#0000FF"]Windows XP[/COLOR]
Your original post mentioned [COLOR="#FF0000"]factory Windows 10 that came with my computer[/COLOR]
Then [COLOR="#800080"]Windows updates which messed up the EFI file and converted the windows into a legacy install.[/COLOR]

Something does not ring true here?

---

### Post by Impavidus on 2021-07-19
Boot-repair definitely got confused. It thinks Windows was installed in legacy mode as there's no Windows entry in the EFI partition, then it suggest to convert Ubuntu to legacy too. But this can never be a legacy system, as it detects the NTFS partition as Windows 8 or 10 and the drive is GPT partitioned.

Somehow the Windows boot files disappeared from the EFI partition. I can imagine buggy update code in either Windows or Ubuntu, a system crash while updating the files in the EFI partition or a broken hard drive. A Windows repair disk may fix this.

---

