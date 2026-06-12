---
title: "GRUB terminal appears after fixing GRUB menu"
date: 2020-12-24
forum: Installation &amp; Upgrades
---

### Post by atinesh2 on 2020-12-24
[COLOR=#191E1E][FONT=Lato]Hello guys, I have a PC with 3 hard disks[/FONT][/COLOR]

[COLOR=#191E1E][FONT=&quot][COLOR=#000000]SSD #1 (Dedicated to Ubuntu 18.04 OS)[/COLOR] [COLOR=#B8312F][SATA3_0][/COLOR]
[COLOR=#000000]SSD #2 (Dedicated to Windows 10 OS)[/COLOR] [COLOR=#B8312F][SATA3_1][/COLOR]
[COLOR=#000000]HDD #3 (For other files)[/COLOR] [/FONT][/COLOR][COLOR=#191E1E][FONT=Lato][FONT=&quot][COLOR=#B8312F][SATA3_2][/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#191E1E][FONT=Lato]Usually, when I boot my system, I get a GRUB menu from where I can choose a specific OS to load (Ubuntu or Windows). For some reason, I had to Reinstall Windows after which I was unable to load Windows from the GRUB menu as it was got corrupted. To fix it, I followed [/FONT][/COLOR][this]("https://www.unixmen.com/how-to-fix-grub-boot-menu-issues-with-boot-repair-utility/")[COLOR=#191E1E][FONT=Lato] post and repaired the GRUB[/FONT][/COLOR]

[COLOR=#191E1E][FONT=Lato]Everything is fine now, I can load both OS without any problem, but there is one small confusion, when I checked the boot order in BIOS I found one extra entry [/FONT][/COLOR][COLOR=#191E1E][FONT=Lato][COLOR=#B8312F]ubuntu (SATA3_1)[/COLOR][/FONT][/COLOR][COLOR=#191E1E][FONT=Lato] i.e. Ubuntu boot manager on Windows hard disk. Usually, there should be only 2 options[/FONT][/COLOR]

[COLOR=#191E1E][FONT=&quot]Windows Boot Manager (SATA3_1)
ubuntu (SATA3_0)[/FONT][/COLOR]

[IMG]https://i.postimg.cc/RF7dCRgD/20201223-212505.jpg[/IMG]

[COLOR=#191E1E][FONT=Lato]If I boot from [/FONT][/COLOR][COLOR=#B8312F][FONT=Lato]ubuntu (SATA3_0)[/FONT][/COLOR][COLOR=#191E1E][FONT=Lato] a GRUB menu appears where I can choose the OS to load and both OS loads without any problem, but when I boot from [/FONT][/COLOR][COLOR=#191E1E][FONT=Lato][COLOR=#B8312F]ubuntu (SATA3_1)[/COLOR][/FONT][/COLOR][COLOR=#191E1E][FONT=Lato] a GRUB terminal appears

[/FONT][/COLOR][IMG]https://i.postimg.cc/PfMyBSpL/20201223-212516.jpg[/IMG][COLOR=#191E1E][FONT=Lato]
[/FONT][/COLOR][COLOR=#191E1E][FONT=Lato]
So my question is can I delete this entry [/FONT][/COLOR][COLOR=#191E1E][FONT=Lato][COLOR=#B8312F]ubuntu (SATA3_1)[/COLOR][/FONT][/COLOR][COLOR=#191E1E][FONT=Lato] somehow, does deleting it will corrupt Windows or Ubuntu boot manager or should I just leave it, as it's not creating any problem[/FONT][/COLOR]

---

### Post by yancek on 2020-12-24
It shouldn't be a problem but it would best to run the Create BootInfo Summary option from Boot Repair and post the link here with the details since you already have boot repair.  Grub files should never be on  a windows partition so I don't know how that happened.

---

### Post by oldfred on 2020-12-24
Boot-Repair should tell us you have an old install of grub that is trying to boot from your data drive's MBR if BIOS or old UEFI entry if UEFI.

---

### Post by atinesh2 on 2020-12-26
> **yancek said:**
> It shouldn't be a problem but it would best to run the Create BootInfo Summary option from Boot Repair and post the link here with the details since you already have boot repair.  Grub files should never be on  a windows partition so I don't know how that happened.
Should I re run boot repair to collect "Create BootInfo Summary" results, I will not perform boot repair will it be safe

---

### Post by tea for one on 2020-12-26
Yes, as requested by [COLOR="#0000FF"]yancek[/COLOR] and [COLOR="#0000FF"]oldfred[/COLOR], please re-run Boot-Repair and create a Boot Info Summary **without** performing the boot repair itself.

It will be extremely safe to just create a Boot Info Summary.

---

