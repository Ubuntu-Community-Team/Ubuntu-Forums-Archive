---
title: "Ubuntu not launching! - Win 10, UEFI, Acer."
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by michalmdc on 2017-11-09
Hi, I'm new to ubuntu, and I'm trying to run my computer on dualboot with Windows 10, but of course i have some problems:

[http://paste.ubuntu.com/25926662/](http://paste.ubuntu.com/25926662/)

i have my Win 10 installed on SSD disc and i tried to install Ubuntu on HDD.
When I turn on my laptop i see only Acer logo for few seconds and then, i guess it boot only windows.
I tried to change bootorder in UEFI but it didn't help, same story after clicking F12 i see only one option "Windows boot manager", and then windows starts.

I tried everything: reinstalling GRUB, boot-repair, Super Grub Disc or running in Live CD mode. Actually I once managed to get to my profile on Ubuntu, i guess from GRUB 2, after clicking ESC in ubuntu install menu, I wrote some commands from internet forums starting: "set root: " etc. sory but i dont remember them, anyway it was like forcing computer to boot ubuntu, and it works, but it doesn't satisfy me. I tried boot-repair but it seems it didn't help, even after adding \EFI\ubuntu\shimx64.efi to bootmgr in CMD in Windows.

To be honest i'm fighting with this problem for few weeks, so maybe i forgot about something. I hope Pastebin and my explanation will give u information, to help me solving my problem.

---

### Post by oldfred on 2017-11-09
Acer has a unique requirement. It requires you to set an UEFI password and enable "trust" from within UEFI of the Ubuntu .efi boot files in the ESP.
What model Acer just to document it.

```
 Boot0000* Unknown Device:     HD(1,GPT,43701925-8c4f-4fde-bbf3-3c3e042c8aa9,0x3f84000,0x2f800)/File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])RC
Boot0001* Unknown Device:     HD(2,GPT,2cc87be3-239f-4aa9-9369-ad644fec3d82,0xc8800,0x96000)/File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])RC 

```

Normally instead of unknown it says Ubuntu, but you can make it whatever you want (I think). 
You show a duplicate entry, although one is drive 1 & one is drive 2 and can remove one with efibootmgr.
See link in my signature and this:
man efibootmgr

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by michalmdc on 2017-11-09
Thanks for reply. I checked your links and advices, but it's a lot to read and do, of course, if it is necessary i will do it, but can u shortly explain me what i have to search and what it requires, for example if  I had to reinstall something (win, ubuntu), or download other programs?

To add some info: my laptop is Acer E5-575, and firstly i tried to install Debian (failed too) maybe it can cause some problems?

---

### Post by oldfred on 2017-11-09
It should be just set UEFI password (never lose that or remove it right after) and enable trust by drilling down in the ESP - efi system partition to /EFI/ubuntu/grubx64.efi or shimx64.efi and give them a name.

I have not done it, so the links are users that have actually done it. 
Some explain better than others, so I gave you several examples.

---

### Post by michalmdc on 2017-11-09
YES! It worked, Thanks for help, I think problem is solved, because after start up I see Grub and i can choose many boot options including Ubuntu and Windows.

I followed steps in this link: [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Thank you for help again! :)

---

