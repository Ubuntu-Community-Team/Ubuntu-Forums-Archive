---
title: "Ubuntu/Win7/Win8 works with GRUB?"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by dorruk on 2013-01-01
Hey guys, I currently am dual booting Windows 7 and 8 and would like to include Ubuntu to the family, installing it to a different partition.

I can just go ahead and do it but I have concerns only about the bootloader. I don't want Ubuntu to automatically add itself to the Windows bootloader because I may consider adding non-Windows operating systems in the future so I want GRUB or GRUB2 instead.

Thing is, how do I guarantee GRUB will definitely see my Windows and everything? What should be the precautions to take in order to prevent not being able to boot Windows 7 and 8? Whatif GRUB fails to read NTFS? That would be a huge problem to me because I'm new with Linux.

Thanks in advance.

---

### Post by darkod on 2013-01-01
Grub2 boots windows just fine, and understands ntfs without problems.

What you should be careful about is whether you are using UEFI boot, or the older legacy/BIOS boot. If you are using UEFI, you have to install ubuntu in uefi mode too. In that case the uefi boot manager does the booting actually, not grub2.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have the older legacy boot, there should be no problems at all. But you might not see all three OSs in the menu. This is because windows combines the boot files when you have more than one version installed. If the boot files got combined during your windows installs, grub2 will report only one windows entry. Booting that entry will then open the windows bootloader which will have options for both windows OSs. So you will have to go through two menus to boot windows. But this is not limitation of grub2, it depends how windows was installed and that it combines its boot files.

---

### Post by dorruk on 2013-01-02
I have the option to enable/disable UEFI Boot in BIOS. Disabled by default. What do you recommend? Just go with legacy boot, or does UEFI have advantages?

Btw my PC is x64.

---

### Post by darkod on 2013-01-02
For me personally, uefi is only problems, no advantages. It makes dual boot more difficult so you stick with only windows. :)

When buying my new board few weeks ago I got sure there is an option to disable uefi and use legacy boot.

But the problem is if your computer came preinstalled with windows in uefi mode. In that case you can't simply disable uefi boot in bios, since windows will not be able to boot in legacy if it was installed in uefi.

But since you seem to be sure you have windows in legacy mode, even better. Simply install ubuntu and that's it.

You might still have the "issue" of combined windows boot files, but that is not up to grub, as explained in my previous post. In that case you will have to go through two boot menus to boot windows.
You can potentially fix that too, but I don't know if it bothers you much or not, if it's worth it.

---

### Post by dorruk on 2013-01-11
It worked! Made sure to be online while Ubuntu is installing. Then GRUB becomes up to date to avoid any compatibility issues. Also windows boot files combined just as you said, but it's cool.

---

