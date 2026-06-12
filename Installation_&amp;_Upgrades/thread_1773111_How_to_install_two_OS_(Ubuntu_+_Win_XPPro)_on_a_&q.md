---
title: "How to install two OS (Ubuntu + Win XPPro) on a &quot;blank PC&quot; ?"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by SenseMaker2011 on 2011-06-01
Hi, Folks !

... I am very new in the world of Linux but love it. After I used Microsoft since 1993 on my own computers, it was time to swap.

Couple of weeks ago, I did a 1st test and installed on a 4th computer (without any OS) Ubuntu first time ever. I used Ubuntu 9 installation disc and then upgrated to the latest Ubungu version via Internet. So great... it was very easy going. Unluckily I am not able to start my audio editing software (Adobe Audition) with Wine. 

2 weeks ago the internal HD 80 GB ATA (NTFS formatted) in my 2nd computer (WinXP Pro, SP2) crashed. This Seagate HD was 6.5 years old and I suppose it become a pensionist. Meanwhile I bought a new HD for that mainboard (bigger size: 250 GB)..

The target: I like to reinstall this computer again with Windows XP Pro (so I can use my audio edition software), and same time I like to have parallel available Ubuntu.

I will not use the new HD for any data storage. Herefore I have a network with a RAID (NAS of 2 TB) and external HDs connected via USB. 

The idea of the architecture on the computer might be: Formatting the 250 GB into 3 partitions...

1st partition of 100 GB size: bootable with Win XP Pro
2nd partition of 100 GB size: bootable with Ubuntu
3rd partition of  50 GB size: just using as an interims storage disc

Here my questions:

1.) Is there a specific software, which I have to install first, so when I boot the computer later, I can decide which OS I like to start ? If yes, it should be a freeware tool...  (pls no tipps for a tool like Partition Magic at prize of 50-60 EUR)

2.) How do I have to format (partition type) the new HD ? - Again for WinXP as C: and for Ubuntu the NTFS as D: ? - And what is the best partition type for E: (with the small 50 GB) as pure data storage ?

3.) How do I make the 3 partitions ? - Should I do it with WinXP or with Ubuntu running each from the installation CD ?

4.) Can I use Ubuntu having installed on one of the 100 GB partition for going through the installation process for the WinXP Pro ? 

I'd thank you for a clear instruction what the best method is to go quickly to that installation process of 2 bootable OS systems.

Tks in advance. Warm regards/SM2011.

---

### Post by jerrrys on 2011-06-01
you may want to do a little reading first

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+dual+boot&as_qdr=all&sa=Google+Search&lang=en#866](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+dual+boot&as_qdr=all&sa=Google+Search&lang=en#866)

---

### Post by baarn on 2011-06-01
> **SenseMaker2011 said:**
> 
1.) Is there a specific software, which I have to install first, so when I boot the computer later, I can decide which OS I like to start ? If yes, it should be a freeware tool...  (pls no tipps for a tool like Partition Magic at prize of 50-60 EUR)

2.) How do I have to format (partition type) the new HD ? - Again for WinXP as C: and for Ubuntu the NTFS as D: ? - And what is the best partition type for E: (with the small 50 GB) as pure data storage ?

3.) How do I make the 3 partitions ? - Should I do it with WinXP or with Ubuntu running each from the installation CD ?

4.) Can I use Ubuntu having installed on one of the 100 GB partition for going through the installation process for the WinXP Pro ? 
1.
What you are talking about is a Bootloader there comes one with Windows and several are available with Linux (default for Ubuntu is Grub2, but there is Grub and Lilo aswell).
I think the XP-Bootloader cannot load Linuxes (the Win7 one can) so you have to use Grub2 (easiest).

2.
Install WinXP and chose how big the Partition should be, leave the rest of the drive unallocated. Maybe create a second Partition for shared data storage aswell (NTFS).
Create the rest of the Partitions with the Ubuntu LiveCD, i think it uses the graphical tool gparted for that. There are several options for doing it manually or automated options even for a system with windows allready installed.

3.
as meintioned above

4.
no

