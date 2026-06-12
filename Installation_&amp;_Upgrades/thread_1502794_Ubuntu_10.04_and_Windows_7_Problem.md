---
title: "Ubuntu 10.04 and Windows 7 Problem"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by tiklr on 2010-06-06
I had been working on Windows 7 for ages now and decided to go for ubuntu 10.04 with a dual boot. Like all novices, I was too sure of my abilities and ended up installing Ubuntu in unallocated free space, which seemed alright initially. My laptop was working fine on dual boot, with access to both Windows and Ubuntu possible. The problem started about a day later. Somehow, my windows stopped working altogether and my system re-booted. 

After that, my system only had ubuntu and Windows was lost. No problem, I told myself. I picked up the original Windows DVD. But my system didn't respond at all to it. Then, I tried installing it by using a bootable pen drive. But as soon as I changed my bios boot options, all that happened was I got a cursor blinking on the left top of the screen and nothing else. Incidentally, when I made the same pen drive bootable for ubuntu ( after the failure with windows installation ), it worked like a charm. 

Someone please help ! 

PS : Am an ubuntu novice, in the most extreme form possible.

---

### Post by metalf8801 on 2010-06-06
you need to press a key as some point when booting from a Windows CD or DVD in order to boot into the disc. Its most likely when you see the blinking line.  

I hope that helps post again if it doesn't 
ps after you install Windows your going to have to re install grub in order to be able to get back into Ubuntu 

good luck 
Dan

---

### Post by wilee-nilee on 2010-06-06
I doubt anything is gone 1st what model is your computer? second, post this boot script in code tags. You will use a live cd or the thumb to use the script.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
If you do anymore fiddling with the system please include a post about it and possibly run the script again.

---

### Post by tiklr on 2010-06-06
@metalf8801 : It doesn't. When I use "boot from cd/dvd" as my sole boot option, it tries for some time and gives a message like "no boot option" or something of that sort. On the other hand, when I keep my hdd as my 2nd preference for boot, after some trying for booting from the dvd, it automatically boots ubuntu from the hdd. Now that I look at the properties of my cd rom in ubuntu, I don't think ubuntu even detects it. Even though, the dvd rotates inside, the properties for the cd/dvd drive show everything to be "unknown"



@wilee - nilee : I have an inspiron 1525.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,652,667   241,652,605   7 HPFS/NTFS
/dev/sda2         241,653,758   488,396,799   246,743,042   5 Extended
/dev/sda5         241,653,760   478,285,823   236,632,064  83 Linux
/dev/sda6         478,287,872   488,396,799    10,108,928  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07B37B686F5A337F                       ntfs       c                             
/dev/sda2: PTTYPE="dos" 
/dev/sda5        14eccbd8-31d5-41d7-aac1-2f7b81a15a95   ext4                                     
/dev/sda6        d7379df4-f1f8-4f50-af7b-c97b9fe96cf6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/c                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/menu.lst: ===========================

title Windows 7
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=14eccbd8-31d5-41d7-aac1-2f7b81a15a95 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=14eccbd8-31d5-41d7-aac1-2f7b81a15a95 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 14eccbd8-31d5-41d7-aac1-2f7b81a15a95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=14eccbd8-31d5-41d7-aac1-2f7b81a15a95 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d7379df4-f1f8-4f50-af7b-c97b9fe96cf6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 154.1GB: boot/grub/core.img
 160.5GB: boot/grub/grub.cfg
 154.0GB: boot/grub/menu.lst
 154.2GB: boot/initrd.img-2.6.32-21-generic
 123.8GB: boot/vmlinuz-2.6.32-21-generic
 154.2GB: initrd.img
 123.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e2 54 2e a4 05 cf 3e 14  d0 c1 e0 3f cb 12 fd 0b  |.T....>....?....|
