---
title: "Cannot install Ubuntu on an old laptop computer."
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by atlantis11500 on 2006-09-04
Hi, guys, I have been trying to install Ubuntu on my laptop computer. 
 
Here are some information about this laptop: 
Intel VIA mobile C3 / 512DDR / 30GB / 12.1 TTF / 100MB Ethernet Adapt / 4 USB Port. 
 
At present, I have DOS and Windows XP installed on this computer, so I tried to install it via a article on the internet. 
[http://old.ubuntu.com.cn/support/documentation/doc/installubuntufromdos](http://old.ubuntu.com.cn/support/documentation/doc/installubuntufromdos) 
 
I know that after hardware checking, it should display the first install dialog...e.g. to select my language, right? But this dialog never displays...It just appears a dark screen each time on my laptop. No any error message displays. 
 
I did installed Ubuntu successfully on my PC, but...is there anything wrong with the hardware of my laptop computer? Anyone can help me out? Thanks in advance!

---

### Post by Carl H on 2006-09-04
Try using the "alternate" CD instead. There are problems with using the normal CD on certain combinations of hardware. I couldn't get it to install on my Dell laptop with the normal CD, but the alternate one worked no problems. 

You don't get the fancy graphical installer, but you can live without that.

---

### Post by atlantis11500 on 2006-09-04
No doubt that I was using a alternate ISO. The same install process works on my PC but failed to work on my laptop. So I suspect that some of my hardware are not supported?

---

### Post by breuerp on 2006-09-04
When you boot from the live cd, go to grub (hit Esc before actually booting) and add the following to the list of boot parameters:  nomce

---

### Post by atlantis11500 on 2006-09-05
I am not quite sure whether I was using GRUB.
The following string was used to install it under the DOS prompt.

```

[COLOR="Red"]**loadlin vmlinuz root=/dev/ram initrd=initrd.gz ramdisk_size=20000 devfs=mount,dall**[/COLOR]

```
So, where should I add the **nomce **parameter?

---

