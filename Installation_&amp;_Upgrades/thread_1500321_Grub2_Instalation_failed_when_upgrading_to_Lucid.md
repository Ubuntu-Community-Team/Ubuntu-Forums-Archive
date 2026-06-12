---
title: "Grub2 Instalation failed when upgrading to Lucid"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by neo1786 on 2010-06-03
Hi guys,
I was upgrading from Karmic to Lucid,i installed all updates and proceeded with upgrade to 10.04
Everything worked fine. 
There was a window where i had to select the partitions which will be shown in grub
At the time i had a external hard drive connected.
-I selected all the options shown there(i guess i also included the ext hdd)
When i restarted i got the grub rescue> prompt
i reinstalled the grub2 following instructions here:

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

I followed Method1.After step 6 reboot i landed i got the
sh.grub> prompt instead...
Now i cant strt windows or ubuntu.
I am also not able to boot from CD. I come to the same sh.grub>
Can anybody help me??
I am using a HP dv4 64bit but i was running a 32-bit OS
I have a lot of data which i cant afford to lose...

---

### Post by neo1786 on 2010-06-03
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

If the link doesnt take you to exact location...on the rght side click on 11.1 Reinstalling from live CD

---

### Post by neo1786 on 2010-06-03
Can anybody guide me how to go on from the sh:grub> prompt???

---

### Post by wilee-nilee on 2010-06-03
Since you haven't shared whether this is your only OS you might tell us more. For all we know this could be a wubi install inside windows it could be virtual you might be dual booting with multiple Linux see where I'm going here.

---

### Post by neo1786 on 2010-06-03
hey thanks for replying....im running a dual boot...windows vista and ubuntu using wubi....

---

### Post by wilee-nilee on 2010-06-03
> **neo1786 said:**
> hey thanks for replying....im running a dual boot...windows vista and ubuntu using wubi....

You will be best to post the bootscript in code tags. To do this paste the script readout after running it from a live cd and highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

So I know very little about wubi so I doubt if I will be of any help but there are others who do. The script will show whats going on though.

---

### Post by neo1786 on 2010-06-03
im sorry but i cant boot from a CD also...i keep getting this screen:

                    GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
sh:grub>_

do u have any idea how to load kernel from this?? since i just upgraded to lucid what will be my kernel version number???

---

### Post by wilee-nilee on 2010-06-03
> **neo1786 said:**
> im sorry but i cant boot from a CD also...i keep getting this screen:

                    GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
sh:grub>_

do u have any idea how to load kernel from this?? since i just upgraded to lucid what will be my kernel version number???

So your going to have to fix the grub problem, if you loaded it everywhere it is the root of the problem. So can you use a key prompt like f12 or whatever it is for your computer to get a choice of what to boot from. If you can then, a live Ubuntu cd should boot. Trying to add a kernel even if you could is not going to fix this.

I would be careful to not mess around with the damage already done.

Do you have a vista install disc?

---

### Post by wilee-nilee on 2010-06-03
So besides installing grub originally in the wrong places, it appears you have overwritten the vista bootloader in the master boot record with trying to fix it by reinstall grub, just so you understand. If you have a vista install disc though the mbr can be reloaded with the vista bootloader. It happens everything is still all there so it is just a matter of doing it correctly, so be careful not to try fixes you think can work this may make things even harder to fix. ;)

---

### Post by kansasnoob on 2010-06-03
> **neo1786 said:**
> im sorry but i cant boot from a CD also...i keep getting this screen:

                    GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
sh:grub>_

do u have any idea how to load kernel from this?? since i just upgraded to lucid what will be my kernel version number???

Nothing about grub should prevent the Live CD from booting. You'll have to be able to boot some live media to fix this.

---

### Post by darkod on 2010-06-03
> **neo1786 said:**
> im sorry but i cant boot from a CD also...i keep getting this screen:

                    GNU GRUB version 1.97~beta4
[Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]
sh:grub>_

do u have any idea how to load kernel from this?? since i just upgraded to lucid what will be my kernel version number???

Go into the BIOS and set in boot devices cd-rom to be before hdd. You are still booting from the hdd.

And just to clarify, it didn't ask you which partitions to show in grub2, but WHERE TO INSTALL grub2!!! There is big difference. You should have selected just the MBR of the internal hdd. No partitions at all, not from the internal or external hdd.
And why are you upgrading an OS with ext hdd connected at all? Are you trying to make things harder for yourself?

