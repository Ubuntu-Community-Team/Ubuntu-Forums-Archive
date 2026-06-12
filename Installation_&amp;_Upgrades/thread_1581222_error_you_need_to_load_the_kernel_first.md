---
title: "error: you need to load the kernel first"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by Fábio Martinho on 2010-09-24
hello

I upgraded my ubuntu version 8 to 10.. 

I was using my new version normally, but on the GRUB screen, I have two choices (ubuntu 1 and 2.. something like 'generic-2.6-32.. bla bla)

I could only choose the second option.. because the first option, return this error: you need to load the kernel first.

Ok, i'm using the second option... but when i'm tried to install the driver of my nvidia 3d board, the second option of boot is also not working.. =( 
return this erros: kernel panic  - not syncing: VFS: Unable to mount root fs on unknown-block (8,33)...

both are kernel problems.. my instalation of ubuntu 10.04 was perfectly successfully (aparently)..


someone can help me? =/

thanks, []'s

---

### Post by arrange on 2010-09-24
Can you please post (via LiveCD for instance) the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by Fábio Martinho on 2010-09-25
arrange.. thanks for your reply..

I only have the livecd of 8.04 version.. can I use this boot_info_script with this version of livecd?

[]´s

---

### Post by arrange on 2010-09-25
Yes, no problem.

---

### Post by drs305 on 2010-09-25
> **Fábio Martinho said:**
> arrange.. thanks for your reply..

I only have the livecd of 8.04 version.. can I use this boot_info_script with this version of livecd?

[]´s

Yes you can. You just have to get to the terminal so you can run the script. 8.04 will be fine.

---

### Post by Fábio Martinho on 2010-09-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdc1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: sistema de arquivos desconhecido 'ext4'

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total de 39102336 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0xe525e525

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total de 78242976 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0x3d343d33

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,220,484    78,220,422   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total de 156301488 setores
Units = setores of 1 * 512 = 512 bytes
Disk identifier: 0x27692768

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   136,311,524   136,311,462   7 HPFS/NTFS
/dev/sdc2         136,311,525   139,476,329     3,164,805   7 HPFS/NTFS
/dev/sdc3         139,476,330   156,296,384    16,820,055   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b54efcb2-e3a4-4f75-8f6d-572732986cae   ext4                                     
/dev/sda1        C2D851E4D851D76F                       ntfs                                     
/dev/sdb1        BA8C41FA8C41B225                       ntfs                                     
/dev/sdc1        7C1C6F8F1C6F436E                       ntfs                                     
/dev/sdc2        7C8893138892CAD2                       ntfs                                     
/dev/sdc3        46B89ED5B89EC2BB                       ntfs       Linux                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu"

---

### Post by Fábio Martinho on 2010-09-29
please, someone can help me ?! 
thx

---

### Post by drs305 on 2010-09-29
Would you confirm this is a wubi install on the sdc Windows drive?

It appears wubi should be on sdc3, but that drive failed to mount and thus none of the grub files are found. Normally the "Operating System" will read Ubuntu X.XX  (10.04 for instance) and the Boot files will include "/boot/grub/grub.cfg and /etc/fstab".

I don't a lot about wubi. Perhaps some people who use it will post here and tell you how to repair it.

If you need to retrieve any files from your wubi file, you might be able to mount it from the LiveCD with these commands, although mounting the partition was the problem in the first place:

```
sudo mkdir /mnt/windows
sudo mount /dev/sdc1 /mnt/windows
sudo mkdir /mnt/wubi
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

Use your file browser to access your files on /mnt/wubi. If you have to reinstall, you can at least copy your files to another partition before you have to reformat the partition.

Grub is installed on the MBR of sdc. Generally Windows should be on the MBR for wubi installs if you have nothing but Windows and a wubi install within Windows. but with the Windows on the other two I don't know how they interact so again I'll have to defer to a Windows 'expert'.

---

### Post by Fábio Martinho on 2010-09-30
drs305.. thanks !

i'm really using wubi, and I will try to make that you said, using live cd, and I will return here with the result.

> Grub is installed on the MBR of sdc. Generally Windows should be on the  MBR for wubi installs if you have nothing but Windows and a wubi install  within Windows. but with the Windows on the other two I don't know how  they interact so again I'll have to defer to a Windows 'expert'. 	

what 'MBR' means?

---

### Post by ronparent on 2010-09-30
Master Boot Record - simply, the section of the disk coded to load the Operation System or a boot loader with a menu to load the OS.

---

### Post by Fábio Martinho on 2010-09-30
> **drs305 said:**
> 
If you need to retrieve any files from your wubi file, you might be able to mount it from the LiveCD with these commands, although mounting the partition was the problem in the first place:

```
sudo mkdir /mnt/wubi
sudo mount /dev/sdc1 /mnt/windows
sudo mkdir /mnt/wubi
sudo mount -o loop /windows/ubuntu/disks/root.disk /mnt/wubi
```Use your file browser to access your files on /mnt/wubi. If you have to reinstall, you can at least copy your files to another partition before you have to reformat the partition.


hello drs305...

this code did'nt return any result...
return this error on the terminal screen: impossible to mount /mnt/wubi, file or directory not exists.

I dont know what I need to do now.. =(

---

### Post by drs305 on 2010-09-30
> **Fábio Martinho said:**
> hello drs305...

this code did'nt return any result...
return this error on the terminal screen: impossible to mount /mnt/wubi, file or directory not exists.

I dont know what I need to do now.. =(

Sorry, I copied the same line twice. The first line should make a *windows* folder
```
sudo mkdir /mnt/**windows**
sudo mount /dev/sdc1 /mnt/windows
sudo mkdir /mnt/wubi
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
```

---

### Post by Fábio Martinho on 2010-09-30
drs305.. in the attach have the results... and didn't return any result again ..

I will translate the errors that appears in the screenshot:

mount: o dispositivo especial /dev/sdc1 não existe
the special device not exist


ubuntu@ubuntu:~$ sudo mount -o loop /windows/ubuntu/disks/root.disk /mnt/wubi
/windows/ubuntu/disks/root.disk: Arquivo ou diretório inexistente

file or directory not exist

---

### Post by drs305 on 2010-10-01
Fabio,

I changed the mount commands so the last one is now:
```
sudo mount -o loop **/mnt**/windows/ubuntu/disks/root.disk /mnt/wubi
```

I do not know why your mount of sdc1 and sdc3 failed to mount to /mnt/windows. They were listed in the RESULTS.txt. Perhaps you removed a drive or they changed device names. Try running the following command to see if the system still sees them (note the lowercase L and not a numeral 1) as sdcX:
```
sudo fdisk -l
```

---

### Post by Fábio Martinho on 2010-10-01
drs305, thanks for you patience.. 

I will paste the result of the last command that you asked me:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d343d33

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1        4869    39110211    7  HPFS ou NTFS

Disco /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27692768

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sdb1   *           1        8485    68155731    7  HPFS ou NTFS
/dev/sdb2            8486        8682     1582402+   7  HPFS ou NTFS
/dev/sdb3            8683        9729     8410027+   7  HPFS ou NTFS


I just dont understand why /dev/sdb2 and 3 are so similar...

perhaps there is the problem.. or not?

[]'s

---

### Post by drs305 on 2010-10-01
> **Fábio Martinho said:**
> drs305, thanks for you patience.. 

I just dont understand why /dev/sdb2 and 3 are so similar...

perhaps there is the problem.. or not?

[]'s

Looking at those results, it appears that - if it exists - you wubi install is now on sdb. So the Windows mount command would be for sdb1. Your RESULTS.txt shows this 80GB drive to include a large partition (60GB+), which would probably be your Windows partition, and two additional partitions of about 1.5GB and 8GB.

You can try the mount commands to inspect your sdb1 to see if you can find your wubi root.disk. However, the boot info script doesn't look promising. Compare your's and mine for the Windows partition with the wubi install:

Yours:
> 
sdc1/Wubi: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Mounting failed:
mount: sistema de arquivos desconhecido 'ext4'


Mine:
> sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab


Your wubi doesn't mount for some reason. But hopefully by mounting Windows and then mounting the root.disk you will be able to at least recover any files you might need.

So let's look at where we are in resolving your problem. If you can't mount the root.disk and see your normal Ubuntu files, the filesystem may have been damaged or incorrectly installed and may not be recoverable. 

If you can see all your files, and you can see the Grub menu when you boot, we may be able to boot the system via the Grub prompt. If you see the Grub menu, press "c" and see if you get a "grub>" prompt. Let me know if you do.

Wubi is really a good way to try Ubuntu without devoting a new partition specifically to a new OS. If you don't have any important files on your wubi install or just can't recover it, you might consider doing a normal installation of Ubuntu. 

If you don't want to do that, we can't find your root.disk contents, and cannot get to the grub prompt, it is likely you are going to have to reinstall wubi. You can remove the old wubi through the Windows add/remove feature.

---

### Post by Fábio Martinho on 2010-10-02
> **drs305 said:**
> Looking at those results, it appears that - if it exists - you wubi install is now on sdb. So the Windows mount command would be for sdb1. Your RESULTS.txt shows this 80GB drive to include a large partition (60GB+), which would probably be your Windows partition, and two additional partitions of about 1.5GB and 8GB.


No, in the 40 gb hd I have the Windows installation, and in the 8 gb partition I probably  have the Ubuntu instalation (Im not sure)

> 
If you can see all your files, and you can see the Grub menu when you boot, we may be able to boot the system via the Grub prompt. If you see the Grub menu, press "c" and see if you get a "grub>" prompt. Let me know if you do.
I dont know if i can see my files on Ubuntu... so first of all, when i turn on my pc, the boot.ini (Windows) is loaded... and i have the option to load Windows Xp or Ubuntu. Ok, i choose Ubuntu.. so the Grub is perfectly loaded... And i have six options in the Grub... none of it works =(

You can guide me in this grub> screen!

> 
Wubi is really a good way to try Ubuntu without devoting a new partition specifically to a new OS. If you don't have any important files on your wubi install or just can't recover it, you might consider doing a normal installation of Ubuntu. 
If I want to use Wubi as a normal OS, being me a ´medium´ user of linux, you recommend that I use Ubuntu in a partition?

Man, thank you for your help.. i hope that we can solve this problem!

---

### Post by drs305 on 2010-10-02
> **Fábio Martinho said:**
> 
I dont know if i can see my files on Ubuntu... so first of all, when i turn on my pc, the boot.ini (Windows) is loaded... and i have the option to load Windows Xp or Ubuntu. Ok, i choose Ubuntu.. so the Grub is perfectly loaded... And i have six options in the Grub... none of it works =(

We don't seem to be making much progress on trying to get the root.disk file mounted.

Let's see if we can boot Ubuntu from the grub menu, since you have the various Ubuntu menu items.

Press "c" at the Grub menu to get to the prompt. 
Type **ls** to see what partitions are available. 
Type **ls (hdX,Y)/** to find your Windows files. Change the X,Y values until you find it. Example: ls (hd1,1)/   (which would be sdb1)

Type **ls (loop0)/boot**
See if it contains your kernel (vmlinuz-2.6..... and initrd.img-2.6-.... files). 
Try any (loopX) values you find. If you dont' have any "loops", try each (hdX,Y) entry you have.

If you can't find the kernel and initrd image, you will need to install Ubuntu again. I would suggest a clean install on its own partition. 

If you find the kernel, remember the (hdX,Y) value and press ESC to get back to the Grub menu. Select an Ubuntu menuentry and press "e" to enter the edit mode.

Your wubi menuentry should look like this* for 10.04:
> 
insmod ntfs
set root='(hd**X,Y**)'
search --no-floppy --fs-uuid --set <uuid>
loopback **loop0** /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.**32-25-generic** root=/dev/sd**XY** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.**32-25-generic**

* The set root value must match the partition on which your Windows and wubi are installed 
* The kernel number may be different but should be the same as what you found in the "ls .../boot" command. 
* The <uuid> will be for your specific partition. (sdb3, sda1, etc)

When everything is correct, press CTRL-x to boot.

---

### Post by Fábio Martinho on 2010-10-04
Man, I could follow your steps, but without result again...

I did'nt understand what I really should edit, I've tried (hd1,3), (hd0,1) and much more numbers, but always return a error message.

When I type ls (hd1,3), return some results, including: Label Linux (was the unic number sequence that appears this name)...

and when I type ls (loop0)/boot, appears a lot of names, but there seems an error.
(something like memtest86+, generic26-32.22, bla bla)

I'm really thinking in reinstall my Ubuntu, i'm get angry !!! :mad:

---

### Post by drs305 on 2010-10-04
Unfortunately I am on the road and don't have access to my wubi test install. However, it sounds like you may have found the correct boot partition in loop0, as in addition to the kernel and initrd it also includes the files you mentioned.

Let's try one more time - we'll try to boot from the grub menu and command line.

Boot to the Grub menu, then press "c" to get to the prompt. 
The one thing I don't know is the loop number. It is normally loop0, so try 
```
ls (loop0)/boot
```
If that comes up with the same files, that is what you will use below. If it doesn't, try 1, then 2.
Assuming it is loop0, (change if it's another):
Type:
```
set prefix=(hd1,3)/boot/grub
set root=(loop**0**)

```
Press ESC to return to the main menu. Highlight the first Ubuntu menuentry and press "e" to edit.
Make the following changes. In the "linux" and "initrd" lines, leave whatever version number you have as it is, don't change it:
> set root=(**hd1,3**)
Delete the entire search line by holding down the DEL key at the start of the line.
> loopback loop**0** /ubuntu/disks/root.disk
set root=(loop**0**)
linux /boot/vmlinuz-**2.6.32-25-generic** root=/dev/sd**b3** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-**2.6.32.-25-generic**
CTRL-x to boot and see what happens.

If you aren't able to boot, it's probably best to reinstall wubi or make a partition and install the full version of Ubuntu. In Windows, find and copy the /ubuntu/root.disk file as you may be able to save some of the files on it by mounting it in Ubuntu at a later time.

---

### Post by Fábio Martinho on 2010-10-07
Man, after so many problems, I decided to uninstall completely and reinstall by USB Drive... now all working so good (for now, rs)..

dr325, thank you so much for your disposition to help me.

=)

---

### Post by drs305 on 2010-10-07
Fabio,

I'm sorry we couldn't get it fixed without a reinstallation but I"m happy you now have a working system.

If you would like, you can mark it SOLVED via the 'Thread Tools' near the top right of the first post. Since you didn't really find a solution, if you want to leave it the way it is that is ok as well.

---

