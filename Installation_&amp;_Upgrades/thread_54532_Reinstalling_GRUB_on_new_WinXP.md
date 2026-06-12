---
title: "Reinstalling GRUB on new WinXP"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by GTar on 2005-08-05
Hi,

I've currently got WinXP installed on my primary HD. I've also got Ubunutu on the secondary HD.
I want to reinstall windows but obviously this will wipe GRUB from the primary disk as well. Just wondering what is the best way to insall it and if there are any guides around?
Also can I boot directly from the second disk?

Thanks.

---

### Post by sooqing on 2005-08-05
switch ur primary and secondary and install grub in linux.. configuring it to boot xp.. that is, after u installed xp while the linux hdd is plugged out..

---

### Post by GTar on 2005-08-05
Ok, so what you're suggesting is:

[list]
[*] Change BIOS to boot from the Linux HDD.
[*] Install GRUB package in Ubuntu
[*] Format and install WinXP on the First HDD
[*] Configure GRUB to be able to boot XP
[/list]

Does anyone know of a guide for configuring GRUB? Also does this mean that the linux drive would be the one I boot from?

---

### Post by iH8forcedRegistration on 2005-08-05
You may need to add another step or two to that. For the purpose of example, i'm going to call your Windows drive /dev/hda, and your Ubuntu drive /dev/hdb. If that's wrong, substitute as necessary.

Currently, you're booting to grub installed on /dev/hda. There's a chance that there is no bootloader installed on /dev/hdb, so I would probably do the following:
[list]
[*]Install GRUB on /dev/hdb. From a terminal in Ubuntu, type
```
grub-install /dev/hdb
```
[*]Reinstall windows on /dev/hda. This will overwrite Grub on /dev/hda (i'd feel better if someone would confirm this won't also overwrite the boot sector of /dev/hdb)
[*]Change your bios settings so that you boot to /dev/hdb
[*]Install GRUB again on /dev/hda (if you want)
[/list] 

A whole lot of information about GRUB and configuring it can be found [here](http://www.gnu.org/software/grub/manual/grub.html), but there are probably better references out [there](http://www.google.com/).

Some example code for adding Windows to GRUB that will **only work if Windows is on /dev/hda6** 
```

title=Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1

```

---

### Post by GTar on 2005-08-07
I think I've managed to get thus far however I'm finiding it impossible to boot from the partition on which ubuntu is installed. I think it might have something to do with the fact that both drives are SATA drives?

---

### Post by iH8forcedRegistration on 2005-08-08
If your BIOS supports SATA drives, the fact that the drives are SATA shouldn't make any difference.

Depending on the size, structure, and location of the Ubuntu partiton, it may actually be impossible to boot to it. At this point, probably the most helpful thing would be if I knew more about your parition structure. Which partitions are where?

A total guess:
There's a distinct possiblity that your BIOS is ignoring /dev/hdb (again, using the guesses at partition structure I made before) because /dev/hda is considered the primary hard drive. Some potential ways around this:
[list]
[*] boot to a Knoppix or Ubuntu Live cd, chroot into /dev/hdb, and re-run grub-install on /dev/hda
[*] Physically swap /dev/hda and /dev/hdb, do a manual boot from grub (because your original grub.conf will not work with the drives swapped), then either [change grub.conf to reflect the change in hardware] or [run grub-install on what used to be /dev/hda and switch them back].[/list]

---

### Post by buster on 2005-08-08
Is it possible that GTar could do this, if and only if, he can get into Ubuntu without the grub on the mbr? Say through the install disc?

1. Reinstall Windows, which rewrites the mbr.
2. Get into Ubuntu some other way.
3. Call up a terminal with root powers and type:

        grub-install /dev/hda

(Must say I've never used the command "grub-install")

?????? Sorry to write right through you GTar  :)

---

### Post by crispingatiesa on 2005-08-08
1. Reinstall windows (will rewrite the mbr)
2. Boot from the ubuntu installation CD (at boot time don't hit enter but, at the prompt write  "rescue") then enter
3. follow the instructions about languaje settings, network etc. U will get to a screan in which the installer will ask you what partition to boot and it will present you with the (hda) (hdb1) and (hdb2) choices (I'm assuming you have to drives and hda is windows, hdb1 your ubuntu and hdb2 swap))
4. select hdb1 this will boot you into your system
5. at the prompt write grub-install /dev/hda
6. reboot

It should fix the problem.

---

### Post by blastus on 2005-08-09
I wondered about that. So it's basically the same procedure in Ubuntu as in Fedora Core. In Fedora Core to reinstall GRUB to the MBR you would insert the rescue disk, enter "linux rescue", wait, select some language settings/network or whatever, wait, then enter...

chroot /mnt/sysimage
grub-install /dev/hda

...then press CTRL-D twice. Fedora Core doesn't give the option to select what partition to boot from although it probably would if there was more than one Fedora Core installation.

But before you do anything PRINT OUT a copy of your GRUB configuration file. That way you can edit it if something goes wrong. I don't know where it is in Ubuntu but in Fedora Core it is /etc/grub.conf.

---

