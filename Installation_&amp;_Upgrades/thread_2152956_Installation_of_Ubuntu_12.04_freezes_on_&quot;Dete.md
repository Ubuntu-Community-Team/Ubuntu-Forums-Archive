---
title: "Installation of Ubuntu 12.04 freezes on &quot;Detecting Hardware&quot;"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by agentofcode on 2013-06-09
I've successfully installed Ubuntu 12.04 Desktop 64bit  replacing the win8 OS on my Toshiba Laptop. I did this by following [the directions on  UEFI]("https://help.ubuntu.com/community/UEFI") that is recommended by the forum. However I ran into an issue and attempted to reinstall the OS. I discovered a [thread with an identical issue]("http://ubuntuforums.org/showthread.php?t=2121615") but then it trails off into talking about RAID and my issue does not extend to that.

Anyway, after I was up and running with a fresh install of Ubuntu I only did two  things:
[LIST=1]
[*] I installed a driver for my wifi which successfully worked 
[*]Then because I had internet I was prompted to install a driver for my video  card, so I did 
[/LIST]
 #2 is where I believe all went downhill. Once the driver installed everything locked up so I tried rebooting. I couldn't get the OS to load. I decided no big  deal, I will just reinstall the OS and try again. However for some  reason I can not reinstall the OS.

**BIOS SET UP**
[LIST]
[*]Secure Boot [disabled] 
[*]Boot Mode [UEFI] 
[*]Boot Speed [Normal] 
[/LIST]
[B]WHAT I'VE TRIED
[/B]Boot from HDD[INDENT]**Result** - I get "checking media, fail...no bootable device -- please restart" (Since I attempted reinstalling the OS and it froze at "detecting hardware", I think the OS is now corrupt.) 
[/INDENT]
Boot from USB[INDENT]**Result** - I get the options as you would expect to Try..., Install..., Check... etc. (No matter if I decide to install using "Try Ubuntu with  out installing"  or "Install Ubuntu", the install freezes on "Detecting  Hardware")
[/INDENT]
Removed the slide show from the install process as the earlier mentioned thread suggested.[INDENT]**Result** - Freezes at "Detecting Hardware"
[/INDENT]
Tried reinstalling as CSM rather than UEFI.[INDENT]**Result** - Freezes at "Detecting Hardware"

[/INDENT]
[B]GOAL
[/B]I would just like to get the OS reinstalled, I will deal with and inquire about the video card driver once I get back to a functional machine, Thanks!

---

### Post by varunendra on 2013-06-09
[COLOR="#FF0000"]**DISCLAIMER :** I am no expert in the issue(s) being discussed here. So if anyone has got any other ideas, please share with us. Thanks ![/COLOR]
> **agentofcode said:**
> ....for some  reason I can not reinstall the OS.

**BIOS SET UP**
[LIST]
[*]Secure Boot [disabled] 
[*]**Boot Mode [[COLOR="#FF0000"]UEFI[/COLOR]]** 
[*]Boot Speed [Normal] 
[/LIST]
Is (was) Ubuntu the ONLY operating system (removing win8) on this laptop? If so, have you tried booting the live cd with Boot Mode = CSM? I see that you've mentioned that you tried installing in that mode, but did you also try the live session ? ("Try", not "Install"..)

I can only think of two things by the description of the problem (which seems to go beyond what I can think, but..) -

[INDENT]**1)** Try booting with advanced options of the live cd, as mentioned here : [https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)
Try the different "**F6**" options or a combination of them, and give "**nomodeset**" the first chance.

**2)** Try installing with the "Alternate" cd, which you can find here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)
I recommend [Ubuntu 12.04.2 alternate (64 bit)]("http://releases.ubuntu.com/12.04/ubuntu-12.04.2-alternate-amd64.iso.torrent"), via torrent to ensure integrity of the downloaded image.
If you don't already know, the alternate cd won't give you the option to "Try". It is an "install-only" cd, no live session.[/INDENT]

