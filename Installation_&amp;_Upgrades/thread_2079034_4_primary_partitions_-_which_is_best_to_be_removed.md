---
title: "4 primary partitions - which is best to be removed/changed into secondary?"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by mastablasta on 2012-11-01
I bought HP Pavilion Dm1, which comes with 4 partitions.
 
1 System
2 no label -> where the os is and the data goes...
3 Recovery
4 HP_tools
 
I've  created recovery USB drive. And at first i wanted to remove the  HP_tools partition but then i see that HP Quickweb is there along with a  few tools.
 
The notebook came with windows 7 starter  (32bit os) and 2GB RAM (can go up to 8GB). i would like to install 64bit  linux and increase the ram (as i plan to use the full potential of the  CPU). i would also like to keep win7 starter since i payed for it and  since it might be usefull for certain tasks.
 
The problem is the preformated 4 primary partitions.
 
I've  read quite a few of the threads with this topic on this and some other  forums. and also how to do it. but none give any definite answer...
 
So  what happens if i change HP_tools into secondary (logical?!) partition ?  will the tools still work? will the HPquickweb still work/boot? or is  it better to remove the recovery partition?
 
HP quickweb is  somekind of linux basedOS, which is kind of funny.  HP might as well  create a 10GB partition on a 500GB disk and install a propper linux  there. it would still boot extremely fast... or rather much faster than  windows 7.


