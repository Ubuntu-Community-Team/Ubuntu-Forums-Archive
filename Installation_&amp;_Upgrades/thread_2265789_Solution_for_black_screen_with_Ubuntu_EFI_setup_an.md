---
title: "Solution for black screen with Ubuntu EFI setup and HP tipps"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by hierstehtnormaleinname on 2015-02-17
Hello,

a lot of people are dealing with a black screen problem around the EFI installer of Ubuntu. The problem in detail acts about a dark screen and a hanging setup after selecting the "Install Ubuntu" or "Try Ubuntu" option within a UEFI install session.

Many hints and answers are in the net about possible solutions. Much people refused and switched back to a legacy install or turn of secure boot, fast boot and other options but in most cases the only problem are the graphic settings at setup time. In 90% of all cases all you need to do is pressing "e" when the installation ask you to choose between "Install Ubuntu" or "Try Ubuntu" and than add the already well known option called ```
nomodeset
``` anywhere at the end of the line where quiet splash is noted like: quiet splash nomodeset"

If you added the term nomodeset to this line press F10 and you will be able to continue your setup as usual in most cases! There also exists a very good (german) guide for all other questions of EFI setup here [http://wiki.ubuntuusers.de/EFI_Installieren](http://wiki.ubuntuusers.de/EFI_Installieren) maybe there is a good english version as well.


Tipps for HP only
For problems with new HP devices including desktops like HP Pavilion there is no need to turn of secure boot option or HP secure boot key in the bios before installing Ubuntu. Just make sure that you have selected a install media (like cdrom) over UEFI boot options at system start. You can reach the boot selection by repeatedly pressing F9 (for most newer HP devices) at start up. If there is no UEFI support activated go to BIOS first (pressing F10 for most newer HP devices) and turn it on. You may also deactivate legacy boot options completely if not needed to avoid booting a legacy install at all!

At setup select "Try Ubuntu &#8230;" and start the terminal after the system is online by pressing [STRG] + [ALT] + t
(If you run into the black screen problem try nomodeset as mentioned before!)

Now enter 
```
sudo apt-get install efibootmgr 
```

into the terminal and check if you'r in EFI setup to avoid installing a legacy version!
```
mount | grep efivars 
```
should give you something like 
```
... /sys/firmware/efi/efivars...
```

and

```
sudo efibootmgr
```


 something like 
```


&#8230;
BootCurrent: 000&#8230;
&#8230;

```

If you get this output you'r in EFI setup mode and can start the Ubuntu installation.
Please note that if you have previously installed Ubuntu on this hdd as UEFI your HP bios may repeatedly throws the error that no system disk could be found or refuses to boot after installing Ubuntu on your hdd. To solve this problem it is not enough to choose "Delete HDD and install Ubuntu" in installer. You need to start your live system and delete all partitions including the EFI partition (use gparted for example) save it, perform a restart and start the installation again.
(Note this is the easiest solution but works for single installations of Ubuntu only. Do not perform this on a multi OS installation or you may loose the possibility to boot at all &#8230;)

After this you should be able to start Ubuntu with UEFI and secure boot without any problems.

):P

---

### Post by vijay10 on 2015-02-18
Hi Sir,
           I want to change folder permission in my OS using chmod 777 -R /path, then i unable to change this, so please guide me.

---

