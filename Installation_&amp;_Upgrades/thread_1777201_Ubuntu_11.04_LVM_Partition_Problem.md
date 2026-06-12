---
title: "Ubuntu 11.04 LVM Partition Problem"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by syoung27 on 2011-06-07
So this morning i booted Xubuntu in an effort to replace Fedora 15, basically just getting a feel for all sorts of different distros. 
although it was slightly more confusing that the others i've tried on install because i had to manually configure partitions, and prompt didn't give a description really of which was which, so i took a shot in the dark at which was fedora to overwrite, and hoped i didn't remove win7
so all went well, but it appears Fedora is still in my system, using roughly 50GB still, it won't boot. but it is in the boot menu, and i can see it from Xubuntu..
Can i remove this to add that bit of space to my new distro?
or would i have to reinstall xubuntu
ideas!?
Seems to be mostly just old folders and such, but it's being shown as a device.

I don't see it in Gparted i don't think..

---

### Post by Quackers on 2011-06-07
Welcome to UF :-)
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by syoung27 on 2011-06-07
so i've been trying and trying, even when i run as root, if it doesn't give me a directory issue it tells me permission denied

---

### Post by Quackers on 2011-06-07
Have you downloaded the zip file? To what directory? Have you extracted that zip file?

---

### Post by syoung27 on 2011-06-07
yeah i downloaded the zip file to home/spencer/downloads
extracted into the same folder. 
i'll do some combinations and get the different errors, put a pic up here.

---

### Post by Quackers on 2011-06-07
In the terminal do this please ```
cd Downloads/boot_info_script060
```
Note the capital D in Downloads
then this ```
sudo bash boot_info_script.sh
```

---

### Post by syoung27 on 2011-06-07
you can see what's happening in the explorer panel, also im not used to having 524mb filesystem...never saw it anyways in zorin or fedora.
i feel like i edited the swap space and created that or something. has all linux items in it it looks like. some with large x's

---

### Post by Quackers on 2011-06-07
Please close your terminal window then open up another.
Then copy/paste the above commands one at a time, pressing enter after each one.

---

### Post by 23dornot23d on 2011-06-07
The first command should just be ....

cd Downloads

