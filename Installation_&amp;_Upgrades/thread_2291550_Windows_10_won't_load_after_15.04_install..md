---
title: "Windows 10 won't load after 15.04 install."
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by colmeweb on 2015-08-20
So I installed 15.04 on my new Lenovo Edge 15 last week and with the exception of the wireless card not being supported everything is going great. 
However I can't get Windows 10 to load. It shows up on GRUB, but when I click it I just get a message that the image won't load and then it goes back to GRUB.

I don't need Windows except for once or twice a year, but when I need it I need it. 

My camera doesn't want to focus on my screen so it may take a while for me to copy the message down.

Thanks.

---

### Post by ubfan1 on 2015-08-21
Can you boot Windows by selecting it from the EFI boot menu (some function key at power up)?  Do you have secure boot off (might still be a bug preventing grub from booting Windows)?

---

### Post by colmeweb on 2015-08-23
UEFI is the only boot mode that is listed in the BIOS menu.

---

### Post by oldfred on 2015-08-23
Did you leave Windows hibernated or its fast startup which is always on hibernation set?

Directly boot Windows from UEFI and turn off fast startup, then you should be able to boot from grub menu.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

If not run this, but do not run any auto repairs until reviewed.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by colmeweb on 2015-08-23
So I shut off fast startup, but I am still getting the no boot image found message.
However if I disable the secure boot I can load Windows. So I guess thats that.

Thanks.

---

