---
title: "No grub menu after disabling safe boot"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2019-05-19
After installing 16.04 on an HP Laptop with Windows 10, the grub menu would come up on boot. But in researching why my wireless didn't work, I found suggestions to disable "safe boot" in the bios. After I did that, it booted directly into Windows unless I activated the bios menu (which sometimes doesn't work). I tried switching back to safe boot but that didn't make a difference. I can't find anything in the bios menu to make the grub menu default. 
 
p.s. Still haven't solved the wireless problem.

---

### Post by yancek on 2019-05-19
When the Grub menu originally came up, did you have options for both Ubuntu and windows and were you able to boot both.

I"m not sure what options you have on your HP, but on some you will be able to tap the Esc key on boot and get several optons including F10 for BIOS/setup.  If you have that, go to System Configuration and on that page you should see Boot Options.  Arrow down to highlight it and hit Enter and you should see the options for windows and Ubuntu.  If you don't there is some other problem such as having Ubuntu installed Legacy while windows is UEFI.  Could be other problems also.

---

