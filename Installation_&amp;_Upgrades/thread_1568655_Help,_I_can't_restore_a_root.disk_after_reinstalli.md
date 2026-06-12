---
title: "Help, I can't restore a root.disk after reinstalling wubi"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by zooster on 2010-09-05
Since the partition of windows7 (C: ) where wubi was installed was too small, I decided to reinstall wubi into another larger partition (E: ), keeping the old root.disk. Sadly when I replaced the root.disk ubuntu cannot boot, the loader says that there is no root.disk file, although it's there...
I guess there is some kind of checksum about the virtual disk toward the loader is poiting... So how can I have my old ubuntu installation back?? I still have the old root.disk.

---

### Post by bcbc on 2010-09-05
> **bcbc said:**
> The grub menu in the old root.disk is referring to the C: partition. When you see the menu, just hit 'e' on the first entry and change the references. For this you'll need to know what partition the E: drive references. 

e.g. assuming your root.disk was installed on /dev/sda3 before, and if E: is now /dev/sda4, then change (hd0,3) to (hd0,4) and /dev/sda3 to /dev/sda4. Also delete the line that says 'search -floppy etc.' Then CTRL+X to boot.

Once booted run "sudo update-grub" to correct.

I'm a little confused how your decision to migrate ended up becoming a reinstall of wubi - but either way, this should work fine. Just don't get rid of that backup root.disk.

> **zooster said:**
> I'm confused as well :)
Well I don't see any menu.lst, I searched windows but there is no such file...

> **bcbc said:**
> When you see the Windows boot manager, select Ubuntu, then you see the grub menu. There is no menu.lst anywhere anymore.

EDIT: I see you have another [thread]("http://ubuntuforums.org/showthread.php?t=1568655") for this - that's a good idea. Why don't you post any follow up there and I'll do the same.

> **zooster said:**
> Sorry, I posted there forgetting this thread, so I posted here...
Well I did what you said, and actually I could boot into old root.disk, I also did a grub update, but rebooting again in ubuntu it is still unbootable. And if I edit the grub hitting E key I see still there hd0,3 and sda3... it's like it didn't store the changes...

I suspect your override is booting a different root.disk. Boot your Ubuntu (whichever or even a live CD) and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

---

### Post by bcbc on 2010-09-05
PS reinstalling to E: to get more space, and then using your old root.disk won't work. With wubi, you choose the size of the root.disk when you install and that size is fixed for that root.disk. So with what you have done, by replacing the new root.disk with the old one will give you exactly the same size.

You'll need to 'resize' the old root.disk or create a separate home.disk virtual disk for your /home directory.

---

### Post by zooster on 2010-09-05
> **bcbc said:**
> PS reinstalling to E: to get more space, and then using your old root.disk won't work. With wubi, you choose the size of the root.disk when you install and that size is fixed for that root.disk. So with what you have done, by replacing the new root.disk with the old one will give you exactly the same size.

You'll need to 'resize' the old root.disk or create a separate home.disk virtual disk for your /home directory.

I know that, but in that partition I didn't have even the space to resize the root.disk... I attached the result.txt

---

### Post by bcbc on 2010-09-05
> **zooster said:**
> I know that, but in that partition I didn't have even the space to resize the root.disk... I attached the result.txt
I've included the bootinfoscript result here for readability... 

Can you tell me what version of Ubuntu you installed (both the old one and the new one)? Have you upgraded the old ubuntu from another version?

Edit: PS I have to step out for a bit. I'll pick this up later.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda4/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,779,263    16,777,216   7 HPFS/NTFS
/dev/sda2    *     16,779,264    16,984,063       204,800   7 HPFS/NTFS
/dev/sda3          16,984,064   121,739,263   104,755,200   7 HPFS/NTFS
/dev/sda4         121,739,264   543,219,711   421,480,448   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       ed8bde3c-d082-4eee-aeeb-b79bd1cf926a   ext3                                     
/dev/sda1        54C6FDAFC6FD920A                       ntfs       Swap File                     
/dev/sda2        CA22F5C422F5B613                       ntfs       System Reserved               
/dev/sda3        C6D83B40D83B2DD5                       ntfs                                     
/dev/sda4        86A010EDA010E609                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext3       (rw,errors=remount-ro)
/dev/sda4        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda4/Wubi/boot/grub/menu.lst: ========================


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=C6D83B40D83B2DD5 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=C6D83B40D83B2DD5

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		86A010EDA010E609
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=86A010EDA010E609 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		86A010EDA010E609
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=86A010EDA010E609 loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		86A010EDA010E609
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

