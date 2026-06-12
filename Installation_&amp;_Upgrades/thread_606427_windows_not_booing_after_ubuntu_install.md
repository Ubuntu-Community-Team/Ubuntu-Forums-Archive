---
title: "windows not booing after ubuntu install"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by fsleeman on 2007-11-07
I am trying to install Ubuntu and Windows XP on the same hard drive. I can install and boot XP fine, and then with Ubuntu. After they are both installed XP won't boot from grub. I get the start up screen with the XP logo, but then I get a blue scree of death with an 7B stop error. I have tried doing this several times with the same results. My XP grub entry is:

rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map(hd1) (hd0)
chainloader +1
boot

Any ideas about what I can do to get XP to boot?

---

### Post by logos34 on 2007-11-07
If they're on the same drive you don't need the map lines. Just
> 
title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

Also, make sure the XP partition is flagged as boot (*).  Check by opening a terminal and running:

**sudo fdisk -l**

---

### Post by fsleeman on 2007-11-08
I tried that but still no luck. As before, Windows will *start* to boot before the BSOD after the Windows XP logo and blue status bar has been up for about 5 seconds. I don't know if the grub installation screwed up something for Windows.

---

### Post by bulldog on 2007-11-08
Think there's something wrong with your windows.
Grub only points to the right partition then the windows loader takes over and grub isn't involved anymore.
To be sure,reinstall the windows bootloader [recovery console] and try if it will boot.

Maybe you can give me the output of ```
sudo fdisk -l
``` from a terminal?

---

### Post by fsleeman on 2007-11-08
I will have to wait until I am home from work to get the real output but I do remember that the NTFS partition is from 1 to something like 18000. It does have the * for booting. How do you reinstall the Windows bootloader? Is it fixboot? If I reinstall the Windows bootloader will that overwrite grub?

---

### Post by bulldog on 2007-11-08
Yes in the recovery console of your windows install disk logon to your windows install and type fixboot and maybe fixmbr.

Yes grub will be overwritten,but you can reinstall it with the live cd.

---

### Post by fsleeman on 2007-11-08
What is the process of reinstalling grub from the LiveCD? If I install grub again, won't that just override the MBR and screw up Windows again?

---

### Post by bulldog on 2007-11-08
> **fsleeman said:**
> What is the process of reinstalling grub from the LiveCD? If I install grub again, won't that just override the MBR and screw up Windows again?

I run four OS's from grub and windows is among them without any problem.
I didn't say windows will boot again when you fixed the windows bootloader,just a maybe to be sure windows is okay.
To install grub from the live cd 
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr[b] but be carefull here,if the find command returned (hd1,?)
the setup should be (hd1) not (hd0)!! [/b]
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by fsleeman on 2007-11-08
I tried fixboot and fixmbr in the recovery console but Windows will not boot. I get a message stating "Invalid partition table". When I tried to install Ubuntu I had a fresh XP install. I cleared the previous partitions, installed windows on the 130 GB it saw on the 320 GB drive and installed Ubuntu on the remaning section. Has anybody been able to install and boot both OS's on the same harddrive? I have dual booted before but with RedHat and with two physical harddrives.

---

### Post by crjackson on 2007-11-08
> **fsleeman said:**
> I tried fixboot and fixmbr in the recovery console but Windows will not boot. I get a message stating "Invalid partition table". When I tried to install Ubuntu I had a fresh XP install. I cleared the previous partitions, installed windows on the 130 GB it saw on the 320 GB drive and installed Ubuntu on the remaning section. Has anybody been able to install and boot both OS's on the same harddrive? I have dual booted before but with RedHat and with two physical harddrives.

Yes, I have 6 systems right now dual booting WinXP & Ubuntu (both 7.04 & 7.10).

---

### Post by fsleeman on 2007-11-08
Whats the trick to get Windows to boot after Ubuntu and grub is installed? Is there a step I am messing up?

---

### Post by Pumalite on 2007-11-08
Use Super Grub to make sure your Windows is OK. Later, if Vista, allocate space for Ubuntu first, then install Ubuntu. If XP, you can use Gparted to prepartition your drive and then install Ubuntu.
Also: where is your sudo fdisk -lu (you can do it from your Ubuntu Live CD)

---

### Post by fsleeman on 2007-11-08
Here is my fdisk -lu output, from Ubuntu normal boot:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
102 heads, 51 sectors/track, 120173 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          51   204797537   102398743+   7  HPFS/NTFS
/dev/sda2       204797538   212798213     4000338   82  Linux swap / Solaris
/dev/sda3       212798214   625139945   206170866   83  Linux

---

### Post by Pumalite on 2007-11-08
You have to edit your menu.lst and add an entry for Windows with 'rootnoverify (hd0,0)'. I suspect Grub will do that for you automatically anyway. You have to let Grub install to MBR (default)

---

### Post by fsleeman on 2007-11-08
I tried that before and still get the same result where XP will start booting with the logo and progress bar but will then BSOD with the 7B error. 

My entry for XP is:

title Microsoft Windows XP Professional
rootnoverfiy (hd0,0)
savedefault
makeactive
chainloader +1

Ubuntu still boots fine.

---

### Post by Pumalite on 2007-11-09
Post:
cat /boot/grub/menu.lst

---

