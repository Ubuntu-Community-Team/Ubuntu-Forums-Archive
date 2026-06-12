---
title: "Move Ubuntu from HD0 to HD1 help"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by purg on 2011-10-30
Edited:
Anyone stumbling across this from search
Unsolved but resolved, read last post
-------------------------------------------------------------------------------

I use a company laptop for home use so have two drives.
Primary being a pgp encrypted company internal drive (no private use allowed). Secondary being a hdd caddy in CD drive slotthat is free for private use. Before this week the secondary was WinXP with truecrypt.

To install Ubuntu from CD I removed company drive swapping for my secondary (cd caddy drive) hdd. This ensured whatever happened the company drive would not be damaged and give me access to the CD drive again.

Installed WinXP quickly followed by Ubuntu 11.09 (then upgraded to 11.10) before getting WinXP truecrypt working without a problem (grub2 loading recovery image thanks to this forum).

With this setup I have no problem... both systems load without an issue.

Sorry for the long intro but **this is where I hit a wall.**

Moving the physical drive from HD0 to HD1 (back to CD caddy slot with company drive as primary) the ubuntu system boots but desktop is basically blank. I dont see any errors but the system is basically useless without any launcher, topbar options (shutdown etc) and little clue how to resolve.

As you can see from getting truecrypt working I can stumble my way around the system but couldnt get from a 2 b without a guide. Im a total new user to Ubuntu and linux so please speak in one syllable words but would really appreciated some help.

---

### Post by oldfred on 2011-10-30
Welcome to the forums.

I know nothing about truecrypt and getting it to work. Have seen a few posts where users damaged company drive when grub overwrote truecrypt boot partition.

But your issue sounds like a video issue. Do you get standard grub menu? If so try nomodeset or whatever is best for your model video.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by purg on 2011-10-30
thanks for the reply but I doubt its video because as I tried to explain when the drives in primary everything works just fine.

physically moving the drive from internal to caddy has broken the desktop! boots up, signon but no desktop after that.

From bios selecting second drive as boot.
I get grub2 menu
able to select OS
(takes longer than normal to boot)
get signon
after signon the screen I get the background, wifi connects but everything else is missing.
no topbar, no launcher, etc

---

### Post by oldfred on 2011-10-30
USB ports are slower that PATA/SATA hard drive ports. So that it is somewhat slower is not unexpected.

But video works when it is installed internally and does not when using it as the external? That is very strange. Have you tried recovery mode?
I would expect Windows not to work as it checks & only boots from internal hard drives.

---

### Post by purg on 2011-10-30
This is correct... internal Ubuntu works, I then moved hdd to caddy Ubuntu desktop is screwed.
(move it back to internal, desktop comes back but this setup is not acceptable for company drive to run from caddy)

fyi Windows works without a problem. This is a laptop so the caddy/bay is basically an internal bay which is why WinXP works from this location.

