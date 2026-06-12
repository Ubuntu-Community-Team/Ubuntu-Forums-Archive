---
title: "If i boot to windows i wont be able lo boot back to linux"
date: 2018-08-01
forum: Installation &amp; Upgrades
---

### Post by chivobrincon on 2018-08-01
I have tried to solve this for three years and i simply can’t and there is not information on this specific problem.

Important note: i am NOT trying to boot after installing windows; I AM TRYING TO BOOT BACK TO LINUX AFTER HAVING BOOTED TO WINDOWS.

I didnt have this problem in other computers. The computer I have  is an HP AIO  19-3013w touchsmart. In another similar computer I had the same issue.

Any help will be apreciated. 

Best regards

---

### Post by QIII on 2018-08-01
It might be helpful if you could provide some more information on "cannot boot".

What behavior do you observe?

---

### Post by oldfred on 2018-08-01
HP violates UEFI spec that says NOT to use description as part of boot. And of course the only valid description is "Windows Boot Manager".
You still should be able to boot from HP's UEFI boot menu, but that is using UEFI's one time boot.
You just cannot set "ubuntu" entry as default boot.
You also may be able to set the hard drive entry as default boot. Originally it is set to be a copy of Windows .efi boot file. But you can run Boot-Repair which will automatically copy shimx64.efi to be the fallback or hard drive entry. Before Boot-Repair did the copy, many users manually copied file.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Have you updated UEFI from HP?
Some with newer systems or updates say this now works.
       
 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309) 
            HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

