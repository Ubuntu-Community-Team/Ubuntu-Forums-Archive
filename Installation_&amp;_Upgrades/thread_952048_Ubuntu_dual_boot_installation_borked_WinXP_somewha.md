---
title: "Ubuntu dual boot installation borked WinXP somewhat"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Frodin on 2008-10-18
Hi,
I decided to install Ubuntu in some free space on the single drive of one of my computers.
I booted the 8.04 live CD and installed Ubuntu in a single 10GB partition between my 20GB NTFS WinXP install and the 120GB NTFS storage partition with no swap partition since i have 2GB ram and will only use this computer for light tasks.
Grub and Unbuntu works fine, however, when I try to boot my WinXP installation, i get this error message:
> "Windows could not start because the following file is missing or corrupt: Windows root>/system32/hal.dll. please re-install a copy of the above file"
When I manouver to the system32 folder on the WinXP partition in Ubuntu, the hal.dll file is there, furthermore, the boot.ini file is now located in the root folder of the storage partition(!)
I then booted the WinXP installation disk and entered the recovery console, to find that the WinXP installation was now on D: as opposed to C:, and the storage partition vice versa.
If I boot the Ubuntu live CD again, this is what the disk partitions look like in the partition manager:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88779&stc=1&d=1224367623[/IMG]
and this is what the boot.ini file looks like:
[PHP][boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/PHP]
Any idea of what to do to fix this?

---

### Post by caljohnsmith on 2008-10-18
> **Frodin said:**
> 
When I manouver to the system32 folder on the WinXP partition in Ubuntu, the hal.dll file is there, furthermore, [COLOR="Blue"]the boot.ini file is now located in the root folder of the storage partition[/COLOR](!)

What happened is you somehow changed your Windows partition from a primary partition to a logical partition since Windows is now on sda5. Windows normally can't be booted from a logical partition unless Windows places its boot files in a primary partition, which is why its boot files (including boot.ini) ended up in your primary partition that you use for storage. 

The good news though is that it is possible to boot Windows directly from a logical partition without having to leave its boot files in a primary partition. So first I would recommend manually moving all your boot files back to your Windows partition, and probably the easiest way to do it is when you are in Ubuntu, open up nautilus as root:
```
gksudo nautilus
```
And then copy/paste the three boot files back into the Windows partition:
```
boot.ini
ntldr
NTDETECT.COM
```
Next please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you would like my help. :)

---

### Post by Frodin on 2008-10-19
Hi, thanks for taking the time!
I copyed the three files back to the Windows partition, here is the output of 
```
sudo fdisk -lu
```
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x049b049a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16065    41961779    20972857+   f  W95 Ext'd (LBA)
/dev/sda2   *    61432560   312576704   125572072+   7  HPFS/NTFS
/dev/sda3        41961780    61432559     9735390   83  Linux
/dev/sda5           16128    41961779    20972826    7  HPFS/NTFS

Partition table entries are not in disk order

```
Hmm, looks like sda1 and sda5 is (almost) the same partition listed twice?

---

### Post by caljohnsmith on 2008-10-19
I know it can be confusing, but sda1 is what is called an "extended" partition, and an extended partition is merely a container for logical partitions; your only logical partition is sda5, so sda5 is inside of sda1 and takes up all of sda1's space. :)

Next do the following:
```
sudo mount /dev/sda5 /mnt
sudo cp /mnt/boot.ini /mnt/boot.ini.backup
gksudo gedit /mnt/boot.ini
```
And edit your boot.ini to change the partition from 2 to 3:
```
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(3)[/COLOR]WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```  
To explain a bit, Windows only counts primary and logical partitions (as far as boot.ini is concerned), not the extended partition container; that means according to Windows your partitions would be:
```
sda2 = partition(1)
sda3 = partition(2)
sda5 = partition(3)
```
And since Windows is now on sda5, you need to use partition(3) in your boot.ini. 

Next you will need to modify your Grub's menu.lst to boot Windows correctly:
```

gksudo gedit /boot/grub/menu.lst
```
Then add the following entry for Windows at the end of the file (and delete any other Windows entries if you see one):
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Next boot your Windows Install CD, and run both:
```
fixboot D:
chkdsk /r D:
```
And run chkdsk as many times as it takes until it reports no errors. Next reboot, select Windows, and let me know exactly what happens. It is likely we will also have to use testdisk to rebuild the Windows boot sector, but give the above a shot first and let me know how far you get. :)

---

### Post by Frodin on 2008-10-19
Thanks again, I'm running checkdisk right now, I will edit this post with updates when it finishes and if I'm able to boot afterwards.
After the second run of checkdisk it did not display any errors corrected, so tried to boot windows, got this error message:
```
Starting up...

A disk error occured
Press Ctrl+Alt+Del to restart
```

---

### Post by caljohnsmith on 2008-10-19
OK, I think we might be really close to getting Windows to boot OK. Next step would be to boot into Ubuntu and do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. :)

---

### Post by Frodin on 2008-10-19
That seems to have done the trick! I'm in Windows now, and everything seems fine so far at least:) Hopefully I have learned something too!
Now I just need to find out how to get all the other things working in Ubuntu, and I won't be needing Windows at all!
Thank you very much for your help!

---

### Post by caljohnsmith on 2008-10-19
That's great news Windows works again, and I'm glad I could help out. Cheers and have fun Ubuntu-ing. :)

---