Just Change directory ..... in to Downloads ..... 
( the filename included after it is causing a problem for the user )
The screenshot in the background shows the file is there ....

                                                    Attached Thumbnails                                           [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194498&stc=1&thumb=1&d=1307488896[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=194498&d=1307488896")                        
                                                                                                    
once in the directory do ....
 
**sudo bash boot_info_script.sh**

Example I just did it

```

keith@keith-Aspire-7730ZG:~$ cd Downloads
keith@keith-Aspire-7730ZG:~/Downloads$ sudo bash boot_info_script.sh
[sudo] password for keith: 

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb4 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdb7 for information... 
Searching sdb8 for information... 
Searching sdb9 for information... 
Searching sdb10 for information... 
Searching sdb11 for information... 
Searching sdb12 for information... 
Searching sdb13 for information... 
Searching sdb14 for information... 

Finished. The results are in the file "RESULTS1.txt"
located in "/home/keith/Downloads/".



```

---

### Post by syoung27 on 2011-06-07
correct?

---

### Post by syoung27 on 2011-06-07
sorry, trying not to flood lol

---

### Post by Quackers on 2011-06-07
Lol, oh dear.
Please post a screenshot of the contents of your Downloads folder

---

### Post by syoung27 on 2011-06-07
look in the background..

---

### Post by Quackers on 2011-06-07
I see the problem now :-)
You haven't extracted the folder. Right-click on the .zip file and from the context menu select "extract here" then try those commands again please :-)

---

### Post by syoung27 on 2011-06-07
haha yes you are correct! oops.
greatly appreciating the help. linux rocks my socks so far, runs smooth and much faster than win7.  just gotta learn the quirks!

---

### Post by Quackers on 2011-06-07
Your Results.txt in code tags.
I'll be reading it and will get back to you :-)
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (vg_spencerltp-lv_home)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda6: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

vg_spencerltp-lv_swap': ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

vg_spencerltp-lv_home': ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg_spencerltp-lv_root': ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    29,362,175    29,360,128  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     29,362,176    29,566,975       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          29,566,976   707,346,055   677,779,080   7 NTFS / exFAT / HPFS
/dev/sda4         707,348,478 1,250,263,039   542,914,562   5 Extended
/dev/sda5         707,348,480   708,372,479     1,024,000  83 Linux
/dev/sda6         708,374,528 1,250,263,039   541,888,512  8e Linux LVM


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/vg_spencerltp-lv_home 130ef273-e7a9-40d3-8784-0c96552cd9e0   ext2       
/dev/mapper/vg_spencerltp-lv_root 54c371cb-77af-4953-b45e-f77009b2f2f4   ext4       _Fedora-15-x86_6
/dev/sda1        EC3829C338298DA0                       ntfs       PQSERVICE
/dev/sda2        187C2A1D7C29F662                       ntfs       SYSTEM RESERVED
/dev/sda3        8E942B90942B7A3B                       ntfs       Acer
/dev/sda5        162e98b4-7c44-4b6f-9f75-37e822448e1d   ext4       
/dev/sda6        ManT9C-RJcj-JctU-25SI-kQAI-RhpU-3qdE7g LVM2_member 
/dev/sdc1        A0D44914D448EDDA                       ntfs       Iomega HDD

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
vg_spencerltp-lv_home
vg_spencerltp-lv_root
vg_spencerltp-lv_swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg_spencerltp-lv_home /                        ext2       (rw,errors=remount-ro)
/dev/sda5        /media/162e98b4-7c44-4b6f-9f75-37e822448e1d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda5/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_spencerltp-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.38.6-27.fc15.x86_64)
	root (hd0,4)
	kernel /vmlinuz-2.6.38.6-27.fc15.x86_64 ro root=/dev/mapper/vg_spencerltp-lv_root rd_LVM_LV=vg_spencerltp/lv_root rd_LVM_LV=vg_spencerltp/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-27.fc15.x86_64.img
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
	root (hd0,4)
	kernel /vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=/dev/mapper/vg_spencerltp-lv_root rd_LVM_LV=vg_spencerltp/lv_root rd_LVM_LV=vg_spencerltp/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Other
	rootnoverify (hd0,1)
	chainloader +1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 337.312013626 = 362.186016768  grub/grub.conf                                 2
 337.312013626 = 362.186016768  grub/menu.lst                                  2
 337.301151276 = 362.174353408  grub/stage2                                    1
 337.321214676 = 362.195896320  initramfs-2.6.38.6-26.rc1.fc15.x86_64.img      3
 337.342451096 = 362.218698752  initramfs-2.6.38.6-27.fc15.x86_64.img          2
 337.300637245 = 362.173801472  initrd-plymouth.img                            1
 337.307314873 = 362.180971520  vmlinuz-2.6.38.6-26.rc1.fc15.x86_64            2
 337.327101707 = 362.202217472  vmlinuz-2.6.38.6-27.fc15.x86_64                1