edit:
filesystem table would look like this
sda1 ntfs windows
sda2 ntfs shared
sda3 ext2 /boot
sda4 --- extended
sda5 ext4 /
sda6 swap swap
sda7 ext4 /home

remember, you can only have 4 primary(or extended partitions) if you want more than 4 partitions you need to create logical partitions inside of extended ones.
i often heard that it could cause problems if windows is not on the first partition and that the /boot partition should aswell be on a primary partition.

another condensed fstab would like this
sda1 ntfs windows
sda2 ext4 /
sda3 swap swap
sda4 ntfs shared
that would use only primary partitions, but i would not recommend it, you could even get rid of swap partition, but i would not recommend that either.

---

### Post by SenseMaker2011 on 2011-06-01
> **jerrrys said:**
> you may want to do a little reading first

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+dual+boot&as_qdr=all&sa=Google+Search&lang=en#866](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+dual+boot&as_qdr=all&sa=Google+Search&lang=en#866)


@jerrrys: oh.... a new search engine, exclusively for Ubuntu... great, I have not found that... will read. Tks.

---

### Post by mike_f on 2011-06-01
For a relative newbie, there is no need to have separate partitions for /boot and /home. I suggest creating the following layout using gparted before installing WinXP:
sda1 - WinXP (30 GB)
sda2 - spare (for new Windows install or ?)
sda3 - Linux swap (= RAM size for hibernate mode if needed)
sda5 - extended (contains logical partitions)
sda6 - NTFS for shared data (all remaining space)
sda7 - Ubuntu / ext4 (20 GB)
To avoid occasional obscure partitioning issues it is a good idea to create partitions in numerical order up front.
Good luck!

---

### Post by oldfred on 2011-06-02
I agree with mike_f that if you are storing data in a data partition you do not need a separate /home. 

But you mention old drive was 80GB, so is system older? And how old?
And normally you do not need a separate /boot except if it is an older system with BIOS limits of 137GB on booting. Then either all of the / (root) partition or a separate /boot partition have to be totally inside the first 137GB. Your windows install also has to be inside the 137GB, but data partitions can be anywhere.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

