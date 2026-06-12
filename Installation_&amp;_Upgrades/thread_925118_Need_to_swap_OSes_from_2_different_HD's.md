---
title: "Need to swap OSes from 2 different HD's"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by thezman007 on 2008-09-20
Hi and thanks to all who help. I have found MANY different discussions on how to uninstall Ubuntu, but I think my situation is a little more complex than that. Trying to find out the easiest/best/safest way to accomplish this.

What I have:

Original 160 GB with WIN XP on it.
New WD 500GB with Ubuntu on it.

What I would like to have:

Windows on 500GB with all my movies, pics, etc.
160 GB drive split between Ubuntu and space available for backups.

Not so much an uninstall as a move of Ubuntu. I also have 2 GRUB style screens for some reason. I installed using the disk created by downloading the files from ubuntu.com and so forth. My BIOS is pretty limited so I asked for help booting from the CD, then installed ubuntu w/o a hitch. Now I have a GRUB which asks which version of Ubuntu I want or windows, choose windows and I get a different screen asking the same thing.

Anyways,

Windows refuses to see the 500 GB drive, I have file sharing issues :( (all from Windows I'm sure), and want to restructure. I'm wary of messing with my partitions as that's at least part of how this got started :) but understand that may be part of the solution.

Could really use the help before set aside the time to park my keister and take care of this. :lol:  Thanks so much.

---

### Post by Pumalite on 2008-09-20
Post:
sudo fdisk -lu

---

### Post by thezman007 on 2008-09-20
Ok, where and how do I post that; or is that a post for me to search for because i don't see it? What can I expect it to do exactly?

Thanks

---

### Post by thezman007 on 2008-09-20
Sorry, :rolleyes: figured that out here's the info:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x064dccfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   965394044   482696991   83  Linux
/dev/sda2       965394045   976768064     5687010    5  Extended
/dev/sda5       965394108   976768064     5686978+  82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   312560639   156280288+   7  HPFS/NTFS

---

### Post by Pumalite on 2008-09-20
Use Gparted Live CD and erase sda1, sda2, and sda5. Fix your Windows MBR with Super Grub:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by thezman007 on 2008-09-21
Thanks Pumalite!!! :biggrin: That worked well, plus I learned how to boot from a USB. The only thing I would like to change now is that I still have a screen asking if I want to boot up WIN XP or Ubuntu, when I don't have Ubuntu anymore (until I swap around some files and reinstall). It's not the GRUB screen. I started getting this screen after I asked the Ubuntu installer disk to help me boot from the CD-ROM.

Any ideas on how to get rid of it?

---

### Post by caljohnsmith on 2008-09-21
> **thezman007 said:**
> Thanks Pumalite!!! :biggrin: That worked well, plus I learned how to boot from a USB. The only thing I would like to change now is that I still have a screen asking if I want to boot up WIN XP or Ubuntu, when I don't have Ubuntu anymore (until I swap around some files and reinstall). It's not the GRUB screen. I started getting this screen after I asked the Ubuntu installer disk to help me boot from the CD-ROM.

Any ideas on how to get rid of it?
It sounds like it might be your Windows boot screen with the option to boot Ubuntu. Try doing the following from your Live CD:
```
sudo fdisk -lu
```
Find which is your windows partition in the form /dev/sdX (like /dev/sda1 for example) by noticing that it is type "NTFS". Then mount it and print it's "boot.ini" file:
```
sudo mount /dev/sdX /mnt
cat /mnt/boot.ini
```
Post the results of the above commands and we can check if its your Windows boot loader that has the option to boot Ubuntu.

---

### Post by thezman007 on 2008-09-21
This is the result:

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)/WINDOWS
timeout=15

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)/WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr="Ubuntu"

I think that means it is Windows, right?

Thanks :)

---

### Post by caljohnsmith on 2008-09-21
> **thezman007 said:**
> This is the result:

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)/WINDOWS
timeout=15

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)/WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
[COLOR="Red"]C:\wubildr.mbr="Ubuntu"[/COLOR]

I think that means it is Windows, right?

Thanks :)
That line above is what I suspected; you installed Ubuntu using Wubi in Windows at some point, and it modified your Windows XP boot.ini file. That is why you are still getting the option to boot Ubuntu on start up. Did you uninstall Ubuntu yet in Windows with the "Add/Remove Programs" from the Windows Control Panel? If you do, it should restore your boot.ini back to the way it was. If you have all ready uninstalled Ubuntu that way, you can manually fix your boot.ini file by doing the following, while you still have your Windows partition mounted on /mnt (from the previous instructions):
```
gksudo gedit /mnt/boot.ini
```
Just delete the line that says:
```
C:\wubildr.mbr="Ubuntu"

```
Save, and you will now boot directly into Windows instead of getting the boot menu with an option for Ubuntu. Let me know how it goes. :)

---

### Post by thezman007 on 2008-09-21
I didn't even know it was installed "Wubi" style! Unfortunately, there seems to be a problem. Windows says "An error occurred while trying to remove Ubuntu. You  do not have access to F:\Ubuntu\Uninstall-Ubuntu.exe. Then it gives me a command line for the uninstall program. And let's me browse for the program. I'm pretty sure that program was obliterated from my hard drive when I formatted the partitions, then migrated my Windows files to my 500 GB drive. Can I do it from the Ubuntu LIVE CD or something?

---