Anyway quickweb can be booted using grub 2.2: [http://phoronix.com/forums/showthread.php?63666-Booting-HP-QuickWeb-%28v3%29-with-Grub2](http://phoronix.com/forums/showthread.php?63666-Booting-HP-QuickWeb-%28v3%29-with-Grub2)


it seems (appears the computer is using BIOS to boot). i did a boot info script:
```

                            
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1449344 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the J:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   938,872,831   938,463,232   7 NTFS / exFAT / HPFS
/dev/sda3         938,872,832   968,450,047    29,577,216   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,119     8,321,072   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
5 heads, 32 sectors/track, 48921 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        02CA6F18CA6F06EF                       ntfs       SYSTEM
/dev/sda2        D492A1C692A1AE04                       ntfs       
/dev/sda3        70705369705334D6                       ntfs       Recovery
/dev/sda4        1A7D-CD7B                              vfat       HP_TOOLS
/dev/sdb1        2205-1EA6                              vfat       TOSHIBA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Kubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/kubuntu/Documents/bootinfoscript-061/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

 
```
i followed this guide on live boot to check if the boot is using BIOS:
[http://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios](http://askubuntu.com/questions/162564/how-can-i-tell-if-my-system-was-booted-as-efi-uefi-or-bios)


and it said BIOS so i guess bios it is.


so i would like to know what are other people's experiences regarding this partitioning?

---

### Post by darkod on 2012-11-01
I would create the set of recovery DVDs and delete the recovery partition. Or simply use the windows Backup tool and create an image of it as it is right now, you can restore the system from that and it's much better than the built in recovery partition.

The best and maybe only choice is to delete the recovery partition from another point: You will probably shrink sda2 to make space for ubuntu. So, even if you delete or convert to logical the HP_TOOLS (sda4) partition, you still will not be able to use the unallocated space created by shrinking sda2 because sda3 will be between them.

You have to think about that too, which partition will you shrink and where the unallocated space will be positioned.

---

### Post by Mark Phelps on 2012-11-01
Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by mastablasta on 2012-11-01
there is a tool that can change primary into secondary (logical) partition. which is what i was thinking to do with hp_tools.

so the partition that i will install ubuntu to has to be the last one on the disk or can be the space created by shrinking the 2nd partition?

The notebook doesn't have any DVD/CD drive. It's one of the ultraportable ones (well the cheap option). so i used 16GB USB drive to create restore disk using the tools provided by manufacturer. however there is no way of knowing if it will work on restore (well, besides doing the restore).

So far i did:
1 use a USB to create restore disk from restore partition (hopefully it works)

2. creating another image of the OS might be a good idea, though i would need an external drive or a new USB key for that. i still can't connect to XP mashcine. i can connect to linux. would it be OK to put the disk image on ext4 linux drive perhaps?

3. hp_tools has diagnostic tools as well as HP quickweb - quick web access (ironocally via their linux) that is available by pressing a special buton on the mashcine. they have a special programme to back up that partition, however some reported that theirs worked after they changed it to a logical drive (secondary?) and the quickweb even if they stuck it on windows partition. but the point is for the diagnostic tools to work they need to be on separate fat32 partition named hp_tools.


---
so another tip i picked up is that the data parittion (where the current OS is) can be turned into logical sicne OS boots of the (1st) system partition and then you can shrink it and create linux in the free space. anyone done that before?

---

### Post by darkod on 2012-11-01
Converting sda4 into logical won't help. As I said, just look at the physical positions of the partitions. Draw it if it's easier for you.

When you convert sda4 into logical it will still be at the end of the disk. When shrinking sda2 to create unallocated space, that space will be between sda2 and sda3, or sda2 and sda1 depending which end you shrink.

In any case it has no touch points with sda4 (because sda3 is in the way) so you can't create more logical partitions from the unallocated space since all logical partitions need to be grouped together.

---

### Post by oldfred on 2012-11-01
You would have to convert both the recovery & hptools to logical with fixparts and then include the space you make by using the Windows MMC to shrink the main Windows install.

While Windows only needs a primary to boot, we have seen where that boot partition gets corrupted and just copying/repairing main install then lets it boot. If logical that would not work, so I would leave main install as primary. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by jerome1232 on 2012-11-01
You can change your c: drive into a logical using miniPatition Tool, it works since that system partition has your boot files on it. That's how I did it on my netbook.

---

### Post by mastablasta on 2012-11-01
> **darkod said:**
> Converting sda4 into logical won't help. As I said, just look at the physical positions of the partitions. Draw it if it's easier for you.

When you convert sda4 into logical it will still be at the end of the disk. When shrinking sda2 to create unallocated space, that space will be between sda2 and sda3, or sda2 and sda1 depending which end you shrink.

In any case it has no touch points with sda4 (because sda3 is in the way) so you can't create more logical partitions from the unallocated space since all logical partitions need to be grouped together.

ah i thought  that i could then create new primary out of newly carved space form data parittion on which i could install linux.

Oldfred thanks for som additional links i already read a few of those before but some of them are new. will look into them. though it should be noted that what is on HP_tools partition changes. just like they reduced the "bloatware" and if i look at it maybe only one app is not really needed, while the rest of them are actually usefull and easy to use.

i've made recovery disk USB image but not repair disk. as i do not have any CD/DVD drive on this maschine. if oyu ask me the could have given the user a usb along with a computer that would retore it to original state. i mean they sell empty 32GB USB drives for 13 or 14EUR. i would gladly pay for them just to be sleeping at peace.

> **jerome1232 said:**
> You can change your c: drive into a logical using miniPatition Tool, it works since that system partition has your boot files on it. That's how I did it on my netbook.

so after creating C as logical what did you do next? carve space from it and partition it for linux? are there any other consequences of doing that? like not being able to restore/reinstall the OS to original state.
-----

Ok so why i even got lhis one... i mean the yhad so many models there and all of them were with no OS preinstalled which is great since here they always come with OS. but then after a lot of reading and investigating i ofund that only 2 fit my criteria. Lenovo and this HP. but lenovo had weaker battery and no bloetooth for same price. so i took HP which came with win7... too bad others didn't fit... either their GPU was bad, or battery weak, or they were overheating or not linux compatible...   if they had a better battery i would probably go with lenovo since the build of that one was better.

---

### Post by jerome1232 on 2012-11-03
> **mastablasta said:**
> 
so after creating C as logical what did you do next? carve space from it and partition it for linux? are there any other consequences of doing that? like not being able to restore/reinstall the OS to original state.



Yes, I shrunk the Windows drive and installed Ubuntu into the free space created in the logical partition. I haven't experienced any negative consequences. As for restoring etc... I haven't given the built in restore tools a try. I haven't had the need to try them. Perhaps when school lets out I can give it all a try, right now I can't have my netbook going down.

---

### Post by SeijiSensei on 2012-11-03
My daughter had a dv6t with the identical issue.  I detailed the steps I took to repartition the drive in [this post](http://ubuntuforums.org/showpost.php?p=11299287&postcount=5).  Warning: It ain't pretty.

---

### Post by mastablasta on 2012-11-04
Thanks both. It seems windows move to logical seems a goo dand easier idea to do (especially since the tools exists that tranforms it). 

i already made recovery disks and i will maybe borrow an external drive (if they still have some free space on it) to create disk image using redobackup.

then update BIOS with latest oupdate offered by HP updater.

transform windows partition into logical one (using that tool), shrink it and then install Kubuntu to newly made disk space. 

windows should work, linux should work, HP quickweb linux should work (maybe if it uses it's own boot otherwise via GRUB ), HP diagnostic tools should work, restore should work. 

now to find the time to do all this....

i already tested Kubutnu 64bit and it's superfast on the mashine, so can't wait to install it.. :-D

---

### Post by jerome1232 on 2012-11-04
quickweb does work on mine btw, I forgot about that, I hardly ever use it.

---

### Post by 23senick on 2012-11-04
I have a dm1 and faced the same issue.  I'm sure people here have given good solutions, here's how mine is configured, in case its of interest.  My configuration may not be ideal but it does work without issues.  Definitely agree you should make windows backup discs.  

sda4 is the extended partition. I think I copied HP tools to another memory and then used sda4 to create and re-size partitions. I figured the HP tools was the thing I could most afford to lose, and that there would always be ways to re-build if it went wrong (from recovery or downloads). 

Within the extended partition I have sda5, 6, 7 and 8.  These provide space for my main ubuntu system, linux-swap, and I re-copied HP tools in one of these. I used Puppy Linux gparted to re-partition and re-size. Best tip I found was always leaving gaps at start and finish of partitions to enable later re-sizing, though I guess that if you're thinking of playing with partitions you know this.  

One other observation - which wireless card do you have? Hope it isn't the Broadcom 4313. It's workable on mine but niggly, and there are many posts from fellow strugglers.

---

### Post by mastablasta on 2013-08-11
ok so after saving up some money i finally managed to buy an external disk to backup the data. i changed windows partition to logical and i did the repartitioning and this is the current situation: [http://ubuntuone.com/2UwHZPUf40LfmMCPVUtdMB](http://ubuntuone.com/2UwHZPUf40LfmMCPVUtdMB)

now my two questions to dual booters and others that already fiddled with this:

1. can i simply select use largest free space during install? i.e. does grub know where it has to go?
2. do you think it would be better to create another logical DATA partition formatted in NTFS and reduce the linux partition? i still intend to use windows 7 on this netbook but at the moment i do not know to what extent... i know i will need windows for online banking since xp will not be supported long and i can't afford security hole with online banking. i also do not know how well the battery will do in linux. i know it lasts very long in windows7.

basically i am looking for some advice and ideas.

EDIT: the wifi card is 03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

---

### Post by oldfred on 2013-08-11
Yes you can use auto install into free space. But it will just auto fill with sizes it chooses for swap & / (root). I prefer to set those sizes myself either in advance with gparted or during install.
I normally suggest the shard NTFS data partition. I still have the one from when I used XP, but will evenually move data to Linux partition as I do not boot XP anymore.

I do all my online banking with Firefox in Linux. I think it was New Zealand came out and said do not use Windows for any banking transactions. Any bank that forces you to only use Windows is a bank who's security would concern me.

---

### Post by mastablasta on 2013-08-11
hmm. yes might be better to create a separate data paritition and maybe reduce the linux partition. especially since i read sometimes windows can act strange after being accessed from linux. but we will see... it's all much easier now that i have a disk to backup to. 

the bank uses chips in USB and they need windows drivers to work (no android, no mac, no linux). so the way it all works is you need to insert the chip and eneter a password to access it in order to sign documents. it's only for the pro version for companies. and it is largest bank here and has probably the best suport for companies. i mean other companies also support it. so if you need accountignprogramme that will do everything online it will support this bank. another thing is they have offices everywhere, while some other banks really don't. and even when they do their working hours are even weirder than here. well let's see if bank will fail since they are the one causing economical troubles in my country (too many generous credits that were never repayed). so online banking is the least of their worries.

for home users it's not a problem as they use a normal certificate that you sign with password and a few other security measures when doing transfers to new account. that one should work fine in Linux and Firefox. and so far as i know it's security was breached once before via phishing. but they've added more security since then.

after this one is done - the old yellow got 2 GB more and it's time for a dual boot with winXP there... that one will be easier. as it's already have system data and something else partition that is basically 25 GB of emtpy disk space.

all i know is i've tried Kubuntu 13.04 on the netbook and it's so much faster than win7 and with most effects turned on and opensource drivers...

---

### Post by mastablasta on 2013-08-18
solved - finnaly. thoguh i had to manually create partitions. but that is the question for Kubuntu installer i guess... thanks all for help.

---

