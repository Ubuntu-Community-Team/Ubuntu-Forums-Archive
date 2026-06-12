---
title: "Boot Repair Help"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by LifeWithoutWindows on 2012-06-01
Ran the boot repair thingy, results here:
[http://paste.ubuntu.com/1017403/](http://paste.ubuntu.com/1017403/)

What do you wise people think I should do?

---

### Post by wilee-nilee on 2012-06-01
You are missing the /boot/grub/core.img of the grub boot in Ubuntu, you also do not have grub in the sdb hardrives mbr where Ubuntu is installed.

Grub was installed to the sda HD where windows is. Do you have a windows recovery or install disc as well

Hows about you actually describe what is happening.

---

### Post by wilee-nilee on 2012-06-01
So if you have no boot go to the bios, make the sdb hard drive first to be read, before the sda HD, use this tool, and the part where the arrow is in the screenshot this is in the advanced options. It will run and tell you what commands to run. 

Tool.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[ATTACH]219040[/ATTACH]

This should fix it so that if you have the sdb booting first you will  see a grub menu boot to ubuntu and run this command. 
```
sudo update-grub
```We can then get the windows bootloader back in the sda so it can boot independently if you want it to.

---

