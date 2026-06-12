---
title: "Can not boot Windows 8 after Ubuntu 12.04 64 bit installation."
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by Matt Z on 2013-05-30
Hello,

I have Lenovo N580 laptop with preinstalled Windows 8.
I wanted to have Ubuntu 12.04 installed on this machine as well (dual boot).
After installation I couldn’t boot Windows anymore.
I tried BootRepair [[https://help.ubuntu.com/community/Boot-Repair]](https://help.ubuntu.com/community/Boot-Repair]) but the problem remains.

error: secure boot forbids loading module from (hd0, gpt9)/boot/grub/nfs.mod
error: no souch device E4AA9ED9AA9EA796
error: unnknown command ‘drivemap’
error: invalid EFI filepath

BootRepair logs:
[http://paste.ubuntu.com/5718070/](http://paste.ubuntu.com/5718070/)

What can I do to ressurect Windows8?
Any hints?

---

### Post by VMC on 2013-05-30
Maybe this will help:
[COLOR=#070F14][FONT=Verdana]**Boot with your windows 8 DVD or USB**[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Follow the Prompts and select[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]***TroubleShoot -> Advanced -> Command Prompt***[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]Once you are in the command prompt run the following commands[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana][I][B]bootrec /fixmbr
bootrec /fixboot[/B][/I][/FONT][/COLOR][COLOR=#070F14][FONT=Verdana][/FONT][/COLOR]

---

### Post by Matt Z on 2013-05-31
Hi,

thanks for your replay.
Unfortunatelly I don't have WIndows 8 CD / USB. This OS was preinstalled on my laptop.

---

### Post by fantab on 2013-05-31
Have you changed the boot order in BIOS to boot Ubuntu?

> 
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file

---

