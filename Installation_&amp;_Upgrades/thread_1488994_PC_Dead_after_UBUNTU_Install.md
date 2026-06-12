---
title: "PC Dead after UBUNTU Install"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Englischdude on 2010-05-20
Hi All,

am a complete Linuy newbie, and just tried to install UBUNTU 10.04 on my laptop.

Acer I5 windows 7 4gb RAM etc.

As am new I chose a parallel install, where I dont need to use a separate partinion. The install went ok, but now when I try to reboot I get nothing.... absolutely nothing, just a black screen.

Any ideas?

Thanks ina dvance for yoour help
Martin

---

### Post by scott1541 on 2010-05-20
I would see about booting from the windows recovery disc (hope you have one)
and running the one of those recovery tools to try and get the computer booting into windows again. If this worked then i would get the partitions sorted out with a tool like gparded (live cd). Then you can attempt another ubuntu install but straight to the pre prepared partition.

---

### Post by darkod on 2010-05-20
Did you run it in live mode first to check for any hardware issues? It might be a video driver problem.

---

### Post by Englischdude on 2010-05-21
Dear Friends,
thank you very much for your support. This is the new situation:

When i start the laptop, there is literally nothing fo about 3 minutes, just a black screen (seems like an eternity when you are waiting), after which, the computer slowly begins to react. The first thing im confronted with after a total of about 4 minutes is a selection of the partitions, the first two are ubuntu, ubuntu recovery, there are some further option with just letters, and the last two are "windows vista loader" and "windows 7 loader".

If I select the first option, Ubuntu loads normally.
If I select the last option "windows 7 loader", then I am redirected to what I think is the GRUB bootloader where I have the coice to select between UBUNTU and WINDOWS. 

If I select here UBUNTU it loads normally, but if I select windows, i get the windows 7 start screen and then it just hangs, I dont get to the screen where I can look at the BIOS etc.

I am a complete newbie so would appreciate your help. Probably should have looked for that before even starting this project eh.

Thanks you all
Martin

---

### Post by Englischdude on 2010-05-21
PS:

YeS, i ran in live mode first. Generally everything was ok, just a webcam issue.

Yes I have the win7 recovery cds, just dont know how to use them :)

When I am back this afternoon I will post a list of all the option im presented with upon booking with the first menu. Says little to me, but im sure you guys could decipher it.

Why do you think the computer hangs for about 3 minutes with a completely black screen upon starting?

Thanks
Martin

---

### Post by wilee-nilee on 2010-05-21
If you let the Ubuntu Cd resize the W7 partition that is your 1st problem. You only want to use the virtual disk manager in W7 for this. You may want to post this script for darkod and the rest of us to see whats going on. Post it in code tags by highlighting the script in the reply and clicking on the # in the reply window.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have a W7 install dvd you can restore it's bootloader with this.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section.

2) Select the command prompt (console) and type in the following commands:

BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

Here is a link that describes getting to the command line in W7.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

These instructions are per oldfred so thank him if it works. 

I would post the bootscript before you do anything though, darkod is very astute at this sort of thing so the boot script gives the information needed.

---

### Post by darkod on 2010-05-21
> **Englischdude said:**
> 
If I select the first option, Ubuntu loads normally.
If I select the last option "windows 7 loader", then I am redirected to what I think is the GRUB bootloader where I have the coice to select between UBUNTU and WINDOWS. 


This shouldn't happen. When selecting win7 it should try to boot win7, not present a windows bootloader menu which has ubuntu entry in it.

Did you also installed wubi inside windows by any chance? That is the only way to get ubuntu entry in the windows bootloader (except some special operations)?

Run the script, as suggested, it will show us more.

---

### Post by wilee-nilee on 2010-05-21
> **darkod said:**
> This shouldn't happen. When selecting win7 it should try to boot win7, not present a windows bootloader menu which has ubuntu entry in it.

Did you also installed wubi inside windows by any chance? That is the only way to get ubuntu entry in the windows bootloader (except some special operations)?

Run the script, as suggested, it will show us more.

Geez I totally missed that part, good call. I'm always concerned about giving any repair options.

---

### Post by Englischdude on 2010-05-21
Hi Team,

is this what you are looking for?

Regards
Martin








