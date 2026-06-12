---
title: "cant boot into LiveUSB with a custom pc (amd processor)"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by steve19137 on 2010-02-20
im not very educated in amd processors, but i think that they are all 64-bit processors.

i downloaded the amd ubuntu 9.10 into my computer, and used the usb maker utility in the system menu. i put in in my new pc (it was given to me), and i tell it to boot into the usb.

then i get this. i am posting a pic.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=147711&stc=1&d=1266711608[/IMG]

sorry about the sideways pic. i took it with my phone. 

anyway, i get the syslinux boot shell script thingy. i have tried lots of things. linux, vmlinuz, lots of other things i found online. so what im wondering is the exact name of the kernel in ubuntu 9.10 amd version. if you need details, then let me know.

---

### Post by PRC09 on 2010-02-20
Dont know if it makes any difference but the pic shows that you are telling it to boot from usb-floppy drive....

---

### Post by steve19137 on 2010-02-20
> **PRC09 said:**
> Dont know if it makes any difference but the pic shows that you are telling it to boot from usb-floppy drive....

thats what my bios calls it. i tihnk that the fact that im getting the syslinux prompt says that the usb is working, its something else thats the issue.

---

### Post by PRC09 on 2010-02-20
I have tried using the usb-fdd option and have never got it to work,something about how your machine sees the files on the drive.....


[http://www.pendrivelinux.com/usb-bios-boot-options/](http://www.pendrivelinux.com/usb-bios-boot-options/)

---

### Post by nerdtron on 2010-02-20
It should not be USB-floppy. It should USB-HDD or USB-FDD. Oh and what tool did you use to create your bootable thumbdrive?

---

