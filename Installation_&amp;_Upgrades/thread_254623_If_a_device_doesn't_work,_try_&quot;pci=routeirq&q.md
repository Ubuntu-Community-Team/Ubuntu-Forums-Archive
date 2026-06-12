---
title: "If a device doesn't work, try &quot;pci=routeirq&quot;"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by like-2-ride on 2006-09-10
I installed ubuntu desktop yesterday and when it came up I had no network card, no usb ports and no sound. Obviously, none of the pci devices were being seen by the os. 

I found the message 'If a device doesn't work, try "pci=routeirq"' when I ran dmesg. I added the command 'pci=routeirq' to kernel line in the default menu option of /boot/grub/menu.lst but nothing worked. I also tried a lot of differnet bios settings, but finally found a fix after poking around the internet for  a while.  

I removed the 'pci=routeirq' command and replaced it with 'acpi=off' and it worked. My kernel line in the default menu option looks like this: 

kernel    /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash acpi=off

I can't guarantee this will work for you, but I after all the trouble I had finding an answer to this I wanted to post it here hoping it will help someone. :wink:

---

### Post by zach014 on 2008-07-11
Thank you! My PCI devices stopped working recently, after I had restored grub after a windows reinstall (i have since removed it however). In restoring grub, it must have messed with my menu.lst and removed the "acpi=off"
Thanks to your instructions, my sound card, network, etc work again.

~zach

---

