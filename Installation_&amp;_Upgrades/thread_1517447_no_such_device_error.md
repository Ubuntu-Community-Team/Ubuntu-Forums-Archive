---
title: "no such device error"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Defeatist on 2010-06-25
Alright this is what my pc looked like before the error occured:
 
partition C: Windows Vista
partition E: Ubuntu (wubi)
partition F: shared docs
 
when starting the pc it would first load the windows boot manager and I got to choose between ubuntu and vista
 
yesterday I tried to upgrade grom 9.10 to 10.04 and used the default settings. It asked me to reboot and all of a sudden it loads grub instead of the vista boot manager and grub crashes:
 
no such device: ....-....-....-.... (some hash)
I get a "grub rescue>" command line and that's it. 
 
There are no important files on the ubuntu partition but there are some on windows. How do I repair/wipe and reinstall ubuntu + grub?

---

### Post by bcbc on 2010-06-25
You probably installed the grub bootloader to your drive MBR (the upgrade is unfortunately misleading). But since you're running wubi, this doesn't work. If that's all you did, then replacing the bootloader will get windows booting again.

However, if you installed grub to your windows bootsector as well, then windows won't boot. NOTE reinstalling grub or the windows bootloader does not fix this.

You need to check out [this link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"). It has info on the bootsector fix - how to diagnose, how to fix (testdisk is the recommended fix as you can do it all from a live cd).

If you didn't damage the bootsectors, you still need to reinstall the windows bootloader. You can do this from a windows repair dvd (bootsec.exe /fixmbr) or you can install lilo (works the same as shown below, and you can do it from live cd).

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

If you're not sure about what's going on, then at least run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

---

### Post by Defeatist on 2010-06-25
I don't have a windows repair CD (OEM)
I made a live cd with ubuntu 10.04 on it and tried to boot from it, but it just keeps loading and then after half an hour the screen goes black and stays like that. When I press the arrow keys it shows a log sort of thing reporting all kinds of script- and input/output errors.

Im now trying to make a puppy linux USB stick so I can back up my files. How do I wipe everything and reinstall ubuntu after that? As it doesnt even load the live CD properly!?

I will run the bootinfoscript in puppy linux and post the results here later on

---

### Post by darkod on 2010-06-25
OK, I'm confused. From using wubi inside windows now suddenly you ask how to wipe everything and reinstall ubuntu? Without windows?
If you are using mainly ubuntu why did you wait so long to get rid of wubi and install full ubuntu? Wubi is only a quick way to try, not to use ubuntu like that.

Anyway, the I/O errors might mean bad image or cd. Can you check the md5sum of the ISO, or maybe get a new ISO from torrent because the software checks for corruptiong during download?
And when burning the cd did you use slow speed, like 4x or 8x max? These days with cds being 56x lots of people consider 20x or 24x slow, or they burn at max speed. For an installation cd you shouldn't use more than 8x, it helps minimize errors.

If it's nothing of the above, it can be hardware incompatibility. You could try hitting any key at the first splash screen, and it should show you the main menu. Hit F6 for advanced options and try nomodeset. Then select Try Ubuntu to load the live mode.
Try other advanced options too, see if something works.

PS. Do you remember when asked where to install grub2 what did you select? It will help if you do. Just the MBR or also the vista partition?
If it was just the MBR, get a vista repair cd image here and repair the MBR:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by Defeatist on 2010-06-25
I installed grub to all partitions (it said that I could select them all if I didn't know what the question meant). 

I backed up my files with puppy linux

this is the result from bootinfoscript. 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 276912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 276912 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 299648 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   315,643,903   312,569,856   7 HPFS/NTFS
/dev/sda3         315,643,904   625,141,759   309,497,856   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     3,915,775     3,915,744   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E68CB6DE8CB6A887                       ntfs       WinRE                         
/dev/sda2        3CE8B8B8E8B871AE                       ntfs       Vista                         
/dev/sda3        B4C6BAC2C6BA8460                       ntfs       Data                          
/dev/sdc1        1B49-2DB9                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=a138681d)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/sda1        /mnt/sda1                ntfs       (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=iso8859-1,errors=continue,mft_zone_multiplier=1)
/dev/sda3        /mnt/sda3                ntfs       (ro,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=iso8859-1,errors=continue,mft_zone_multiplier=1)
/dev/sda2        /mnt/sda2                fuseblk    (rw,relatime,user_id=0,group_id=0,default_permissions,blksize=4096)
/dev/sdb1        /mnt/sdb1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)
/dev/sdc1        /mnt/sdc1                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 02 00  |ë<.MSWIN4.1..@..|
00000010  02 00 02 00 00 f8 ef 00  20 00 80 00 20 00 00 00  |.....øï. ... ...|
00000020  e0 bf 3b 00 00 00 29 b9  2d 49 1b 4e 4f 20 4e 41  |à¿;...)¹-I.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   ú3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |É.Ñ¼ü{..½x.Åv..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U¿"..~..N.±.üó¤|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |..½.|ÆEþ..F..Eù8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}".Á.èw.r..ë:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |¡.|f;..Wüu..Ê..V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |..Ã.sí3É.F..÷f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F..Ñ.v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |ü.Vþ¸ .÷æ.^..ÃH÷|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |ó.Fü.Nþa¿..è#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`±.¾Ø}ó¦at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t..Ç ;ûrçëÝ¾.}¬.|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.ð¬.Àt.<ÿt.´.»..|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |Í.ëî¾.}ëå¾.}ëà.Í|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f..Í.¾.}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |þ.N.÷á.Fü.Vþ±.èÁ|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.rÖê..p.´Bë-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j..ôtì..3Ò|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |÷v..÷v.B.Ê÷v..ò.|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |èÀÌ..Ì¸...V$Í..d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.IuwÃ.|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem diskÿ..Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O errorÿ..Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A»...~..é@ÿ..Uª|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdd sde sdf sdg sdh sdi 
=============================== StdErr Messages: ===============================

losetup: invalid option -- 'a'
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

losetup: unrecognized option '--show'
BusyBox v1.15.0.svn (2009-07-25 18:23:53 GMT-8) multi-call binary

Usage: losetup [-o OFS] LOOPDEV FILE - associate loop devices
    losetup -d LOOPDEV - disassociate
    losetup [-f] - show

Options:
    -o OFS    Start OFS bytes into FILE
    -f    Show first free loop device

Found Wubi on sda3. But could not create a loop device


So is it possible to get my vista install working again? Because if that works, I then know how to wipe the broken ubuntu installation and install it properly :)

