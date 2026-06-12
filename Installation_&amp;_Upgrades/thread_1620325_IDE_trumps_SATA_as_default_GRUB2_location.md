---
title: "IDE trumps SATA as default GRUB2 location?"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Innigo on 2010-11-12
Hi Ubuntu folks,

I've read
"Can't choose my 2nd HDD to install Ubuntu"
[http://ubuntuforums.org/showthread.php?t=1613869](http://ubuntuforums.org/showthread.php?t=1613869)
and
"How to move GRUB?"
[http://ubuntuforums.org/showthread.php?t=1556738](http://ubuntuforums.org/showthread.php?t=1556738)
and
"installer doesn't see all drives / partitions"
[http://wwww.ubuntuforums.org/showthread.php?p=9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738)

but my problem seems not exactly the same as them. I have three drives:
1) SATA drive on first port with Windows on it
2) IDE drive with Ubuntu9.10 on it
3) new SATA drive for Ubuntu10.04
I want to remove the IDE drive and put it in a safe place as a backup.

I installed 9.10 on the new SATA, intending to see if I could get Upgrade Mangager to offer me Lucid Lynx. I should have unplugged the IDE drive but I didn't. Anyway, the Ubuntu9.10 CD installer did find the new SATA disk which I had partitioned using my original 9.10 setup on the IDE. It did put Ubuntu onto the first partition of the new SATA where I wanted it. However, if I disable the IDE in BIOS I get just a blinking underscore at the top left conrer of the screen on reboot. 

Why would the installer do this to me? Nevermind, perhaps a better question is this: How do I check where GRUB2 has been installed and if, as I suspect, it's put GRUB2 on the IDE, what's the simplest and safest way to get GRUB2 put on the boot sector of the new SATA disk?

---

### Post by psusi on 2010-11-12
When you install 10.04 or 10.10 from the desktop cd, the first screen of the installer at the bottom has a selector for where to install grub to.

---

### Post by cybergnome on 2010-11-13
Removing the IDE channel has nothing to do with GRUB2.  You can manually install GRUB2 anywhere you want.  The IDE and SATA relationship is controlled by the motherboard's chipset controller, and will have configuration options in the BIOS, if there are any.  That's processed well before any boot loaders become involved.

You can have only one default boot hard drive, and that's typically where the boot loader should be placed.  To boot from another hard drive, you will  need either a BIOS enabled hot key that will let you choose from a menu (that's an OEM utility), or you will have to chain boot from another device, such as a Super Grub CD.

The question is then whether or not your system allows booting from a non-IDE hard drive.  Some older ones don't. If you find that's your case, look to see if a BIOS update fixes that     .](*,)

---

### Post by Innigo on 2010-11-14
Thanks for those replies. I have a 10.04 Live CD so I might try that and look out for that GRUB location selector. 

My BIOS does allow booting from SATA as that was where Windows was booting from. When I put in the Ubuntu9.10 CD, I assumed(quite reasonably I thought at the time) that the BIOS hard disk boot order would be respected. Apparrently not.  

If "there can be only one" as far as default boot disk goes, then I'll have another minor problem. How do I install GRUB to the SATA, then delete the old GRUB without losing access to the system? Or is it better to just install a new instance of Ubuntu10.04, this time choosing the SATA disk?

---

### Post by oldfred on 2010-11-14
You just need to install grub2 to the MBR of the correct drive. During install of Ubuntu, it defaults to installing to sda, not the drive you install to. I guess it assumes you are booting sda, so that is where you will want grub2. then in BIOS set that drive as the boot drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

If you want to know what is where from Ubuntu or liveCd:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

I like to run script before (to document) and after any system changes so I know I install everything where I thought I did.

---

