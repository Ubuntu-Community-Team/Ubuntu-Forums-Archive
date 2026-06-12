---
title: "After installation Raring doesn't boot"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by ultrapeer on 2013-06-01
Hi there,

I tried to install Ubuntu Raring amd64 on an HP Pavilion p6-2310ef desktop computer which already has Windows 8. The problem is that at each boot, it booted directly Windows as if there were no Ubuntu. There was no dual boot menu whatsoever. So I installed Boot-Repair and clicked the "Recommended repair" button. Now, when I choose Ubuntu, I only get the following two lines and the computer becomes unresponsive:
 Loading Linux 3.8.0-19-generic ... 
Loading initial ramdisk ...  

The URL Boot-Repair asked to write down is [http://pastebin.ubuntu.com/5722930](http://pastebin.ubuntu.com/5722930) 

Unfortunately I can't get rid of Windows 8 on this PC, but I can't live with only that OS either so I really need your help.

---

### Post by angryfirelord on 2013-06-01
Is this a UEFI-enabled computer? If it is, you need to make sure the Ubuntu disc boots from a UEFI-enabled bootloader. Otherwise, it'll install the bootloader to the MBR, which doesn't work under UEFI. In addition, you should also make sure secure boot is disabled.

---

### Post by ultrapeer on 2013-06-01
Yes, this is a UEFI enabled computer and Secure Boot is disabled. But  how do I know if Ubuntu boots from a UEFI-enabled boot loader? (Note  that Windows boots just fine).

---

