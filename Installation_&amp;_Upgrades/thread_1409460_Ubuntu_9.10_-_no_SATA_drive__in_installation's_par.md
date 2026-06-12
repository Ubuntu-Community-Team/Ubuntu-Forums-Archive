---
title: "Ubuntu 9.10 - no SATA drive  in installation's partitioner"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by teo2403 on 2010-02-17
Hi all, i have a strange problem while trying to install Ubuntu 9.10 64bit (also tried with x86 - no luck).

My system specs : 

Motherboard : ASUS P5B VM SE (PATA : JMB368  / Intel ICH8)
HD  : Seagate SATA II 3GBit 320 MB  (connected in SATA port 1)
CPU : Intel Core 2 Quad 2500 GHz

I must state i installed Windows 7 without a problem. After that, i tried to install Ubuntu 9.10, first 64bit then x86 but in every case the setup starts, i select language / location etc and when the partitioner starts i see no hard disk drive. Same happens if i try the alternate install cd.

I must mention here that if i click on "Exit" and access Ubuntu Live CD desktopm i can go System > Administrator > Disk Utillity  and GParted. In both utillities my HD shows up just fine. So what could be the problem ??? 

I tried starting ubuntu with pci=nommconf irqpoll -> no luck

Here is the lspci output :

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

---

### Post by MCVenom on 2010-02-17
I hope you get an answer to your question, I'm having a similar issue (see sig) :|

---

### Post by darkod on 2010-02-17
Usually this happens when you have raid meta data settings on the hdd. 9.10 can detect them and is confused whether the hdd is part of raid array or not.

First make sure you don't have any raid settings enabled in bios, because they can put raid info on the hdd even when it's only one hdd. The SATA Type option should not be RAID.

Of course, all of this if you are NOT running raid. If you are, that's another story.

Then boot the ubuntu live desktop, and in terminal do:

sudo dmraid -E -r /dev/sda (if you have one hdd, for more you might need to use /dev/sdb, /dev/sdc, etc)
sudo apt-get remove dmraid

Restart the install process and it should be fine. Provided that was the problem.

---

### Post by oldfred on 2010-02-17
Besides the potential raid issue is that windows may use up all four primary partitions. From a terminal in the liveCD.

```
sudo fdisk -l   
```

---

### Post by teo2403 on 2010-02-18
First of all uys thanx for the help. Unfortunately this PC is located at my parents house and i can't try your proposals til Saturday but i ll definitely write here what happened cause i ve been searching for days now and found no solution in the net. 

"The SATA Type option should not be RAID."  --> The motherboard is cheap one - i haven't seen any kind setting in the BIOS for SATA TYPE.

There is only 1 HD drive connected in SATA(ICH8) and 2 DVD-RW in IDE (JMicron)


"Besides the potential raid issue is that windows may use up all four  primary partitions." --> As i said earlier i have checked the disk with GParted and Disk Utility from Ubuntu and Windows Disk Manager and windows only take up 2 partitions :
1) 100MB partition (probably for boot loader ???)
2) 60GB partition for Windows.
There is left ~240GB partition which is unallocated (all in 1 segment).

Guys thanks very much for the help.

---

### Post by teo2403 on 2010-02-18
Forgot to mention that i have tried to install Ubuntu to another SATA HD as well. I disconnected Seagate 320GB SATA II and i attached WD120GB SATA I but again i had same problems (no disk/partirion appears in Ubuntu Intall Partitioner but i could access the disk and its 1 partition by Disk Utillity and GParted).

---

### Post by teo2403 on 2010-02-20
darkod --> Your method worked.. I run the 2 commands you provided and i got to see the hard disk in the installation partitioner .. 

However, i managed to finish the Ubuntu installation but GRUB had not recognized Windows 7 and when i tried to boot Ubuntu had another error (no partition found...). Once i have time i ll try again.

You might think it's a faulty HD but as i said before, i have tried with another one and had same results..

---

### Post by darkod on 2010-02-20
It might be another issue, don't reinstall ubuntu right away. When you have more time to troubleshoot it, just post here more exactly the problem.
I already have an idea but if you don't have time now...

---

### Post by teo2403 on 2010-02-21
Ubuntu installation completed succcesfully.. From the partitioner i had seen the 2 windows partition and the extra space which i used for Ubuntu (3GB for swap and 30 for / ). I did not setup Ubuntu partitioner to mount the 2 NTFS partitions (dont think it has to do anything with grub though).\

When the pc restarted, GRUB only contained Ubuntu as an option - no Windows 7 option. When i selected Ubuntu there was an error message (no partition found). Had an error code as well (i think 07 but i m not sure - i was in a hurry).

---

### Post by darkod on 2010-02-21
I think it's time to run the boot info script now. Follow these instructions and post your results here.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by ChrisThompson on 2010-03-03
Hi everyone else in the thread.

I found this thread because I've been fighting a similar battle for weeks and it's been driving me nuts.