### Post by Innigo on 2010-11-15
Thanks oldfred. I ran that boot_info_script but it thinks my NTFS  partitions (with no OS and not marked bootable in Palimpset) are Windows  Installs as did GRUB which gave me redundant boot menu entries for  them. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=5ca9f1ec-d92b-44d6-acbb-a4ffb66af1cd)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 78300873.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 109691820.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc3 starts at sector 271980450.
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,300,809    78,300,747   6 FAT16
/dev/sda2          78,300,810   976,768,064   898,467,255   5 Extended
/dev/sda5          78,300,873   244,316,519   166,015,647   6 FAT16
/dev/sda6         966,968,478   976,768,064     9,799,587  82 Linux swap / Solaris
/dev/sda7         244,316,583   966,968,414   722,651,832  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c42dfb8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,192,964     4,192,902   6 FAT16
/dev/sdb2           4,192,965    72,276,434    68,083,470   f W95 Ext d (LBA)
/dev/sdb5           4,193,028    72,276,434    68,083,407   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d9867

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   109,691,819   109,691,757  83 Linux
/dev/sdc2         109,691,820   271,980,449   162,288,630   c W95 FAT32 (LBA)
/dev/sdc3         271,980,450   498,111,389   226,130,940   c W95 FAT32 (LBA)
/dev/sdc4         498,111,390   967,032,674   468,921,285   5 Extended
/dev/sdc5         498,111,453   967,032,674   468,921,222  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        1934-8EE6                              vfat       G80bak                        
/dev/sda6        f0de8e81-0d52-4740-8476-da86453014d7   swap                                     
/dev/sda7        6ea8ad99-4da9-4d52-bcac-9a2a37099748   ext4                                     
/dev/sdb1        5023-E837                              vfat                                     
/dev/sdb5        DA5032175031FAB9                       ntfs                                     
/dev/sdc1        5ca9f1ec-d92b-44d6-acbb-a4ffb66af1cd   ext4                                     
/dev/sdc2        4B02-882A                              vfat       G80                           
/dev/sdc3        52D5-8750                              vfat       LAC                           
/dev/sdc5        61336f2e-3360-4792-a844-eeddeeb2215e   ext4       XCF                           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc3        /media/LAC               vfat        (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc5        /media/XCF               ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect 

=========================== sda7/boot/grub/grub.cfg: 


```

I'm thinking to run sudo grub-install which will run grub-mkconfig and  grub-setup for me, all pointable at sdc and then run sudo update-grub.  Then I'd want to delete the existing GRUB2 from the IDE. Does that sound fairly safe?

---

### Post by oldfred on 2010-11-15
Yes you can reinstall grub to the MBR of your choice. If you wan to confirm you can rerun script and see what boot loader is where. Just that either grub2 or the script do not always show drive correctly. Mine says same drive from sda but is booting from partition sdc7. There is no partition 7 on sda.


reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by oboedad55 on 2010-11-15
The other option is to shut down and unplug the IDE drive and boot from a live cd and reinstall Grub this way;

"If you have installed Windows after Linux, or you may have somehow lost the Grub at the startup, and are unable to load your Linux, then this article may be helpful.

Firstly, boot from your Linux or Ubuntu CD, and choose the option of trying Ubuntu without installation.

After Ubuntu gets loaded from the Live CD, you have to find out that which of the drive or partition was the one, containing your previously installed Linux. For checking out the partitions, goto the terminal ( Applications -> Accessories -> Terminal ), and write:

sudo fdisk -l
or
fdisk -l

This will show you the list of partitions you have in your system.

After you get to know the partition where your Ubuntu was installed, write the following commands. For example, if the partition is /dev/sda1, you have to write the following commands (you have to replace the sda1 from your partition name):

sudo mount /dev/sda1 /mnt
sudo mount –bind /dev /mnt/dev
sudo mount –bind /proc /mnt/proc

Now write:

sudo chroot /mnt

and then install Grub by the following command:

grub-install /dev/sda

If any errors found after entering the above line, then try this one:

grub-install –recheck /dev/sda

This is it.

Now you can reboot your system, and enjoy using your previously installed Ubuntu, after un-mounting the system by:

sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

and simply reboot:

sudo reboot"

---

### Post by Innigo on 2010-11-26
The absolute safest way would have been to do what oboedad55 said - booting from LiveCD and then mounting the relevant drive. As I was fairly sure which drive was what, I just did what oldfred said. Problem solved. :-)

---

### Post by oboedad55 on 2010-11-26
> **Innigo said:**
> The absolute safest way would have been to do what oboedad55 said - booting from LiveCD and then mounting the relevant drive. As I was fairly sure which drive was what, I just did what oldfred said. Problem solved. :-)

Woohoo! :P

---

