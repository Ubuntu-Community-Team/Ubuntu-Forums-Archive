---
title: "Problem with Windows 8 dual boot. http://paste.ubuntu.com/5635716/"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by wilmer11 on 2013-05-05
Hello,

I am having problems problem with Windows 8 dual boot installation. I have an ASUS N56VJ DH71 - Core i7 3630QM - Windows 8 Home -bit - 8 GB RAM. 

1. I installed 12.04 alongside Windows 8 according to guidelines at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). I ran into problems with Secure boot where if secure boot not selected I could load UBunto and if selected I could load Windows.

2. I tried the boot repair as outlined at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) for which I burned  Ubuntu-Secure-Remix. This did not solve the problem and I tried a new installation of Ubuntu under  Ubuntu-Secure-Remix. This time the installer asked for partition space (something that 12.04 did not ask for), I assigned 50% of the Windows data space.

3. After 2. No system would load. I did an MBR under Windows, didn't realize the first time that Windows 8 would go into a Windows 32 directory and did a legacy MBR by mistake. Repeat the operation and did the EFI MBR.

4. I repeated the boot-repair under Ubuntu, it asked for several downloads and installs and now I have:
        a) With Secure Boot disabled load Ubuntu but Windows 8 attempt will produce "error: can't five command drivemap"; "error: Invalid EFI file path".

        b) With the Secure Boot enabled I get the Secure Boot Violation error: Invalid signature detected. And directs me to the Bios setup screen.

5. I have tried restoring Windows 8 from the hard drive but the systems claims that a partition is missing.

This is my system reported information: [http://paste.ubuntu.com/5635716/](http://paste.ubuntu.com/5635716/)

Help highly appreciated to have this dual boot running.

Wilmer

---

### Post by oldfred on 2013-05-05
Ubuntu (and Windows) install in UEFI mode or BIOS boot mode depending on how you boot installer. Also default repairs from Boot-Repair work the same way. I believe if in BIOS mode with Boot-Repair you can select UEFI repair.

But you originally installed in BIOS mode and it created a bios_grub for grub to boot in BIOS mode. You cannot easily dual boot with Ubuntu in BIOS mode and Windows in UEFI mode. Both need to be UEFI.

It looks like Boot-Repair added grub-efi, but left a boot flag on your Windows partition. In BIOS booting, you have to have a boot flag on the Windows partition with the boot flag. But with UEFI and gpt partitioning you can oly have a boot flag on the efi partition. Your sda4 is your Main Windows install and sda1 is the real efi partition.

```
 Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448     2,459,647     1,843,200 Windows Recovery Environment (Windows)
/dev/sda3       2,459,648     2,721,791       262,144 Microsoft Reserved Partition (Windows)
/dev/[COLOR=#ff0000]sda4[/COLOR]       2,721,792   784,130,047   781,408,256 [COLOR=#ff0000]EFI System partition[/COLOR]


```

Boot live installer and use gparted, click on sda4, and right click manage flags, & remove boot flag. Make no other changes to sda4 as NTFS is sensitive to any changes.

Then try booting with either secure boot on or off.

---

### Post by wilmer11 on 2013-05-05
Thank you Olfred,

I tried the solution but the problem persists, same error messages. gparted has a warning sign next to sda4: unable to read the contents of this file system. Because of this some operations may be unavailable. Any other recommendation?

Wilmer

---

### Post by oldfred on 2013-05-05
Gparted will show that if it need chkdsk or is hibernated and Windows 8 is always hibernated, unless you turn that off. May not be an issue, but sometimes then if Windows 8 is hibernated, you may have issues getting back into it.

From UEFI are you booting the renamed Windows file? That should work with secure boot on as it really is grub's shim file.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by wilmer11 on 2013-05-05
The Grub Menu offers:

Ububtu
Advanced options or Ububtu
Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader
Windows Recovery Environment (loader) (on /dev/sda2)
Windows 8 (loader) (on / dev/sda4)

I had never tried Windows ***UEFI bkpbootmgfw.efi***, I did and the system did a drive D: repair and Windows started with no problems. Now without Secure Boot ***Windows Boot UEFI loade*r **also works (before repair it did not work). ***Windows 8 (loader) (on / dev/sda4) ***Does not work. With Secure Boot control no operation is possible. This is a much better situation though, now I can use both operating systems when Secure Boot is disabled.

Three questions:

1) I am a Linux novice, are the Grub options listed or do I have extra options that could be eliminated? If so, how do I eliminate them?

2) Is there a way to restore the Secure Boot control? What are the consequences of not doing so?

