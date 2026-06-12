---
title: "Grub2 is playing it REALLY hard"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by martin11235 on 2013-06-09
Hi,

hope I choosed right section for this...

My laptop doesnt have CDROM so i created 1GB FAT partition and burned ubuntu iso like it was USB stick.
From that time i couldt start my windows or anything from HDD...But while booting PC i pressed F12 and choosed to boof from that 1GB drive...and it worked..i installed ubuntu on 50GB partition on disk. Rebooted. And ? Still no bootloader appeared same thing ...So I booted ubuntu live installed grub on /dev/sda so it should be on MBR and rebooted. I got grub prompt. I can boot my intalled Ubuntu when i write down to prompt following:
root (hd0,5)
kernel /boot/vmlinuz-************* root=/dev/sda6
initrd /boot/initrd-************
boot

i manually have to write down to grub what he has to do...i booted installed ubuntu, everything worked fine i used update-grub command he found all my operating systems including windows 7 said no error executed 100% correct. Then i rebooted and still grub prompt! 
I reinstalled grub several times, always on MBR pdated it even more times everything alwasy goes well, but i cannot get rid of grub prompt...
When i wrote to grub this:
rootnoverify(hd0,1)
(makeactive)
chainloader +1
boot

screen just flashed and came back to grub prompt, so no windows this way...I got seriously mad and deleted even my windows, used his big partition for my Ubuntu install again selected while isntalling to install grub on /dev/sda but same thing again ...grub prompt...driving me crazy for 3 days...If someone has solution...Another detail...this pc was by factory set to UEFI i changed it in bios to Legacy support even windows was installed using standard bios but new HDDs are compatible and still have MBR so this shouldnt be problem....

Its late night and im totally destroyded by this evil grub so my vocabulary might be not under 18age...

---

### Post by oldfred on 2013-06-10
One issue with new UEFI capable systems is Ubuntu may boot in either UEFI or BIOS mode. You have to boot in same mode as Windows is installed to easily dual boot. And how you boot installer is how it installs. 
UEFI and BIOS write hardware info differently to drive for systems to use, so you cannot dual boot when different systems are not in same mode. You can dual boot if you go into UEFI/BIOS and change to/From UEFI or BIOS to match install.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by martin11235 on 2013-06-11
Nice! That Boot-Repair is quite amazing noob-like-me-helper :)
Even though i choosed Legacy boot in bios settings that Boot_repair tool said that system is in EFI mode and needs that ~200MB partition...
After I runned this Boot-Repair some grub started and booted me my Ubuntu. (i still didt created that UEFI partition i guess i wll do it now)
So I have to reinstall my windows, then install Ubuntu once again and i hope it will we OK...

I guess my info about booting computer is pretty weak i should spend some nights doing my homework ;).

Btw here is link from Boot-Info if someone is interested: [http://paste.ubuntu.com/5753932/](http://paste.ubuntu.com/5753932/)

Thanks

---

