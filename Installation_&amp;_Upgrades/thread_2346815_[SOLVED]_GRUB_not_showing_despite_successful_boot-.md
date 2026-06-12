---
title: "[SOLVED] GRUB not showing despite successful boot-repair"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by davidwong.ucl on 2016-12-19
Hello everyone,

[FONT=arial]I am installing Ubuntu 16.04.1 alongside Windows 10. This configuration has previously worked seamlessly on my laptop. However, after re-installation, GRUB will not show up and I currently have no way to boot into Ubuntu.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Boot info can be found here:[/FONT]
[FONT=arial][http://paste2.org/AaZ91zZW](http://paste2.org/AaZ91zZW)

EDIT: secure boot is disabled, and boot order has been set using efibootmgr[/FONT][FONT=arial]
[/FONT]
[FONT=arial]Any help will be greatly appreciated.[/FONT]
[FONT=arial]Thank you.[/FONT]

---

### Post by minecraft-electricity on 2016-12-19
Hi !
I had quite the same problem, so I opened the bios and in the boot options, I have another option which is probably written for you like "hard disk boot order" in wich you can choose to start with grub or windows boot loader.
I don't think I explained well so if you want I can record you how I did ?

---

### Post by oldfred on 2016-12-19
I see mention of Acer. What model?
All Acer we have seen so far have needed you to set an UEFI password and enable trust on the grub/ubuntu .efi boot files in the ESP - efi system partition.
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

Your UEFI entries show three different GUIDs. UEFI uses GUID not UUID. So you must have created ESP several times. Best to houseclean old entries.

see also
man efibootmgr
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B 
    
       to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda

---

### Post by davidwong.ucl on 2016-12-20
Thank you so much for your help!

GRUB is showing up again after:

[LIST=1]
[*]finding redundant boot entries -->  sudo efibootmgr -v     ---> lsblk -o PARTUUID
[*]deleting redundant boot entries --> sudo efibootmgr -b xxxx -B
[*]enabling secure boot
[*]entrusting shimx64.efi
[*]switching boot order
[/LIST]

This is an Acer Aspire R5-417T

Many many thanks again.

---

