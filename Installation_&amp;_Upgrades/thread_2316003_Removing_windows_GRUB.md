---
title: "Removing windows GRUB"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by Stevenukas on 2016-03-04
I have replaced old HDD with SSD, installed Ubuntu on the new drive. Now that I have received caddy, I have added old drive, after reboot, I see that there is another boot menu from Windows 10. How can I remove it ?

---

### Post by yancek on 2016-03-04
You need to clarify your intentions.  Do you or "did" you have windows 10 on the old HD?  Did you remove it or format the partition with windows and not want it any more?  Are you booting from the HD or the SSD?  Are you seeing the windows entry in the Ubuntu Grub boot menu?  If you don't have windows 10 any longer, sudo running update-grub should remove the entry as it only includes detected systems.  If that is not what your situation is, clarify it.

---

### Post by oldfred on 2016-03-04
If actually Windows and not UEFI, then it will be the BCD.
From Linux you cannot edit or change BCD.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

---

### Post by Stevenukas on 2016-03-04
> **yancek said:**
> You need to clarify your intentions.  Do you or "did" you have windows 10 on the old HD?  Did you remove it or format the partition with windows and not want it any more?  Are you booting from the HD or the SSD?  Are you seeing the windows entry in the Ubuntu Grub boot menu?  If you don't have windows 10 any longer, sudo running update-grub should remove the entry as it only includes detected systems.  If that is not what your situation is, clarify it.
Thank you, for your replay, I have SSD running now and deleted windows, updated grub and now all is good.  
> **oldfred said:**
> If actually Windows and not UEFI, then it will be the BCD.
From Linux you cannot edit or change BCD.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

You are right, it was UEFI. Thanks your for your input.

---