======================== sda4/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set c6d83b40d83b2dd5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set c6d83b40d83b2dd5
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set ca22f5c422f5b613
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda4/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda4/Wubi: Location of files loaded by Grub: =================


   1.3GB: boot/grub/grub.cfg
   1.2GB: boot/grub/menu.lst
   1.3GB: boot/initrd.img-2.6.32-24-generic
   1.3GB: boot/vmlinuz-2.6.32-24-generic
   1.3GB: initrd.img
   1.3GB: vmlinuz
```

---

### Post by zooster on 2010-09-05
Well I installed wubi on c (sda3), I got all the upgrade of modules, packages and kernel. After all these upgrades the space wasn't enough so I wanted to resize the partition, but I could not create a new larger root.disk in C, with lvpm, since there wasn't enough space. So I had to move the root.disk to another partition, but wubi in windows doesn't have that option... I've seen this option only during first wubi installation, so I tried uninstalling wubi on C, reinstalling it on E and replacing root.disk. In that way I thought I could had the chance to use lvpm to resize root.disk since the partition is larger.
The version of Ubuntu is the one that came with wubi, 10.04, maybe updated during the use of ubuntu, here I see Ubuntu 10.04.1 (2.6.32-24-generic).
Here is again the list of my partitions.

---

### Post by bcbc on 2010-09-05
OK installs with 10.04 or 10.04.1 use grub2 and the ext4 file system, so the following are unexpected:
> sda4/Wubi: _________________________________________________________________________

    File system:       [COLOR="Red"]ext3[/COLOR]
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   [COLOR="red"]/boot/grub/menu.lst[/COLOR] /boot/grub/grub.cfg /etc/fstab
> ============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        [COLOR="red"]ext3[/COLOR]       (rw,errors=remount-ro)
/dev/sda4        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

> ============================= sda4/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               [COLOR="red"]ext4[/COLOR]    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

So grub-legacy appears to have been installed (menu.lst etc), the wubi root.disk has a file system type of ext3, yet the /etc/fstab believes it is ext4. There's also this strange entry in menu.lst:
> title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot

So, maybe you can slowly explain everything you've done because bootinfoscript doesn't tell the whole picture. Also confirm that the old wubi was also installed with release 10.04, or did you upgrade from a previous version of ubuntu.

Also, please post the output of "grub-install --version"

---

### Post by zooster on 2010-09-06
Thank you bcbc for your effort.
1) installed ubuntu 10.04 with wubi directly since the first time on C
2) used for some time and got all the upgrades
3) needed to move it, still in virtual disk, to another windows partition
4) decided to move to E that was encrypted
5) unencrypted E to allow this
6) uninstalled wubi on C and not rebooting windows
7) reinstalled the same wubi on E and overwrited the new root.disk (12GB) with the old one (6GB)  before completing reboot and installation >> ubuntu not booting
8) uninstalled wubi and not rebooting windows
9) reinstalled wubi (root.disk 6GB) completing rebooting and new installation
10) reboot into windows and overwrited root.disk
11) ubuntu not booting and asked help
12) changed hd0,3 and sda3 in 4 without deleting the line of floppy ( I forgot), updated grub >> ubuntu not booting at reboot, changes not stored
13) edited again the entries and deleted floppy line, updated grub again >> ubuntu not booting at reboot, changes not stored
14) booted into old root.disk manually and edited manually menu.lst to change uuid, and applied the one of the new partition >> ubuntu still not booting at reboot

result of that command for grub version is: 
> loop: impossibile aprire il device /dev/loop0: Permesso negato
grub-install (GNU GRUB 0.97)

p.s. I've noticed that I have wubildr.mdr and .cfg, also in the root of C: and not only inside ubuntu folder in E:, both same date

Can a resize with lvpm fix this?

---

### Post by bcbc on 2010-09-06
> **zooster said:**
> Thank you bcbc for your effort.
1) installed ubuntu 10.04 with wubi directly since the first time on C
2) used for some time and got all the upgrades
3) needed to move it, still in virtual disk, to another windows partition
4) decided to move to E that was encrypted
5) unencrypted E to allow this
6) uninstalled wubi on C and not rebooting windows
7) reinstalled the same wubi on E and overwrited the new root.disk (12GB) with the old one (6GB)  before completing reboot and installation >> ubuntu not booting
8) uninstalled wubi and not rebooting windows
9) reinstalled wubi (root.disk 6GB) completing rebooting and new installation
10) reboot into windows and overwrited root.disk
11) ubuntu not booting and asked help
12) changed hd0,3 and sda3 in 4 without deleting the line of floppy ( I forgot), updated grub >> ubuntu not booting at reboot, changes not stored
13) edited again the entries and deleted floppy line, updated grub again >> ubuntu not booting at reboot, changes not stored
14) booted into old root.disk manually and edited manually menu.lst to change uuid, and applied the one of the new partition >> ubuntu still not booting at reboot

result of that command for grub version is: 


p.s. I've noticed that I have wubildr.mdr and .cfg, also in the root of C: and not only inside ubuntu folder in E:, both same date

Can a resize with lvpm fix this?

OK so that all sounds good, except 10.04 doesn't use grub-legacy (0.97). If you install through wubi it's not possible to have grub-legacy unless a) you installed in a release prior to 9.10 and upgraded it or b) you installed grub-legacy.

If it's b) then this might explain why it's not booting. At the moment, you are using grub2 to manually boot the root.disk - you are not using the grub that is on the root.disk.

Also, from 9.10 wubi defaulted to an ext4 file system, whereas your bootinfoscript reports ext3 (although confusingly the fstab thinks it's ext4).

Is it possible you tried to run LVPM and then canceled it? Or something else unusual? It helps to know what has happened in order to suggest a possible fix.

How long have you been using wubi? In other words, how long have you had that 6GB root.disk?

---

### Post by zooster on 2010-09-06
> **bcbc said:**
> OK so that all sounds good, except 10.04 doesn't use grub-legacy (0.97). If you install through wubi it's not possible to have grub-legacy unless a) you installed in a release prior to 9.10 and upgraded it or b) you installed grub-legacy.

If it's b) then this might explain why it's not booting. At the moment, you are using grub2 to manually boot the root.disk - you are not using the grub that is on the root.disk.

Also, from 9.10 wubi defaulted to an ext4 file system, whereas your bootinfoscript reports ext3 (although confusingly the fstab thinks it's ext4).

Is it possible you tried to run LVPM and then canceled it? Or something else unusual? It helps to know what has happened in order to suggest a possible fix.

How long have you been using wubi? In other words, how long have you had that 6GB root.disk?

I clicked on lvpm 2 times, once on transfer and it gave me all the partitions, and another time to resize and it prompted for the new size. Both times I didn't click ok and I didn't proceed.

Oh, I forgot to mention that before this mess, using old wubi, I resized once successfully the root.disk from 4GB to 6GB.

---

### Post by bcbc on 2010-09-06
OK that explains why you have an ext3 file system but your fstab thinks it's ext4 (LVPM uses ext3 and when it resized it created the new one as ext3 but copied all your files as they are - /etc/fstab remained the same setup as ext4).

Doesn't explain why you have grub-legacy. But I suppose it's possible that something happened when you started and then aborted the LVPM transfer. I know that it installs grub-legacy (in the target) and maybe it got messed up.

So, what to do...

Before anything, guard that 6GB backup (we may need to try a few things and you don't want to lose it - at the end of the day, if this becomes a recovery and reinstall mission, then you want to have that available). You don't want to accidentally do something to the backup.

---

### Post by bcbc on 2010-09-06
I haven't re-installed grub2 after grub-legacy in a wubi install. So I am not really sure what will happen. But make sure that you DON'T select any devices when prompted - if it pops up a window listing /dev/sda or /dev/sdb you must not select any of these!

So, boot into your new wubi with the replaced root.disk as before and run:
```
sudo apt-get install grub-pc
```

You will probably be prompted with an empty command line, OK hit enter, another line with 'quiet splash' - also OK, then the device page /dev/sda (leave unchecked). (You use the TAB key to navigate to the OK button and then ENTER).

After this, reboot and cross fingers.

Also, edit fstab:
```
sudo nano /etc/fstab
# Or if you prefer gedit you can use:
gksu gedit /etc/fstab
```
Change ext4 to ext3
CTRL+X to save.

---

### Post by zooster on 2010-09-06
Ok I'll try this...  but don't you think that trying to resize again that root.disk with lvpm would fix this mess?

---

### Post by bcbc on 2010-09-06
> **zooster said:**
> Ok I'll try this...  but don't you think that trying to resize again that root.disk with lvpm would fix this mess?

All the resize is supposed to do is create a brand new virtual disk, format it, and copy all files from the old root.disk to the new one. Then you have to rename the new.disk to root.disk yourself in windows before rebooting into Ubuntu. So there should be no difference to the contents, e.g. whether it uses grub or not. (The only change was that lvpm assumes that wubi is using the ext3 filesystem)

I'm not sure how you got grub-legacy installed - that normally happens when you use lvpm to transfer a wubi install to partition (since lvpm hasn't been changed since grub2 came out). But we'll have to fix this manually if you're hoping to boot wubi using the normal mechanism.

---

### Post by zooster on 2010-09-06
Ok, but I already know that I still need a larger root.disk, there are only 236mb left... So I'll need to resize it for sure... Can I still do it?

---

### Post by bcbc on 2010-09-06
Yeah, I don't see that it will make any difference.

Just hold on to the 6GB backup and consider making a new backup of the larger root.disk (if possible) so you can easily refresh it if something goes wrong in your attempts to resolve your issues.

---

### Post by zooster on 2010-09-06
Ok, so I'm gonna try this solution, but just to be clear the only root.disk that I have now is the old 6GB one, I overwrote the one created with the new installation with the old backup one,and this is the only root.disk I have.

---

### Post by bcbc on 2010-09-06
> **zooster said:**
> Ok, so I'm gonna try this solution, but just to be clear the only root.disk that I have now is the old 6GB one, I overwrote the one created with the new installation with the old backup one,and this is the only root.disk I have.

Yes the 6gb old one. You'll want to keep a backup of this.

---

### Post by zooster on 2010-09-07
When I do sudo apt-get install grub-pc I get this, and not an empty line:
> Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  dkms
Usare "apt-get autoremove" per rimuoverli.
Pacchetti suggeriti:
  desktop-base
I seguenti pacchetti saranno RIMOSSI:
  grub lvpm
I seguenti pacchetti NUOVI saranno installati:
  grub-pc
0 aggiornati, 1 installati, 2 da rimuovere e 10 non aggiornati.
È necessario scaricare 618kB di archivi.
Dopo quest'operazione, verranno occupati 238kB di spazio su disco.
Continuare [S/n]? 
Shall I click yes??

---

### Post by bcbc on 2010-09-07
> **zooster said:**
> When I do sudo apt-get install grub-pc I get this, and not an empty line:

Shall I click yes??

ah so that's how you got grub legacy installed - it looks like it's a dependency of lvpm.
If you've already resized then it's safe to remove lvpm.

Just make sure you don't install grub2 to any devices if prompted e.g. /dev/sd*

---

### Post by zooster on 2010-09-07
So I go straight with that command that autoremoves lvpm?
If prompted any device I just press ok or what?

---

### Post by bcbc on 2010-09-07
Yes.
You may see a screen with checkboxes for devices on it - leave them blank. You may just see a screen that says "you chose not to install grub to any devices, are you sure?" Check this box and click on Forward.

I don't see you have a choice to try this unless you want to boot wubi manually each time. (And you have that backup of the root.disk in case it case something goes wrong)

---

### Post by zooster on 2010-09-07
Hey it worked thank you!!!
Now I have to do also sudo nano /etc/fstab ? why? where, in terminal or when?

---

### Post by bcbc on 2010-09-07
> **zooster said:**
> Hey it worked thank you!!!
Now I have to do also sudo nano /etc/fstab ? why? where, in terminal or when?

Great :)

Yeah /etc/fstab is identifying your root.disk as an ext4 filesystem, but it's actually ext3. So you should change it. It doesn't seem to be causing any problems but it seems like the right thing to do ;) So you can run 'sudo nano /etc/fstab' in a terminal or 'gksudo gedit /etc/fstab' if you prefer. 

But anyway - awesome it's all sorted itself out.

---

### Post by zooster on 2010-09-08
Ok, but since the problem of the size is still there, I'd need to resize the wubi partition with lvpm... Would it mess everything up again?

---

### Post by bcbc on 2010-09-08
> **zooster said:**
> Ok, but since the problem of the size is still there, I'd need to resize the wubi partition with lvpm... Would it mess everything up again?

I thought you said you were going to do that first. 

This is what lvpm does:
```
sudo -i
cd /host/ubuntu/disks
dd if=/dev/zero of=new.disk bs=1M count=**"$newlsize"**
mkfs.ext3 -F new.disk
mkdir /media/extra
mount -o loop,sync /host/ubuntu/disks/new.disk /media/extra
rsync -av --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/root/.gvfs' / /media/extra
umount /media/extra
rmdir /media/extra
exit

