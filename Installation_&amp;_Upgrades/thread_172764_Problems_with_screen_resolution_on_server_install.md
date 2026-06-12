---
title: "Problems with screen resolution on server install"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by happytechie on 2006-05-09
Hi all, I have a server only breezy install which is intended to be used as an intranet server at home.  Besides the struggles with webmin / apache and ftp I have a serious issue with the display.  I'm running on old hardware (a P 233 with 64Mb and a ancient AGP gfx card) on a very new monitor, a viewsonic 201 TFT screen.  The probblem is that I'm not getting the top line of my display which means I can't read the top line of a file in vim ;(  I am also missing the far left of the screen which makes the first character dificult to read.

Does anyone know where I should start to get all of my 26 lines and 80 columns visible ;)

Tia

Paul

---

### Post by louis_nichols on 2006-05-09
There is this parameter that can be added to the boot options and influences the behavior of consoles. I have

vga=792

as the last thing on the kernel line. I don't really know what different values mean, but someone recommended me the value 792 and works well, so I didn't get into it too deep.

---

### Post by happytechie on 2006-05-09
I'll check that parameter, which file is it specified in?

tia Paul

---

### Post by louis_nichols on 2006-05-09
oh!

It's in /boot/grub/menu.lst

On the line with the kernel you're booting, add it in the end, like this:
```

title		Ubuntu, kernel 2.6.15-21-k7 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.15-21-k7 root=/dev/mapper/kubuntu-root ro single **vga=792**
initrd		/initrd.img-2.6.15-21-k7
boot 
```

---

### Post by happytechie on 2006-05-09
thanks alot Louis, I probably should have told you that I am I am hideously new to Linux and strugling to remeber any of my *nix skills having worked with MS tools for about 6 years now.

i presume that the number tells you the number of lines on the display or something similar ?

Paul

---

### Post by louis_nichols on 2006-05-09
well, you actually made me curious, so I did a quick google about it.

And I found [this link]("http://techpatterns.com/forums/about342.html"), which I think explains stuff.

---