00000010  e3 08 e6 a1 4c bb ad 98  a7 d8 5d eb e6 bc d1 70  |....L.....]....p|
00000020  12 24 06 12 74 79 14 53  40 d4 bd 54 2f 8d 6d 0f  |.$..ty.S@..T/.m.|
00000030  0f 8f bc 51 90 58 0c e0  29 fa 1f 7e 76 e1 0f ec  |...Q.X..)..~v...|
00000040  10 5b 72 c4 32 3c 98 29  e8 6e a4 40 2b 6f d6 42  |.[r.2<.).n.@+o.B|
00000050  1c 26 01 dd 1a 1b 04 55  7f 13 c3 04 89 f8 c3 0c  |.&.....U........|
00000060  d1 a1 25 bc 79 e4 3b 7b  d1 b6 32 8a 43 00 a8 14  |..%.y.;{..2.C...|
00000070  d7 4d c4 37 93 51 ad ca  60 d0 8f 24 28 9a 2b f9  |.M.7.Q..`..$(.+.|
00000080  ef 9e 0b 42 8b 14 06 74  f1 d3 a3 3e 98 24 57 21  |...B...t...>.$W!|
00000090  cf 9e 3a 14 f2 7a 63 f6  43 ea ef 63 93 90 9a 04  |..:..zc.C..c....|
000000a0  1a fa e0 bb f6 39 ee 0a  98 66 01 70 f9 d4 7a 02  |.....9...f.p..z.|
000000b0  60 67 ab 36 21 6b 10 86  6f 1a 0c f2 43 ff 1a 2b  |`g.6!k..o...C..+|
000000c0  3c e1 1e f5 89 7f 8e 7b  85 e6 44 4c 92 49 db b5  |<......{..DL.I..|
000000d0  be 16 42 a9 d4 ea cf 4e  44 58 de 4c 6d 72 22 41  |..B....NDX.Lmr"A|
000000e0  17 ab 81 21 78 c6 c4 20  73 2a e3 d5 57 a8 98 1a  |...!x.. s*..W...|
000000f0  69 86 f1 5a 4c fe 50 37  6d b7 07 97 18 92 a8 96  |i..ZL.P7m.......|
00000100  a3 d9 08 bd 25 b5 46 cc  57 0b a6 5f 4b 22 80 37  |....%.F.W.._K".7|
00000110  4a 94 38 47 b1 22 ea 16  8d fb af ac ab 65 23 53  |J.8G.".......e#S|
00000120  6e bd 2f 2b 72 54 b7 2c  3d 63 7d 62 46 16 82 e1  |n./+rT.,=c}bF...|
00000130  62 fa ce 59 08 e4 54 23  d4 37 53 0e 3e 2b 75 f0  |b..Y..T#.7S.>+u.|
00000140  8f 12 7d 2d b9 60 be 30  8d cb 10 88 fd 2a 19 df  |..}-.`.0.....*..|
00000150  f5 1e 44 4a 29 59 a1 e8  ad 4c e4 48 ca 0d 17 92  |..DJ)Y...L.H....|
00000160  88 fb ad d5 d4 15 d9 48  2a ab 39 f6 fd 67 0a 99  |.......H*.9..g..|
00000170  22 b1 b0 24 34 d9 47 85  d6 c1 d7 fe 5e 3c ed 6a  |"..$4.G.....^<.j|
00000180  64 e8 f6 37 b7 e4 8b 05  20 83 f4 b4 c3 4c d3 2f  |d..7.... ....L./|
00000190  3e 23 ea ae 17 ad 9d 47  3d c1 9d d8 07 16 bb d2  |>#.....G=.......|
000001a0  ca 30 50 da 59 c4 ac c4  f7 3a b4 ae a3 91 78 dc  |.0P.Y....:....x.|
000001b0  99 f0 29 ee fa 65 9b 40  4a aa 49 0b b6 47 00 fe  |..)..e.@J.I..G..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 1a 0e 00 fe  |................|
000001d0  ff ff 05 fe ff ff 4e bd  1a 0e b4 42 9a 00 00 00  |......N....B....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Here's the output. 

Thanks.

---

### Post by wilee-nilee on 2010-06-06
I see a sizable ntfs partition in sda1 but no boot stuff attached, but I'm not a expert in this area, so now that we have the script posted the ones that are really good at this will probably have some ideas. I don't think W7 is gone so I would at the least look in the home sidebar of Ubuntu and open that partition and see whats there, just so you can recognize that it is probably still there but I'm not sure why sda1 doesn't show a bcd boot or some other MS boot.

---

### Post by tiklr on 2010-06-06
I opened the partition and it is completely empty. Only 68 MB of the 115.2 GB is being used and there are no files whatsoever, hidden or otherwise. 
Thanks for your help :)

Someone expert in this particular field, please help :|

---

### Post by darkod on 2010-06-06
First, the not so important question: Did you create yourself /boot/grub/menu.lst file trying to make win7 boot? If yes, simply delete that file. Grub2 doesn't uses menu.lst plus your file seem to have only entry for win7 in it, not ubuntu, and it's wrong anyway. Go in /boot/grub and delete it.

Second, if opening /dev/sda1 in ubuntu is showing it as almost empty, then that's a big problem. Depending what else was tried on the partition, most of the data should be there.

Get an external hdd big enough to fit that partition, boot ubuntu and use Photorec to try and save the files. [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

If you don't have any files to save, I guess you can just boot with the win7 dvd and install win7 again in /dev/sda1. After that you will need to reinstall grub2 to the MBR, NOT whole ubuntu again.

If the win7 dvd doesn't boot for you out of what ever reason, and you want to try with a usb stick, just copying the files is not enough. You have to create the boot files too, but I only know how to do this on windows machine, not on ubuntu. If you need instructions, ask.

---

### Post by alain_sat on 2010-06-06
I had that trouble but allready forgot how i soled it, the answer is here somewhere.
You have overwritten your win boot sector.
There is a utility in Ubuntu that you can run to reconstruct these boot sectors, I hope someone knows what it is , I used it last week and worked for me.

---

### Post by oldfred on 2010-06-06
I agree with Darko and wilee-nilee that the NTFS partition does not look right to be a bootable partition. It shows no remains of boot files. The little menu.lst refers to drive3, was this trying to boot a CD or another drive?
It also does not show the typical 100mb boot/recovery partition that new installs of win7 would have.

You might try testdisk to see what partitions were there before but I would hesitate to recover unless you are sure it does not make things worse.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by metalf8801 on 2010-06-07
> **tiklr said:**
> @metalf8801 : It doesn't. When I use "boot from cd/dvd" as my sole boot option, it tries for some time and gives a message like "no boot option" or something of that sort. On the other hand, when I keep my hdd as my 2nd preference for boot, after some trying for booting from the dvd, it automatically boots ubuntu from the hdd. Now that I look at the properties of my cd rom in ubuntu, I don't think ubuntu even detects it. Even though, the dvd rotates inside, the properties for the cd/dvd drive show everything to be "unknown"


Even with the without the hard drive I you need to press a key or its not going to boot from the Windows CD or DVD. At first that didn't make sense to me ether which is why I waited to reply. 

Good luck I hope you can get everything to work 
Dan

---

### Post by gwaar on 2010-06-07
> **metalf8801 said:**
> Even with the without the hard drive I you need to press a key or its not going to boot from the Windows CD or DVD.
Dan

Are you thinking of the bios options for what device to boot from? It seems he has CD as the first choice so he won't need to press a key and select the device - and for the windows set up, you press a key only when it says "press any key." 

Though this is now beside the point perhaps, it seems that your CD is broken (though you may know better if that's possible), what with not being able to recognize it anywhere.

---

### Post by wilee-nilee on 2010-06-07
Posts 7 and 9 are the key here, if anything can be recovered. What you have now is not fixable by just reloading the bootloader.

---

### Post by oldfred on 2010-06-07
I just saw in another thread where the computer had efi boot not BIOS boot, is your computer efi based? That used to be just apple but now it can be other computers. EFI is smarter than BIOS and may be giving the no bootable drive message.

---

### Post by wilee-nilee on 2010-06-07
> **oldfred said:**
> I just saw in another thread where the computer had efi boot not BIOS boot, is your computer efi based? That used to be just apple but now it can be other computers. EFI is smarter than BIOS and may be giving the no bootable drive message.

Kind of a strange case this one a whole OS disappearing but the partition is still there, and as mentioned no 100mb boot partition as well. I wondered if this was a case of a different type of booting mechanism that I am just not familiar with.

---

### Post by darkod on 2010-06-07
> **wilee-nilee said:**
> Kind of a strange case this one a whole OS disappearing but the partition is still there, and as mentioned no 100mb boot partition as well. I wondered if this was a case of a different type of booting mechanism that I am just not familiar with.

Don't look so hard for the 100MB win7 boot partition. It's not always there. You can't make any conclusions just because the partition exists or not. After my first win7 install and noticing that it creates it, the other few installs I made were without it (why waste a primary partition for that).

The 100MB is only created if you are creating the win7 system partition from unallocated space using the win7 installer. In that case it slices 100MB off the partition size you specified and creates two primary partitions.

BUT, if you install win7 on already existing ntfs partition by just formatting it and installing on it, or if you create ntfs partition with Gparted from linux live mode, no 100MB is created. Simply the existing ntfs partition is used.

That's a very easy way to avoid wasting a primary partition which might be important if dual booting on single hdd.

---

### Post by wilee-nilee on 2010-06-07
> **darkod said:**
> Don't look so hard for the 100MB win7 boot partition. It's not always there. You can't make any conclusions just because the partition exists or not. After my first win7 install and noticing that it creates it, the other few installs I made were without it (why waste a primary partition for that).

The 100MB is only created if you are creating the win7 system partition from unallocated space using the win7 installer. In that case it slices 100MB off the partition size you specified and creates two primary partitions.

BUT, if you install win7 on already existing ntfs partition by just formatting it and installing on it, or if you create ntfs partition with Gparted from linux live mode, no 100MB is created. Simply the existing ntfs partition is used.

That's a very easy way to avoid wasting a primary partition which might be important if dual booting on single hdd.

I hadn't really noticed that missing until it was mentioned, what I saw was no boot information in sda1, so I new like almost always, I have no clue really. I have used gparted every time to preformat the ntfs being that I had another OS on my netbook and had noticed that even then the custom install built the 100mb boot partition anyway. This makes no sense in that if you hit the install to this partition, you would think that it would put everything in that partition.This just may be due to the computer model a acer aspire one but this makes no sense either. Every install of W7 about 10 on this computer has the boot partition no matter what. It is a upgrade install, but every W7 dvd has the same information on it, but there is a Ei.cfg utility that makes the edition specific.
[http://lifehacker.com/5438005/eicfg-removal-utility-lets-you-use-any-product-key-with-your-windows-7-disc](http://lifehacker.com/5438005/eicfg-removal-utility-lets-you-use-any-product-key-with-your-windows-7-disc)

There is a tutorial on the windows 7 forum on how to remove that boot partition and put the boot into the main partition, I haven't been able to find it last time I looked for it.

---

### Post by darkod on 2010-06-07
> **wilee-nilee said:**
> I hadn't really noticed that missing until it was mentioned, what I saw was no boot information in sda1, so I new like almost always, I have no clue really. I have used gparted every time to preformat the ntfs being that I had another OS on my netbook and had noticed that even then the custom install built the 100mb boot partition anyway. This makes no sense in that if you hit the install to this partition, you would think that it would put everything in that partition.This just may be due to the computer model a acer aspire one but this makes no sense either. Every install of W7 about 10 on this computer has the boot partition no matter what. It is a upgrade install, but every W7 dvd has the same information on it, but there is a Ei.cfg utility that makes the edition specific.
[http://lifehacker.com/5438005/eicfg-removal-utility-lets-you-use-any-product-key-with-your-windows-7-disc](http://lifehacker.com/5438005/eicfg-removal-utility-lets-you-use-any-product-key-with-your-windows-7-disc)

There is a tutorial on the windows 7 forum on how to remove that boot partition and put the boot into the main partition, I haven't been able to find it last time I looked for it.

Hmm... strange. I might be wrong then. But I really thought I had it figured out.

1. On my netbook when installing win7 I deleted all partitions and created the win7 partition from unallocated space. The 100MB was created too.

2. On my desktop, I installed win7 over vista in the same ntfs partition, no 100MB.

3. I was helping a friend install his newly bought PC, brand new blank hdd. Booted with my ubuntu usb stick, used Gparted to create 3 ntfs partitions. Booted with win7 dvd and selected to be installed in part #1. Again, no 100MB created.

So, I thought the above logic applies...

PS. Sometimes if using restore/recovery dvd I guess the result might be different because the restore process might be set to create the 100MB part.

---

### Post by wilee-nilee on 2010-06-07
> **darkod said:**
> Hmm... strange. I might be wrong then. But I really thought I had it figured out.

1. On my netbook when installing win7 I deleted all partitions and created the win7 partition from unallocated space. The 100MB was created too.

2. On my desktop, I installed win7 over vista in the same ntfs partition, no 100MB.

3. I was helping a friend install his newly bought PC, brand new blank hdd. Booted with my ubuntu usb stick, used Gparted to create 3 ntfs partitions. Booted with win7 dvd and selected to be installed in part #1. Again, no 100MB created.

So, I thought the above logic applies...

PS. Sometimes if using restore/recovery dvd I guess the result might be different because the restore process might be set to create the 100MB part.

I have the upgrade ISO, and the DVD they all have done this, I would say though that you have a much better grasp of the overall, I use the word stuff here. These are full install media but are set to recognize another os being replaced, in order for the key to work. The key has been a problem every time the only time it worked without a crack or contacting MS or auto phone option was the 1st install where I did it from the live XP, with the .exe install and it put the boot into the XP recovery partition, which I couldn't remove even with help from the MS W7 tech squad, or so called tech squad. I am a noob in the true geek world and I knew more then they did. 

Actually I was able to remove the recovery but the boot had been put in there, and at that time 9 months ago I didn't know what it was so that I could of just removed everything but that, and shrunk the partition. The MS tech didn't know either they advised me to just remove the partition and it still should just boot. I laughed and said to them I will follow your instructions but I know this will break the setup. Sure enough it did so now it is a fresh install every time without the XP to confirm the upgrade and a real hassle to get the key activated. It was always a fresh install anyway as there is no upgrade path from XP to W7. Ms is so nice to allow this but without any ease of use for a person like me who might remove and install a OS's regularly. I also at that time didn't know how to just make the 100mb partition and load it with the boot files, which would of saved time in not having to wipe the whole HD and do another fresh install that the key wouldn't activate.

I have never had to use the neosmart recovery/restore cd.

---