3) is there a relation between the **Fast Boot** option of the Aptio Setup Utility and the **hybrid boot **and the way to disable it outlined at [http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8). I am planning to disable hybrid boot.

Thank you,

Wilmer

---

### Post by oldfred on 2013-05-06
Grub2's os-prober still has a bug and creates the BIOS boot entries. You can just turn the prober off until it gets fixed. Also if Boot-Repair finds too many extra efi files it may add extra boot entries in 25_custom which you can just edit out. All entries in 25_custom are from Boot-Repair.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

UEFI boots faster than BIOS, but on some systems the fast boot setting bypasses the capability to press the keys ot get into UEFI/BIOS or one time boot key. If your system is one of those leave Fast Boot off.  Some have left it on and when they could not boot had no way to boot a repairCD/flash whether Windows or Linux. The underlying assumption seemed to be always boot into Windows and then back to UEFI. But when Windows does not work, you have a brick. If you can use your keys to get into UEFI then it may be ok to leave it on.

Windows 8 has made configuration settings to boot faster. They did not really redesign system to make it better, but rely on UEFI fast boot and hibernation being on all the time. I believe the second setting is for Winows hibernation. Similar info here:
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Since you created a shared NTFS data partition, you should not write data into the Windows 8 system partition. You can mount it so it is not shown or as read only if you want.
       Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
You can use device:
/dev/sda4 /media/sda4 ntfs nls=iso8859-1,ro,umask=227 0 0 
Better to use UUID like this:
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

---

### Post by wilmer11 on 2013-05-06
Thank you Olfred,

 I tried both commands but them produced errors (please see log bellow). What should I do to have Read Only for Windows partition?

sudo blkid

/dev/sda1: LABEL="SYSTEM" UUID="6079-A199" TYPE="vfat" 
/dev/sda2: LABEL="Recovery" UUID="2CF4196AF4193812" TYPE="ntfs" 
/dev/sda4: LABEL="OS" UUID="46E21DB9E21DAE65" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="F21E20A41E2063B7" TYPE="ntfs" 
/dev/sda6: UUID="5690a556-0dcf-41d2-8433-5b77b2ebf70e" TYPE="swap" 
/dev/sda7: LABEL="Restore" UUID="4C6623F16623DB0A" TYPE="ntfs" 
/dev/sda9: UUID="ff86291d-ae9b-44cf-981e-c8c183d33a68" TYPE="ext4" 


 /dev/sda4 /media/sda4 ntfs nls=iso8859-1,ro,umask=227 0 0
bash: /dev/sda4: Permission denied

UUID=46E21DB9E21DAE65 /WinC ntfs defaults,noauto,ro,umask=227 0 0
bash: /WinC: No such file or directory

---

### Post by sireangelus on 2013-05-06
[http://askubuntu.com/questions/211339/windows-8-wont-boot-after-installation-of-12-10](http://askubuntu.com/questions/211339/windows-8-wont-boot-after-installation-of-12-10)

this one solved it for me

---

### Post by oldfred on 2013-05-06
Those are not bash terminal commands, but the entries you add to fstab. 

Complete example of a read/write mount of either NTFS or ext4 partition.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by wilmer11 on 2013-05-08
Thank you Olfred and Sireangelus,

I was able to edit fstab and mount Windows 8, Restore and Recovery as read only. I can see the folders with file manager /media although no files are displayed. This fine with me. In order to be able to exchange data with Windows 8, I left the Data partition as it was, this allows me to mount it with file manager, I have not tried yet exchanging files. In the proccess of editing fstab I have leftover directory*** windowsData ***which was originally intended to mount the Data partition but I abandoned the idea to allow the file exchane between the two OS. To protect against the hybernation issues, I disabled the ***fast start up*** on Windows 8. My Aptio setup includes ***fast boot ***and the system is working fine with this option. I have only two last questions:


[LIST=1]
[*]How do I delete /media /*** windowsData? ***I am using rmdir /windowsData but i get error: "failed to remove `/windowsData': No such file or directory" 
[*]I still get an error when using ***Secure Boot enabled***,I get "Secure Boot Violation error:  Invalid signature detected", and I am directed to the Aptio setup screen. Is this important? Can it be fixed? 
[/LIST]

Best,

Wilmer

---

### Post by oldfred on 2013-05-08
Post fstab.
       cat /etc/fstab
    
Some Windows systems only boot Windows with secure boot on, some will boot with it off. Ubuntu has the Microsoft signing key, so it can also boot with secure boot on. If you really want the secure boot you have to boot in secure boot mode and use Boot-Repair with secure boot checked to get the signed kernel and signed copy of grub installed.

One user posted this:
 > The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.


 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

