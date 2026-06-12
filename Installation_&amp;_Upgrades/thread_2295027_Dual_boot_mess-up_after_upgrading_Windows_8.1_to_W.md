---
title: "Dual boot mess-up after upgrading Windows 8.1 to Windows 10"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by jorge27 on 2015-09-15
I've  been having trouble restoring my dual boot configuration (Ubuntu 14.04)  after upgrading to Windows 10. I've searched and tried different  solutions from different forums, but nothing has done the trick. Here is  my story so far:


  
[LIST]
[*]Upgraded Windows 10, and after first reboot I had to use grub-repair on a Live USB to make Windows start again.

[*]After Windows 10 finished installing, it would always boot straight into Windows, no grub.

[*]I ran boot-repair again and got a Blue Screen of Death.

[*]I used a Live USB and TestDisk to restore my Ubuntu partition and use it as a bootable primary.

[*]Rebooted and Grub would show up, but wouldn't list Windows, just Ubuntu and it worked fine.


[*]Used boot-repair and now it always boots straight into Windows again.


[/LIST]
  So here I am not knowing what else to do. Anyone have ideas that might help me?

---

### Post by grahammechanical on 2015-09-15
You should run Boot Repair yet again, give it authority to create a boot repair report and then post the URL to the pastebin site where that report has been stored. Then we can see what boot repair is seeing.

It seems that you are using Boot Repair to restore the Windows boot loader and that of course does not recognise any Linux OS.

Regards.

---

