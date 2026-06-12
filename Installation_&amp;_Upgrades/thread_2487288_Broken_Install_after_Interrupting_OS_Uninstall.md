---
title: "Broken Install after Interrupting OS Uninstall"
date: 2023-05-29
forum: Installation &amp; Upgrades
---

### Post by milifilou on 2023-05-29
So, I did a big oopsie. I saw progress stall on my os uninstall of windows, and decided a nice reboot would probably fix the issue.
Yes, in hind sight that's absolute rookie material. I now badly boot to grub, hopelessly out of my depth on how to fix that. I have used a live usb of ubuntu to run the boot-repair diagnostic, and would like some insight into what to do next.
Here's the paste bin: [https://paste.ubuntu.com/p/bHqx44HXkN/](https://paste.ubuntu.com/p/bHqx44HXkN/)
I will state in advance that this laptop has nothing of value on it, so I would be willing to nuke the install with a new install. The only things keeping me from that are the fear that I could mess it up worse somehow, and a handful of files that are of low importance and probably on my external harddrive anyway.

---

### Post by grahammechanical on 2023-05-29
You do not have Ubuntu or Opensuse on sda. You have Grub boot files for both Ubuntu and Opensuse in sda2 but those boot files cannot find the grub.cfg file for you do not have /boot/grub/grub.cfg location. This is why Grub is loading to a rescue prompt.

You could try entering the UEFI utility and directing the motherboard to boot the Microsoft boot manager.

Regards

---

### Post by milifilou on 2023-05-30
Hmm.
Sounds like the os-uninstall, which was meant to change the grub file to completely remove the windows install, was able to remove the grub file but not write a new one.

The UEFI for this Toshiba laptop is rather unhelpful, considering that my boot priority is USB stick first, and I still had to mess with grub to access my live USB with Ubuntu.
The Microsoft boot manager has similar issues, as it didn't list my Ubuntu install in the past. When I used to boot, it first chose between Ubuntu and windows boot manager, and windows boot would give me the option for windows or secure booting windows

Boot repair does not have a recommended fix for me at this point.

Thanks for the help



Thank you

---

### Post by tea for one on 2023-05-30
> **milifilou said:**
> Sounds like the os-uninstall, which was meant to change the grub file to completely remove the windows install, was able to remove the grub file but not write a new one.
How were you removing Windows?
Boot-repair shows you still have Windows 8 or 10 on sda4 - line 103
> **milifilou said:**
> Boot repair does not have a recommended fix for me at this point.
Boot-repair cannot repair Windows Boot Manager, you need Windows tools for this task.
> I will state in advance that this laptop has nothing of value on it, so I would be willing to nuke the install with a new install
Probably the best solution now. Would that be Windows 10/11 or Ubuntu 22.04?

---

### Post by milifilou on 2023-05-30
I was removing windows using an application called OS-uninstaller. Considering the circumstances, there is a non-zero chance that it somehow decided to uninstall the ubuntu it was running on instead of the windows.

I wasn't trying to repair the windows boot process, since I was using a different boot manager (grub? ubuntu noob writing here) to enter the windowsboot, and that first step wasnt happening.

I will be trying to install Ubuntu 22.04 again, since all of this started with me trying to remove Windows.
I have gone through Windows installs before, but I have little motivations in owning another one.

---

### Post by yancek on 2023-05-30
There is no point in 'uninstalling' an OS, simply format the largest windows partition with a Linux filesystem.  You can do the same to the other partitions for windows later if you want.  Do not remove the vfat/EFI partition.   sda7 and sda8 have Linux filesystem on them but nothing else shows as mentioned above so the install wasn't complete or something else happened.  There are entries for both Ubuntu and Opensuse in the EFI menu but nothing to boot on the drive so your best option is to reinstall both or either.

---

