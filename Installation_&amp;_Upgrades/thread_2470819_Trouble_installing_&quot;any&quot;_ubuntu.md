---
title: "Trouble installing &quot;any&quot; ubuntu"
date: 2022-01-12
forum: Installation &amp; Upgrades
---

### Post by Seadevil on 2022-01-12
I KEEP GETTING ERROR MESSAGES  :  "creating ext4filesystem for /in partition # 9 of scs13 (0,0,0)(sda)"

install just hangs up in the final lap of installation.

---

### Post by ubfan1 on 2022-01-12
How big is the partition?  Might take awhile to create the filesystem.  Do you get any disk activity during the "hang up"?

---

### Post by Seadevil on 2022-01-12
partition is only 60 gb.
no disk activity during the hangup.

tried to reinstall...now it says :   the attempt to mount a file system with type vfat in scs13 (0,0,0) partition #1 (sda) at boot/efi failed.  You may resume partitioning from the partitioning menu.

go back ...takes me to quit and start over.  

is this a Bios problem ??

---

### Post by T6&amp;sfpER35% on 2022-01-13
is this a ubuntu install alone , or installing next to windows?
usually i just let the installer take care of partitioning , i don't mess around with creating partitions 1st.
at installation where it ask about disk or something ,i can't remember , just choose use hole disk, the installer will create a partition then.
installing next to windows is another matter though i know nothing about

---

### Post by yancek on 2022-01-13
>  I KEEP GETTING ERROR MESSAGES  :  "creating ext4filesystem for /in partition # 9 of scs13 (0,0,0)(sda)"
 

That is not an error message it is just informing you of what the installer is doing which is the default for Ubuntu, creating an ext4 filesystem for the / (root) of the system.

>  install just hangs up in the final lap of installation. 		

The final 'lap' would be the bootloader installation which you refer to in your last post, the vfat partition with /boot/efi.  It would be useful to post information on whether you are trying to install in EFI mode and whether you have another OS already installed and there is a currently existing EFI partition and if that OS is windows.  If you have windows installed EFI, you might take a look at the link below which is the Ubuntu documentation on dual booting UEFI with windows.  If that is not the case. post more detail on exactly what you have.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by MAFoElffen on 2022-01-13
What might be helpful here is to run both the Boot-Repair disk on it to generate a report from boot-info to see what the disk layout and such is... And run the UbuntuForums system-info script in my signature line, to see whatthey system hardware is and whatelse is there, You can run that from any Ubuntu Flavored LiveCD.

The one question would be: Does this system successfully boot off an Ubuntu LiveCD and run stably f you select "TRY"?

---

