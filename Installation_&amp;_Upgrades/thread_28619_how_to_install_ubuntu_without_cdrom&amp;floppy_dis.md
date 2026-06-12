---
title: "how to install ubuntu without cdrom&amp;floppy disk?"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by lylrq on 2005-04-21
My laptop's cdrom can not read the setup cd, and has no floppy disk drive, how can I install ubuntu on it?

---

### Post by TravisNewman on 2005-04-21
What os is currently installed? This is theoretically possible, but kinda complicated. Did you get a bad burn by any chance? Have you tried re-downloading/burning?

---

### Post by lylrq on 2005-04-21
My laptop can not read any cds now, and nothing on it, just like a brand new computer without cdrom&floppy.

The setup cd is ok, I've already installed on my desktop.

---

### Post by soul_rebel on 2005-04-21
If your laptop can boot from a usb external cd rom, or do a network boot, it can be done someway; else, if you have only windows installed i think that it's nearly impossible (but could be funny). If you have some linux than you have to do an installation like gentoo's one: installing a base system and then chrooting there.

---

### Post by soul_rebel on 2005-04-21
addon: you can also consider to mount the hd on another machine and do a normal install

---

### Post by woifi on 2005-04-21
[QUOTE=soul_rebel]If your laptop can boot from a usb external cd rom, or do a network boot, it can be done someway;[/QUOTE]

ack

---

### Post by lylrq on 2005-04-21
[QUOTE=soul_rebel]If your laptop can boot from a usb external cd rom,[/quote]
no, it can't.

>  do a network boot
how can I do it? I can't get into computer except bios.

> if you have only windows installed i think that it's nearly impossible (but could be funny).
No OS on the computer.



The only way is network boot, but I don't know how to do it.

---

### Post by lylrq on 2005-04-21
[QUOTE=soul_rebel]addon: you can also consider to mount the hd on another machine and do a normal install[/QUOTE]

How can I do it? Could u give the insturction?

---

### Post by lylrq on 2005-04-22
Up

---

### Post by BAshworth on 2005-04-22
I was trying to do this myself, being that my cd-burner gave up the ghost about three weeks ago.

I had extracted the kernel (vmlinuz) and initdr.gz files into a separate folder, placed the ISO file on a Fat32 partition, and was using a floppy with grub on it to boot the kernel and initdr, but I never got it to work.  Kept getting kernel panics.

I have installed Fedora this way before, and was using the kernel arguments given for booting that, so it's possible that I may have just had the arguments incorrect.

---

### Post by ed_agamemnon on 2005-04-22
I've written a little guide that might help you out some...

[http://www.ubuntuforums.org/showthread.php?t=28948&highlight=floppy](http://)

else, you could always use QEmu and just emulate a live cd of linux.... it's pretty slow though...

---

