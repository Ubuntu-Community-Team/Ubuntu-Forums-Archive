---
title: "Unable to install Ubuntu 13.04 along side Windows 8 on Dell Inspiron 3521"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by RAJESHKSV on 2013-06-19
I bought a new laptop - Dell Inspiron 3521 which came preloaded with windows 8 and GPT partitioning. As usual, My first step after buying a new laptop is to install latest version of Ubuntu.

Hence followed this guide - [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system) and disabled secure boot (UEFI is still enabled) and installed Ubuntu 13.04

Now restarted my system. Now I don't see grub. When I selected F10 to enter boot options, I see both Ubuntu and Windows boot manager options. I am able to enter Windows but when i select Ubtuntu, it takes me to grub command line but not GUI. I even tried repairing with boot manager but still it didn't help. boot repair continues till some steps and fails saying - "Please close all your package managers and continue" . I have verified that there are no package managers running. But still it says the same. Here is my boot repair summary - [http://paste.ubuntu.com/5779528/](http://paste.ubuntu.com/5779528/)

I tried other ways as well but was not able to boot into Ubuntu.

Please help. Thanks

---

### Post by Boola on 2013-06-19
@[**[COLOR=#000000]RAJESHKSV[/COLOR]**]("http://ubuntuforums.org/member.php?u=474534")

Thank you very much!

I installed ubuntu 12.04 at first with my newly dell inspiron 3521 and i just could not  get it too work. Then i saw you thread here and installed ubuntu 13.04 and now it works like a charm. Thank you!

---

### Post by slooksterpsv on 2013-06-19
I had this problem when installing Ubuntu - I had to use an older version of Wubi to make the USB stick, also, it had to be in my USB 3.0 port not USB 2.0 or maybe it was vice-versa. Either way; it took me a few tries; are you burning the ISO or using a USB key?

---

### Post by oldfred on 2013-06-20
It looks like you originally installed in BIOS/legacy/CSM mode as you have grub in the protective MBR. Then Boot-Repair converted install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

If you get to or past grub menu then it is not boot although sometime extra boot parameters may be required.

Have you tried recovery mode? May be under sub-menu or Advanced options.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