> **You can check the date of your computer's BIOS** by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: [    Getting Product Information]("http://members.iinet.net/%7Eherman546/p1.html#Getting_Product_Information").
                                     
                                     Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit _______________________________(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)____(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation _______________________(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit) _________(September 2001)
                                     

---

### Post by SenseMaker2011 on 2011-06-05
1st of all, tks for all the tips here....

As I understood, I started folllowing:

1st: I installed WinXP Pro with SP2, then I upgrated WInXP Pro to Sp3... on the HD with 250 GB...

During the intallation process i was asked about the formatting. I used NTFS... After installing Win XP Pro I splitted the HD into 3 1st bootabla partitions:

C: WinXP Pro (SP3) - 100 GB
D: NTFS - 100 GB
E: NTFS -  37 GB (which is the available space of the 50 GB blank partition)

[E:] I want keep as pure Data storage for interims storage, e.g. for downloads, unzipping etc. ...

Now comes the 2nd part, I wanted to install Ubuntu on D:

After the computer was booted with Win XP Pro the CD with Ubuntu 9 was recognized on F: and I was asked if I like to install Ubuntu running under WIndows... But that's not the real solution I want. So I shut down the computer again and let the Ubuntu 9 CD inside.

With rebooting, this CD was regognized and Ubuntu started asking me if I like to install it. So I confirmed... The Ubuntu installation CD recognized Win XP Pro installation, and asked from the beginning, if I like to install Ubuntu on D. I decided to keep 60 GB in reserves for Ubuntu, so I would have another 37 GB available on D.

All seemed fine and went throught the whole process... it seemed to come to the end, with the last procedure:

"*running post-installation trigger initram-fstools*" and indicated 100% installation. (I dont know what that means.)

I was asked to wait and that Ubuntu would be available very soon. But nothing happened over hours..... All the time only: "*running post-installation trigger initram-fstools*" and indicated 100%. - It looked like the screen was frozen. Only I was able to move the mouse and even use the Firefox browser and visit the Internet. But that was all... no restart, no rebooting...

So I did a cold start: Now I get folllowing message during the boot process (without starting WinXP and without starting Ubuntu):

[B]GRUP LOADING
error: no such partition
grup rescue>

([/B]Rec.: [Shall I try this now ?]("http://ubuntuforums.org/showthread.php?t=1359802")[B])
[/B]
What to do now ????? I do not know if the process of Ubuntu installation was finished correctly... how can I start my WinXP Pro again ? Or is it damaged ? (hope not, it took me 7-8 hours to setup up 1st the win xp pro mashine on last thursday).

Hearing from you...

---

### Post by SenseMaker2011 on 2011-06-05
> **oldfred said:**
> I agree with mike_f that if you are storing data in a data partition you do not need a separate /home. 

But you mention old drive was 80GB, so is system older? And how old?
And normally you do not need a separate /boot except if it is an older system with BIOS limits of 137GB on booting. Then either all of the / (root) partition or a separate /boot partition have to be totally inside the first 137GB. Your windows install also has to be inside the 137GB, but data partitions can be anywhere.

[http://members.iinet.net.au/~herman546/p15.html#18]("http://members.iinet.net.au/%7Eherman546/p15.html#18")

yes ,its an old mainboard, from 2001... during the boot process of the WinXP it is shown to recognize only 137 GB, right... I installed WinXP Pro inside that size, takes round about 40 GB with all programmes (beside the OS) inclusively... 

So I installed the Ubuntu on the 2nd virtual partition D: with 100 GB (pls read my last posting here in the thread) ....  is it now inside the 1st 137 GB? I do not know...

How can I delete the ubuntu installation on D: and then get my WinXP Pro back as I started with 1st step... Do I have to install Ubuntu under C: , too which has only 100 GB size ????

---

### Post by Quackers on 2011-06-05
Ubuntu cannot install to NTFS paritions. Your D: and E: partitions are only called that in Windows. 
I would suggest that you boot from the XP installation disc and repair the Windows bootloader, so that Windows will boot again.
When Windows boots I would recommend that you delete the D: and E: partitions, leaving free space for Ubuntu to install into.
You can then install Ubuntu using the manual partitioning option in the installer.

---

### Post by SenseMaker2011 on 2011-06-05
> **Quackers said:**
> Ubuntu cannot install to NTFS paritions. Your D: and E: partitions are only called that in Windows. 
I would suggest that you boot from the XP installation disc and repair the Windows bootloader, so that Windows will boot again.
When Windows boots I would recommend that you delete the D: and E: partitions, leaving free space for Ubuntu to install into.
You can then install Ubuntu using the manual partitioning option in the installer.

aha... Tks Quackers :-) Yes, seems I was little bit "greenhorny", hm ?  OK, will thry that. Hope my Windows Installation CD recognizes SP3, too.... ?????

---

### Post by Quackers on 2011-06-05
Should be fine. I can't remember on XP whether there is an automatic startup repair function. If not go to the command prompt option in the recovery console and run fixmbr. That should fix the booting.

---

### Post by SenseMaker2011 on 2011-06-05
@Quacker: OK, I repaired the Windows Bootloader... I used the Windwos XP Installation CD, selected "R" for Repair Consol. I found in a German forum, three comand lines: 

*fixmbr*
 *fixboot*
 *bootcfg /REBUILD*
 
after "fixmbr" it was said, that the Bootloader was installed new. It did not react to Fixboot and same not to bootcfg /rebuild. The reaction comment was: Something is damaged, use chkds command. 

Do you think, that with "fixmbr" alone the Windows Bootloader is repaired correctly ? I can boot and re-boot the system and always Windows XP Pro starts... 

Then I have deleted D: to E: It became one single drive without any "letter name", it is not identified with NTFS and of 135 GB size. 

As I understand, now I can install there ubuntu with the Ubuntu 9 CD, right ?

---

### Post by Quackers on 2011-06-05
If Windows is booting ok then it will be fine.

Can I ask why you are using an older version of Ubuntu?

Please boot from the Ubuntu live cd and select "try Ubuntu" and when the desktop loads connect to the internet.
Then please go to System > Admin > gparted and post a screenshot of that screen.

If your bios has a HDD limit of 137GB it should also have a LBA or large drive switch that you can enable. This may prove important as some of grub's boot files may be stored outside that limit, which will cause a failure to boot.

---

### Post by SenseMaker2011 on 2011-06-05
> **Quackers said:**
> If your bios has a HDD limit of 137GB it should also have a LBA or large drive switch that you can enable. This may prove important as some of grub's boot files may be stored outside that limit, which will cause a failure to boot.

about your 1st question: why Ubuntu 9. Probably because of lazyness. It worked with the 1st mashine I installed and later upgrated to the latest version via Internet.... but you are right. I probably should use the latest version...

about 2nd aspect: I cannot expand the max. size in the Bios. not possible... so lets see, just now the installatoin process is going, and lets hope that the grub boot files will be inside the 137 GB.... otherwise probably agan, same procedure as every year, hm ?! :-)

