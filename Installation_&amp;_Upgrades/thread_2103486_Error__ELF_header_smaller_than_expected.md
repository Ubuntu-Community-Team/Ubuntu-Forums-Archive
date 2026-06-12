---
title: "Error:  ELF header smaller than expected"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by Chipo on 2013-01-10
I recently installed Ubuntu 12.10 on my Dell Inspiron 1520.  It is a dual boot machine with Window 7 and XP.  

After I installed the Ubuntu from a CD, when I rebooted I get "Error: ELF header smaller than expected"  
Next, I ran Boot-Repair, but I still get the same message.  The pastebin info is here:  [COLOR=Black][http://paste.ubuntu.com/1516732/](http://paste.ubuntu.com/1516732/)
[/COLOR]

Thanks for your help

---

### Post by dino99 on 2013-01-10
you need to reinstall grub.

So you will choose to boot in recovery mode, then select to open a terminal , and run:

sudo grub-install /dev/sda
sudo update-grub

then reboot as usual

---

### Post by salil2 on 2013-08-21
Hi dino99,

I have the same issue when I installed Ubuntu  13.04 desktop 64 bit on Sony VAIO. 
However, when I boot from a live CD, I am getting errors while using Grub update using terminal.

---

### Post by salil2 on 2013-08-21
The Boot-repair log is at paste.ubuntu.com/6005483

---

