---
title: "GRUB needs updating??"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by toekneevee on 2008-05-23
Upgraded to 8.04 yesterday.  GRUB menu still says 7.10 with no options for 8.04. I choose the first selection in GRUB which says 7.10. When I click on System, then About Ubuntu, it says 8.04 Hardy Heron.  Why is 7.10 still around?  How do I get rid of 7.10 in the GRUB menu and add 8.04?  Any assistance will be appreciated. Thanks.

---

### Post by Eclipse. on 2008-05-23
Run "sudo update-grub" from the terminal, normally its done automatically.

---

### Post by toekneevee on 2008-05-23
Still the same.  Should there be 2 "kernel" entries as pasted below?  I'm very new to this...just asking.  Thanks for your help. 


tony@tony-desktop:~$ sudo update-grub
[sudo] password for tony: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