---

### Post by Quackers on 2011-06-05
Maybe not the latest version (11.04) as some seem to be having problems with that, but certainly 10.04, which is a long term support version might be a good idea.
If you install a version and the boot files are outside the 137GB limit, you could re-install using a small /boot partition.
Something else to bear in mind is that even if the installed system boots you can still be faced with a non-booting system at some time in the future when grub's files are updated.

---

### Post by SenseMaker2011 on 2011-06-05
OK, now the installation process worked proper, so it is said at the end of the installation. But that was only on the 1st view :-( 

... restarted the computer, and I got Grup, offers me to select same WinXP Pro, which then is booted correctly. In WinXP I see C: with 100 GB for Windows as NTFS partition and then the rest as "unknown partitions", splitted in 132.3 GB + 2.8 GB size. (Rec.: So it was not planned. I wanted keep a 3rd virtual partition as pure data storage, which can be used by both, by Linux + Windows. Cannot this one be Fat32 and recognized so by both ?)

Lets see if Linux is working on its own: Grup (Versin 1.97 beta4) is showing me the option "Ubuntu, Linux 2.6.31-14-generic". During the boot process as result it is said: 

"[B]error: no such device: 30c5a8a7-a9dc-491e-93cc-a11a040240a2
Press any key to continue...[/B]"

Same happens with the recovery version. Not possible to start Linux.

> **Quackers said:**
> Please boot from the Ubuntu live cd and select "try Ubuntu" and when the desktop loads connect to the internet. Then please go to System > Admin > gparted and post a screenshot of that screen.

Have downloaded the latest "live cd" (version 11.04) and followed your procedure by booting from. Here the datas from the screenshot with /dev/sda (232.89 GB):

Partition - File System - Size - used - unused - flags
------------------------------------------------------------------
/dev/sda1   - ntfs - 97.65 GB - 15.75 GB - 81.91 GB - boot (colour green)
/dev/sda2   - extended - 135.23 GB - --- - --- - ... (colour turkis blue)
  /dev/sda5 - ext4 - 132.36 GB - 4.28 GB- 128.08 GB - ... (colour dark blue)
  /dev/sda6 - linux-swap - 2.86 GB - --- - --- - ... (colour red)
unallocated - unallocated - 2.49 MB - --- - --- - ... (colour pastel green)

Rec.: sda2 and sda6 both have a key symbol. sda5 and sda6 are "sub divisions" of sda2.

Do you need the sectors too ? I give you...

Size - 1st sector - last sector - total sectors - UUID - status
--------------------------------------------------------------------------------------------
97.65 GB - 63 - 204796619 - 204796557 - 94EC6CA3EC6C817A - Not mounted
135.23 GB - 204796620 - 488392064 - 283595445 - --- - Busy (at least one logical partition is mounted)
132.36 GB - 204796683 - 482383754 - 277587072 - **30c5a8a7-a9dc-491e-93cc-a11a040240a2** - not mounted
2.86 GB - 482383818 - 488392064 - 6008247 - b3b908da-820b-4671-b456-daced6caef64 - Active
2.49 MB - 488392065 - 488397167 - 5103 - --- - ---
 
Hope thats all what you need... tks in advance helping me out.

---

### Post by Quackers on 2011-06-05
We need to get a better look at what has been installed and where (in terms of file placement).
From the live cd desktop please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by SenseMaker2011 on 2011-06-05
```


                **Boot Info Script 0.60    from 17 May 2011**


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda2         204,796,620   488,392,064   283,595,445   5 Extended
/dev/sda5         204,796,683   482,383,754   277,587,072  83 Linux
/dev/sda6         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        94EC6CA3EC6C817A                       ntfs       
/dev/sda5        30c5a8a7-a9dc-491e-93cc-a11a040240a2   ext4       
/dev/sda6        b3b908da-820b-4671-b456-daced6caef64   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 30c5a8a7-a9dc-491e-93cc-a11a040240a2
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 30c5a8a7-a9dc-491e-93cc-a11a040240a2
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=30c5a8a7-a9dc-491e-93cc-a11a040240a2 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 30c5a8a7-a9dc-491e-93cc-a11a040240a2
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=30c5a8a7-a9dc-491e-93cc-a11a040240a2 ro single 
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 94ec6ca3ec6c817a
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=30c5a8a7-a9dc-491e-93cc-a11a040240a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b3b908da-820b-4671-b456-daced6caef64 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  97.969468594 = 105.193915904  boot/grub/core.img                             1
  97.969483852 = 105.193932288  boot/grub/grub.cfg                             1
  97.993821621 = 105.220064768  boot/initrd.img-2.6.31-14-generic              3
  97.966886044 = 105.191142912  boot/vmlinuz-2.6.31-14-generic                 2
  97.993821621 = 105.220064768  initrd.img                                     3
  97.966886044 = 105.191142912  vmlinuz                                        2


```

---

### Post by SenseMaker2011 on 2011-06-05
> **Quackers said:**
> This will give a full overview of your current system.

just uploaded it, pls see my last posting... I appreciate your support. 

The question is if it is worth to use so much time for repairing/understanding. Hope we can come soon to an end, or ?

I had no itentions to invest lot of time (and actually have not plenty of it) just for installing Linux as 2nd OS. I want keep Ubuntu in reserves, that I can enter into the computer quickly if MS WinXP Pro should crash unexpected without using CDs, USB sticks etc. ... a kind of rescue system.

:-)

