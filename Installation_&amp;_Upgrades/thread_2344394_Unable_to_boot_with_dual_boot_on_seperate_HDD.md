---
title: "Unable to boot with dual boot on seperate HDD"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2016-11-25
Hi All,

I have been having issues with booting up my system.
I initially had a dual boot with Older Ubuntu and Windows 7 installed.
I have recently installed a 16.04 LTS on a new SSD also
Now when i have both the HDD connected or just the older one it does not boot up.
If i have just the new SSD connected , everything is smooth and fine.

I was reading about the new UEFI thing and wondered if the way installed the 1604 would have messed things up?

Could you guide me to investigate and fix this.

---

### Post by ajgreeny on 2016-11-25
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system  and should give us much more detail of whether your Ubuntu is installed in UEFI mode.

Windows 7 was not UEFI by default but used MBR/BIOS, so you needed to install Ubuntu in that legacy mode as well, but all this detailed info will be shown by the report.

---

