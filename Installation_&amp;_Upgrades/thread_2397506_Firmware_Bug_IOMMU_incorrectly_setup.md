---
title: "Firmware Bug IOMMU incorrectly setup"
date: 2018-07-30
forum: Installation &amp; Upgrades
---

### Post by langdon-7 on 2018-07-30
new ACER Laptop. Cant install 18.04 becuase of Firmware Bug 

[Firmware Bug]: AMD-Vi : IOAPIC[4] not in IVRS table

An online search suggests the manufacturer has a error in the Firmware. The OIMMU table is either not present on incorrectly setup. I found instructions to correct this manually, but the instructions say things like

[LEFT][COLOR=#242729][FONT=Arial]"Boot your kernel by adding [/FONT][/COLOR][/LEFT]amd_iommu_dump=1[LEFT][COLOR=#242729][FONT=Arial] to the kernel options. You can do this via grub menu during boot."


What does this actually mean? How do I "add to the kernel options".  I can get to a grub menu but what then ? .he kernel is not loaded and I cant edit /etc/default/grub because an OS has never been loaded on the system. I cant manually load the kernel. If I type ls to find the file system I just see another >GRUB prompt. 

Send it back to ACER right?

[/FONT][/COLOR][/LEFT]

---

### Post by deadflowr on 2018-07-30
What do you see the Grub menu (which has entries for Ubuntu and advanced Options)
or do you see GRUB prompt>

The former should only need to press e to invoke the grub edit option, which you can then add your setting to the line right after the quiet splash part, then it should run.
If the latter then something else is going on, as that's typical of grub being in a messy state.

To Edit Grub:
[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter]("https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter")

Grub Prompt rescue:
[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux%20]("https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux%20")

And no I don't think you need to return the machine just yet.

---

### Post by oldfred on 2018-07-31
Have you updated UEFI from Acer. 
All systems need to be on latest available UEFI anyway, for Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Both Windows & Linux have updated kernels, but new variants regularly seem to be found.

---

### Post by langdon-7 on 2018-07-31
thanks for replies. 

I looked for a Firmware update on the ACER website, but there was no update. The Laptop has gone back.

---

