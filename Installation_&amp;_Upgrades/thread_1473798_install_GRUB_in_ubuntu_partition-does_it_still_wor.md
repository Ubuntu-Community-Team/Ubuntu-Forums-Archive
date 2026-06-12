---
title: "install GRUB in ubuntu partition-does it still work"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by davexnet on 2010-05-05
Hello all, 
with my legacy Ubuntu (prior to 9.04) I had installed
the boot loader into the Ubuntu partition then used 
a command similar to this to create a small file which could be
added to Windows boot menu.  (This allowed me keep the MBR and Windows
loader in tact)
dd if=/dev/sda10 of=/home/linux.bin bs-512 count=1

I just did a fresh install of 9.10 and apparently this method no longer
works.  (The first 512 Bytes of the partition are binary zeroes).

I tried using the "linux.bin" I had previously been using,and when Ubuntu
is selected it leads me to a GRUB prompt.

Is there any method to maintain the Windows MBR and bootloader and boot Ubuntu?
How to proceed from my present situation? I do not want to overwrite
the MBR.
TIA for any info.

---

### Post by davexnet on 2010-05-05
I reinstalled and did it a different way.

My original setup was XP.  Then I installed Vista to a second
partition, and Vista installed it's boot loader,
allowing xp/Vista to boot.

Now  I installed 9.10 into a third partition, and put grub on the
2nd HDD, and all the OS' remain on disk 1.

Modified the BIOS to boot from disk 2, and sure enough, Vista and 
9.10 are accessible, but XP is not.  Selecting XP, the PC
just reboots.

If I enter the BIOS and reselect HDD 1 as the boot drive,
Ive get my old Vista boot loader back.

At this point I'm thinking of scrubbing it again and doing a
clean install of Jaunty - at least that way I get the old-style
GRUB and can presumably use my original method.

Why is XP not bootable?  I did it Ubuntu's way and it doesn't work.

---

### Post by efflandt on 2010-05-05
The best way to put grub or grub2 on a partition with standard Windows mbr, is to put grub on a "primary" Linux partition on the first drive (where XP is).  Then use gparted or fdisk to mark the partition with grub as the boot partition.