(the full, gory details of my fight can be found [here]("http://ubuntuforums.org/showthread.php?p=8881813")
READER'S DIGEST VERSION:  Used to run 9.10 on an old PATA that has died.  9.10 build never detected my SATA drives, I never cared enough to make it, but now that PATA's dead I have no choice.  Trying to dual boot with Windows XP on an IDE-controlled, non-RAID SATA drive but Install Partitioner, GParted, and Disk Utility do not see it on Install or in LiveCD.

Removing DMRAID (both in terminal and Synaptic) does nothing.  F6 Boot options, including NOLAPIC and NO DMRAID do nothing.  Alternate-text installer, 8.10 installer, 10.04 installer...nothing.  MoBo (ASUS a8v-xe) has 3 SATA controller options:  PCI, RAID, and AHCI.  Changing them does (you guessed it) nothing.

Darko, here's my boot info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```I'm spent on ideas.  I'll take whatever help anyone can offer.  Thanks.

---

### Post by oldfred on 2010-03-03
ChrisThompson
It would be much better to start your own thread, we get confused when we see two different results.txt and are not sure who is who.

The script did not even see your drive. It looks like a new drive that has never been partitioned or the partition table was damaged.

---

### Post by ChrisThompson on 2010-03-03
> **oldfred said:**
> ChrisThompson
It would be much better to start your own thread, we get confused when we see two different results.txt and are not sure who is who.
Apologies for the breech in etiquette; I will certainly do so in the future.
> **oldfred said:**
> The script did not even see your drive. It looks like a new drive that has never been partitioned or the partition table was damaged.
That's exactly my problem, actually.  Nothing sees either drive.  I know they're in there and I know they work; XP runs on 'em just fine.  It's simply a matter of getting ubuntu to notice.

---

### Post by ChrisThompson on 2010-03-04
Teo,

I've started my own [thread ]("http://ubuntuforums.org/showthread.php?t=1421942")for the issue I posted above.  If I get any answers there I'll pass them along to you, hopefully they'll help you out too.

--Chris

---

### Post by ChrisThompson on 2010-03-06
Teo,

adding 'pci=nomsi' to the boot options allowed my drives to be detected.  [Here's a thread]("http://ubuntuforums.org/showthread.php?t=1421942") with lots of details on how to do this.

Hope this helps!

--Chris

---

### Post by teo2403 on 2010-03-26
First of all sorry for the late response - as i said in the past i have limited time on the pc that has this problem.

By adding pci=nomsi i managed to to see the partitions in the Ubuntu setup process and finish installation successfully.. 

However when ubuntu restarts after installation i cannot boot into Ubuntu.. Again same error message --> "Out of disk".

I tried adding pci=nomsi there as well but no luck... Any ideas ?

---

### Post by oldfred on 2010-03-26
teo2403, did you ever run this that darko suggested? You can run from liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by teo2403 on 2010-03-27
I finally found the solution last night!! ( I had run the info script but for a while i was working with other things and did not have time to work on this problem...)

From grub menu i entered 'e' to edit grub's command and besides pci=nomsi i removed the 2nd line in my script 

        recordfail=1
----->if [ -n \${have_grubenv} ]; then save_env recordfail; fi <---- REMOVED this line
        ..............

i hit CTRL+X and it worked...  As mentioned in other threads, i edited /etc/default/grub to make pci=nomsi fix permanent but i still had problem with this "if" line appearing. So i edited

sudo gedit /etc/grub.d/10_linux

and i removed line 61 
 if [ -n \${have_grubenv} ]; then save_env recordfail; fi

saved the file and run update-grub.

Now pc loads perfectly without any interaction by me. However i think that if grub is updated from apt-get in the future i ll have to perfom this change again ..

Finally, here is the output of the boot script AFTER all the above changes: 

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aca21

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   122,882,047   122,675,200   7 HPFS/NTFS
/dev/sda3         122,897,250   171,718,784    48,821,535   5 Extended
/dev/sda5         122,897,313   132,648,704     9,751,392  82 Linux swap / Solaris
/dev/sda6         132,648,768   171,718,784    39,070,017  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0C3C86023C85E754                       ntfs       System Reserved               
/dev/sda2        E6BC2964BC29308B                       ntfs                                     
/dev/sda5        eede11ee-226b-459f-958a-7578ed48ac2e   swap                                     
/dev/sda6        c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1

    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67 ro   quiet splash pci=nomsi
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1

    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1

    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67 ro   quiet splash pci=nomsi
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1

    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0c3c86023c85e754
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c326fdcc-3c38-4cd4-9e3d-b0ddec30ff67 /               ext4    errors=remount-ro 0       1
# /media/windows was on /dev/sda2 during installation
UUID=E6BC2964BC29308B /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=eede11ee-226b-459f-958a-7578ed48ac2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  72.5GB: boot/grub/core.img
  74.5GB: boot/grub/grub.cfg
  68.2GB: boot/initrd.img-2.6.31-14-generic
  69.5GB: boot/initrd.img-2.6.31-20-generic
  68.5GB: boot/vmlinuz-2.6.31-14-generic
  68.5GB: boot/vmlinuz-2.6.31-20-generic
  69.5GB: initrd.img
  68.2GB: initrd.img.old
  68.5GB: vmlinuz
  68.5GB: vmlinuz.old

```

---

