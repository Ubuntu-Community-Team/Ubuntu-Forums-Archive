---
title: "Can't Start Ubuntu!?"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Sepe Hyke on 2005-09-09
My problem is this: I'd installed ubuntu 5.04 and everything seems to be allright. But when i give my user name ( or root ) and password, i'm only get light brown screen and mouse arrow, nothing else! If i tried any options ( GNOME in safe mode or some else ) my computer stops completely! I'd read some hints in this forum how to edit Xorg.conf -file but i can't open it cause gedit don't work at all! I'm only getting some display error! Can i boot whit "e" (editing command lines before boot) and put something in line " kernel /boot....bla bla.... splash" to start in basic vga or vesa driver? Cause i think the problem is that my display adapter (GAINWARD Nvidia GeForce 6800 LE AGP 128 MB) is not working properly.  I have install Ubuntu twice, once in normal-mode and once whit expert-option but for nothing. I'm a beginner in linux-world though i have had built my own computers and "play" in WIN-world over ten years. My computer: AMD XP 2200+, MSI KT3V, 1 Gb mem., GeForce 6800 LE, 2 hardd's (250 Gb Western Digital and 80Gb something, both IDE), SMC 1244TX 10/100 network card, winstar cable modem, SB 128 pci, 17" fujitsu tube, logitech corded keyb., MX 510 usb-mouse. WIN XPPro is in 250 Gb hd and Ubuntu in 80 Gb, GRUB-bootloader. Thank's in advance!

---

### Post by rafakl on 2005-09-09
If your network is up and running, try editing the file via emacs, but first install it.

sudo apt-get install emacs

---

### Post by 23meg on 2005-09-13
i'm suffering from the same problem. i have a geforce go6200 graphics chip in my laptop. i've read that the solution is to install the proprietary nvidia drivers, but i haven't had any success with that either. right now i'm left without my loved ubuntu on my new computer  ](*,) 

by the way, you don't need emacs, you can use nano to edit your xorg.conf file. 

```
sudo nano /etc/X11/xorg.conf 
```

---

### Post by 23meg on 2005-09-14
anything new on your side?

---

