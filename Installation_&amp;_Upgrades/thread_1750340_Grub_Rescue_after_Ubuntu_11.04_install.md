---
title: "Grub Rescue after Ubuntu 11.04 install"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by GeorgeMichaelBluth on 2011-05-05
Last night I installed Ubuntu 11.04 over Ubuntu 10.10. I did not upgrade to 11.04, but erased 10.10 and did a clean install using a Live CD. Everything went fine until the very end of the install, right before it gives a slideshow of what's new in Ubuntu. An error appeared that said something along the lines of the installer has encountered an error and that I needed to submit a bug or something. After I closed the error, the slideshow also closed. I then proceeded to restart the computer. As it restarted I got the following prompt:

```

#Some random string of numbers and letters

Boot Rescue >

```I hit enter a few times, and then typed: help, which it then gave me a "command not found". I am currently dual booting Ubuntu and Windows 7 and I am not able to boot into either. Instead, I keep getting the Boot prompt. I've installed Ubuntu 10.10 a few times in the past and have never encountered this, or any problem for that matter. I'm not sure what to do as I am a noob, so any help would be greatly appreciated. Thank you for your time.

P.S. I vaguely remember reading somewhere about having Adobe products installed and how they can have an effect on the install or MBR or something like that. I do have Dreamweaver installed in Windows 7. Not sure if that is helpful or even relevant but I thought I would just put it out there.

---

### Post by Dutch70 on 2011-05-05
Hi and welcome to UF

Let's have a look at your boot info script. Someone should be able to help you with it if I can't.

From the live cd, run the following command in a terminal.*(copy&paste)*
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

That should put the boot info script in your downloads folder. Cut & Paste it to your desktop, and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info between code tags using the "#" symbol in the tool bar of your next post.

 Again, to put it between code tags, just click the # symbol in the tool bar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

### Post by GeorgeMichaelBluth on 2011-05-05
Thanks for the quick reply Dutch70 :). I'll get on this as soon as I get home.

---

### Post by GeorgeMichaelBluth on 2011-05-05
Here are my results:

```

                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   460,136,447   460,134,400  83 Linux
/dev/sdb2         460,138,494   488,396,799    28,258,306   5 Extended
/dev/sdb5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris
/dev/sdb6         460,138,496   468,523,007     8,384,512  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,768,064   976,768,002   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CA447E3E447E2CF7                       ntfs       
/dev/sdb1        24cef8af-ee3b-45e0-99b6-07354fa94306   ext4       
/dev/sdb5        111745ad-9649-4f9a-a1b6-8859115f8d6c   swap       
/dev/sdb6        a2f54789-6d39-45df-a9c8-71a1925d9fd0   swap       
/dev/sdc1        190B-2494                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=24cef8af-ee3b-45e0-99b6-07354fa94306 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a2f54789-6d39-45df-a9c8-71a1925d9fd0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.133281708 = 103.222325248  boot/vmlinuz-2.6.38-8-generic                  1
  96.133281708 = 103.222325248  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  26 93 00 01 00 00 00 01  |........&.......|
000001c0  01 00 0b fe ff ff 3f 00  00 00 02 4c 38 3a 00 00  |......?....L8:..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Dutch70 on 2011-05-05
Well, it looks like you installed Grub2 to /dev/sda instead of /dev/sdb. I hope that didn't mess windows up. 

Try running the following commands from the live cd/usb.

```
sudo mount /dev/sdb1 /mnt
```
and then...
```
sudo grub-install --root-directory=/mnt /dev/sdb
```

Then hopefully you can reboot to Ubuntu & run this command.
```
sudo update-grub
```

---

### Post by drs305 on 2011-05-05
According to the RESULTS.txt there isn't an initrd.img file in /boot nor a core.img or grub.cfg file in /boot/grub. This most likely means the installation didn't continue far enough to generate them. Whether or not the system is recoverable is unknown. I can advise that it could very well take longer to repair the OS than to reinstall it, especially since we don't know the extent of what else might be missing.

The commands given you by Dutch70 may restore the missing grub.cfg and core.img files, though they will be incomplete without the initrd.img file. To try to repair things, you would need to boot the LiveCD, chroot into sdb1, then try to generate the image file, then the grub files by reinstalling grub.

If you would like to try this let us know and we can give you more specifics.

---

### Post by GeorgeMichaelBluth on 2011-05-05
I took your advice drs305 and tried reinstalling Ubuntu 11.04  again. This time I got an error saying that I could not install on /dev/sda1 or something like that. I tried installing Ubuntu on another partition from the drop down menu, but when I would select one and press ok, it would not do anything. Not sure if this was a good idea or not , most likely not, but I booted up using my Windows 7 disc and just formatted over Ubuntu and all the logical partitions it had created hoping that I would then just be able to boot into Windows, as that is the only OS currently installed on my system now. However, when I booted up I got this error:

```

error: no such device: 9c29ce07-e56d-444b-95e8-09603f0b3c89

grub rescue> _

```Not sure where to go from here. If I must install Windows again and start all over again I will, I'm just hoping maybe there's another way to recover from this. What do you advise?

---

### Post by drs305 on 2011-05-05
Sorry the Ubuntu installation isn't going well.

You can get back to Windows fairly easily if the Windows boot files haven't been disturbed.

Boot the LiveCD, then install 'lilo'. You don't fully install it, so run these two commands and disregard any other messages.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot and you should get your customary Windows boot screen.

If this doesn't work, you will have to restore things with the Windows repair or installation disk.

[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by GeorgeMichaelBluth on 2011-05-05
It worked!!! :D I am able to boot into Windows now with no problems. Thank you so much drs305 and Dutch70 for your help. I'm not giving up on Ubuntu 11.04, I am big fan, but I am going to give it some time for them to work out the bugs before I attempt to install again. Hopefully this will be of some help to somebody. Goodnight from North Carolina.

---

### Post by Dutch70 on 2011-05-05
Sorry to hear that. 

Maybe next time try a usb stick for installation. They are faster & easier.

---