---

### Post by Quackers on 2011-06-05
Thanks for that. Everything looks fine to me. All grub's files are before the 137GB mark, so that's good :-)
Try rebooting and at the grub menu let it do its own thing. Don't press any keys and when the countdown finishes it should try to boot the top otion (which should be Ubuntu). See if you get the same message. If you do, press the space bar and report what happens.
It seems that your root partition is not being found, for some reason, although it appears that it's fine.

---

### Post by oldfred on 2011-06-05
Because of your partition sizes you will eventually have problems. The entire boot process must be within the 137GB. Linux may put new files any where inside a partition. 

So if windows is 83GB the Linux boot partition (or entire system partition) can be 137-83 or 54GB max. Data partitions NTFS or /home as ext3 or ext4 can then be in the remaining space and have no issue. I actually recommend 20 to 25GB for / (root) and the rest for /home. But if you are primarily windows, leave /home in root and make root 30 to 40GB. Just store most data then in a NTFS partition that is after 137GB.

Even windows user often suggest a smaller windows system partition of 20-30GB for XP and larger for Vista/7 and separate NTFS data partition so you can reinstall windows without having to reinstall all your data (backups still required).

---

### Post by SenseMaker2011 on 2011-06-05
> **Quackers said:**
> Try rebooting and at the grub menu let it do its own thing. Don't press any keys and when the countdown finishes it should try to boot the top otion (which should be Ubuntu). 

Grup is not starting automatically... before the list appears on an own window with all the different programmes (Ubuntu, Win XPPro)  one window before in a line comment appears "no device" (only seen for some milli seconds)... 

Then Grup just keeps on standby on the top line (which is Ubuntu) but does not start it. If I select manually WinXP Pro, I get it started. That's all.

