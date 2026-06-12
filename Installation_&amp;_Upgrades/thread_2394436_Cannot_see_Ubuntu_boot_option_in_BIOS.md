---
title: "Cannot see Ubuntu boot option in BIOS"
date: 2018-06-16
forum: Installation &amp; Upgrades
---

### Post by magicpro97 on 2018-06-16
I cannot see Ubuntu boot option in BIOS. I tried to install ubuntu alone but it's not working.

That's my boot-repair report.
[http://paste.ubuntu.com/p/Fg4VPsYCgr/](http://paste.ubuntu.com/p/Fg4VPsYCgr/)

---

### Post by oldfred on 2018-06-16
I see mention of Acer graphics, is this an Acer system?

All Acer systems need you to set an UEFI password and enable "trust" for the Ubuntu/grub .efi boot files from within UEFI.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by magicpro97 on 2018-06-16
[SIZE=2][SIZE=3] Thank you very much. I try to look for the answer but now you give me the best answer. My problem is solved. Can you close my topic, please?[/SIZE][/SIZE]

---

### Post by orpheum on 2018-06-17
I had the same issue.

I'm installing Xubuntu on Acer Aspire ES1-432-C79F

Basically the BIOS only has secure boot enable/disable and there's no way to see ubuntu on the boot loader. 

Tried all combo I know and found and this showed me the answer

[http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html](http://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html)

To explain in short, one needs rEFInd imaged on USB to act as the primary boot. Then, then Linux can be added in the boot list and be rearranged so Ubuntu can boot first.

Hope this helps.

---

### Post by oldfred on 2018-06-17
If not getting the option to enable "trust" when secure boot is on & you have set password, then you need to update UEFI from Acer.

And all systems need UEFI updates for Meltdown and Spectre CPU vulnerabilitie. Both Windows & Ubuntu have updated kernel, but UEFI update also required.

---

