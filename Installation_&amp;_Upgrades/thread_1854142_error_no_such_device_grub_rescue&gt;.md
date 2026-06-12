---
title: "error: no such device: grub rescue&gt;"
date: 2011-10-03
forum: Installation &amp; Upgrades
---

### Post by MNBill on 2011-10-03
I tried to install ubuntu alongside Windows 7 on my computer this afternoon. Now I cannot boot any operating system anymore, unfortunately.

When trying to boot, the following error message appears on my display:

error: no such device: c4d250ab-b08f-4a9a-84b9-344d9ea61e03.
grub rescue>

The following steps led to this problem:

1) First try with wubi

- I made a new partition of 100MB, using the Windows 7 system tools. I gave this partition the name U: and restarted the computer twice
- I then downloaded Wubi from ubuntu.com/download and tried to install ubuntu 11.04 on this new partition U:
- Installing worked well, but after rebooting an error message appeared (after ubuntu sucessfully booted) and told me "no root file system is defined". When I clicked on "okay", the message just appeared again and did not let me continue.
- Thus I un-installed ubuntu 11.04 again in Windows 7 (using the Windows 7 system tools to un-install programs)

2) Second try

- In a second attempt I first deleted the before newly made partition (i.e. I told windows to let this space free, can't remember how that was called actually, this partition was un-used now however, and had no letter anymore) and followed the following step-by-step explanation how to install ubuntu:
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)
- The installation worked well, then it told me to re-boot to finish the installation
- My computer did not shut down properly but stopped doing anything while shutting down. After 20 minutes I manually turned it off. After rebooting, the error message which I posted above, appeared.

3) Try to rescue

- I then booted ubuntu from my USB stick and tried to re-install ubuntu from there
- The installation worked properly again (this time I chose to "install ubuntu alongside Windows 7" instead of the bottom option, where you can assign space on your hard disk manually)
- At the end of the installation it told me to re-boot my computer
- The computer did not shut down
- When manually rebooting -> the same problem as before.

Can anybody help me, please? Thank you very much!!

---

### Post by bcbc on 2011-10-03
The first step is to boot the Ubuntu USB and select "Try it" - boot to the desktop and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by Blasphemist on 2011-10-03
From the grub rescue> prompt, type this command.
```
ls
```
You should see some listing of drive and partition in this format. hd0,3 would translate to the first hard drive and partition 3. Note the hard drive numbering starts at 0 but the partition numbering starts at 1.

Then follow these commands. If you get any errors or have any questions, just post them.
> 1. set prefix=(hdX,Y)/boot/grub
Use the values determined earlier. Example: If the Ubuntu system is on sda5, enter: set prefix=(hd0,5)/boot/grub
2.* set root=(hdX,Y)
Example: set root=(hd0,5)
3. insmod normal
Attempt to load the normal module.
4. normal
Activate the normal module. If successful, the GRUB 2 menu may appear.
5. set
(Optional) Review the current settings.
6. ls /boot
(Optional) Check for a vmlinuz and a initrd.img entry.
7. insmod linux
An error message usually means the path is incorrect.
8.* linux /vmlinuz root=/dev/sdXY ro
Selects the latest kernel. Example: linux /vmlinuz root=/dev/sda5 ro
9. initrd /initrd.img
Selects the latest initrd image.
10. boot

This should bring up grub. I don't think that the installation of grub finished and that is where it hung. See what entries you have and try to boot ubuntu. Then in ubuntu install boot-repair from the software center. Have it reinstall grub. This could be done manually but boot repair would be easier and provide a summary you could post the url for if you have further questions.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If any of this doesn't go as expected, just post the details.

---

### Post by MNBill on 2011-10-03
Hi bcbc, thanks for your help.

These are the results of the bootinfoscript**:**

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_dffiejdfai_ARRAY1 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 5 for /boot/grub.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 2112440 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

isw_dffiejdfai_ARRAY11: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_dffiejdfai_ARRAY12: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dffiejdfai_ARRAY13: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    31,250,015    31,249,953   b W95 FAT32


Drive: isw_dffiejdfai_ARRAY1 _____________________________________________________________________

