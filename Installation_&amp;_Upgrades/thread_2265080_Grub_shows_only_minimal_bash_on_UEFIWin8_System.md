---
title: "Grub shows only minimal bash on UEFI/Win8 System"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2015-02-12
I am trying to install Zorin 9 along Windows 8. If i deactivate UEFI, Windows cannot boot so i need to have UEFI on all the time.

Computer: Acer Aspire Laptop

I told the Zorin installer to put the bootloader directly on sda, not a ceratin partition, because i didnt want it to shoot down the windows loader. After the install, i only get the grub minimal bash and have no idea what to do. ( i still can boot windows by using a special function "choose boot device" of the BIOS, so the windows loader appears to be fine, but normaly after switched on, the broken grub appears)

Tried bootrepair on live CD, it didnt help: [http://paste2.org/_dbIdFkMd](http://paste2.org/_dbIdFkMd)

Also, the folder /boot/UEFI is empty, on the Zorin partition.

---

### Post by oldfred on 2015-02-12
It looks like you overwrote an Ubuntu install with Zorin. You still show the ubuntu folder in efi partition. If not using Ubuntu you can delete that and if you still have an UEFI entry you can also delete that with efibootmgr.

Script does not show contents of grub.cfg in /EFI/zorin, or the grub.cfg in the old ubuntu folder may be confusing it. Post that also.

The grub.cfg in zorin should be just three lines as a configfile pointing to the actual grub.cfg in Zorin's /Boot partition.

---

### Post by docdoc2 on 2015-02-12
Thank you very much for such a quick reply!

Yes, i installed kubuntu first which totaly failed, so i decided to use zorin and whiped kubuntu. Using EasyUefi in Windows, i also saw the ubuntu entry and disabled it. But that was all i could do with that programm.

content of /mnt/boot/EFI/zorin/grub.cfg:
> search.fs_uuid e2520d19-82bd-402f-8a44-0578146c0d5d root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

I tried a reinstall of grub2 via chroot from live cd but it only says:> root@zorin-os:/# grub-install /dev/sda
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
root@zorin-os:/# grub-install --recheck /dev/sda
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.

Also, when i used the 'set' command in the minimal bash, it said it couldnt do anything because of secure boot. Well, i guess it is quiet senseless to reinstall zorin on legacy and activate uefi afterwards?

---

### Post by ubfan1 on 2015-02-12
The "i386-pc" part of the grub-install path looks like the 32 bit legacy grub,not the UEFI grub, maybe some additional switches on the command like
sudo grub-install --target=x86_64-efi  --efi-directory=/boot/efi --uefi-secure-boot /dev/sda2

---

### Post by docdoc2 on 2015-02-13
I forgot to change back to UEFI. The Grub rerinstall worked without errors in UEFI mode, but did not help. I am still confronted with that annoying minimal bash of grub.

Should i change something in the grub.cfg in EFI/zorin?

---

### Post by oldfred on 2015-02-13
Are you getting grub> or grub rescue> ?

Have you tried manually booting from grub?

Did you just install grub to sda, or do the full uninstall/reinstall of grub from advanced mode? That sometimes fixes more things.

---

### Post by docdoc2 on 2015-02-13
Ahhh i was way too impatient and did the installation in legacy mode. I let the installer replace the system (old zorin) as i was used to do it (tired of doing this partition thing over and over) and the installer completely wiped windows and all other partitions. All data lost, i guess? It seems i have to stick to zorin now as i dont have a windows installation disc. well, i learned NEVER DO AUTOMATIC INSTALLATION again.

Thanks anyway!

---

