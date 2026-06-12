---
title: "Dual Boot: Installing Windows AFTER Ubuntu"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by speedway on 2007-05-15
Hi all

Not sure if this is the right forum for this, but here goes.

I have a new job where I need a full blown Windows machine. I plan to install a new 250Gb drive in my current machine and install Windows on that. Also in the machine is my baby 80Gb drive with Ubuntu Fiesty on it. 

What's the trick to get both operating systems appearing for selection when I reboot the machine?

Note: I do not want to install any VM's of any description. The software development I am undertaking requires a *real* Windows machine. Thanks.

Cheers
Bruce

---

### Post by newlinux on 2007-05-15
this tutorial from system76 should help. You can replace the using the dapper live disk with using the feisty live disk and adapt this to your situation. The key information is towards to bottom (reinstalling grub and adding windows to the boot after windows blows away grub):

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by confused57 on 2007-05-15
> **speedway said:**
> Hi all

Not sure if this is the right forum for this, but here goes.

I have a new job where I need a full blown Windows machine. I plan to install a new 250Gb drive in my current machine and install Windows on that. Also in the machine is my baby 80Gb drive with Ubuntu Fiesty on it. 

What's the trick to get both operating systems appearing for selection when I reboot the machine?

Note: I do not want to install any VM's of any description. The software development I am undertaking requires a *real* Windows machine. Thanks.

Cheers
Bruce
Maybe this would be an option for you:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I believe what you would do is connect your new drive as master, install Windows, then move the Window's drive to the slave position and your Ubuntu drive as master.

---

### Post by speedway on 2007-05-16
Thanks guys

Much appreciated. I'll look into both options.

Cheers
Bruce

---

