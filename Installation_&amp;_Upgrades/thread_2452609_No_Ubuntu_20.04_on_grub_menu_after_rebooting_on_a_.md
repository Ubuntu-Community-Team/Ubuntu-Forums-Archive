---
title: "No Ubuntu 20.04 on grub menu after rebooting on a triple boot system"
date: 2020-10-25
forum: Installation &amp; Upgrades
---

### Post by SUPERFITTER on 2020-10-25
I triple booted Ubuntu 20.04 on an existing Zorin 15 os and Ubuntu 16.04 os.   
When I boot there is no Ubuntu 20.04 on grub menu just Zorin and Ubuntu 16.04? 
The Ubuntu 16.04 is on a second hard drive. 
Is there away to correct this situation?

Thank You

---

### Post by oldfred on 2020-10-25
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Are all systems installed in UEFI boot mode or all in BIOS boot mode.
Are you using LVM and need lvm2 in new install to see old install?

---

### Post by SUPERFITTER on 2020-10-26
Downloaded [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and it fixed my grub menu.

Thank You 
Oldfred

---