---

### Post by neo1786 on 2010-06-03
@darkod
I really did mess up with tht grub installation.had no idea wat i was doing..i had the external tp backup some fies..i didnt remove it before upgrading :(
________________________________________________________________
Well, i was able to boot from the CD. dont know why it wasnt happening before...Wat do i do now??

---

### Post by neo1786 on 2010-06-03
> **wilee-nilee said:**
> You will be best to post the bootscript in code tags. To do this paste the script readout after running it from a live cd and highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

So I know very little about wubi so I doubt if I will be of any help but there are others who do. The script will show whats going on though.

Here is the contents of RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 3588600 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 3591520 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 3596136 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 3593216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27265bbe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,153,463   306,151,416   7 HPFS/NTFS
/dev/sda2         306,153,472   533,413,879   227,260,408   7 HPFS/NTFS
/dev/sda3         533,413,888   594,855,935    61,442,048   f W95 Ext d (LBA)
/dev/sda5         533,415,936   594,855,935    61,440,000   7 HPFS/NTFS
/dev/sda4         594,855,936   625,135,615    30,279,680   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7b7d5358-53a4-4f24-8ec6-6f6beb0337e0   ext4                                     
/dev/sda1        BC46842C4683E58C                       ntfs                                     
/dev/sda2        428836EE8836E059                       ntfs       Fastrack                      
/dev/sda4        82B6FEAFB6FEA339                       ntfs       RECOVERY                      
/dev/sda5        727413427413088D                       ntfs       Ubuntu                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/BC46842C4683E58C  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

```

---

### Post by darkod on 2010-06-03
Boot in ubuntu live mode and use this fix on your /dev/sda1 partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, that's partition #1 on disk /dev/sda.

After you have fixed that, don't restart yet. Open terminal and run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. Restart and hopefully you should see your vista loading.

---

### Post by neo1786 on 2010-06-03
> **darkod said:**
> Boot in ubuntu live mode and use this fix on your /dev/sda1 partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, that's partition #1 on disk /dev/sda.

After you have fixed that, don't restart yet. Open terminal and run:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give. Restart and hopefully you should see your vista loading.

IT WORKD!!!!YAY!!! The grub screen was as it used to be before!
Im in vista rght now..will i be able to load ubuntu properly aftr selecting it from the grub2?? or do i have to make any more changes?? Thank you soo much :D

---

### Post by darkod on 2010-06-03
> **neo1786 said:**
> IT WORKD!!!!YAY!!! The grub screen was as it used to be before!
Im in vista rght now..will i be able to load ubuntu properly aftr selecting it from the grub2?? or do i have to make any more changes?? Thank you soo much :D

Check it out, it should work too without any other procedures.

I didn't even know you were using wubi until I saw the results file. In your case, what ever you selected in that window would make a problem for you unfortunately. :(

But you sorted it out all right. :)

---

### Post by neo1786 on 2010-06-03
when i selected the new kernel from grub,
Linux 2.6.32-22-generic
I got this screen
[Linux-bzImage, setup=0x3400,size=0x3d4860]
[Initrd, addr=0x37809000,size 0x7e6ac2]
[2.278296] Kernel panic - not syncing:VFS: Unable to mount root fs on unknown-block(0,0)
_
And the cursor keeps blinking.
I guess the unknown block is my ext hdd??is it??

---

### Post by darkod on 2010-06-03
Does the older kernel work? Do you have it still in the menu?

If it works just use that for now.

---

### Post by neo1786 on 2010-06-03
> **darkod said:**
> Does the older kernel work? Do you have it still in the menu?

If it works just use that for now.

Yes it works...LUCID LYNX looks good :)
I really appreciate all your help...Thank You so much!

---

### Post by Duane A on 2010-06-03
I am not sure if my grub2 failed or what. I have a hdd, ide variety, and have xp and jaunty installed and they both did work. Tried upgrading to lucid and lost boot sector, I think. May not be boot, but it stops there and asks for boot disk.

I turn cmpt on (bios is set properly) and "insert system disk and press enter" is there and nothing else.

Running live will access jaunty. 

What is my next step?

I have had Ubuntu for 4 past issues. I can sort of find my way around if I know what to look for or what to ask specifically. If you need a log, I will need to know how to find it. I can run terminal but only if I know what command to use.
And I have googled the crap out of this problem with no answer.

---

### Post by darkod on 2010-06-03
> **Duane A said:**
> I am not sure if my grub2 failed or what. I have a hdd, ide variety, and have xp and jaunty installed and they both did work. Tried upgrading to lucid and lost boot sector, I think. May not be boot, but it stops there and asks for boot disk.

I turn cmpt on (bios is set properly) and "insert system disk and press enter" is there and nothing else.

Running live will access jaunty. 

What is my next step?

I have had Ubuntu for 4 past issues. I can sort of find my way around if I know what to look for or what to ask specifically. If you need a log, I will need to know how to find it. I can run terminal but only if I know what command to use.
And I have googled the crap out of this problem with no answer.

Since you know how to use terminal you should have no problem running the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file here to show us more details.

---

### Post by Duane A on 2010-06-08
> **darkod said:**
> Since you know how to use terminal you should have no problem running the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file here to show us more details.

Sorry this has taken so long.

Here is results of trying to get [http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4) below:

nancy@nancy-desktop:~$ sudo bash boot_info_script055.sh
[sudo] password for nancy: 
bash: boot_info_script055.sh: No such file or directory
nancy@nancy-desktop:~$ sudo bash boot_info_script055.sh
bash: boot_info_script055.sh: No such file or directory
nancy@nancy-desktop:~$

I don't know where or how to send you the file you want. Don't know as much as you want me to know. 

Thanks for your efforts.

---

### Post by darkod on 2010-06-08
No problem.

Click the link in my signature to download the boot info script (it's a file). It will probably download in Places-Downloads. Open the folder just to check if it's there.

If it is in that folder, to execute it open terminal and execute:

sudo bash ~/Downloads/boot_info_script*.sh

It will create results.txt file in the same folder where the script file is. Just open that txt file and copy the whole text like from a document.

Then paste is here in your reply.

---

### Post by Duane A on 2010-06-09
> **darkod said:**
> No problem.

Click the link in my signature to download the boot info script (it's a file). It will probably download in Places-Downloads. Open the folder just to check if it's there.

If it is in that folder, to execute it open terminal and execute:

sudo bash ~/Downloads/boot_info_script*.sh

It will create results.txt file in the same folder where the script file is. Just open that txt file and copy the whole text like from a document.

Then paste is here in your reply.

I think this is what you want.
Skip
Subject: 	missing grub report
Date: 	06/09/2010 10:08:14 AM



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 169219819 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 169261651 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   168,939,539   168,939,477   7 HPFS/NTFS
/dev/sdb2         168,939,540   312,576,704   143,637,165   5 Extended
/dev/sdb5         168,939,603   306,632,654   137,693,052  83 Linux
/dev/sdb6         306,632,718   312,576,704     5,943,987  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F628515B28511C45                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5CC452FBC452D6BC                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        21340900-1db1-4a38-86c9-20407f380619   ext4                                     
/dev/sdb6        75a79bad-beda-4016-bf9d-b910ba84d2f4   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=21340900-1db1-4a38-86c9-20407f380619 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=21340900-1db1-4a38-86c9-20407f380619 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=21340900-1db1-4a38-86c9-20407f380619 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=21340900-1db1-4a38-86c9-20407f380619 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 21340900-1db1-4a38-86c9-20407f380619
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f628515b28511c45
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5cc452fbc452d6bc
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=21340900-1db1-4a38-86c9-20407f380619 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=75a79bad-beda-4016-bf9d-b910ba84d2f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  86.6GB: boot/grub/core.img
  99.6GB: boot/grub/grub.cfg
  87.3GB: boot/initrd.img-2.6.31-20-generic
  87.4GB: boot/initrd.img-2.6.32-22-generic
  87.0GB: boot/vmlinuz-2.6.31-20-generic
  87.4GB: boot/vmlinuz-2.6.32-22-generic
  87.4GB: initrd.img
  87.3GB: initrd.img.old
  87.4GB: vmlinuz
  87.0GB: vmlinuz.old

---

### Post by Duane A on 2010-06-14
Is it safe to assume the log I sent contains nothing to help?

---

