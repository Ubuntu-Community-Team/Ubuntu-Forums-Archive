---
title: "boot: prompt, VIA chipset install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by orotrev on 2006-06-05
I am a relative Ubuntu noobie. I am trying to install Ubuntu on a slim pc with a VIA chipset. It has been able to run Ubuntu in the past. I had Fedora Core 4 installed on it but I wanted to try and install a LAMP setup. I am able to install by forceing 640X480. When I boot after install my system just reboots. I saw in the help menu an entry about running special boot entries from the boot: prompt. How do I get to the boot: prompt? I believe in order for it to boot properly I need to run the installer with acpi off. Any other tips anyone has has for getting this to work on a VIA chipset would be great.

---

### Post by llamakc on 2006-06-05
Perhaps hitting the escape key will drop you into the old text-mode installer?

---

### Post by soulglo83 on 2006-06-05
try booting in rescue mode and editing your menu.lst, then adding "noapic nolapic pci=noacpi" to the line that reads kernel at the bottom of the file, in your ubuntu entry.

that section of the menu.lst should resemble the following:


title           Ubuntu, kernel 2.6.15-23-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdd1 ro vga=791 noapic 
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

as for manually accessing at boot time, i have no idea how to do that!

---

### Post by orotrev on 2006-06-05
I tried this when I re-ran the installer. It doesn't seem to work. I just go from normal installer to expert installer. I think the one thing I failed to mention is that my monitor is a TV. Should I try the install using a regular monitor?

---

### Post by orotrev on 2006-06-05
[QUOTE=llamakc]Perhaps hitting the escape key will drop you into the old text-mode installer?[/QUOTE]

Oops, I did that post wrong. refer to above post

---

