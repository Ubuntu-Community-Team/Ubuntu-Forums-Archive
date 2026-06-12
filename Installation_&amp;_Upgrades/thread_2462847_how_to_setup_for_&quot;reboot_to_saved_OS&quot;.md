---
title: "how to setup for &quot;reboot to saved OS&quot;"
date: 2021-05-28
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-05-28
I am sorry for repost, but my original post got lost in irrelevant stuff
grub has an option to save current OS and reboot to it.
It is my understanding that on EFI  system efi manager software takes  precedence 
in booting process , thus bypassing 
grub and its option to boot to save OS. 

IMHO 
the  useful and simple to implement option of grub to boot to saved system is therefore gone with the wind.

It seems possible to implement the "save option" i in efi manager by setting the boot order 
BUT it is not as simple  - decoding the efi manger way to actually boot is not as simple as /dev/sxx

---

### Post by oldfred on 2021-05-29
UEFI does have a boot order.
sudo efibootmgr -v
And you can change boot order with efibootmgr and -o option.
See also:
man efibootmgr

But major grub updates or Windows updates including its boot loader will change UEFI default to that system.
So you have to manage UEFI.

Grub still has its default settings & if UEFI first boot option is grub then your choice in grub will be used.

---

### Post by yancek on 2021-05-31
> It is my understanding that on EFI  system efi manager software takes  precedence 
in booting process , thus bypassing 
grub and its option to boot to save OS.  

On an EFI system, when booted it access the firmware on the system board  then goes to the boot priority and selects the disk in first boot  priority and then goes to the EFI partition to access that directory  which contains the EFI boot files for that particular OS.  This could be  ubuntu, windows, or  some other OS all of which should have separate  folders on that EFI partition.  With Ubuntu, it then goes to Grub and  there is a grub.cfg file on the EFI partition inside the ubuntu folder.  So it doesn't bypass Grub.  The grub.cfg file on the EFI partition  points to the actual grub.cfg file on the Ubuntu partition which  contains all the menuentries

The boot saved option will reboot to the last OS booted when it reboots.   Not sure that is what you want.  If it is, all you need to do is edit  the /etc/default/grub file as sudo and change the entry:

GRUB_DEFAULT=0  TO GRUB_DEFAULT=saved

You also need to add the line in this file:  GRUB_SAVEDEFAULT=true

After doing t'his, run sudo update-grub.  This worked for me on 20.04

---

