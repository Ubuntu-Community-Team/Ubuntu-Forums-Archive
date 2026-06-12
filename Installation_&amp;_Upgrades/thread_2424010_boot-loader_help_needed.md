---
title: "boot-loader help needed"
date: 2019-08-01
forum: Installation &amp; Upgrades
---

### Post by daniel-cornea on 2019-08-01
Hello Community, 

I am having an issue dual booting windows 10 and Ubuntu, I installed ubuntu in UEFI with secure boot disabled. I did follow the steps in boot-repair after the instalation,  however it does not load the GRUB. 

The output of the boot-repair can be found [here]("http://paste.ubuntu.com/p/FDWzB5rpny/"). 

Please help!

Thank you very much, 
Daniel

---

### Post by yancek on 2019-08-01
If it doesn't load Grub, what exactly does happen?  You have the correct EFI files on the EFI partition for both windows and Ubuntu.  You have also installed Grub code to the MBR which isn't used/necessary on an EFI install.  Did you disable Legacy/CSM in the BIOS?

---

### Post by daniel-cornea on 2019-08-01
Well, the UEFI in bios is enabled without secure boot. It just loads windows as usual.

---

### Post by oldfred on 2019-08-01
All Acer require you to set "trust" from within UEFI for ubuntu entry.
Then you should be able to set ubuntu entry as first in boot order.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
    
Grub only boots working Windows, so make sure fast start up is off. 
After setting trust with secure boot on, you may need to turn it back off.
If grub does not boot Windows, you should be able to directly boot Windows from UEFI boot menu. If not just a Windows issue.

---

