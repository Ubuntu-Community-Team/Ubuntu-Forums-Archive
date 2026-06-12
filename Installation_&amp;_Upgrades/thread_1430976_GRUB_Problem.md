---
title: "GRUB Problem"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by matthew5025 on 2010-03-16
I installed ubuntu on a External HDD, and after that i need to plug in my Ext HDD for grub to load, otherwise it will give me a Try (Hdd0,0). Is there anyway to revert back to Windows MBR?
BTW if t helps, i bought my Ext HDD as an additional storage as my Hdd was getting full, than i decided to install ubuntu on the drive. Now the boot screen shows 4 ubuntu boots (2 recovery) and 2 Windows boot (1 recovery. That i know although it wasn't stated) The problem is that my Internal HDD is 160GB partioned into 2 parts (1 for Vista, 1 for Windows 7). Now other than the problem above, GRUB will not detect Windows 7. Not a big problem as i said i backed everything up to my Ext HDD. Just thought it might help.

---

### Post by kio_http on 2010-03-16
Try 
```
sudo update-grub
```

If Windows 7 is still not detected by grub, then please specify which version of windows on which partition, needs to be on mbr.

Once Windows 7 or Vista loader is on mbr, you can set up an entry with **EasyBCD 2 BETA** (Karmic is unsuppoted by v 1.0) under Windows.

---

### Post by matthew5025 on 2010-03-16
Nono, you don't get me. I want to remove grub and use Windows MBR instead of grub. I also want to be able to boot my computer without my Ext HDD.

---

### Post by kio_http on 2010-03-16
> **matthew5025 said:**
> Nono, you don't get me. I want to remove grub and use Windows MBR instead of grub. I also want to be able to boot my computer without my Ext HDD.

To be able to respond I need to know the version on Windows whose bootloader you want to be on MBR!

I also need to know on which partition it is installed to.

---

### Post by matthew5025 on 2010-03-17
All I need is to be able to remove grub and be able to boot up ubuntu by using the BIOS.
Windows Vista-- C:\ (80GB)
Windows 7-- D:\ (80GB)
Ubuntu-- External HDD (320 GB)

---

### Post by presence1960 on 2010-03-17
Simple Fix- you want to put GRUB on MBR of the external disk & then fix internal disk MBR to be windows. Both can be accomplished from the 9.10 CD (that is if you install karmic 9.10 on the external disk). First let's fix the internal disk so it boots windows. Boot the Ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore the warning. next in terminal run ```
sudo lilo -M /dev/sda mbr
```Your internal disk MBR is now windows, when you boot without the external plugged in you will boot to windows.

Now you want to put GRUB on MBR. Still from the Live CD run in terminal with the external plugged in ```
sudo fdisk -l
```That is a lowercase L in -l
Post the output of that command back here and I will give you two commands to run to put GRUB on the external disk MBR. This will allow you to boot without the external and go to windows, and if you set the external to boot before the hard disk in Device Boot order in BIOS when your external is plugged in at boot you will get GRUB and boot ubuntu from the external.

If you are using a different version of Ubuntu (not 9.10) let me know and I will go from there.

---

### Post by matthew5025 on 2010-03-18
I only have the CD for 9.04 but i updated ubuntu to 9.10

---

### Post by presence1960 on 2010-03-18
> **matthew5025 said:**
> I only have the CD for 9.04 but i updated ubuntu to 9.10

You can fix the MBR of the internal disk to boot windows with the 9.04 Live CD by following the instructions I posted for that. But as far as putting GRUB on MBR I need more info since you upgraded to 9.10

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external disk plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by matthew5025 on 2010-03-18
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub4Dos is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdc1 already mounted or sdc1 busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb3f9332

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  12 Compaq diagnostics
/dev/sda2    *     20,482,048   166,539,263   146,057,216   7 HPFS/NTFS
/dev/sda3         166,539,264   312,578,047   146,038,784   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0f90e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A20A-9608                              vfat       PQSERVICE                     
/dev/sda2        A22AA8492AA81BF3                       ntfs       ACER                          
/dev/sda3        D87ED1B97ED1911C                       ntfs                                     
/dev/sdc1        5ff202e4-2e4d-4fe2-919b-860e1f8de0bc   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


```

---

### Post by presence1960 on 2010-03-18
I am assuming that sdc (320 GB) is your external disk here. You can fix the internal disk to boot windows by following the instructions I gave in post #6 using 9.04 Live CD.

As far as your external there appears to be a problem there. But you can try to put GRUB on the MBR of the external and see what happens. it won't hurt anything. First fix the internal MBR as I explained in an earlier post. Then from terminal still in the Live CD do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd3,0)". 
3. Type "root (hd3,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
4. Type "setup (hd3)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

On reboot go into BIOS and set USB or Removable ahead of hard disk in the Device Boot priority. Save changes to CMOS & continue booting. What this will do is when your external is plugged in that will boot first and bring up GRUB so you can boot Ubuntu, when the external is unplugged your machine will boot right to windows.

---

### Post by kio_http on 2010-03-19
You can also launch the startup repair tool under the recovery options in Windows Vista/7 DVD setup. (If you have a recovery disk you can't do this)

---

### Post by uRock on 2010-03-19
First thing I did after clean installing Win 7 was to back it up and burn the repair disk.

---

### Post by matthew5025 on 2010-03-19
> **kio_http said:**
> You can also launch the startup repair tool under the recovery options in Windows Vista/7 DVD setup. (If you have a recovery disk you can't do this)
Nope, I don't have the CD. The OEM kept it.

---

### Post by matthew5025 on 2010-03-19
> **presence1960 said:**
> I am assuming that sdc (320 GB) is your external disk here. You can fix the internal disk to boot windows by following the instructions I gave in post #6 using 9.04 Live CD.

As far as your external there appears to be a problem there. But you can try to put GRUB on the MBR of the external and see what happens. it won't hurt anything. First fix the internal MBR as I explained in an earlier post. Then from terminal still in the Live CD do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd3,0)". 
3. Type "root (hd3,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
4. Type "setup (hd3)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

On reboot go into BIOS and set USB or Removable ahead of hard disk in the Device Boot priority. Save changes to CMOS & continue booting. What this will do is when your external is plugged in that will boot first and bring up GRUB so you can boot Ubuntu, when the external is unplugged your machine will boot right to windows.
Without the external HDD, booting up from my internal HDD looks like this
GRUB loading stage1.5.
GRUB loading, please wait...
Error 21
That is what im trying to remove, cause without my external HDD i can't boot up, and that really is quite stupid isn't it?

---

### Post by oldfred on 2010-03-20
presence's post #6 is the best way from Ubuntu to reinstall a windows boot loader into the MBR of your interal drive. A windows boot loader really only looks for the boot (active) partition and jumps to that partition PBR or boot sector to continue booting. Since windows only boots from the active partition, the second install of windows is combined into the first for booting. 
Grub will not be able to boot each unless they are separated. Many lose boot to a second win when they uninstall a earlier win as essential files are deleted.

You can also use windows disk and run repair or from command line fixboot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by matthew5025 on 2010-03-26
> **oldfred said:**
> presence's post #6 is the best way from Ubuntu to reinstall a windows boot loader into the MBR of your interal drive. A windows boot loader really only looks for the boot (active) partition and jumps to that partition PBR or boot sector to continue booting. Since windows only boots from the active partition, the second install of windows is combined into the first for booting. 
Grub will not be able to boot each unless they are separated. Many lose boot to a second win when they uninstall a earlier win as essential files are deleted.
 
You can also use windows disk and run repair or from command line fixboot.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 Thx it worked!

---