---

### Post by agentofcode on 2013-06-10
> **varunendra said:**
> 
Is (was) Ubuntu the ONLY operating system (removing win8) on this laptop? If so, have you tried booting the live cd with Boot Mode = CSM? I see that you've mentioned that you tried installing in that mode, but did you also try the live session ? ("Try", not "Install"..)

Ubuntu was dual boot with Win8, I established Ubuntu was working so I decided to replace Win8. So Ubuntu is now the only OS on this machine. I have also tried booting in CSM in the "Try without Install" and then actually tried to install but still no go.

I attempted the first solution you provided but the F keys aren't working for me...I can't even access them. I bypassed the alternate cd solution because my current image's integrity has been tested and checked out OK. Is there anything else the the alt. cd method that I may be unaware of?

---

### Post by agentofcode on 2013-06-10
I went extreme and tried repartitioning the drive Ubuntu is installed on. I created a 30gb partition for / and 8gb for swap and the rest for /home. I attempted installing to these fresh partitions but still freeze on "Detecting Hardware".

---

### Post by varunendra on 2013-06-10
> **agentofcode said:**
> F keys aren't working for me...I can't even access them.
That's too bad. I know you can manually add "nomodeset" option to the boot line, but not sure how to get that in live cd. In an installed system, you can get it by pressing "E" at the boot menu, can't say about live mode. The only way I know of to get the boot line in live mode involves the function keys :(.

> I bypassed the alternate cd solution because my current image's integrity has been tested and checked out OK. Is there anything else the the alt. cd method that I may be unaware of?
The live cd boots with many extra drivers and settings to provide you the live session. Whereas the alternate cd boots in minimal mode, with only those drivers that are absolutely necessary to put the OS on the drive with only necessary hardware detection and probing. This is especially useful when a system has graphics compatibility issue.

Since you doubt it all began with the installation of the proprietary graphics driver, I suspect that may be an alternate cd could help you go through installation, then you can start troubleshooting your graphics issue. But all this is just a guess of course. Still, you should give the alternate cd a chance. (and/or try resetting BIOS, then doing the necessary changes again in it).


**EDIT:**
> **agentofcode said:**
> I went extreme and tried repartitioning the drive Ubuntu is installed on. I created a 30gb partition for / and 8gb for swap and the rest for /home. I attempted installing to these fresh partitions but still freeze on "Detecting Hardware".
How did you do that??
Were you able to boot into a working session?

---

### Post by agentofcode on 2013-06-10
> **varunendra said:**
> 
How did you do that??
Were you able to boot into a working session?
I executed the "Install Ubuntu" from the live session and selected **Something Else** under "Installation Type". This allowed me to access the master boot record/main hard drive and create partitions and set up mount points. It still did not let me install but I thought that was some sort of progress. Atleast I can still see/access the main HDD with the file system. Just can't boot into it.

Here is a temporary dropbox folder I am using to share snapshots of what I did/doing. [https://www.dropbox.com/sh/yo94s8jsmozutlh/0lbPI0d_nO](https://www.dropbox.com/sh/yo94s8jsmozutlh/0lbPI0d_nO)

---

### Post by oldfred on 2013-06-10
Even if you have essentially erased drive, run this. More just to see what partitions, drives system shows. It may give some more info that just a partition list.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

What system is it? Is it an UltraBook?

---

### Post by varunendra on 2013-06-10
> **agentofcode said:**
> Here is a temporary dropbox folder I am using to share snapshots of what I did/doing. [https://www.dropbox.com/sh/yo94s8jsmozutlh/0lbPI0d_nO](https://www.dropbox.com/sh/yo94s8jsmozutlh/0lbPI0d_nO)

One quick error that I noticed in your screenshots is that you chose to install the boot loader in **/dev/sda[COLOR="#FF0000"]1[/COLOR]** (the partition) while it should have been **/dev/sda** only (the drive). Although this shouldn't be the root of your problem, so while trying that, please also post the boot-info summary as oldfred asked.

---

### Post by agentofcode on 2013-06-10
@oldfred - Your requests require internet which I do not have. That is [being dealt with in another post]("http://ubuntuforums.org/showthread.php?t=2152759") once I accomplish a clean install of the OS. Is there an alternative method of obtaining the repositories needed?

---

### Post by oldfred on 2013-06-10
@varunendra
If UEFI install it could be correct to install grub to sda1 if that is efi partition. But most Windows have efi partition as sda2? And installing grub2 to any NTFS partition corrupts Windows.

You can still download Boot-Repair CD and run it. Then copy its report to a flash drive and post. It may be too large to post to forum as it normally directly copies to pastebin.

You can also separately download bootinfoscript which is only the first part of the BootInfo report. And copy that report - results.txt. 

Bit of a workaround, it would be better to resolve Internet issues in Live installer first.
Are you just resolving Wireless issues. Almost all systems work with a wired connection and then may need wireless drivers downloaded as there seem to be too many versions to include in installer. 

       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by varunendra on 2013-06-10
> **oldfred said:**
> @varunendra
If UEFI install it could be correct to install grub to sda1 if that is efi partition. But most Windows have efi partition as sda2?
I didn't even think of that, although logically it makes perfect sense. Thank you sir for the info (these are things why EFI scares me.. :P)

@ agentofcode
> **oldfred said:**
> Bit of a workaround, it would be better to resolve Internet issues in Live installer first.
..should always be as easy as copying the firmware file I posted, and running the two commands suggested in [that post]("http://ubuntuforums.org/showthread.php?t=2152759&p=12683737#post12683737").

Your wired connection *should* work out-of box in 13.04, but not in 12.04 I'm afraid. But the wireless is easier, if required.

---

### Post by agentofcode on 2013-06-10
> **varunendra said:**
> 
..should always be as easy as copying the firmware file I posted, and running the two commands suggested in [that post]("http://ubuntuforums.org/showthread.php?t=2152759&p=12683737#post12683737").


Yeah, I've already attempted that. For some reason the command **sudo modprobe -rfv rtl8192ce** locks up the OS. I just figured it was a limitation of the live session.
> **varunendra said:**
> 
Your wired connection *should* work out-of box in 13.04, but not in 12.04 I'm afraid. But the wireless is easier, if required.

Should I just be using 13.04 now? The only reason I chose 12.04 is because of LTS.

---

### Post by agentofcode on 2013-06-10
> **oldfred said:**
> 
What system is it? Is it an UltraBook?
[URL="http://ubuntuforums.org/showthread.php?t=2152759"]
[/URL]Toshiba Satellite S855D-S5148

> **oldfred said:**
> 
Bit of a workaround, it would be better to resolve Internet issues in Live installer first.
Are you just resolving Wireless issues. Almost all systems work with a  wired connection and then may need wireless drivers downloaded as there  seem to be too many versions to include in installer.

I have no wired or wireless connection.

---

### Post by varunendra on 2013-06-10
> **agentofcode said:**
> Yeah, I've already attempted that. For some reason the command **sudo modprobe -rfv rtl8192ce** locks up the OS. I just figured it was a limitation of the live session.
Hmm.... don't know about that, maybe try without the -f (force) option to see if you get back any relevant error messages. That is : **sudo modprobe -rv rtl8192ce**

> Should I just be using 13.04 now? The only reason I chose 12.04 is because of LTS.
I wouldn't recommend that over LTS. The reason why it is *supposed* to work for your wired connection is because of its upgraded kernel, and you can use that kernel in 12.04 as well once it is installed.

But as of now, I think you can just download the Boot-Repair cd or the Secure-remix cd to get the current job done. If the output of the boot-info summary is too long, you can manually upload it to pastebin.ubuntu.com, then post its link here.

---

### Post by agentofcode on 2013-06-10
> **varunendra said:**
> try without the -f (force) option to see if you get back any relevant error messages. That is : **sudo modprobe -rv rtl8192ce**
Still froze

When I get more than a few minutes I will work on the other requests.

---

### Post by varunendra on 2013-06-10
> **agentofcode said:**
> Still froze

When I get more than a few minutes I will work on the other requests.

Probably we should just focus on generating the boot-info summary somehow. It may help you fix the installation issue and then the rest of things can be dealt with much more flexibility.

---

### Post by agentofcode on 2013-06-10
**bootinfoscript** Results
```

 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........S.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1480144 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       194,559       192,512 EFI System partition
/dev/sda2         194,560 1,937,864,703 1,937,670,144 Data partition (Windows/Linux)
/dev/sda3   1,937,864,704 1,953,523,711    15,659,008 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
16 heads, 32 sectors/track, 7644 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     3,913,727     3,905,664   b W95 FAT32


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          8,064    15,646,719    15,638,656   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1322-F157                              vfat       
/dev/sda2        ae4c8f33-8ca2-4517-8fed-a7eda3a3b1e8   ext4       
/dev/sda3        fd6a7ba5-a5ed-4647-ae70-bc63745c31d9   swap       
/dev/sdb1        CA7F-4143                              vfat       UBUNTU
/dev/sdd1        2036CBB236CB86EE                       ntfs       SPARE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /media/SPARE             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=ae4c8f33-8ca2-4517-8fed-a7eda3a3b1e8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=1322-F157  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=fd6a7ba5-a5ed-4647-ae70-bc63745c31d9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/vmlinuz-3.5.0-23-generic                  1
               =                boot/vmlinuz-3.5.0-23-generic.efi.signed       1
               =                vmlinuz                                        1

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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2013-06-10
It does not look like grub installed, so you cannot boot.  You have an efi partition for booting with UEFI mode but it is not showing any grub files and there is no grub.cfg to boot from. 
There is no core.img if booting in BIOS mode, but that would also require a bios_grub partition.

It used to be with some system a very large (over 500) GB / (root) partition caused grub issues. I have seen that with UEFI, but generally better to have a 25GB / (root) partition and a large /home or my preference - data partition(s).

---

### Post by varunendra on 2013-06-10
> **agentofcode said:**
> **bootinfoscript** Results
```

Disk /dev/**sdd: 8011 MB**, 8011120640 bytes
**41 heads, 41 sectors/track**, 9307 cylinders, total 15646720 sectors
....
/dev/sdd1    *          8,064    15,646,719    15,638,656   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

**/dev/sdd1        2036CBB236CB86EE                       ntfs       SPARE**

```

Do you recognize this 8GB drive **/dev/sdd** ? Is it an external removable drive or an inbuilt ssd?

I'd leave this for oldfred because my expertise in UEFI setup can almost guarantee a further messed up system.

**EDIT:**
Oops!
Late, as usual, I am.. sitting aside and watching the game now.

---

### Post by agentofcode on 2013-06-10
> **varunendra said:**
> Do you recognize this 8GB drive **/dev/sdd** ?
Yes, its the USB drive I had in to copy over the results to.

---

### Post by agentofcode on 2013-06-10
> **oldfred said:**
> It does not look like grub installed, so you cannot boot.  You have an efi partition for booting with UEFI mode but it is not showing any grub files and there is no grub.cfg to boot from. 
There is no core.img if booting in BIOS mode, but that would also require a bios_grub partition.

It used to be with some system a very large (over 500) GB / (root) partition caused grub issues. I have seen that with UEFI, but generally better to have a 25GB / (root) partition and a large /home or my preference - data partition(s).

So why is it not as simple and wiping the hdd clean and recreating the partitions and installing according to how you said? I have tried this but it won't let me reinstall. I attempted a 30gb / and 8gb swap with everything else in /home. But it would not install.

Should I move on to the **boot repair portion** of your recommendations?

---

### Post by redmk2 on 2013-06-10
> **agentofcode said:**
> So why is it not as simple and wiping the hdd clean and recreating the partitions and installing according to how you said? I have tried this but it won't let me reinstall. I attempted a 30gb / and 8gb swap with everything else in /home. But it would not install.

I'm not trying to butt in to AoC's thread here, but I wounder why there is a partition with this```
/dev/sda1           2,048       194,559       192,512 EFI System partition
```

AoC said he partitioned the laptop HDD as 30GB for / and 8GB for *swap* and the rest (960 GB?) for* /home*.  Did the installer make a smaller partition for the EFI?  Does this mean maybe AoC should NOT have partitioned the drive at all?  just let the installer do it?  How do you create a partition for* /home* then.  I saw a reference to the *root *partition usually ending up on sda2; Is this because of EFI?  Is there a selection for UEFI partition and if so how big should it be?

I'm looking to create a workstation with the latest chipset and UEFI always comes into the picture.  That's my reason for all the questions.  I've never dealt with UEFI before.

---

### Post by oldfred on 2013-06-10
UEFI is a lot different than BIOS. With BIOS computers use BIOS to enumerate hardware & it writes  that info for system to use and jumps to MBR to boot.
UEFI enumerate differently and loads boot code from an efi partition which can be a lot larger than the MBR and is like multiple MBRs as it can have many boot loaders in one efi partition.
IF you are booting with UEFI, system must have efi partition and drive is gpt partitioned.

---

### Post by redmk2 on 2013-06-10
> **oldfred said:**
> UEFI is a lot different than BIOS. With BIOS computers use BIOS to enumerate hardware & it writes  that info for system to use and jumps to MBR to boot.
UEFI enumerate differently and loads boot code from an efi partition which can be a lot larger than the MBR and is like multiple MBRs as it can have many boot loaders in one efi partition.
IF you are booting with UEFI, system must have efi partition and drive is gpt partitioned.

How big should I make the efi partition?

---

### Post by oldfred on 2013-06-10
Most cases it does not have to be large. I think Windows default is only 100MB, but I normally suggest 250 to 300MB if multi-booting. 
It is the first partition so it is difficult to expand later. And you may in the future use other features. 

This suggests 100 to 250MB.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by redmk2 on 2013-06-10
Thanks @oldfred.  That helps a lot.

---

### Post by agentofcode on 2013-06-11
> **varunendra said:**
> Your wired connection *should* work out-of box in 13.04, but not in 12.04 I'm afraid. But the wireless is easier, if required.
I tried v13.04. No problems at ALL. WiFi worked right away as you expected. During the  install process it downloaded all the packages, got past the dreaded  "Detecting Hardware", installed grub and now I am up and running. I got to the point where I don't mind if its not LTS. Having a non LTS for a short period of time is better than not having an OS at all, right?


**P.S.**

I  wonder if the install process/detecting issues has anything to do with  no internet? I noticed this go around having internet the install  actually took time and downloaded the packages before moving on. In  12.04 with out the internet it just zipped right past that part of the  install straight to "Detecting Hardware" and freezing. I also noticed grub is installed after the hardware is detected. This explains why I didn't have grub installed as oldfred pointed out.

---

### Post by varunendra on 2013-06-12
Congratulations!! :)
> **agentofcode said:**
> I  wonder if the install process/detecting issues has anything to do with  no internet? I noticed this go around having internet the install  actually took time and downloaded the packages before moving on. In  12.04 with out the internet it just zipped right past that part of the  install straight to "Detecting Hardware" and freezing.
Could be the packages that are available only for the newer kernel that 13.04 comes with. You should have been able to get all the hardware support that 13.04 offers in 12.04 as well, after installing the "linux-generic-lts-raring" package in it.

Maybe you can just overwrite the current installation with 12.04 when and if needed.

But since 'installing' itself was proving to be the biggest hurdle, and now you have a working system, I guess it is best to leave it as it is.

---

