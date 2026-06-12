---
title: "Boot repair diagnosis / help please"
date: 2023-02-27
forum: Installation &amp; Upgrades
---

### Post by simonspringett on 2023-02-27
Good evening all,

I have an HP Probook 455.  Dual boot broke some time ago, when upgrading to Ubuntu 22.04 I think.  In fact I _can_ get to the grub dual boot menu by a roundabout way - pressing esc during start up, then selecting boot options, then selecting ubuntu - this takes me to the dual boot screen.  Otherwise after some error messages I boot straight into Ubuntu.



The pastebin from Boot Repair is here: [https://paste.ubuntu.com/p/57fpp3yxk6/](https://paste.ubuntu.com/p/57fpp3yxk6/)

Previous attempts to use boot repair have not improved the situation at all.

Updated with the error messages during boot.  

Failed to open \EFI\ubunutu\S - Invalid parameter etc

Any advice gratefully received.

Springnuts.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291844&stc=1[/IMG]

---

### Post by ubfan1 on 2023-02-27
Saw that error message when trying to get shim/grub to boot instead of Windows on an old Toshiba (2012).  Used bcdedit to set the "{bootmgr} to shim, (seemed to work, but errored with the above).  However, did have a default shim/grub bootloader /EFI/Boot/bootx64.efi which was then used, and after that, my grub boot did work as expected.  Never quite sure why the shimx64.efi name got cut off in the error message, bcdedit would show the full name.

---

### Post by oldfred on 2023-02-27
Your Windows UEFI boot entry is trying to also boot using Ubuntu's shim. See line 94.
You need to use Windows repair disk and correct that or maybe efibootmgr. 

sudo efibootmgr -v
New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
see also
man efibootmgr

Make sure UEFI is default booting in UEFI mode, not old BIOS/CSM/Legacy mode.
You have old BIOS boot loaders in MBR, which ne ver should be used.

---

### Post by simonspringett on 2023-02-28
Thank you very much.  Springnuts.

---

### Post by simonspringett on 2023-02-28
Thank you very much.

Have I understood correctly that the problem will not be corrected by the Boot Repair package?

I am not super-experienced with this stuff, so could you please run me through step by step the changes you suggest. 

sudo efibootmgr -v returns:

  BootCurrent: 0000
  Timeout: 0 seconds
  BootOrder: 0000,0001
  Boot0000* ubuntu    HD(1,GPT,f7fe6964-a8bd-4659-a080-c750b091fea2,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
  Boot0001* Windows Boot Manager    HD(1,GPT,f7fe6964-a8bd-4659-a080-c750b091fea2,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3................

Apologies but I did not understand the line "New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:"

Thanks again for your assist, and apologies again for my lack of understanding!

Springnuts.

---

### Post by oldfred on 2023-02-28
See
man efibootmgr

The command assumes your ESP is sda1, if it is not sd1 you need extra parameters.
That comment is more for others that may read this thread and not have their ESP as sda1 can not read the man page to know that extra parameters are required.
New Windows entry - assumes default sda1  add -d /dev/sda -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by simonspringett on 2023-03-01
Thank you very much. Regards, Springnuts.

---