```


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 640.1 GByte, 640135028736 Byte
255 Köpfe, 63 Sektoren/Spur, 77825 Zylinder, zusammen 1250263728 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   662,457,027   637,674,180   7 HPFS/NTFS
/dev/sda4         662,458,366 1,250,263,039   587,804,674   5 Extended
/dev/sda5         662,458,368 1,227,313,151   564,854,784  83 Linux
/dev/sda6       1,227,315,200 1,250,263,039    22,947,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        F0FC1254FC121586                       ntfs       SYSTEM RESERVED               
/dev/sda3        5600196400194C7D                       ntfs       ACER                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7937588b-cabc-4972-af7d-a5d27f29e561   ext4                                     
/dev/sda6        40251a51-a58f-48fa-8720-c64f85490d42   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Recovery1         udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sda3        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
set locale_dir=($root)/boot/grub/locale
set lang=de
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7937588b-cabc-4972-af7d-a5d27f29e561 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
    echo    'Linux 2.6.32-21-generic wird geladen …'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7937588b-cabc-4972-af7d-a5d27f29e561 ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7937588b-cabc-4972-af7d-a5d27f29e561
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f0fc1254fc121586
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7937588b-cabc-4972-af7d-a5d27f29e561 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=40251a51-a58f-48fa-8720-c64f85490d42 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 468.1GB: boot/grub/core.img
 506.8GB: boot/grub/grub.cfg
 468.1GB: boot/initrd.img-2.6.32-21-generic
 468.1GB: boot/vmlinuz-2.6.32-21-generic
 468.1GB: initrd.img
 468.1GB: vmlinuz





```

---

### Post by darkod on 2010-05-21
The results look normal, except that you do have wubi (or traces of it) inside your win7. Since you already have a full install of ubuntu too, you could try booting into win7 and removing wubi (ubuntu) from Programs.

As for why it gets delayed in showing the grub menu, I don't know. According to you, this happens even before showing the grub menu, which means it is related to hardware. If it happens even before you get to the selection screen, it's not related to the OSs because you haven't even selected an OS yet.

Have you done any hardware changes?

---

### Post by Englischdude on 2010-05-21
> **darkod said:**
> The results look normal, except that you do have wubi (or traces of it) inside your win7. Since you already have a full install of ubuntu too, you could try booting into win7 and removing wubi (ubuntu) from Programs.

As for why it gets delayed in showing the grub menu, I don't know. According to you, this happens even before showing the grub menu, which means it is related to hardware. If it happens even before you get to the selection screen, it's not related to the OSs because you haven't even selected an OS yet.

Have you done any hardware changes?

Hi there,

can you give me any tips for booting into windows 7? When I try this from the grub menu it just hangs. One post here suggests that I should try to boot using the recovery dvds, but how do I action this boot?

I have done zero hardware changes, it is a new computer.   

Thanks you
Martin

---

### Post by darkod on 2010-05-21
> **Englischdude said:**
> Hi there,

can you give me any tips for booting into windows 7? When I try this from the grub menu it just hangs. One post here suggests that I should try to boot using the recovery dvds, but how do I action this boot?

I have done zero hardware changes, it is a new computer.   

Thanks you
Martin

If you can't boot win7, there might be some corruption or something. That can also happen when the ubuntu installer is shrinking the win7 system partition during the install.

It better to use win7 Disk Management to shrink the system partition first, if you need to make space for ubuntu. Then boot win7 few times to do its disk checks. Only then start the ubuntu installer.

Now... you could try and force win7 to run chkdsk (the disk check). Boot ubuntu and install the package ntfsprogs:

sudo apt-get install ntfsprogs

Try to check the /dev/sda3 partition:

sudo ntfsfix /dev/sda3

This is a basic check and won't do too much good but it will set the option win7 to check the partition next time you try to boot it.

So, reboot and select win7 from grub menu. Hopefully it will start the disk check and repair the problem, if the assumption is correct.

---

### Post by Englischdude on 2010-05-21
Thank you very much Darko, I will try this later and keep you informed.

Greetings from Austria!
Martin

---

### Post by Englischdude on 2010-05-21
> **Englischdude said:**
> Thank you very much Darko, I will try this later and keep you informed.

Greetings from Austria!
Martin


when i try and do the ntfsfix command I get this error message

"Refusing to operate on read-write mounted device /dev/sda3."

What can I do?

---

### Post by darkod on 2010-05-21
> **Englischdude said:**
> when i try and do the ntfsfix command I get this error message

"Refusing to operate on read-write mounted device /dev/sda3."

What can I do?

Well why is /dev/sda3 mounted? Windows partition do not get mounted automatically unless you set it up that way.

And in general, auto-mounting the windows system partition is not what I would do. You can mount it occasionally for access.

If it was only mounted to take a look at something, there should be icon for it on the desktop, just right-click and select Unmount.

Also, you should be able to unmount in Gparted, or terminal (but for terminal you need to know where it is mounted):

sudo umount /media/win7 (for example, you need your exact mount point)

---

### Post by Englischdude on 2010-05-21
Hi there,

ok, I could dismount the ACER drive and enter the command in the terminal, but upon rebooting nothing happens when selecting, only the logo comes saying windows is starting but then it just hangs.