---

### Post by darkod on 2010-06-25
The window in the upgrade process said to install to all DISKS if not sure, not all DISKS and PARTITIONS.

I know the commands from ubuntu, not sure how it would work from puppy. So if you can't make ubuntu cd/usb boot in live mode, that could be a problem. Otherwise it's a quick fix most of the times.

Use this procedure to remove grub2 from the vista partition /dev/sda2. So, that's partition #2 on disk /dev/sda:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

And as already said, you can remove grub2 from the mbr with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by bcbc on 2010-06-25
> **Defeatist said:**
> I installed grub to all partitions (it said that I could select them all if I didn't know what the question meant). 
This has caught a lot of people. Normally the option of installing the grub bootloader is suppressed for wubi users, so most haven't seen anything like it until the 10.04 upgrade. If you select nothing (the correct response), then it warns you that you may not be able to boot ubuntu. And even if you installed it to all drives your system would have been unbootable (easier to fix though).

Good news is it doesn't affect your data, as you've seen.

> **Defeatist said:**
> So is it possible to get my vista install working again? Because if that works, I then know how to wipe the broken ubuntu installation and install it properly :)

Ironically, the ubuntu installation may be the only thing that is working. I know there are some errors in the bootinfoscript results, but this may be because you ran it on puppy. Maybe. Typically, what we see is ubuntu works fine, windows is hooped.

PS for long-term use, installing ubuntu to its own partition is recommended.

---