Disk /dev/mapper/isw_dffiejdfai_ARRAY1: 2000.4 GB, 2000405397504 bytes
255 heads, 63 sectors/track, 243202 cylinders, total 3907041792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dffiejdfai_ARRAY11                 63        80,324        80,262  de Dell Utility
/dev/mapper/isw_dffiejdfai_ARRAY12   *         81,920    27,865,087    27,783,168   7 NTFS / exFAT / HPFS
/dev/mapper/isw_dffiejdfai_ARRAY13         27,865,088 3,702,237,183 3,674,372,096   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dffiejdfai_ARRAY1p1 5450-4444                              vfat       DellUtility
/dev/mapper/isw_dffiejdfai_ARRAY1p2 82DA4512DA4503BF                       ntfs       RECOVERY
/dev/mapper/isw_dffiejdfai_ARRAY1p3 D4F84A64F84A44C8                       ntfs       OS
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        64ED-5B1A                              vfat       PENDRIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dffiejdfai_ARRAY1
isw_dffiejdfai_ARRAY1p1
isw_dffiejdfai_ARRAY1p2
isw_dffiejdfai_ARRAY1p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_dffiejdfai_ARRAY11


Unknown BootLoader on isw_dffiejdfai_ARRAY12


Unknown BootLoader on isw_dffiejdfai_ARRAY13



========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY11: No such file or directory
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY11: No such file or directory
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY12: No such file or directory
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY12: No such file or directory
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY13: No such file or directory
hexdump: /dev/mapper/isw_dffiejdfai_ARRAY13: No such file or directory

---

### Post by MNBill on 2011-10-03
Hi Blasphemist, thanks for your help, too!

Typing "ls" gives me the following line:

(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

Since I installed, un-installed and re-installed ubuntu, I have no clue on which partition my actual installation is, sorry. Can I find that out somehow?

Thanks a lot!

---

### Post by bcbc on 2011-10-03
What sort of raid are you running? Was the error you got during the wubi install "no root file system defined"?

---

### Post by MNBill on 2011-10-03
- What's the meaning of "raid"? Sorry, I'm a total noob in this... :)

- Yes, exactly, the error was "no root file system is defined"

---

### Post by Blasphemist on 2011-10-03
These commands should let you see what partition you should use.
> ls (hdX,Y)/
This result should include vmlinuz and initrd.img
ls (hdX,Y)/boot
This result should include the specific kernel and initrd.img files
ls (hdX,Y)/boot/grub
Included should be numerous *.mod files and the grub.cfg file, as well as various *.img files.

This will determine which partition has the grub files. You need to use hd0 and try 1, 2 and 3 for the partitions. Example-
```
ls (hd0,1)/
```
ls is like the windows dir command.

---

### Post by bcbc on 2011-10-03
> **MNBill said:**
> - What's the meaning of "raid"? Sorry, I'm a total noob in this... :)

- Yes, exactly, the error was "no root file system is defined"
Well... it looks like your computer came with a fakeraid setup - and some of these are not supported by Ubuntu e.g. Raid 0 or Raid 10 (1+0). I don't know a whole lot about [raids]("http://en.wikipedia.org/wiki/RAID") but I'm surprised that you were able to install via the USB if Wubi failed. You should have seen that 'no root file system' error in both cases.

I'm not sure how to approach this, but I'd start by booting a windows repair disk and running: bootrec /fixmbr 
Hopefully that will get windows running at least ;)

---

### Post by MNBill on 2011-10-03
Hi Blasphemist,

I just tried the **ls (hd0,X) command** with different X's, there is always the same error:

grub rescue> ls (hd0,1)/
error: unknown filesystem.
grub rescue> ls (hd0,2)/
error: unknown filesystem.
grub rescue> ls (hd0,3)/
error: unknown filesystem.

The **ls (hd0,X)/boot command** gives the following output:

grub rescue> ls (hd0,1)/boot
error: no such partition.
grub rescue> ls (hd0,2)/boot
 error: no such partition.
grub rescue> ls (hd0,3)/boot
 error: unknown filesystem.

---

### Post by Blasphemist on 2011-10-03
I don't know about the raid issue as it is rare and I don't know that I fully trust the output of the boot info script in this case. I do know that I failed to include a first step in what I posted, by error. From the grub rescue> prompt try this command and see if the prompt changes to grub>
```
normal
```
If that changes the prompt to grub>, do what I posted earlier.

If not, do you have a windows repair disk so you can do what bcbc posted to get the windows boot back? 
> start by booting a windows repair disk and running: bootrec /fixmbr

If you don't have the windows repair/recovery disk, boot the ubuntu cd/usb and install this. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Look at the MBR options tab image shown on that link and you'll see how you could put the windows ipl (initial program loader) back in the MBR.