---

### Post by Quackers on 2011-06-05
Ok, at the grub menu, with the list of operating systems, the top item should be Ubuntu and it should be highlighted. Press enter and if you get the same error as before press enter again. See what happens please.

---

### Post by oldfred on 2011-06-05
I am not sure but maybe the BIOS has to read the entire partition so just having files inside 137GB limit now still may not work.

Use gparted and shrink sda5 so the end is inside the 137GB limit. It may then boot.

---

### Post by Quackers on 2011-06-05
Good point oldfred. Definitely worth a try :-)

---

### Post by SenseMaker2011 on 2011-06-05
> **Quackers said:**
> Ok, at the grub menu, with the list of operating systems, the top item should be Ubuntu and it should be highlighted.

yes, as mentioned, it does...

> **Quackers said:**
> Press enter and if you get the same error as before press enter again.

1x "press enter" end with same result
2x "press ender" after getting the error: grub just jumps back to the menu...

---

### Post by SenseMaker2011 on 2011-06-05
> **oldfred said:**
> Use gparted and shrink sda5 so the end is inside the 137GB limit. It may then boot.

I kept c: with 99 GB for WinXP and shrinked the Ubuntu sda5 down to 35 GB... then restarted, but same troubles... same error message. :-(

---

### Post by SenseMaker2011 on 2011-06-05
OK, folks... we tried a lot, I think... but do not really progress. Its great you all gave me your advice, support and solutions... sorry taking your time.

... think, its better to stop further attempts, we are close to a new working week, its 10:30 pm late Sunday evening. 

I have to realize, that this computer is just too old, a mainboard of 2001... 10 years cannot be compensated with such an old bios to read a bigger 250 GB HD. So it is... 

I have a 3rd computer same with Win XP Pro, but its a newer one with two hard discs of 80 GB as C: and actually for data storage of 110 GB... maybe I will give a try there, later.
--------------------------

How can I deinstall Linux and get it out completely ? - Same with uninstalling I like to get Grub out of the system, just booting regularly WinXP Pro as before... 

Possible ? - What to do... and sorry guys taking your time.

---

### Post by Quackers on 2011-06-05
I'm sorry that you seem to have run out of time.
Oldfred's suggestion may work but you may also need to purge and re-install grub as well. It may be better to re-install Ubuntu (either version) to that new partition you just reduced in size. That way grub will also get re-installed.
But obviously that's for a different day, perhaps.

To get grub out of the mbr of the drive you will need to repair the Windows bootloader, the same way you did before (with fixmbr from the command prompt when booting from the Windows installation disc).
Once Windows boots again you can just delete the Ubuntu partitions.

---

### Post by oldfred on 2011-06-05
From grub rescue prompt try manual booting.Your partition is sda5 or hd0,5.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

set prefix=(hd[COLOR=DarkRed]0,5[/COLOR])/boot/grub  
set root=(hd[COLOR=DarkRed]0,5[/COLOR])
insmod linux
linux /vmlinuz root=/dev/sd[COLOR=DarkRed]a5[/COLOR] ro  
initrd /initrd.img
boot

---

### Post by SenseMaker2011 on 2011-06-05
As mentioned I cannot afford such time eating repairings etc. .... It was a Sunday afternoon for nothing. 

I have deleted now the whole partitions, Ubuntu and grup... WinXP Pro SP3 is now starting alone. Lets see what to do next with the idea to have a 2nd OS on that mashine. 

Tks for everybody... wish you all a good start into the next week. Take care/LJ
--------------

P.S.: On my "singular pure Ubuntu mashine" I still have a monitor problem, yet nobody in the forum gave feedback. Maybe you Linux specialists like to have a look there: [http://ubuntuforums.org/showthread.php?t=1775861](http://ubuntuforums.org/showthread.php?t=1775861)

---

### Post by Quackers on 2011-06-05
I'm sorry you haven't had any help yet on the other thread but it's not every user that has more than one screen to worry about, so your helpers will be more limited.
Hopefully someone will come along soon :-)

---

