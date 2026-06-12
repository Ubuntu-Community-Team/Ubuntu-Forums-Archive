---
title: "Ubuntu 20.04 to 22.04 Not Working END KERNEL PANIC NOT SYNCING:VFS UNABLE TO MOUNT RO"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by query22 on 2022-09-07
Good morning everyone,

 after a week of frustration I  am asking you for help. 

I tried to look for solutions on the various  sites without success, many suggested solutions  do not work on my PC. 

I have been using Ubunu for about 2 years on an  Asus K53SC Laptop, Processor : Intel Core i7 2670QM 2.20 Ghz - 16GB 4 GB  64 Bits - Dual Boot W10 / Ubuntu 20.04 LTS 

A week ago in addition to  the various updates proposed, the system proposed the change of version,  which I did. 
The computer crashed, during the update, I relaunched the  update with the result that none of the options present (including  recovery mode) work. 

I find six starting options: 
1) Linux  5.15.0-46 lowlatency + Recovery Mode 
2) Linux 5.4.0-125 lowlatency +  Recovery Mode
3) Linux 5.4.0-124 lowlatency + Recovery Mode
none  of the 6 working (the first version seems out of place....) all end  with "END KERNEL PANIC - NOT SYNCING:VFS UNABLE TO MOUNT ROOT FS ON  UNKNOWN BLOCK (0,0) 

Obviously I no longer see the folders that were in  the home with their data. 

Among other things I tried to use boot repair,  but to no avail, I then chose the option of tracking the execution,  below the link 
[https://paste.ubuntu.com/p/ZSrPkCXSnT/](https://paste.ubuntu.com/p/ZSrPkCXSnT/) 

From what I could see the fstab file has no reference.

I look forward to  help. 
Thanks in advance

---

### Post by ubfan1 on 2022-09-07
fstab is at line 218, and seems to have the right UUID info.  Sometimes it helps if you can rerun sudo update-grub to rewrite the /boot/grub/grub.cfg file.  A wrong device on the linux kernel line would be one of the possible causes of that error.

---

### Post by oldfred on 2022-09-07
See line 723.

It looks like you have bold BIOS/MBR configuration. But Ubuntu (at least now) is set for UEFI boot as you have the mount of the ESP - efi system partition in fstab on line 224.

So you have two versions of grub installed? One in MBR and one in ESP which is not shown in report as you ran report from a BIOS boot.
One grub will not work, other may work?
How you boot live installer UEFI or BIOS is how it installs or how it does repairs.

Windows looks like it is in BIOS boot mode, which it must be if drive is MBR(msdos). 
You cannot mix BIOS & UEFI on same drive, and should not mix on system. If UEFI system, better to have both Windows & Ubuntu in UEFI boot mode.

If you have current Windows and really want old BIOS boot, use Boot-Repair's advanced mode booted in BIOS mode. Choose to totally reinstall grub and check to install newest kernel also.

---

### Post by query22 on 2022-09-09
I've been trying to solve the problem for 10 days now. 

I decided to reinstall the system. 

Thank you all

---

### Post by reaversword3d on 2022-09-16
So, no solution, eh?.

I'm in the same kernel panic situation after finish upgrade and reboot.

Should I open a new thread or must I continue this one trying to request for help?

22.04 way released almost five months ago, easy upgrade option from 20.4, a month ago.

How it is possible to finish with a kernel panic after all this time?

---

### Post by oldfred on 2022-09-16
@reaversword3d
Please start your own thread as boot issues are often not same issue.
Post brand/model system.
Post link to summary report from Boot-Repair.
And post what you have tried already.

---

