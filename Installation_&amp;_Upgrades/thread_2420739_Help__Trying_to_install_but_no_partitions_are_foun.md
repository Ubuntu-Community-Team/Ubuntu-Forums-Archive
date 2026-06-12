---
title: "Help : Trying to install but no partitions are found."
date: 2019-06-10
forum: Installation &amp; Upgrades
---

### Post by fullmetal978 on 2019-06-10
I recently ran into an error with my manjaro installation. It failed to recognise boot/efi. Then somehow everything went botched windows stopped working too. Ultimately there was nothing in the boot manager except pxe-rom and live usb. Out of options I try to install lubuntu but when partioning it shows no partition except the usb pendrive. Now I tried to use boot-repair and the output.


boot-repair output:

paste.ubuntu.com/p/ZG8qgZdqwx/

---

### Post by Impavidus on 2019-06-10
It doesn't see your hard drive. Probably a hardware error, like a broken hard drive or a loose connector. Check the connections. You can also try to put the harddrive in an enclosure and access it from a different computer.

 I hope you've got backups.

---

### Post by fullmetal978 on 2019-06-10
It was detected earlier but it doesn't now.

---

### Post by yancek on 2019-06-10
> I recently ran into an error with my manjaro installation. It failed to recognise boot/efi.


What error?  You mean not recognizing boot/efi?   You mention a windows install but neglect to indicate which windows.  If it is 10 and you have an EFI install, have you done any updates on windows recently?  Have you got fastboot and/or hibernation on?  If you turned it off previously and did an update in windows it will turn it back on without notifying you.  

Boot0000 from efibootmgr seems to be the internal hard drive and should boot from the BIOS or boot options if you select it from EFI.  I expect that would boot the windows pre-installed.  Have you tried that?  I'd first check the drive connections suggested above, simplest thing to do.

---

### Post by fullmetal978 on 2019-06-10
Yes. Not recognizing boot/efi was the start. Then I went into windows(10 Btw)  to sort it out create a lve usb. But windows was ridden with problems like dll problems and no application opened. Then I did an update which was going well and then tried to reset. Finally the system showed windows is getting ready. Then forced the pc to restart. Then followed all the other problems.



> Boot0000 from efibootmgr seems to be the internal hard drive and should  boot from the BIOS or boot options if you select it from EFI. 

How do I do that? How to select it from efi?

---

### Post by yancek on 2019-06-11
You should be able to select the option mentioned from the BIOS.  THis varies with manufacturer.  On my HP, I hit the Esc key then get options for boot (F9), BIOS (F10) so you need to watch the screen to see what key you need to use to select that option.

---

