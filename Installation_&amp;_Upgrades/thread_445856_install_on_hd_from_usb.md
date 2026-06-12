---
title: "install on hd from usb"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by cetheriel on 2007-05-16
i think what i want to do is way easy, i just don't know how to start it.
i wanted to install xubuntu7.04 on my pc, problem is i just can't find a decent media - thus i keep getting checksum errors and failures at install. after burning 10 medias, i gave up.
i thouhgt i could place the instalation files directly on the hd, which is still a possibility. (i have another pc)
but i thought i could place them on an usb drive and boot from it.
i found people doing live ubuntu from usb, which required partitions and all. i don't need all that. i just need to make it boot and install from the .iso (or from the files that i may uncompress).
is it possible?

---

### Post by cetheriel on 2007-05-16
found this faq
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
i'm trying it right now.

---

### Post by WezH on 2007-05-16
I have tried it now, doesn't work for me. 

I try to install ubuntu-7.04-server and problem is that system can't find USB stick and I can't mount my USB stick. 

"No such device" every time when I try to mount /dev/sde1

USB stick is /dev/sde1, I did check it from logs.

Any ideas?

ETA: Found something else from syslog: 
> hw-detect: Missing modules 'ide-core (Linux IDE support), ide-mode (Linux IDE driver), ide-probe-mode (Linux IDE probe driver), ide-detect (Linux IDE detection)
Is this the problem?

ETA: maybe, 'cause trying to mount floppy and log says > FATAL: Module vfat not found

---

### Post by cetheriel on 2007-05-16
didn't work...
can't boot.

---

### Post by mountaindude1 on 2007-09-05
I also get the "No such device" error when trying to mount the USB stick as cdrom.
Anyone found a reason for/solution to the problem?

/MD

---

### Post by scapalexis888 on 2007-09-20
I also have the same problem. I can't mount my PNY 1gb flash drive as a cdrom. I switched to a 2gb SanDisk Cruzer and that didnt even boot. I think the main reason for this trouble is the combination of your mobo and the flash drive. Try different combos and see what works. Thats what i am doing.

---