Then grub should boot from that partition and XP should work from that.  It works for me (grub2 is on sda3, but I update-grub from sda6).  Attempting to put grub on a "logical" partition could be problematic (I don't think a Windows mbr could boot that).

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf806f806

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32 (HP Recovery)
/dev/sda2             620       17194   125307000    7  HPFS/NTFS (WinXP Home)
/dev/sda3   *       17195       21366    31540320   83  Linux (32-bit 9.10)
/dev/sda4           21367       25841    33831000    5  Extended
/dev/sda5           21367       21669     2290648+  82  Linux swap / Solaris
/dev/sda6           21670       25841    31540288+  83  Linux (64-bit 9.10)

```

---

### Post by davexnet on 2010-05-06
Thanks for responding, it's something that didn't occur to me.
I do indeed install /root and /swap into logical partitions
and thus, can not be booted directly.

Regarding your disk layout, you have one install of Ubuntu on
sda3 and another on sda6 ?  (sda3 presumably Primary)

What do you mean by "but I update-grub from sda6" ?

---

### Post by efflandt on 2010-05-06
When I installed 64-bit 9.10 on sda6, I told it to put grub on primary partition sda3 (from the **Advanced** button in summary screen after setting up partitions and my user.  So sudo update-grub from the system on sda6 make grub2 at the bottom of sda3 get its files from /boot/grub on sda6.

Since I also put grub2 on sda3 when I installed 32-bit 9.10 on sda3, that can step on grub and make it look for /boot/grub on sda3 instead of sda6, but update-grub finds all kernels including any on sda6.  So I can always boot to sda6 and do sudu update-grub from there to list sda6 kernels at the top of the grub menu, instead of at the bottom.

If that is confusing, as long as the grub version is the same, the part of grub put on the base of a partition just points to a partition where grub can find the rest of its core and menu, whether /boot/grub is on the same partition or different partition (primary or logical).  As long as the mbr of the drive can boot a primary partition containing the base of grub, grub can take if from there.

You can have up to 4 primary partitions on a drive, or one of those 4 can be an extended partition with any number of logical partitions.  But you do not even need an extended partition if you are only using up to 4 partitions total, or if you can put Linux on the 3rd primary partition and any additional partitions as logical partitions in extended partition 4.

---

### Post by frantid on 2010-05-06
> **davexnet said:**
> I reinstalled and did it a different way.

My original setup was XP.  Then I installed Vista to a second
partition, and Vista installed it's boot loader,
allowing xp/Vista to boot.

Now  I installed 9.10 into a third partition, and put grub on the
2nd HDD, and all the OS' remain on disk 1.

Modified the BIOS to boot from disk 2, and sure enough, Vista and 
9.10 are accessible, but XP is not.  Selecting XP, the PC
just reboots.

If I enter the BIOS and reselect HDD 1 as the boot drive,
Ive get my old Vista boot loader back.

At this point I'm thinking of scrubbing it again and doing a
clean install of Jaunty - at least that way I get the old-style
GRUB and can presumably use my original method.

Why is XP not bootable?  I did it Ubuntu's way and it doesn't work.

You would have to map the xp partition to look like it is the first drive.  
something like this

drivemap -s (hd0,1) (hd1,1)

Where (hd1,1) is your xp partition seen as the second hard drive by grub booting of HDD2

---

### Post by oldfred on 2010-05-06
Windows combines its boot files into the active partition (boot flag). From grub then you can only boot one windows and from that select which windows to boot. To see how windows boots review pictures, to totally understand it read the (long) article.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Grub2 lets you boot windows but will only find one unless you modify the installs so they can be booted separately. (But then from a windows boot loader in sda you will only be able to boot one or the other (which ever has boot flag).

---

### Post by davexnet on 2010-05-06
My first HD looks like this
Primary  (XP)
Logical (XP 2nd install)
Logical Vista
Logical data
logical Linux swap
Logical ext4 root

Second Hard Drive:
Pimary (data)
logical (more data)

In the beginning, XP was installed in the primary,
then a 2nd Xp in the logical.  Then Vista was installed
and it look over the boot loader.  The menu would have the choice
of "earlier version of Windows" (which if you selected would give you another
 choice of either of the two XP's) or Vista itself.

I then (about two years ago) installed Linux and put grub
on the logical partition (sda10) you can see above.
I used the method mentioned in my first post to boot Linux.

Now with 10.4, that method doesn't work.  So instead I installed
Grub to the MBR of the second harddrive, and by modifying the
bios to boot from there, I can access Linux and Windows.
As before, if I select Windows,
the Vista menu is active  and gives me the choices of 
booting from "earlier versions of windows".  At which point if
I select one of them the PC reboots and it gets me nowhere.
Selecting Vista instead is successful

Since this install of 10.4 is fresh and has no personal data,
I downloaded another distributon, the latest from
PCLinuxOS.  Installed it as mentioned above - same as 10.4,
with Grub on the 2nd HDD.  However, this time when I select 
windows and either of the XP's to boot, they boot normally.

Now, I don't know what version of grub they're using, or what
else they're doing differently, but theirs works.

I also don't understand your latest comments about pointing
 grub to XP directly - do you think that the PCLinuxOS install
did this extra step?  How can we check ?
Logically, to me, Vista Loader should handle the booting of XP -
I don't see why Grub has to even deal with that.

---

### Post by oldfred on 2010-05-06
Its windows that moves files into the one bootable partition. Maybe PCLinuxOS moves them back. I know you cannot delete your windows in the primary without major issues on the versions in extended. Windows will not normally boot directly into a logical partition.

For curiosity run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by davexnet on 2010-05-07
Hi oldfred, 
I'm on a 2nd PC now, but I'll run the script later today.
Not sure what you mean by moving files around. What files?

I'm aware of the significance of the Primary partition.  I'm
pretty sure it's intact.  I installed grub to the 2nd harddrive
as I mentioned.  If I reenter the BIOS and modify it to boot
from the first HDD, Vista's boot loader gets immediate control
and works fine, since the MBR and Vista loader haven't been touched.  (One benefit of a 2nd HDD!)

---

### Post by oldfred on 2010-05-07
This is a typical combined boot:

    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

The boot.ini, and nt files are for XP.

The bootmgr, BCD & winload are Vista or 7. Those files will all be on the active partition and the second install of windows will not have all of them and normally cannot be directly booted. Also the boot sector may not have data on the second partition.

---

### Post by davexnet on 2010-05-07
Hi - here's the script results.  Perhaps it will shed some light...

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /linux.bin looks at sector 
                       398045084 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #10 for /boot/grub/menu.lst. Grub 
                       in the file /linuxold2.bin looks at sector 471456412 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location. Grub 2 in 
                       the file /linuxold3.bin looks at sector 1 of the same 
                       hard drive for core.img, but core.img can not be found 
                       at this location. Grub in the file /linuxold.bin looks 
                       at sector 471456412 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /boot/bcd 
                       /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /grldr /GRLDR /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 1493. But according to the info from fdisk, 
                       sda8 starts at sector 98367488. According to the info 
                       in the boot sector, sda8 has 286838783 sectors, but 
                       according to the info from fdisk, it has 286839081 
                       sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /WINDOWS/system32/winload.exe 
                       /WINDOWS/SYSTEM32/winload.exe 
                       /windows/system32/winload.exe

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.32.12-pclos1.bfs on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02a702a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,049,489    28,049,427   7 HPFS/NTFS
/dev/sda2          28,049,551   488,392,064   460,342,514   5 Extended
/dev/sda5          28,049,553    49,078,574    21,029,022   7 HPFS/NTFS
/dev/sda6          49,078,638    76,630,049    27,551,412   7 HPFS/NTFS
/dev/sda7          76,630,113    98,365,994    21,735,882   7 HPFS/NTFS
/dev/sda8          98,367,488   385,206,569   286,839,082   7 HPFS/NTFS
/dev/sda9         385,206,633   389,110,364     3,903,732  82 Linux swap / Solaris
/dev/sda10        389,110,428   488,392,064    99,281,637  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5e5170e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   250,533,674   250,533,612   7 HPFS/NTFS
/dev/sdb2         250,533,675   320,159,384    69,625,710   f W95 Ext d (LBA)
/dev/sdb5         250,533,738   320,159,384    69,625,647   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       73dbf5e7-5bc7-487f-be47-cfa6f82b4027   ext4                                     
/dev/sda1        DE3C91D93C91AD51                       ntfs       WINME                         
/dev/sda5        CAF06920F069144B                       ntfs       D-DRIVE                       
/dev/sda6        1484CE7E84CE61BA                       ntfs       NTFS XP                       
/dev/sda7        02A006CFA006C95D                       ntfs       G-DRIVE                       
/dev/sda8        F484276784272C14                       ntfs       K-vista                       
/dev/sda9        2d8623dd-b4cc-45a5-b407-c16b2ba65615   swap                                     
/dev/sdb1        5E00E80A00E7E74D                       ntfs       I-ntfs                        
/dev/sdb5        C4480EAD480E9E74                       ntfs       J-DRIVE                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional F:" /fastdetect /usepmtimer /NoExecute=OptOut /numproc=2
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional C:" /fastdetect=OptIn /usepmtimer
c:\linux.bin="Ubuntu"

================================ sda1/BOOT.INI: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional F:" /fastdetect /usepmtimer /NoExecute=OptOut /numproc=2
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional C:" /fastdetect=OptIn /usepmtimer
c:\linux.bin="Ubuntu"

========================== sda10/boot/grub/menu.lst: ==========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,9)/boot/gfxmenu
default 0

title linux
kernel (hd1,9)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=73dbf5e7-5bc7-487f-be47-cfa6f82b4027  splash=silent vga=788
initrd (hd1,9)/boot/initrd.img

title linux-nonfb
kernel (hd1,9)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=73dbf5e7-5bc7-487f-be47-cfa6f82b4027 
initrd (hd1,9)/boot/initrd.img

title failsafe
kernel (hd1,9)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=73dbf5e7-5bc7-487f-be47-cfa6f82b4027  failsafe
initrd (hd1,9)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title windows1
root (hd0,0)
makeactive
chainloader +1

=============================== sda10/etc/fstab: ===============================

# Entry for /dev/sda10 :
UUID=73dbf5e7-5bc7-487f-be47-cfa6f82b4027 / ext4 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda9 :
UUID=2d8623dd-b4cc-45a5-b407-c16b2ba65615 swap swap defaults 0 0
none /dev/pts devpts defaults 0 0
tmpfs /dev/shm tmpfs defaults 0 0

=================== sda10: Location of files loaded by Grub: ===================


 201.5GB: boot/grub/menu.lst
 201.5GB: boot/grub/stage2
 199.3GB: boot/initrd-2.6.32.12-pclos1.bfs.img
 199.3GB: boot/initrd.img
 201.5GB: boot/vmlinuz
 201.5GB: boot/vmlinuz-2.6.32.12-pclos1.bfs

---

### Post by oldfred on 2010-05-07
I am surprised it works, I reformated entry so you can easily see you have the same entries multiple times with different capitalization. Windows does not see capitals and small letters differently, but linux does:

Boot files/dirs: 
/boot.ini 
/BOOT.INI 
/bootmgr 
/BOOTMGR 
/boot/bcd
/BOOT/bcd 
/Boot/bcd 
/boot/BCD 
/BOOT/BCD 
/Boot/BCD
/grldr 
/GRLDR 
/ntldr 
/NTLDR 
/NTDETECT.COM 
/ntdetect.com

Boot files/dirs: 
/Windows/System32/winload.exe
/WINDOWS/system32/winload.exe
/WINDOWS/SYSTEM32/winload.exe
/windows/system32/winload.exe

I thought if you had duplicate files like this windows got confused and did not work. Do you have these multiple entries or is the script seeing something that is not there.

---

### Post by davexnet on 2010-05-13
Hi oldfred, yes it certainly works.
I'm unable to see any dups at all, as you were wondering.

What is c:\grldr ? Never noticed that before - something to do with grub?

Frankly, I consider myself lucky that I had the 2nd HDD, and a place to
put grub loader without interfering with the original MBR.

2 observations.  A lot of people are having trouble with Grub 2.
What is the point of it?  As I mentioned when I installed grub to the
2nd HDD with 10.4, XP would not boot.  However scrapping Ubunto and installing
PCLinuxOS XP booted fine. (Apparently grub 0.97)

2nd point, why was GRUB restructured so that you couldn't install it to
the linux partition?  That made life so much easier.

---