================= sda5: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 337.548756599 = 362.440217600  extlinux/cat.c32                               1
 337.548995018 = 362.440473600  extlinux/chain.c32                             1
 337.548996925 = 362.440475648  extlinux/cmd.c32                               1
 337.548040390 = 362.439448576  extlinux/config.c32                            1
 337.548897743 = 362.440369152  extlinux/cpuid.c32                             1
 337.548856735 = 362.440325120  extlinux/cpuidtest.c32                         1
 337.548975945 = 362.440453120  extlinux/disk.c32                              1
 337.548962593 = 362.440438784  extlinux/dmitest.c32                           1
 337.548408508 = 362.439843840  extlinux/elf.c32                               1
 337.548928261 = 362.440401920  extlinux/ethersel.c32                          1
 337.548744202 = 362.440204288  extlinux/gfxboot.c32                           1
 337.548892021 = 362.440363008  extlinux/gpxecmd.c32                           1
 337.548666954 = 362.440121344  extlinux/hdt.c32                               1
 337.548723221 = 362.440181760  extlinux/host.c32                              1
 337.548899651 = 362.440371200  extlinux/ifcpu64.c32                           1
 337.548056602 = 362.439465984  extlinux/ifcpu.c32                             1
 337.548689842 = 362.440145920  extlinux/ifplop.c32                            1
 337.547859192 = 362.439254016  extlinux/kbdmap.c32                            1
 337.547876358 = 362.439272448  extlinux/linux.c32                             1
 337.548154831 = 362.439571456  extlinux/ls.c32                                1
 337.548380852 = 362.439814144  extlinux/lua.c32                               1
 337.548145294 = 362.439561216  extlinux/mboot.c32                             1
 337.548862457 = 362.440331264  extlinux/meminfo.c32                           1
 337.548813820 = 362.440279040  extlinux/menu.c32                              1
 337.548845291 = 362.440312832  extlinux/pcitest.c32                           1
 337.548111916 = 362.439525376  extlinux/pmload.c32                            1
 337.548098564 = 362.439511040  extlinux/pwd.c32                               1
 337.548963547 = 362.440439808  extlinux/reboot.c32                            1
 337.548686981 = 362.440142848  extlinux/rosh.c32                              1
 337.548889160 = 362.440359936  extlinux/sanboot.c32                           1
 337.548715591 = 362.440173568  extlinux/sdi.c32                               1
 337.548096657 = 362.439508992  extlinux/sysdump.c32                           1
 337.548749924 = 362.440210432  extlinux/vesainfo.c32                          1
 337.548034668 = 362.439442432  extlinux/vesamenu.c32                          1
 337.548970222 = 362.440446976  extlinux/vpdtest.c32                           1
 337.548718452 = 362.440176640  extlinux/whichsys.c32                          1

============== sda5: Version of COM32(R) files used by Syslinux: ===============

 extlinux/cat.c32                   :  COM32R module (v4.xx)
 extlinux/chain.c32                 :  COM32R module (v4.xx)
 extlinux/cmd.c32                   :  COM32R module (v4.xx)
 extlinux/config.c32                :  COM32R module (v4.xx)
 extlinux/cpuid.c32                 :  COM32R module (v4.xx)
 extlinux/cpuidtest.c32             :  COM32R module (v4.xx)
 extlinux/disk.c32                  :  COM32R module (v4.xx)
 extlinux/dmitest.c32               :  COM32R module (v4.xx)
 extlinux/elf.c32                   :  COM32R module (v4.xx)
 extlinux/ethersel.c32              :  COM32R module (v4.xx)
 extlinux/gfxboot.c32               :  COM32R module (v4.xx)
 extlinux/gpxecmd.c32               :  COM32R module (v4.xx)
 extlinux/hdt.c32                   :  COM32R module (v4.xx)
 extlinux/host.c32                  :  COM32R module (v4.xx)
 extlinux/ifcpu64.c32               :  COM32R module (v4.xx)
 extlinux/ifcpu.c32                 :  COM32R module (v4.xx)
 extlinux/ifplop.c32                :  COM32R module (v4.xx)
 extlinux/kbdmap.c32                :  COM32R module (v4.xx)
 extlinux/linux.c32                 :  COM32R module (v4.xx)
 extlinux/ls.c32                    :  COM32R module (v4.xx)
 extlinux/lua.c32                   :  COM32R module (v4.xx)
 extlinux/mboot.c32                 :  COM32R module (v4.xx)
 extlinux/meminfo.c32               :  COM32R module (v4.xx)
 extlinux/menu.c32                  :  COM32R module (v4.xx)
 extlinux/pcitest.c32               :  COM32R module (v4.xx)
 extlinux/pmload.c32                :  COM32R module (v4.xx)
 extlinux/pwd.c32                   :  COM32R module (v4.xx)
 extlinux/reboot.c32                :  COM32R module (v4.xx)
 extlinux/rosh.c32                  :  COM32R module (v4.xx)
 extlinux/sanboot.c32               :  COM32R module (v4.xx)
 extlinux/sdi.c32                   :  COM32R module (v4.xx)
 extlinux/sysdump.c32               :  COM32R module (v4.xx)
 extlinux/vesainfo.c32              :  COM32R module (v4.xx)
 extlinux/vesamenu.c32              :  COM32R module (v4.xx)
 extlinux/vpdtest.c32               :  COM32R module (v4.xx)
 extlinux/whichsys.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on vg_spencerltp-lv_swap'


