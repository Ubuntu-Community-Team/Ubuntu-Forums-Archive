---
title: "What is the correct SSD-Setup for Legacy Boot Mode?"
date: 2022-10-19
forum: Installation &amp; Upgrades
---

### Post by robytoby on 2022-10-19
[FONT=Helvetica]Hello,[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]Read posts about Legacy-Boot - mode, but I’ve no idea what to do.[/FONT]
[FONT=Helvetica]I’m not able to make changes to the bios. The admin password is set and lost. It's a DELL m3800.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]The bios-boot-setup looks like this:

[/FONT][IMG]http://www.kempfi.de/austausch/IMG_0641.jpg[/IMG][FONT=Helvetica]

[IMG]https://my.hidrive.com/lnk/siHIzYNu[/IMG][FONT=Verdana]
I am not able to change anything there.

[/FONT][/FONT][FONT=Helvetica]Before the install-process I deleted all partitions, so that the process took the right options.[/FONT]
[FONT=Helvetica]I installed ubuntu with the latest iso from their web-page. After installation, it boots correct if I choose manually the [/FONT]
[FONT=Helvetica]UEFI options:[/FONT]
[FONT=Helvetica]    ubuntu [/FONT]
[FONT=Helvetica](Otherwise it does not see a boot-partition and asks for it - it seems, it always boots from mini ssd?)[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]How can I manage, that the ubuntu-partition appears in the legacy options  (see the picture above)?[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica]My ssd-setup after installation looks:

[IMG]https://my.hidrive.com/lnk/siHIzYNu[/IMG][FONT=Verdana]
[/FONT][/FONT][IMG]http://http://www.kempfi.de/austausch/IMG_0640.png[/IMG][IMG]http://www.kempfi.de/austausch/IMG_0640.jpg[/IMG][FONT=Helvetica][FONT=Verdana]
[/FONT][/FONT]
[FONT=Helvetica]In the meantime I experimented with windows 10 with boot records mbr as well as gpt.  [/FONT]
[FONT=Helvetica]It allways ends up with similar situation like in the first picture. Always I’ve to choose then boot-partition manually because it appears in: UEFI Options.[/FONT]

[FONT=Helvetica]I've no idea, what todo.[/FONT]

---

### Post by yancek on 2022-10-20
If you booted the Ubuntu live usb in UEFI mode and installed it UEFI then it will boot UEFI.  You would need to install it in Legacy mode to see it in the Legacy options.

If your hard drive is GPT, you will need to install windows in UEFI mode as it won't boot from a GPT drive in Legacy mode.

---

### Post by robytoby on 2022-10-20
Oh No! 
I've to choose the USB-Stick in the Legacy Options - section.
That's all. 
Thank you very much.

---

