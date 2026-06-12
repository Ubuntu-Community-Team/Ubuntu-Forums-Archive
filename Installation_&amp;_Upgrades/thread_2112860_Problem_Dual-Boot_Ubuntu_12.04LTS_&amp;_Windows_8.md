---
title: "Problem Dual-Boot Ubuntu 12.04LTS &amp; Windows 8"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by knowNothing23 on 2013-02-05
Secure boot: Disabled
When I set boot all with Legacy: Ubuntu boots, but Windows 8 doesn't.(UBUNTU partition is primary boot)

When I set boot all with EFI: Ubuntu boots without GUI and Windows 8 doesn't. (UBUNTU partition is primary boot)

When I set boot from Windows Manager as primary: Windows boots, but Ubuntu does not appear as a choice to boot. I have been told that they are not compatible in that Windows boot program.

Boot-repair from live CD gives me this:
[http://paste.ubuntu.com/1614848/](http://paste.ubuntu.com/1614848/)

Help! 
I am about to install Oneiric Ocelot to see, if its a problem of 12.04 LTS.

BTW, all OS are 64bits.
Also, when I try to boot Windows I get the error:
error: unknown command 'drivemap'
error: invalid EFI file path

---

### Post by oldfred on 2013-02-06
If your system had Windows 8 pre-installed you have secure boot.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 

Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
You did not mention Lenovo model. Others that worked (eventually):
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

And one that has issues:
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by knowNothing23 on 2013-02-06
Thank you, Fred.

This thread saved me:
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Nevertheless, I get in GRUB a bunch of Windows options to load:
Windows boot recover on EFI <and some path to .efi>
WIndows boot recover on EFI <other path>
...

There's one that doesn't show recovery but it does appear in an odd way | 
Windows boot EFI <another path> 
Anyway, that one works. 

I guess these bugs will be addressed eventually.

Thank you!

---

### Post by oldfred on 2013-02-06
Also Boot-Repair may not automatically know which efi files in efi partition are boot files, so everything in efi partition is created as a boot entry. 
Some vendors create a separate somewhat hidden efi type partition with all the repair efi files. They must somehow switch efi flag to boot those. 
But some like yours seem to put all the recovery repair efi files in the same efi folder.

I would back up efi partition and edit 25_custom for any entries you may not want. But you may need those for repairs? 
And you can turn off os-prober to stop the grub2 invalid entries.

       # Edit 25_custom entries created by Boot-Repair:
Also change execute flag or it will run both current & backup.
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

   # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub

---

### Post by knowNothing23 on 2013-02-06
Thank you, I will definitely take a look.

Now, I have problems with a Broadcom wireless card. The wireless signals shown are minuscule. At least on Windows 8, I can connect.

Oh well, it's good to be a CS student using Ubuntu.

---

### Post by oldfred on 2013-02-07
There have been a lot of threads on Broadcom, but I do not have that. May be best to search forum or start a new thread on that issue.

---

### Post by knowNothing23 on 2013-02-07
[QUOTE=I would back up efi partition and edit 25_custom for any entries you may not want. But you may need those for repairs? 
And you can turn off os-prober to stop the grub2 invalid entries.

       # Edit 25_custom entries created by Boot-Repair:
Also change execute flag or it will run both current & backup.
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

   # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub[/QUOTE]

I don't know where I can find the file mentioned for editing. 
Would the code instructions that you give me would open the files mentioned for editing?

---

### Post by oldfred on 2013-02-07
This opens 25_custom for editing in administrative mode.

gksudo gedit /etc/grub.d/25_custom

But I suggest backing it up first, but if you keep backup in same folder it will run twice if still executable. So we also have to turn it off. Or you can copy to another folder as a backup.

---

### Post by sushi80 on 2013-02-07
Hi all

I have a similar problem:
I have 6 windows entries

Windows UEFI recovery bootmgfw.efi  ----this runs win8
Windows Boot UEFI recovery           ----this runs win8
Windows UEFI recovery LrsBootmgr.efi ----this runs the recovery app from lenovo
Windows Boot UEFI recovery bootx64.efi   ----this runs the recovery app from lenovo
Windows Recovery Environment (loader) (on /dev/sda3)  ----this is broken
Windows Recovery Environment (loader) (on /dev/sda3)  ----this is broken

how do i fix and what should i remove??


here my config
[http://paste.ubuntu.com/1621618/](http://paste.ubuntu.com/1621618/)


thanks :):)

---

### Post by oldfred on 2013-02-08
If you turn os-prober script off, then these two will be eliminated.

> Windows Recovery Environment (loader) (on /dev/sda3)  ----this is broken
Windows Recovery Environment (loader) (on /dev/sda3)  ----this is broken


The others are your choice. Backup efi partition and 25_custom and/or grub.cfg. Then if you system boots with more than one entry you can just delete or comment out with # those boot stanzas you do not want.

---

### Post by sushi80 on 2013-02-11
All done! Thanks oldfred

It looks much better now!! :)

---