```
Then you have to boot into windows and rename root.disk to root.disk.old and new.disk to root.disk. So you could just do it yourself. Just replace "$new1size" to the new size, 30GB is 30000. e.g. count=30000

**NOTE:**_Just be really careful with the dd and mkfs commands. They are VERY dangerous if you get it wrong or make a typo._

One last thing - you can run "df -h /host" to make sure that the amount of space you want is available.

PS just ran a test on the above and it works. I used ext4 (since all wubi installs from 9.10 use that, but other than that change it works).

---

### Post by zooster on 2010-09-08
So it's better to let lvpm do all itself... Well the space is available so it's no problem, I think I'm gonna choose 12GB...
But after this resize I'll do again that sudo apt-get install grub-pc?

---

### Post by bcbc on 2010-09-08
> **zooster said:**
> So it's better to let lvpm do all itself... Well the space is available so it's no problem, I think I'm gonna choose 12GB...
But after this resize I'll do again that sudo apt-get install grub-pc?

Yes, if you're more comfortable with lvpm, you'll need to reinstall grub-pc afterwards.

---

### Post by zooster on 2010-09-11
> **bcbc said:**
> Yes, if you're more comfortable with lvpm, you'll need to reinstall grub-pc afterwards.
I've resized the restored root.disk with lvpm. Now it works again without grub... should I still have to reinstall it?

---

### Post by bcbc on 2010-09-11
> **zooster said:**
> I've resized the restored root.disk with lvpm. Now it works again without grub... should I still have to reinstall it?

The wubi boot mechanism since 9.10 is tied in to grub2, so you don't have much choice. I guess it's loading the existing grub.cfg, but this won't be updated anymore if you've got grub legacy installed. So if you want to get your grub menu updated automatically e.g. when a new kernel is installed - then yes you need to reinstall.

---

### Post by zooster on 2010-09-11
Ok so I'll repeat the procedure you posted [here]("http://ubuntuforums.org/showpost.php?p=9813388&postcount=12")

---

### Post by bcbc on 2010-09-11
> **zooster said:**
> Ok so I'll repeat the procedure you posted [here]("http://ubuntuforums.org/showpost.php?p=9813388&postcount=12")

That'll do it. You won't need to edit the fstab again as you only needed to do that once.

---

### Post by zooster on 2010-09-12
Ok, I've done it again. Everything ok :) Thank you.
I was wondering... now it's installed in sda3, what happens If I format sda3 from primary to extended, creating also logical partitions? Will it boot anyway?

---

### Post by bcbc on 2010-09-12
> **zooster said:**
> Ok, I've done it again. Everything ok :) Thank you.
I was wondering... now it's installed in sda3, what happens If I format sda3 from primary to extended, creating also logical partitions? Will it boot anyway?

you'll have to repeat the same thing you did to move wubi the last time - because the logical partitions will be /dev/sda5 and up, and the uuid's will all change.

---

### Post by zooster on 2010-10-29
Bcbc, still here messing with window partitions...
After the fix you kindly suggested it worked out, but I still have 40GB of unallocated space left. Now I want to partition that free space BUT, since I have already 4 primary partition, to do that W7 wants to change all the partition to dynamic (except C). If I proceed with this operation will I get an unbootable wubi (installed on E) again??

---

### Post by bcbc on 2010-10-29
> **zooster said:**
> Bcbc, still here messing with window partitions...
After the fix you kindly suggested it worked out, but I still have 40GB of unallocated space left. Now I want to partition that free space BUT, since I have already 4 primary partition, to do that W7 wants to change all the partition to dynamic (except C). If I proceed with this operation will I get an unbootable wubi (installed on E) again??

I don't know exactly how windows 7 manages dynamic partitions. If it leaves the current 4 visible to legacy apps, and virtually manages the new 5th one itself, I suppose it's possible it will work. But I wouldn't bet the farm on that. 

I've seen users with problems installing wubi on dynamic partitions (but I've also seen bootinfoscript show dynamic partitions (SFS) with normal dual boots.) 

So, hard to say, but I am afraid you're on your own on this one.

---

