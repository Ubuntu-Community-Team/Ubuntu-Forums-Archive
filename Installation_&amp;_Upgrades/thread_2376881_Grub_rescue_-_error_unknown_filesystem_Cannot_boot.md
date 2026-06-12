---
title: "Grub rescue - error: unknown filesystem Cannot boot into Win10"
date: 2017-11-07
forum: Installation &amp; Upgrades
---

### Post by zsquared on 2017-11-07
Hi, I am new to Ubuntu and I think I am in a mess right now...Please help....
I have Windows 10 installed then I installed Ubuntu 16 after it.

However the next time I reboot the system I went straight to Grub Rescue.

error: unknown filesystem. 
grub rescue>

I know my Ubuntu is at partition 7 so I use these command to boot Ubuntu:

set root=(hd0,7)
set prefix=(hd0,7)/boot/grub
insmod normal
normal

I was able to boot Ubuntu successfully and I use these 2 commands to repair Grub:

sudo update-grub
sudo grub-install /dev/sda

It didn't work. 
I tried with [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"). Still, doesn't work. 
The summary is attached here:
[http://paste.ubuntu.com/25908632/](http://paste.ubuntu.com/25908632/)

In my BIOS setup utility, I have set Secure Boot as disabled.
In my Startup, I have to choose Boot Priority (UEFI first or Legacy first).
I choose UEFI.
(If I choose Legacy, nothing gets booted...)

I have important files on Windows so I really don't want to reformat the whole thing...
Thanks in advance for the help!

---

### Post by oldfred on 2017-11-07
Can you directly boot Windows from UEFI menu, often f10 or f12 check manual. Make sure UEFI boot is on. If you have an UEFI only setting use that, but do not allow BIOS boot.
My motherboard had a UEFI and BIOS first settings, but the only one that worked in UEFI mode was a UEFI only setting.

You have a grub installed to the gpt protective MBR for the old BIOS/Legacy boot (which now will not work), but you seem to also have installed the UEFI version of grub as your fstab shows mounting of the /EFI/ubuntu partition from ESP - efi system partition to /efi/boot.

---