This is not USB to help reduce confusion here is a sales link of the hdd caddy.
[http://shop.accessory4you.com/05-chanpin/p-001-1.asp?id=38](http://shop.accessory4you.com/05-chanpin/p-001-1.asp?id=38)

---

### Post by oldfred on 2011-10-31
That seems like it should be seen as a full second hard drive.

Can you also boot USB so you can run this with both installed?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by purg on 2011-10-31
as requested this was taken using a puppy usb pen
to offer more info....
Disk /dev/hda: = company pgp encrypted drive (nothing to do with this issue and will not be touched)
Disk /dev/hdc: = is the drive I physically moved to and from hda to enable installing Ubuntu.


```


Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy is installed in the MBR of /dev/hda and looks at sector 3534 
    of the same hard drive for the stage2 file, but no stage2 files can be 
    found at this location..
 => Grub2 (v1.99) is installed in the MBR of /dev/hdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

hda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

hdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

hdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdc5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, hdc5 starts 
                       at sector 63. But according to the info from fdisk, 
                       hdc5 starts at sector 102392768. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

hdc3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
mount: wrong fs type, bad option, bad superblock on /dev/hdc3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


hdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: hda _____________________________________________________________________

Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/hda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: hdc _____________________________________________________________________

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/hdc1    *     51,196,383   102,392,639    51,196,257   7 NTFS / exFAT / HPFS
/dev/hdc2         102,392,766   625,136,399   522,743,634   f W95 Extended (LBA)
/dev/hdc5         102,392,768   625,136,399   522,743,632   b W95 FAT32
/dev/hdc3               2,048    47,116,287    47,114,240  83 Linux
/dev/hdc4          47,116,288    51,195,903     4,079,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/hdc3        860b3a31-26a1-484d-8cdb-a1eeb6fabec8   ext3       
/dev/hdc4        d7353bc7-a220-458c-9ab0-b2aed1159b58   swap       
/dev/hdc5        1B16-45C7                              vfat       
/dev/sda         E4C0-87C5                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/sda         /mnt/sda                 vfat       (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on hda1

00000000  4a 01 f7 30 fe fa 98 d6  66 35 a9 82 70 93 33 38  |J.÷0þú.Öf5©.p.38|
00000010  8f 3e de 60 34 df 7b eb  2d 50 f7 2f e4 f0 cc 21  |.>Þ`4ß{ë-P÷/äðÌ!|
00000020  89 0d 89 4b fc 25 ff 95  7b 99 90 89 f6 e2 0a 02  |...Kü%ÿ.{...öâ..|
00000030  7b d2 f7 dc 2d 4a 79 20  03 87 36 f0 01 04 97 c2  |{Ò÷Ü-Jy ..6ð...Â|
00000040  fd 1a 7f 52 0c 23 5a 9e  c3 36 a2 9e 7b 98 11 27  |ý..R.#Z.Ã6¢.{..'|
00000050  60 04 a1 a4 09 b5 d9 4b  db b8 ed 59 67 00 69 1c  |`.¡¤.µÙKÛ¸íYg.i.|
00000060  b6 45 a5 d4 a2 40 25 64  8a 78 ce b3 0d da 6b 25  |¶E¥Ô¢@%d.xÎ³.Úk%|
00000070  66 7b 87 89 cb b8 bd 70  27 28 3c 1c 85 7e 70 7c  |f{..Ë¸½p'(<..~p||
00000080  bf a0 9d 30 ce 79 75 6d  c3 8d 65 95 66 5b b1 51  |¿*.0ÎyumÃ.e.f[±Q|
00000090  cb fa 7b 95 91 07 60 69  8e 71 d4 e5 78 c7 d1 58  |Ëú{...`i.qÔåxÇÑX|
000000a0  40 7e 7c e4 67 76 c7 69  9e d3 3a 74 a4 05 58 7b  |@~|ägvÇi.Ó:t¤.X{|
000000b0  87 87 92 65 f5 72 09 2e  e5 64 d7 23 5d dd 89 c1  |...eõr..åd×#]Ý.Á|
000000c0  49 38 4b af 0c 6b 19 4b  31 5c 37 0e e8 76 07 aa  |I8K¯.k.K1\7.èv.ª|
000000d0  5c 52 46 e3 d9 bd b3 f8  74 88 8f 3a 8d e3 61 84  |\RFãÙ½³øt..:.ãa.|
000000e0  e2 26 ac b5 12 46 aa 0b  1f 17 c2 4e 56 90 94 64  |â&¬µ.Fª...ÂNV..d|
000000f0  15 95 ba 6b a5 e2 b6 11  25 6d ba 26 87 1f 60 f8  |..ºk¥â¶.%mº&..`ø|
00000100  d0 97 52 c1 93 92 e6 93  73 74 26 11 a5 2e 54 3b  |Ð.RÁ..æ.st&.¥.T;|
00000110  27 bc 1d 74 03 6b 9a 0b  bd df b0 34 4b 28 9d 8b  |'¼.t.k..½ß°4K(..|
00000120  61 b8 bb cd 02 25 f3 44  ea 37 d3 ab 88 9d 2c 2c  |a¸»Í.%óDê7Ó«..,,|
00000130  8f 72 f4 30 f4 a8 c2 68  51 f7 49 92 db 93 ef c1  |.rô0ô¨ÂhQ÷I.Û.ïÁ|
00000140  32 08 5f 34 fd 28 3d be  58 b7 70 04 ce 5a f0 a5  |2._4ý(=¾X·p.ÎZð¥|
00000150  e6 e2 ce 22 24 49 b1 7b  8d 0d 5c ee 98 a5 0c c7  |æâÎ"$I±{..\î.¥.Ç|
00000160  2d 15 72 c8 dd c7 7e 8b  8e ca 70 51 6c a0 76 5b  |-.rÈÝÇ~..ÊpQl*v[|
00000170  c0 00 77 2a 66 31 82 23  34 bb a7 a1 b6 fd 29 68  |À.w*f1.#4»§¡¶ý)h|
00000180  93 f3 85 2c b3 4b a4 1a  0a 21 22 06 e4 ae 30 ea  |.ó.,³K¤..!".ä®0ê|
00000190  09 f2 86 b6 c3 b2 4e 76  e9 11 5a 2a 8c b2 f1 31  |.ò.¶Ã²Nvé.Z*.²ñ1|
000001a0  00 52 f6 10 af d7 ea fc  85 79 3b 18 58 eb bc 35  |.Rö.¯×êü.y;.Xë¼5|
000001b0  fa 7a 6e f0 49 32 10 b9  56 5e 82 ed 64 45 f1 1d  |úznðI2.¹V^.ídEñ.|
000001c0  a3 67 27 14 15 b3 5e 2d  6e ff 9a ca 9d dd 8b 87  |£g'..³^-nÿ.Ê.Ý..|
000001d0  2f de 1b c0 23 65 aa aa  35 05 17 29 39 8f 2e a8  |/Þ.À#eªª5..)9..¨|
000001e0  69 61 4a 55 f7 7c 0f bb  84 62 e9 52 59 1e a9 72  |iaJU÷|.».béRY.©r|
000001f0  45 d6 44 d4 ad a8 02 ed  e7 d3 67 b0 6f af 27 90  |EÖDÔ*¨.íçÓg°o¯'.|
00000200

Unknown BootLoader on hdc1

00000000  03 e3 b4 99 81 92 00 b3  82 e0 fe f7 58 7a b0 b3  |.ã´....³.àþ÷Xz°³|
00000010  f5 e3 31 af ab d5 5b 86  ce cb a5 a7 f5 0b 20 14  |õã1¯«Õ[.ÎË¥§õ. .|
00000020  77 c4 fd 99 94 ae 3b 26  bf 57 bd 65 4d 75 4a dd  |wÄý..®;&¿W½eMuJÝ|
00000030  64 df 05 ca 43 00 91 77  fd f6 8a c4 49 8b cd 1b  |dß.ÊC..wýö.ÄI.Í.|
00000040  20 01 d5 0c b4 bb 45 9d  d5 1b c9 ca cf 9e 30 b8  | .Õ.´»E.Õ.ÉÊÏ.0¸|
00000050  db 06 0c ce df cb e1 51  dc 5f ae 11 2a 0d 76 40  |Û..ÎßËáQÜ_®.*.v@|
00000060  50 4d d7 41 bd 55 95 70  2d b5 e9 92 59 87 53 80  |PM×A½U.p-µé.Y.S.|
00000070  2a 02 f0 57 6b 55 f1 ac  0e 33 39 bd 00 47 55 4f  |*.ðWkUñ¬.39½.GUO|
00000080  df 72 08 ac 21 e8 9c 0c  8c 51 f6 96 f8 71 54 dd  |ßr.¬!è...Qö.øqTÝ|
00000090  13 a9 71 62 1c 1b 55 69  63 0d c2 3d d8 88 99 9c  |.©qb..Uic.Â=Ø...|
000000a0  0d 1b 0a 64 16 df 69 28  5d 2f 44 54 62 34 1f ac  |...d.ßi(]/DTb4.¬|
000000b0  c2 db 35 12 6a de 1e c5  e8 e9 30 ac 9b e1 56 98  |ÂÛ5.jÞ.Åèé0¬.áV.|
000000c0  d0 94 67 57 b9 16 55 a2  30 25 dc 91 c2 b5 c3 91  |Ð.gW¹.U¢0%Ü.ÂµÃ.|
000000d0  1e dc 44 33 90 be 36 3a  d3 f2 a9 9e a7 d4 dd 4b  |.ÜD3.¾6:Óò©.§ÔÝK|
000000e0  e2 1b 51 4b e2 91 c6 82  8d a5 49 3b 82 cd ec 4c  |â.QKâ.Æ..¥I;.ÍìL|
000000f0  e0 53 52 f3 c1 ad 55 35  3d 3b c0 f6 50 e6 ee 9a  |àSRóÁ*U5=;ÀöPæî.|
00000100  ed 6a c0 0f 72 90 dc 4e  b8 9d 84 69 b0 05 74 14  |íjÀ.r.ÜN¸..i°.t.|
00000110  7a ad 98 75 6f 4c 4b fe  a6 31 c4 6a 12 a1 da 3b  |z*.uoLKþ¦1Äj.¡Ú;|
00000120  71 84 6f 21 04 04 a8 10  27 93 0b 47 ad 8e fe d3  |q.o!..¨.'..G*.þÓ|
00000130  45 0e ad 65 ed 97 5e 41  88 aa a4 4d 8b fc f9 a9  |E.*eí.^A.ª¤M.üù©|
00000140  13 8c f7 6c 16 05 20 37  47 44 1c 43 24 b1 c2 51  |..÷l.. 7GD.C$±ÂQ|
00000150  58 6a 29 3c 26 e8 bc e2  4e 93 a7 9f f0 69 5b 49  |Xj)<&è¼âN.§.ði[I|
00000160  72 46 37 fe 69 53 be ac  7b 0c d9 00 a7 9b 36 79  |rF7þiS¾¬{.Ù.§.6y|
00000170  52 bd a0 14 7a 88 e1 7a  60 87 3e dd 36 90 fe b4  |R½*.z.áz`.>Ý6.þ´|
00000180  b3 09 f3 f0 c1 72 c9 ba  cd 78 92 8b 7c 3c 52 9c  |³.óðÁrÉºÍx..|<R.|
00000190  8f 8b 0a 1f 3b ba 87 78  f5 f1 ca 60 b4 07 ba 4d  |....;º.xõñÊ`´.ºM|
000001a0  84 d8 6b 1a 5e 8e b2 e5  8d 3d f3 d8 74 e0 ab fc  |.Øk.^.²å.=óØtà«ü|
000001b0  70 f9 70 4d c9 bb d0 71  95 f8 89 e4 0c 20 08 81  |pùpMÉ»Ðq.ø.ä. ..|
000001c0  62 16 36 76 db 48 40 c4  b8 86 fa a0 e8 e5 d0 39  |b.6vÛH@Ä¸.ú*èåÐ9|
000001d0  f4 49 13 a4 23 58 43 98  8a ed b9 6d 4e f6 d8 88  |ôI.¤#XC..í¹mNöØ.|
000001e0  bd 8d b9 9b c6 8a 94 d2  30 c6 fe f8 d3 c3 dc da  |½.¹.Æ..Ò0ÆþøÓÃÜÚ|
000001f0  72 ef 38 bb 85 c2 9d d6  ce 81 77 98 29 2c c7 17  |rï8».Â.ÖÎ.w.),Ç.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

hdb hdd sda sdb sdc sdd sde sdf sdg sdh sdi 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 2571: printf: -v: invalid option
printf: usage: printf format [arguments]
To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".

```

---

### Post by oldfred on 2011-10-31
Script cannot mount encrypted partitions which would be expected. I have not seen script run with Puppy, but Puppy must be missing some of the scripting tools used. It may just not able to mount the ext3 Linux partition or you have issues in the partition, it is hard to tell. 

Do you have liveCD or LiveUSB of Ubuntu? That works a lot better for analyzing Ubuntu issues.

---

### Post by purg on 2011-10-31
thanks for your help... will update this thread tomorrow after downloading a larger live iso for the script.

---

### Post by purg on 2011-11-01
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy is installed in the MBR of /dev/sda and looks at sector 3534 
    of the same hard drive for the stage2 file, but no stage2 files can be 
    found at this location..
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb5 starts at sector 102392768. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........6.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1438952 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *     51,196,383   102,392,639    51,196,257   7 NTFS / exFAT / HPFS
/dev/sdb2         102,392,766   625,136,399   522,743,634   f W95 Extended (LBA)
/dev/sdb5         102,392,768   625,136,399   522,743,632   b W95 FAT32
/dev/sdb3               2,048    47,116,287    47,114,240  83 Linux
/dev/sdb4          47,116,288    51,195,903     4,079,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sdb3        860b3a31-26a1-484d-8cdb-a1eeb6fabec8   ext4       
/dev/sdb4        d7353bc7-a220-458c-9ab0-b2aed1159b58   swap       
/dev/sdb5        1B16-45C7                              vfat       
/dev/sdc         9488-8B3C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /media/shared            vfat       (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000)
/dev/sdc         /mnt                     vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=860b3a31-26a1-484d-8cdb-a1eeb6fabec8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=860b3a31-26a1-484d-8cdb-a1eeb6fabec8 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=860b3a31-26a1-484d-8cdb-a1eeb6fabec8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=860b3a31-26a1-484d-8cdb-a1eeb6fabec8 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 860b3a31-26a1-484d-8cdb-a1eeb6fabec8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_windows_truecrypt ###
# Windows with TrueCrypt
menuentry "Microsoft Windows Truecrypt" {
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
linux16 ($root)/boot/memdisk iso raw
initrd16 ($root)/boot/truecrypt.iso
}
### END /etc/grub.d/40_windows_truecrypt ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=860b3a31-26a1-484d-8cdb-a1eeb6fabec8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=d7353bc7-a220-458c-9ab0-b2aed1159b58 none            swap    sw              0       0
# shared sda5 partition
/dev/sdb5	/media/shared	vfat	user,auto,fmask=0111,dmask=0000	0	0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

============================== sdc/syslinux.cfg: ===============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit vga=788 -- quiet

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Install
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz vga=788  -- quiet

label ubnentry2
menu label ^Command-line install
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=788  -- quiet

label ubnentry3
menu label ^Expert install
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz priority=low vga=788  --

label ubnentry4
menu label Command-^line expert install
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=788  --

label ubnentry5
menu label ^Rescue mode
kernel /install/netboot/ubuntu-installer/i386/linux
append initrd=/install/netboot/ubuntu-installer/i386/initrd.gz vga=788  rescue/enable=true -- quiet

label ubnentry6
menu label ^Install Ubuntu
kernel /install/vmlinuz
append initrd=/install/initrd.gz file=/cdrom/preseed/ubuntu.seed vga=788  quiet --

label ubnentry7
menu label ^Check disc for defects
kernel /install/vmlinuz
append initrd=/install/initrd.gz MENU=/bin/cdrom-checker-menu vga=788  quiet --

label ubnentry8
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry9
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry10
menu label expert
kernel /install/vmlinuz
append initrd=/install/initrd.gz file=/cdrom/preseed/ubuntu.seed priority=low vga=788  --

label ubnentry11
menu label ^Rescue a broken system
kernel /install/vmlinuz
append initrd=/install/initrd.gz rescue/enable=true vga=788  --

--------------------------------------------------------------------------------

================== sdc: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

=============== sdc: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  4a 01 f7 30 fe fa 98 d6  66 35 a9 82 70 93 33 38  |J..0....f5..p.38|
00000010  8f 3e de 60 34 df 7b eb  2d 50 f7 2f e4 f0 cc 21  |.>.`4.{.-P./...!|
00000020  89 0d 89 4b fc 25 ff 95  7b 99 90 89 f6 e2 0a 02  |...K.%..{.......|
00000030  7b d2 f7 dc 2d 4a 79 20  03 87 36 f0 01 04 97 c2  |{...-Jy ..6.....|
00000040  fd 1a 7f 52 0c 23 5a 9e  c3 36 a2 9e 7b 98 11 27  |...R.#Z..6..{..'|
00000050  60 04 a1 a4 09 b5 d9 4b  db b8 ed 59 67 00 69 1c  |`......K...Yg.i.|
00000060  b6 45 a5 d4 a2 40 25 64  8a 78 ce b3 0d da 6b 25  |.E...@%d.x....k%|
00000070  66 7b 87 89 cb b8 bd 70  27 28 3c 1c 85 7e 70 7c  |f{.....p'(<..~p||
00000080  bf a0 9d 30 ce 79 75 6d  c3 8d 65 95 66 5b b1 51  |...0.yum..e.f[.Q|
00000090  cb fa 7b 95 91 07 60 69  8e 71 d4 e5 78 c7 d1 58  |..{...`i.q..x..X|
000000a0  40 7e 7c e4 67 76 c7 69  9e d3 3a 74 a4 05 58 7b  |@~|.gv.i..:t..X{|
000000b0  87 87 92 65 f5 72 09 2e  e5 64 d7 23 5d dd 89 c1  |...e.r...d.#]...|
000000c0  49 38 4b af 0c 6b 19 4b  31 5c 37 0e e8 76 07 aa  |I8K..k.K1\7..v..|
000000d0  5c 52 46 e3 d9 bd b3 f8  74 88 8f 3a 8d e3 61 84  |\RF.....t..:..a.|
000000e0  e2 26 ac b5 12 46 aa 0b  1f 17 c2 4e 56 90 94 64  |.&...F.....NV..d|
000000f0  15 95 ba 6b a5 e2 b6 11  25 6d ba 26 87 1f 60 f8  |...k....%m.&..`.|
00000100  d0 97 52 c1 93 92 e6 93  73 74 26 11 a5 2e 54 3b  |..R.....st&...T;|
00000110  27 bc 1d 74 03 6b 9a 0b  bd df b0 34 4b 28 9d 8b  |'..t.k.....4K(..|
00000120  61 b8 bb cd 02 25 f3 44  ea 37 d3 ab 88 9d 2c 2c  |a....%.D.7....,,|
00000130  8f 72 f4 30 f4 a8 c2 68  51 f7 49 92 db 93 ef c1  |.r.0...hQ.I.....|
00000140  32 08 5f 34 fd 28 3d be  58 b7 70 04 ce 5a f0 a5  |2._4.(=.X.p..Z..|
00000150  e6 e2 ce 22 24 49 b1 7b  8d 0d 5c ee 98 a5 0c c7  |..."$I.{..\.....|
00000160  2d 15 72 c8 dd c7 7e 8b  8e ca 70 51 6c a0 76 5b  |-.r...~...pQl.v[|
00000170  c0 00 77 2a 66 31 82 23  34 bb a7 a1 b6 fd 29 68  |..w*f1.#4.....)h|
00000180  93 f3 85 2c b3 4b a4 1a  0a 21 22 06 e4 ae 30 ea  |...,.K...!"...0.|
00000190  09 f2 86 b6 c3 b2 4e 76  e9 11 5a 2a 8c b2 f1 31  |......Nv..Z*...1|
000001a0  00 52 f6 10 af d7 ea fc  85 79 3b 18 58 eb bc 35  |.R.......y;.X..5|
000001b0  fa 7a 6e f0 49 32 10 b9  56 5e 82 ed 64 45 f1 1d  |.zn.I2..V^..dE..|
000001c0  a3 67 27 14 15 b3 5e 2d  6e ff 9a ca 9d dd 8b 87  |.g'...^-n.......|
000001d0  2f de 1b c0 23 65 aa aa  35 05 17 29 39 8f 2e a8  |/...#e..5..)9...|
000001e0  69 61 4a 55 f7 7c 0f bb  84 62 e9 52 59 1e a9 72  |iaJU.|...b.RY..r|
000001f0  45 d6 44 d4 ad a8 02 ed  e7 d3 67 b0 6f af 27 90  |E.D.......g.o.'.|
00000200

Unknown BootLoader on sdb1

00000000  03 e3 b4 99 81 92 00 b3  82 e0 fe f7 58 7a b0 b3  |............Xz..|
00000010  f5 e3 31 af ab d5 5b 86  ce cb a5 a7 f5 0b 20 14  |..1...[....... .|
00000020  77 c4 fd 99 94 ae 3b 26  bf 57 bd 65 4d 75 4a dd  |w.....;&.W.eMuJ.|
00000030  64 df 05 ca 43 00 91 77  fd f6 8a c4 49 8b cd 1b  |d...C..w....I...|
00000040  20 01 d5 0c b4 bb 45 9d  d5 1b c9 ca cf 9e 30 b8  | .....E.......0.|
00000050  db 06 0c ce df cb e1 51  dc 5f ae 11 2a 0d 76 40  |.......Q._..*.v@|
00000060  50 4d d7 41 bd 55 95 70  2d b5 e9 92 59 87 53 80  |PM.A.U.p-...Y.S.|
00000070  2a 02 f0 57 6b 55 f1 ac  0e 33 39 bd 00 47 55 4f  |*..WkU...39..GUO|
00000080  df 72 08 ac 21 e8 9c 0c  8c 51 f6 96 f8 71 54 dd  |.r..!....Q...qT.|
00000090  13 a9 71 62 1c 1b 55 69  63 0d c2 3d d8 88 99 9c  |..qb..Uic..=....|
000000a0  0d 1b 0a 64 16 df 69 28  5d 2f 44 54 62 34 1f ac  |...d..i(]/DTb4..|
000000b0  c2 db 35 12 6a de 1e c5  e8 e9 30 ac 9b e1 56 98  |..5.j.....0...V.|
000000c0  d0 94 67 57 b9 16 55 a2  30 25 dc 91 c2 b5 c3 91  |..gW..U.0%......|
000000d0  1e dc 44 33 90 be 36 3a  d3 f2 a9 9e a7 d4 dd 4b  |..D3..6:.......K|
000000e0  e2 1b 51 4b e2 91 c6 82  8d a5 49 3b 82 cd ec 4c  |..QK......I;...L|
000000f0  e0 53 52 f3 c1 ad 55 35  3d 3b c0 f6 50 e6 ee 9a  |.SR...U5=;..P...|
00000100  ed 6a c0 0f 72 90 dc 4e  b8 9d 84 69 b0 05 74 14  |.j..r..N...i..t.|
00000110  7a ad 98 75 6f 4c 4b fe  a6 31 c4 6a 12 a1 da 3b  |z..uoLK..1.j...;|
00000120  71 84 6f 21 04 04 a8 10  27 93 0b 47 ad 8e fe d3  |q.o!....'..G....|
00000130  45 0e ad 65 ed 97 5e 41  88 aa a4 4d 8b fc f9 a9  |E..e..^A...M....|
00000140  13 8c f7 6c 16 05 20 37  47 44 1c 43 24 b1 c2 51  |...l.. 7GD.C$..Q|
00000150  58 6a 29 3c 26 e8 bc e2  4e 93 a7 9f f0 69 5b 49  |Xj)<&...N....i[I|
00000160  72 46 37 fe 69 53 be ac  7b 0c d9 00 a7 9b 36 79  |rF7.iS..{.....6y|
00000170  52 bd a0 14 7a 88 e1 7a  60 87 3e dd 36 90 fe b4  |R...z..z`.>.6...|
00000180  b3 09 f3 f0 c1 72 c9 ba  cd 78 92 8b 7c 3c 52 9c  |.....r...x..|<R.|
00000190  8f 8b 0a 1f 3b ba 87 78  f5 f1 ca 60 b4 07 ba 4d  |....;..x...`...M|
000001a0  84 d8 6b 1a 5e 8e b2 e5  8d 3d f3 d8 74 e0 ab fc  |..k.^....=..t...|
000001b0  70 f9 70 4d c9 bb d0 71  95 f8 89 e4 0c 20 08 81  |p.pM...q..... ..|
000001c0  62 16 36 76 db 48 40 c4  b8 86 fa a0 e8 e5 d0 39  |b.6v.H@........9|
000001d0  f4 49 13 a4 23 58 43 98  8a ed b9 6d 4e f6 d8 88  |.I..#XC....mN...|
000001e0  bd 8d b9 9b c6 8a 94 d2  30 c6 fe f8 d3 c3 dc da  |........0.......|
000001f0  72 ef 38 bb 85 c2 9d d6  ce 81 77 98 29 2c c7 17  |r.8.......w.),..|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/mnt/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-11-01
Is your sdb1 partition also encrypted. Script could not parse it. If encrypted it is probably ok, otherwise it may need chkdsk.

You may just need to repair the MBR of the external. Note this time it mounted as sdb, but before it was sdc, so you have to use the correct location to reinstall grub2's boot loader.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdb3 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb3 if not correct:
sudo fdisk -l
#confirm that linux is sdb3
sudo mount /dev/sdb3 /mnt
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Other ways to try to repair or boot:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by purg on 2011-11-02
didnt get anywhere with updating grub / MBR etc.
**Thank you** for all your help I was hoping to use this as another learning curve.

Ive taken the easiest option and reinstalled everything. Its a new setup so repartitioned the drive differently but also moved truecrypt. Between the two alterations the systems booting how I expected first time around. Had realised after reading about encrypting Ubuntu only /home would normally be changed so done the same. The TC partition will store sharable media after I figure how to get truecrypt playing nicely on Ubuntu but already seen a few links about this.

sda - pgp encrypted company drive

sdb - grub2 MBR
sdb1 - Windows XP
sdb2 - TC encrypted FAT32 partition
sdb3 - Ubuntu
sdb4 - Swap


Not sure what went wrong first time aorund but would suspect its grub2 and treucrypt both requiring extra blocks.

---

### Post by oldfred on 2011-11-02
You can encrypt /home, but it cannot be FAT32. All Linux system partitions have to use Linux formated partitions to support ownership & permissions. Windows formats do not.

I stopped using FAT for my shared data partition (but not encrypted) as I lost large files. Changed to NTFS for shared. FAT32 has a maximum of 4GB and has no journal, so recovery is problematic.  FAT32 is ok for small devices like flash drives or camera cards.

---

