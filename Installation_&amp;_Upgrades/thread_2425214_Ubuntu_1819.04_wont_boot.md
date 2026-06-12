---
title: "Ubuntu 18/19.04 wont boot"
date: 2019-08-22
forum: Installation &amp; Upgrades
---

### Post by Semn on 2019-08-22
Hi, I installed Ubuntu 18.04 some months ago and haven't used it since. I reformatted the partition tables from MSDOS to LPT, but since I Have had problems booting. Now I can't get in at all, how can I go back to MSDOS partition tables without booting in Ubuntu?

Thanks

---

### Post by yancek on 2019-08-22
>  I reformatted the partition tables from MSDOS to LPT, 

Did you mean "GPT"?  Do you have another OS installed and if so, what is it?  The link to the Ubuntu documentation below has a section on "Converting to Legacy MOde" although with the minimal information you have posted, I have no idea if this will resolve your problem.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-08-22
If after install, you changed from MBR to gpt, you probably have to reinstall grub. UUIDs & GUIDs will change. You may also need to edit fstab.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Semn on 2019-08-23
Yes, [COLOR=#000000]GPT and Ubuntu is the only system[/COLOR]

---

### Post by yancek on 2019-08-23
If you are still having problems, you need to download and run boot repair with the Create BootInfo Summary option and post the link you get when it finishes.  Use the Ubuntu install DVD/USB to do it.

---

