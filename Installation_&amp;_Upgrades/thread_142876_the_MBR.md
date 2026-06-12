---
title: "the MBR"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by cvtboudreaux on 2006-03-11
I want to install Ubuntu on my laptop with windows XP, however, i don't want it to rewrite my MBR with grub. I just don't like grub.

I installed Unbuntu on my desktop computer but used another harddrive by itself. Then I reconnected my Windows HDD and used this bootpart program to take the first 512 bytes off the second harddrive. Then I put a link to it in the boot.ini file and it works like a charm and boots Ubuntu.

Now my question is, is it possible to have this same setup but with two partitions on one harddrive? I don't recall Unbuntu's setup asking me if I wanted it to install grub or where I wanted it to install grub (it just did it automatically). Does anyone know if there is a choice? B/c I'd like to install grub on the linux partition then boot to it with the boot.ini file. (none of which I know will actually work if XP and Unbuntu are on the same harddrive with different partitions)

Can anyone help? Thanks!

---

### Post by Koybe on 2006-03-11
Yes this is possible. But i don"t know how to set this during install. Anyway you just need to :
grub-install (hd0,4) for example.

---

### Post by cotcot on 2006-03-11
During install the ubuntu installer asks you if you want to install grub to MBR. Reply NO. Than the installer will ask you where to put the boot bootloader. You can than specify the drive where you want it (/dev/fd0 ; /dev/hdb1 ...)

---

### Post by aysiu on 2006-03-11
You don't "like" Grub? What don't you like about it? You can change the look, you know.

Well, if you're insistent on using Windows' boot loader, [this link](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) might help.

---

### Post by et_the_beta_tester97 on 2006-03-11
I have installed mandrake linux using 2 partitions (1 from 1 hdd and the other from the other hdd.) but installing ubuntu on 2 partitions can be very tricky. The last time i did that, it overwrote the MBR so i couldnt set it to dual boot (and that was using 2 different hdd's.). so what i did was i installed it on 1 hard drive and had windows installed on another drive and just switched between the two whenever i wanted to boot to ubuntu or linux.

--CJ

---

### Post by cvtboudreaux on 2006-03-11
Cotcot: Thanks that's what I needed just to make sure!

---

### Post by cvtboudreaux on 2006-03-11
[QUOTE=et_the_beta_tester97]I have installed mandrake linux using 2 partitions (1 from 1 hdd and the other from the other hdd.) but installing ubuntu on 2 partitions can be very tricky. The last time i did that, it overwrote the MBR so i couldnt set it to dual boot (and that was using 2 different hdd's.). so what i did was i installed it on 1 hard drive and had windows installed on another drive and just switched between the two whenever i wanted to boot to ubuntu or linux.

--CJ[/QUOTE]

Google bootpart, it will make your setup alot easier. I have the same thing on my desktop.

---

### Post by cvtboudreaux on 2006-03-11
[QUOTE=aysiu]You don't "like" Grub? What don't you like about it? You can change the look, you know.

Well, if you're insistent on using Windows' boot loader, [this link](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html) might help.[/QUOTE]

I just don't like it because Windows is my main OS and probably will be for some time so I don't want to do anything too drastic to it.

---

### Post by aysiu on 2006-03-11
[QUOTE=cvtboudreaux]I just don't like it because Windows is my main OS and probably will be for some time so I don't want to do anything too drastic to it.[/QUOTE] You're perfectly welcome to do what you want. I just want to make sure it's an *informed* choice.

You can install Grub to the MBR and still have Windows be your main OS and your *default* OS. The advantage to installing Grub to the MBR is Grub's ability to detect and automatically add Windows to the boot menu. Windows boot.ini does not have this ability, and will in all cases not recognize or add Ubuntu to its menu.

Once you have Grub on the MBR, you can always have the default OS to Windows. That way, if you do nothing, it'll boot straight into Windows. If you press the up or down arrows, you can choose to boot into Ubuntu.

If you understand all that and still don't want Grub on the MBR, you're entitled.

---

