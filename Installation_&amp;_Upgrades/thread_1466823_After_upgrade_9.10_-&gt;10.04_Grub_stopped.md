---
title: "After upgrade 9.10 -&gt;10.04 Grub stopped"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Whitedragon150 on 2010-04-30
I have problem with grub loader. Wehn i upgrade my ubuntu i change my grub but after restart grub get error. grup_puts_ ....... How fix it?

---

### Post by doktorOblivion on 2010-04-30
Do you get the grub loader prompt with the list of vmlinuz* to boot (and windows if you have that installed)?  If you don't even get that far, sounds like your MBR may have gotten hosed.  You will need a rescue disk I think to get around that issue.

---

### Post by fatigue on 2010-05-03
You can boot/fix grub menu by Super Grub Disk
 
[LIST]
[*]Download [Super  Grub Disk]("http://forjamari.linex.org/projects/supergrub/")
[*]Burn into a  cdrom (better) or a floppy
[*]Boot    from it
[/LIST]
 
 This program, QGRUBeditor is really good program to fix/add new Grub  menu.
 [URL="http://linuxappfinder.com/package/qgrubeditor"]
http://linuxappfinder.com/package/qgrubeditor[/URL]
 
 1 First, use super grub disk and "advance and tool" and "show partition"
 Find out what is your windows root number (hd0,?). ? part is important
 
 2 By using QGRUBeditor, you can add windows grub menu.
 
 Windows will be like this
 
 title Windows 7 (Boot)
 root (hd0,*)
 chainloader +1


Ubuntu will be like 

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=e3265ff1-6500-457 ro  quiet splash 
initrd /boot/initrd.img-2.6.32-21-generic
quiet

---

