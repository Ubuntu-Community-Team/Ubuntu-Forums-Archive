---
title: "missing windows 7 boot option"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by AlAyyubi on 2011-06-05
just recently, while attempting to boot to windows 7, i happened to select the wrong boot option by mistake, that is the windows 7 recovery (something like that, cant remember it specifically, but the word 'recovery' is there). the option has been there eversince i installed ubuntu 11.04 on my system, of which i cant find the answer as to why it existed there. so once i selected it (which was by mistake), it took me into some recovery process which i abandoned as quickly. it restarted and the windows 7 option was no longer there. the windows 7 recovery option, however, is still there. can anyone help me to get my windows 7 boot option back? 

thank you in advance!

(i apologise for my english, im still learning):KS

---

### Post by oldfred on 2011-06-05
Welcome to the forums.

If you started recovery, you may have overwritten something. 

But to see what is where post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by AlAyyubi on 2011-06-06
thank you for your reply:D


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 19531778. But according to the info from 
                       fdisk, sda5 starts at sector 260708352.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........D.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1410760 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 512002048.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         241,176,574   625,100,799   383,924,226   f W95 Extended (LBA)
/dev/sda5         260,708,352   621,182,975   360,474,624   7 NTFS / exFAT / HPFS
/dev/sda6         621,185,024   625,100,799     3,915,776  82 Linux swap / Solaris
/dev/sda4         625,100,800   625,142,447        41,648  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1998 MB, 1998585856 bytes
62 heads, 62 sectors/track, 1015 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,901,659     3,901,598   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   512,002,047   512,000,000   7 NTFS / exFAT / HPFS
/dev/sdc2    *    512,002,048   532,482,047    20,480,000   c W95 FAT32 (LBA)
/dev/sdc3         532,482,048   976,703,487   444,221,440   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       338878d5-f6ef-4060-aa87-7bc23970c09d   ext3       
/dev/sda1        4EFE5713FE56F2A7                       ntfs       
/dev/sda2        86F4-D40A                              vfat       7`9SËòSYÝj·
/dev/sda5        4A648D6C648D5B97                       ntfs       
/dev/sda6        2ed2f55c-4c80-42b0-9999-1ea6404581b3   swap       
/dev/sdb1        A097-4D0D                              vfat       Kingston
/dev/sdc1        F06CBC076CBBC69E                       ntfs       Al Ayyubi
/dev/sdc2        4DA9-B09E                              vfat       
/dev/sdc3        8AFE7DFFFE7DE43B                       ntfs       Super Matador

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Al Ayyubi         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 80 0c  |........?.......|
00000020  00 00 e0 01 f2 3b 00 00  00 00 00 00 72 09 01 00  |.....;......r...|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0a d4 f4 86 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sdc2

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 3c 00  |.X.MSWIN4.1..@<.|
00000010  01 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 80 38 01 c4 09 00 00  00 00 00 00 02 00 00 00  |..8.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9e b0 a9 4d 4e  4f 20 4e 41 4d 45 20 20  |..)...MNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  0e 06 80 b5 8a 77 57 40  |.............wW@|
000001a0  b3 9a e3 df 8e 81 b1 a1  3b d6 67 49 29 2e d8 4a  |........;.gI)..J|
000001b0  83 99 f6 a3 39 e3 d0 01  00 00 e0 02 00 00 00 00  |....9...........|
000001c0  00 00 80 d2 00 00 00 00  00 00 20 a2 00 00 00 00  |.......... .....|
000001d0  72 53 76 44 02 00 00 00  00 00 78 78 78 78 78 78  |rSvD......xxxxxx|
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

i ran bootinfoscript whilst booting into my liveusb.

---

### Post by oldfred on 2011-06-06
You have no system files for either windows nor Ubuntu shown from the script.

Grub is trying to boot from sda7 which does not even exist. The only windows files shown is in sda2 which is probably your recovery partition. 

Depending on how much was overwritten testdisk may recover some old partitions, but if any part of a bootable partition was written into then it will not be bootable. If you do not have a good backup you can use photorec to recover some data. Photorec just scans a drive for something that looks like a file. It does not recover file names, but does know types & photos & flac files have internal data that you can use to rebuild a file name. Sorting files can take hours or days. I had one text file I recovered and it had saved it many times as I kept editing it. I had to look at each one and try to file changed data. Lots of grepping & viewing files. 

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by AlAyyubi on 2011-06-06
thanks again for your kind reply :D really appreciate your assistance. 

im sorry i should have mentioned earlier that, prior to running the bootinfoscript, i managed to actually try the recovery process via windows recovery boot option (i left the process earlier, during an attempt to boot to windows 7). i was expecting a different result, but unfortunately, the problem still remains (no option to boot to windows 7). only now everything got erased. i was lucky to have all my files backed up to my external hd.

my question now is, how do i restore my system to the way it was when everything was running normal and i get to boot to either ubuntu or windows with ease?:sad:

---

### Post by oldfred on 2011-06-06
You are starting over.

I think most recovery systems are just an image of the hard drive as of the day you purchased it and it has to use the entire drive or at least the part that was the main install. Then you have to run all the updates & houseclean all the cruft that windows has.

Then you have to shrink windows and create partitions for Ubuntu. I recommend a shared NTFS partition for any data that you may want to use in both. I have my Firefox & Thunderbird still in my shared NTFS but now boot XP very little.

---

### Post by Quackers on 2011-06-06
Running the recovery function's initial boot up should not cause anything to be over-written. That should only happen if you actually run the recovery, not just booting it. 
As oldfred has already stated, the only possible way to get everything back is by using testdisk, or a similar program.
If that doesn't work you are faced with having to re-install your operating systems. If the Windows recovery doesn't work (as you seem to be suggesting) you will need another source for Windows, like an installation disc or if it was an OEM installation, the computer manufacturer may sell recovery discs.

---

### Post by AlAyyubi on 2011-06-07
thanks Quackers and oldfred for your replies:) i agree with both of you. i should start over and i really feel i need to reinstall my OSs. but i still have a question, at least for the moment (since im a fair pc user), is there an alternative to the recovery or installation disks given that my laptop does not come with optical drive?

---

### Post by oldfred on 2011-06-07
I have never run a full recovery. My laptop is now older and has a CD drive. If it crashed I would just install Ubuntu from a USB flash drive.:)

What does the vendor of your laptop suggest. Some may just work from the recovery partition or have a way to create a recovery USB?

---

### Post by Quackers on 2011-06-07
To get the recovery option to run, there will be a key (or keys) to press during boot. You should find out what those keys are and try that first. It may work :-)
Sadly, as I don't have a netbook I have never made enquiries as to further recovery procedures without a cd drive. Actually a USB cd drive is quite cheap nowadays and could be another option.
Definitely contact the manufacturer though and see what they say, though I suspect they may just tell you to run it from the hard drive (using the above key(s).

---

### Post by AlAyyubi on 2011-06-07
thanks for both of the replies:)

Quackers> i have done that. for asus eee pc, its f2. but as i said, it took me into several processes and after a while, the system restarted and nothing was changed (that is, everthing got erased, including ubuntu) and i had to reinstall ubuntu over again. it seemed like theres no way out of to this problem. i was thinking of getting a usb cd drive too:) thanks! but at the same time, im hoping that there would be another turnaround for this.

---

### Post by Quackers on 2011-06-07
It sounds as if your recovery partition may not be working properly. That could be a bargaining tool with the manufacturer :-)  but probably not :-(
Even if you get a cd drive you still need to find a cd to boot from :-) and the only way to get the OEM system back would be to obtain one from the manufacturer. 
I find that making a backup image of the drive with Clonezilla gives me some peace of mind :wink:  Too late for that now though.

Actually looking at your last post and browsing the interweb it seems that the key to press for recovery on your system may be F9, during boot.
Doesn't F2 take you to the bios (where, incidentally you may need to turn off a boot booster?).

---

### Post by AlAyyubi on 2011-06-07
i apologise for my lack of knowledge about my own laptop. yes you are right (embarassed:P), f2 does take me to BIOS. hehe. as for f9, it does not work (for me). i tried pressing many times before the system loads, but nothing happens. 

p/s: (my boot booster has been disabled forever)

---

### Post by Quackers on 2011-06-07
Hmm, well it's worth checking what the correct key is for your particular machine, as eee pc's do vary, it seems. Check your documentaion or contact support, maybe, or google for your specific machine's recovery key.
If the recovery partition is intact it should really work I would think.

---

### Post by AlAyyubi on 2011-06-07
i think so too. but anyway, thanks for your great help! i will look for windows 7 and start everything from there  :D

you guys have been very nice and helpful here. this is my first time involving in a forum ;)

---

### Post by Quackers on 2011-06-07
I'm sure I speak for oldfred as well when I say that you're welcome :-)
I hope you have more luck with that.

---

### Post by gaffajoiner on 2011-06-07
Have sent for a replacement disk at support, I have downloaded the Ubuntu 11.04 disk from the Ubuntu  site, burnt to ISO,  installed so it said but still goes  to windows 7 at boot up, is it compactable with win 7 ? can you please tell me where to go for help, I have 4 Ubuntu’s on my hard drive and I do not know how to remove them. Without formatting my hard drive

---

### Post by Quackers on 2011-06-07
gaffajoiner you will be better off starting your own thread as this one seems near to closing.
If you enclose the output from the boot info script we can get a better look at your system.
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

