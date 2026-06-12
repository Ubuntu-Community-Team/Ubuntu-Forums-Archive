---
title: "Lost access to Windows partition after install (but it's still there)"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by superchar42 on 2014-08-08
This surprised me because I've been using linux on and off for 10 years. 

I just did an install of Ubuntu on my laptop. I created empty space using the tool built into windows, created a partition with the ubuntu installer, then proceeded to install on the not-windows partition. 

So I boot up my shiny new ubuntu, notice that the grub menu didn't pop up, and made a mental note to look into that later. Later was a couple days when I wanted to play Star Trek Online, and tried to get to Windows 7 after getting grub to load up and it wasn't even there! 

So I thought I had wiped my Windows partition out but when I'm in Ubuntu I can access all the data. 

My guess is I need to repair the bootloader?

---

### Post by Bashing-om on 2014-08-08
superchar42; Hi !

Sounds reasonable !
Try from the ubuntu install:
Terminal command:
```

sudo update-grub

```
To pick up the Windows install, and chainload it to grub's menu.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by superchar42 on 2014-08-10
Alright, ran it and got this -- I'll update what happens on reboot. :) 

> $ sudo update-grub
[sudo] password for charlie: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
done


---

### Post by superchar42 on 2014-08-11
Success! 

Thanks a bunch!

---

### Post by Bashing-om on 2014-08-11
superchar42; Great !

Ain't grub a wonder to behold !

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT]of your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

