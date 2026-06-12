---
title: "Dual boot in ubuntu BootRepair log"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by c.pfarher on 2014-02-25
Hello, I have ubuntu installed in my notebook toshiba with efi, but I don't see the grub when start... and automatically start on ubuntu (instead of show windows 9 or ubuntu option)...
This is my bootinfo log get it by boot- repair:[http://paste.ubuntu.com/6996981/]("http://paste.ubuntu.com/6996981/")
It is safe to execute the recommend repair option of boot repair in order to restore de grub with the options of select the operating system?

Thank you.

---

### Post by oldfred on 2014-02-25
You may do better with 13.10 or 12.04.4 as the UEFI and other parts have been updated a lot.
But if you do reinstall see caution in link in my signature. You must use Something Else.

You can run Boot-Repairs fixes, but do not run 'buggy' UEFI fix unless you have a system that will not boot anything but Windows.
Have you tried the ubuntu entry in UEFI menu? this shows it is there?

>  BootOrder: 0004,0003,2003,2001,2002
Boot0001* EFI Network 0 for IPv6 (00-26-6C-2E-17-4E) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(00266c2e174e,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot0002* EFI Network 0 for IPv4 (00-26-6C-2E-17-4E) 	ACPI(a0341d0,0)PCI(1c,0)PCI(0,0)MAC(00266c2e174e,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0003* Windows Boot Manager	HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* [COLOR=#ff0000]Ubuntu[/COLOR]	HD(2,e1800,82000,04b9edc2-fc48-11e1-8ec1-e7137b3aaf29)File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device	RC



---

### Post by c.pfarher on 2014-02-25
Hello, thank you for your answer... When I started the computer it doesn't show any menu option..... only a violet screen ( ubuntu color as background - without any text...) and then boot automatically to ubuntu...... it doesn't show the uefi menu...
Thank you

---

### Post by oldfred on 2014-02-25
You have to press whatever key gets you into UEFI/BIOS or one time boot key.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by c.pfarher on 2014-02-26
Hello, if I press F2 or F12 it is show me the setup page or the boot menu...... 
- I attached the boot menu image (after F12) 
[IMG]http://s24.postimg.org/vkzzlrlb9/IMG_20140226_153756.jpg[/IMG]
(windows 8 it isn't present)
- In the set up page I have an option in advance settings where it is selected UEFI boot (the other option is CSM)). I press ESC and the system was restarted and showed me the grub menu with three options: Ubuntu, Advanced (it is show different kernel verions) and System configuration... But the windows 8 option it isn't present ;|

Thank you

---

### Post by oldfred on 2014-02-26
You are showing the sub-menu for network boot.
But do you have secure boot on?
What is sub-menu under hard drive, or is there another selection somewhere?

You should be seeing all the choices in post #2 as that is just an extraction from your UEFI.

---

### Post by c.pfarher on 2014-02-26
Secure boot is off. 
I will view the sub menu under hard drive tonight....
If that submenu will show me the "Boot0003* Windows Boot Manager" entry then I can suppose if I select this option, it boots on windows?
Thanks.

---

### Post by oldfred on 2014-02-26
It probably will just say Windows, boot 0003 is internal.

---