Unknown BootLoader on vg_spencerltp-lv_home'


Unknown BootLoader on vg_spencerltp-lv_root'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_spencerltp-lv_swap': No such file or directory
hexdump: /dev/mapper/vg_spencerltp-lv_swap': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_spencerltp-lv_home': No such file or directory
hexdump: /dev/mapper/vg_spencerltp-lv_home': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/vg_spencerltp-lv_root': No such file or directory
hexdump: /dev/mapper/vg_spencerltp-lv_root': No such file or directory

```

---

### Post by Quackers on 2011-06-07
Sadly as you are using LVM I am unqualified to comment on what may be wrong. I have no experience at all with LVM. I can see a couple of inconsistencies but would not like to suggest a course of action.
Hopefully somebody with LVM experience will come along and give you some advice.
I'm sorry I can't be more helpful to you.

Windows 7 still looks to be there though :-)

---

### Post by syoung27 on 2011-06-07
yup windows is there i booted it.
maybe i should reinstall ubuntu all together to fix the partitions? although that's what got me here in the first place so ill wait and keep browsing:p 
but if you're still in this thread quick question. 
i have an old compaq, ~1ghz, 512, nothing speciall..old and heavy.
i wanted to do a full linux distro to essentially use it as a media server. what would be your pick?  i've only been using linux all together for a few weeks :)

---

### Post by Quackers on 2011-06-07
Is there a particular reason that you are using LVM?
The compaq may be enough to run Ubuntu, certainly Lubuntu and maybe others too.
Others may have better suggestions too.

---

### Post by syoung27 on 2011-06-07
in all honesty i'm not familiar with what lvm is. i see it in the log but i didn't know there's an option.
brief description? i can switch if that helps! lol just help the process..
i use linux because i have no need for windows anymore; it bores me, it slows me.
wanted to learn a new os without buying a mac lol

---

### Post by Quackers on 2011-06-07
I really don't know enough about LVM to comment. Not even to delete it. All I know is that it's some kind of partitioning scheme that allows some flexibility to expand partitions. That's it!  Maybe if you google around about it you can find out more until somebody with the proper experience comes along :-)
I would say that it is a good idea to make sure you have Windows backed up and that you have recovery options other than the recovery partition (ie make recovery dvd's). You should also have a Windows repair disc too. You can make them easily enough in Windows.

Maybe you could change the title of the thread (using Go advanced) to include a reference to LVM so others can see it

---

### Post by syoung27 on 2011-06-07
oh when i downloaded ubuntu i selected the lvm option? lol

---

### Post by 23dornot23d on 2011-06-07
Check this thread out [LINK]("http://ubuntuforums.org/showpost.php?p=10895054&postcount=7")

I have just had a google around and LVM seems to be a pain to remove easily ....
without re-installing Fedora to do it as from what I am reading Ubuntu does not have
a lot of support for this .....

It may need more than the [COLOR=Red]**[10 minutes I have just had looking around]("http://www.google.com/search?client=ubuntu&channel=fs&q=lowhy+bash+execute&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=gparted+remove+format+lvm&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a91b69f6bd0a7737&biw=1018&bih=577")**[/COLOR] ...... :confused:

I too never use it ......

[oldfred]("http://ubuntuforums.org/member.php?u=852711") and [srs5694]("http://ubuntuforums.org/member.php?u=1032238")

seem pretty clued up on it though ..... might be worth talking to one of them .....

---

### Post by Quackers on 2011-06-07
Please boot from the Ubuntu live cd/usb and select "try Ubuntu". When the desktop loads go to System > Administration > gparted.
Please post screenshots for /dev/sda and for /dev/mapper. These options should be available from the little box near top right of the window by clicking on the little arrow next to /dev/sda

Also see above post :-)

---

### Post by syoung27 on 2011-06-07
so from the boot disk i had downloaded and burned, it doesn't give me a try option.
im using Ubuntu 11.04 server specifically, which could account for the LVM...
i have install ubuntu or install ubuntu enterprise cloud.

also i should mention on the boot screen i have fedora and it specifies to root 
next boot i will write down the specifics...
vg lm are in the lines, they aren't in any others, same with root.
so until then ill message those folks. thanks again guys!

---

### Post by Quackers on 2011-06-07
Yes, no live desktop with server edition.
There's probably no need to pm them. If you change the title of your thread to include LVM they may appear on their own :-)  But only if they're online!

---

### Post by syoung27 on 2011-06-07
edit title

---

### Post by Quackers on 2011-06-07
Hmm, that happened to me the other day :-)
If you click on the report abuse icon on the left under your Beans count and in the new window type a request to the forum moderators to change your thread title to include LVM, that should do it.

---

### Post by syoung27 on 2011-06-07
lol ok done

---

### Post by Quackers on 2011-06-07
Very nice too :-)
I don't think the two users are online tonight unfortunately.
Don't despair though, I'm sure they'll see the thread :-)

---

### Post by syoung27 on 2011-06-07
ohya im looking forward to this site, i've been on [www.thecomputermechanics.con](www.thecomputermechanics.con) for such a long time, lots of help just from one city mostly so this is sweet.
im not sure if you guys know but may as well refer you to the other problem im having lol if you're kickin around for a while.
[http://ubuntuforums.org/showthread.php?t=1777443](http://ubuntuforums.org/showthread.php?t=1777443)

---

### Post by Quackers on 2011-06-07
Sorry but that's not an area I've needed to delve into. I've been luckier than some it seems.
There are many knowledgable people here though :-)

---

### Post by oldfred on 2011-06-07
I do not know LVM, sorry.

I have saved a few links though as usual.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

The boot script will parse LVM if this is installed.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)

---

### Post by Quackers on 2011-06-08
Thanks very much for your invaluable saved links oldfred :-)

---

### Post by syoung27 on 2011-06-08
crap...any of you folks think it would work if i reboot ubuntu and partition the drives all over again? ill just need help with how the screen works a tad with all the device properties and selections. assuming you guys know what i mean and have had similar things since you have ubuntu lol, so i possibly avoid this lvm fedora thing

---

### Post by syoung27 on 2011-06-08
"Download Parted Magic [it contains Gparted] and burn the iso image to a CD.
Boot to the live CD. If you choose the defaults during boot of Parted Magic it will eject the CD and run from RAM. 
After it boots use Gparted to remove the unwanted partitions. 
Windows will be clearly indicated as ntfs so you should be able to delete all the other partitions easily. 
LVM is a Logical Volume Management system and it contains file systems like ext4 inside it.

After this Windows will not boot yet. When you then install your Linux of choice the grub loader will find Windows."

from a user on thecomputermechanics


Well I'm about to give it a shot! I'll be back with an answer in a while.

---

### Post by syoung27 on 2011-06-08
success, went very easily with gparted, deleted ubuntu and lvm etc..left windows alone with lots of unallocated space, rebooted ubuntu 11.04 with no lvm, lots of space again:)
unfortunately i still suffer from terrible usb speeds with linux.

---

### Post by Quackers on 2011-06-08
Ah, you bit the bullet :-)  Sounds like a nice result. Well done!
If I see anything about poor USB speeds I'll cone back :-)

---

### Post by 23dornot23d on 2011-06-08
> 
unfortunately i still suffer from terrible usb speeds with linux.
Me too ..... 1 terrabyte ones are slow ..... especially my Iomega drive ....

But the 500 Gig Seagates and below seem to be a lot better - speed wise .....

Glad to see you got sorted out though .....was reading some real horror stories 
about removing lvm(2)

---

### Post by syoung27 on 2011-06-08
yeah we probably have the same iomega tb drive lol, 59.99 at future shop a while back, hard to resist.
actually after rebooting ubuntu i copied roughly 90gb of music from my external back onto linux, and took less than an hour i say. so something improved, ill try large single files later.
now im having problems with my usb speakers. ****

---