Also, that usb looked odd in the boot info script. What is it and how did you burn the iso to it?

Let us know if some of this works. Also, if you use boot-repair, post the summary url it will give you.

---

### Post by MNBill on 2011-10-04
1) When typing "normal" at the beginning:

grub rescue> normal
Unknown command 'normal'

2) I did not generate a windows repair disk, since installing ubuntu worked very well when I installed ubuntu on my notebook (not this computer I have the problems with) a few months ago... shame on me :(

3) I installed Boot Repair with the following commands which I copied from the boot repair home page:

```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```Installing seemed to work well, but then a new window appeared that said "Enabling RAID. This may require several minutes..."

This window stayed there for around two hours, I then aborted the installation of Boot Repair.

After aborting the installation of Boot Repair, I could open Boot Repair with gksu boot-repair, there is no error message. I still did not use it to not do any damage... what should I do now?

4) To create the USB to boot from, I followed the instruction on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (Second Point, Options: USB Stick & Windows).

I did not format my USB stick, however. Should I have formatted it, or should I format it and add ubuntu to it again from my notebook?

---

### Post by bcbc on 2011-10-04
There's very little documentation on what Yannbuntu's boot repair does that I can find. It's only appeared recently so hard to say what might have happened there. 

You can burn a Windows 7 repair CD from any computer with Windows 7 running. You probably need to match the architecture (i.e. 64 bits if that is what you installed). All you need is a blank CD-R.

---

### Post by MNBill on 2011-10-04
Hi bcbc, thanks for your message.

I just found a Dell "Drivers and Utilities" disc. When I boot from this disc, a first screen appears:

> ****
Choice Action
1 Run the 32 Bit Dell Diagnostics
0 Quit without any action (Return to DOS)
***When I first enter 1, and then 0, the following screen appears:

> 
Your CD/DVD drive during this boot cycle is f:
A RAMDISK drive is available for this boot cycle as C:
It contains several Hard Drive setup tools. Please use these
tools only under the direction of Dell Support Staff.

F:\>Does that help? If not, I will buy me some blank CD-R's and go looking for somebody with a 64bit Windows 7, because my notebook has only 32bit, unfortunately.

Thanks for your help again!

---

### Post by bcbc on 2011-10-04
> **MNBill said:**
> Hi bcbc, thanks for your message.

I just found a Dell "Drivers and Utilities" disc. When I boot from this disc, a first screen appears:

When I first enter 1, and then 0, the following screen appears:

Does that help? If not, I will buy me some blank CD-R's and go looking for somebody with a 64bit Windows 7, because my notebook has only 32bit, unfortunately.

Thanks for your help again!

The 32 bit might work in this case, as you only need to install the bootloader. As long as you don't try to repair the existing install - just boot to a repair prompt - and then run 'bootrec /fixmbr' you *might be okay*.

---

### Post by MNBill on 2011-10-04
I just downloaded a Win7 recovery disk from here: [http://cybernetnews.com/windows-7-recovery-disc/](http://cybernetnews.com/windows-7-recovery-disc/). I then burned the disk and used 'bootrec /fixmbr'... and Win7 boots again! :) Thank you very much for your help!!

Is there any chance to install ubuntu, or should I refrain from installing it on this machine?

---

### Post by bcbc on 2011-10-04
Sweet!

This is what I'd do:
1. figure out what Raid you have
Chances are, if you didn't know you have it, you don't need it. It's probably halving the amount of disk space you have available.
2. Lose the raid and use the additional space available for ubuntu
3. If it turns out you don't have a raid - you just have some weird fakeraid metadata messing up ubuntu - you can remove it.
Maybe someone who knows something about raid will see this and add their opinion ;)

Or, install vmware player (free) or virtual box (free and opensource I believe) and install ubuntu on that. I like that while I'm stuck on Windows as I can do them simultaneously.

---

### Post by bcbc on 2011-10-04
PS looking again at the bootinfoscript I'm convinced you have a 2 disk raid in place. So this makes a little light reading and might give you some insight as to what the problem is: [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

---

### Post by MNBill on 2011-10-04
Cool, thanks a lot!

---

### Post by preginald on 2012-06-06
Thanks bcbc, 'bootrec /fixmbr' worked for me!

> **bcbc said:**
> The 32 bit might work in this case, as you only need to install the bootloader. As long as you don't try to repair the existing install - just boot to a repair prompt - and then run 'bootrec /fixmbr' you *might be okay*.

---