Interestingly enough, I have also changed the BIOS so I can boot from a disk, I ut in th recovery disks and the following happened when booting:
- the disk was recognised, and the files were loaded
- then the windows 7 logo saying windows is starting, after which it just hangs.

So I cant even start Windows with the recovery cds!!!

Oh man, if I can just get the windows back to its original state without Linux I will be very happy. Any suggestions?

Thanks in advance
Martin

---

### Post by darkod on 2010-05-21
Not sure. Something is wrong with windows it seems. It doesn't necessarily mean it was ubuntu's fault.

You can't even boot the recovery disc. :(

---

### Post by Englischdude on 2010-05-22
Hi Darkod,

since my last post I have installed UBUNTU new, overwriing all existing partitions. The situation is now so:

- When I switch on the computer there is still aboout a 2 minute delay before the computer actually starts to boot. Why could that be?!?!? I have googled about but cant find anything similar. After the two minutes I get the first splash screen where I can enter the BIOS.

- Windiws still will not start from the recovery dvds. It starts to load, but then just hangs at the windows logo. I have googled this and many people are having this problem. It seems to be a hardware issue. I have contacted ACER now on this one.

Thanks Darkod
MArtin

---

### Post by darkod on 2010-05-22
> **Englischdude said:**
> Hi Darkod,

since my last post I have installed UBUNTU new, overwriing all existing partitions. The situation is now so:

- When I switch on the computer there is still aboout a 2 minute delay before the computer actually starts to boot. Why could that be?!?!? I have googled about but cant find anything similar. After the two minutes I get the first splash screen where I can enter the BIOS.

- Windiws still will not start from the recovery dvds. It starts to load, but then just hangs at the windows logo. I have googled this and many people are having this problem. It seems to be a hardware issue. I have contacted ACER now on this one.

Thanks Darkod
MArtin

If you have to wait 2min before it even shows you a BIOS screen, it definitely sounds like hardware issue. That should be instant, it's the first thing a computer goes trough, the BIOS.

---

### Post by Englischdude on 2010-05-22
thats what I thought, then I found this.....

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563480](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563480)


Has this happened to anyone else?

---

### Post by darkod on 2010-05-22
It depends what exactly are we talking about. The person that reported that bug is talking about the purple ubuntu splash screen I think. But that has nothing to do with BIOS.

The BIOS is activated after power on, and it should quickly finish its POST (Power On Self Test). If that is successful, it continues with booting the bootloader.

The ubuntu splash can come only after all of that is done and ubuntu is selected to be booted (if you have a dual boot the grub menu will offer you to select an OS).

In your post you said you waited 2min for the BIOS screen but maybe you meant the ubuntu splash image.

If the delay is even before you have chance to enter BIOS, or before the grub menu is shown, that has nothing to do with windows or ubuntu. But if the delay is actually after selecting to boot ubuntu, that's a different matter.

---

### Post by Englischdude on 2010-05-25
Hi Darkod,

you are right, the delay comes between power on and the acer welcome screen where I have a chance to enter the BIOS. I am in the process of trying to find a way to update the BIOS, current version is 1.09, my version is 1.04. Unfortunately, I cant seem to find a way to update the BIOS from Linux at the moment. Have tried to make a bootable USB stick with FREEDOS on it using the UNETBOOTIN utility, but that has not worked up till now.

Any suggestions on updating the BIOS from LINUX platform? 

Although my WIN7 Installation dvds are not working, I will see if it is possible installing win xp on this machine. Maybe it will be easier to troubleshoot this problem from a windows platform as there are maybe more utilities available.

Regards
Martin

---

### Post by Englischdude on 2010-06-03
Hi All,

so after dealing with ACER customer support I did a clean install, managed to update the BIOS, but the long delay problem still persisted. Acer CS was sure it must be a hardware problem. I brought the laptop back to the store and was able to change for a new laptop. 

Full of enthusiasm I came home, made the WIN7 recovery dvds and isntalled UBUNTU........... I STILL HAVE THE SAME PROBLEM!!!

At least we know it is not a hardware problem, but still, I cannot live with a computer in this state.  Has anyone got any ideas please:

Main symptom at the moment is a 2 minute delay between power-on and BIOS welcome screen.

Thanks in advance
Martin

---

### Post by Englischdude on 2010-06-03
Problem solved!!!!

I wanted to get at the CMOS battery to see if removing it would do the trick. COuld not get at the battery, but had to remove the main battery and power supply in the process. This alone seems to have cleared a "blockage" somewhere and now I boot up as normal within 30 seconds.

Simple solution, but it took alot of trial and error to get there. I hope this experience saves someone from the same hassle.

Regards
Martin

---

