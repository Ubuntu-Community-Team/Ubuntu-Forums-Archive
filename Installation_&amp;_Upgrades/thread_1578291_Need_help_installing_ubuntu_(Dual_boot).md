---
title: "Need help installing ubuntu (Dual boot)"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by websnake on 2010-09-20
Hey i am new ubuntu user i was using ubuntu 9.10 directly from my USB drive (ubuntu live usb creator)
but i wanted to use ubuntu permanently. so i installed it to my computers harddrive.


i had windows 7 and windows XP installed on my system and i done a stupidity :confused: .
after installing windows 7 i don't need XP anymore so i decided to install ubuntu on XP partition.

i installed ubuntu form usb into my windows xp partition by directly formating it form ubuntu installation process.

and after installing ubuntu windows 7 was not booting i tried to add it on grub boot list but that didn't work also tried to repair it using windows 7 DVD but that also didn't worked.
so i finally decided to reinstall windows 7 :( because i need it for somekind of work.

after installing windows 7 i tried to add ubuntu into boot list from ubuntu live disc ( using grub) but that also didn't worked for me.
ubuntu is still installed on my computer 10gb ext 3 partition (view attachments for more info ) .

please help me to get ubuntu back.

thanks for reading my long post.

---

### Post by garvinrick4 on 2010-09-20
Is windows 7 booting? And run this in Ubuntu live Cd (install Cd using try ubuntu.)
Open a terminal.
```
sudo fdisk -l
``` (lower case L)
Need to get linux version of your drive with this. C: D: E: and so on are for windows.
Post results by copy and pasting here.

---

### Post by arubislander on 2010-09-20
Also you might want to reconsider your partitioning scheme. You have 6.33 GB unallocated that will never be used if you stick with the current layout.

---

### Post by websnake on 2010-09-20
> **garvinrick4 said:**
> Is windows 7 booting? And run this in Ubuntu live Cd (install Cd using try ubuntu.)
Open a terminal.
```
sudo fdisk -l
``` (lower case L)
Need to get linux version of your drive with this. C: D: E: and so on are for windows.
Post results by copy and pasting here.

yes windows 7 is booting.
i reinstalled it because i can't repair it using windows 7 DVD and if i add it on grub boot menu it won't boot. \

here is the fdisk information.........
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1281    10289601   83  Linux
/dev/sda2   *        2299        4865    20618240    7  HPFS/NTFS   (windows 7 partition)
Partition 2 does not end on cylinder boundary.
/dev/sda3            4866       19457   117210240    f  W95 Ext'd (LBA)
/dev/sda4            1282        1472     1534207+  82  Linux swap / Solaris
/dev/sda5            4866        9730    39078081    b  W95 FAT32
/dev/sda6            9731       14595    39078081    b  W95 FAT32
/dev/sda7           14596       19457    39053983+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         492     3948480    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38 ) 
```A snap of gparted in attacments. ( bootable live linux USB is very usefull ;) )

---

### Post by garvinrick4 on 2010-09-20
Put in Live CD and and open gparted and right click on swap and delete. You have to hit green apply arrow to make things take. Format unallocated space to ext3 with right click and format to. resize sda1 leaving 2 gig left over for swap. Now give rest to swap about 2000 meg. Now should have used up your dead space and made partition a bit larger. Get out of gparted and open a terminal.
 This is with sda1 as linux partition you want to use grub to boot. Always change to the
correct sdaX and always use sda as the recipient of grub, never sda1, sda5 and so on.
     Code:
     ```
sudo mkdir /media/root
```     Code:
     ```
sudo mount /dev/sda1 /media/root
```     Code:
     ```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```     Code:
     ```
sudo umount /media/root
```It will now look for boot in sda1 to put in mbr(your ubuntu install of grub) always put is sda
Now reboot take disk out and boot into your hard drive install of ubuntu and:


     Code:
     ```
sudo update-grub
``` This will have all Operating Systems in Grub now.
If grub gets screwed up anytime just use your live cd (install cd of Ubuntu using Try Ubuntu) and reinstall. What you have done is:
1. Make a directory
2. Mount /dev/sda# in with that directory
3. install grub as shown from sda# to sda
4. unmount (umount is right)
You want to see your whole file on your desktop in text file use this. Takes 30 seconds.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by garvinrick4 on 2010-09-20
Here is a nice site for you. Any problems post if ok mark thread as solved.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by websnake on 2010-09-21
i done as you said garvinrick4 now ubuntu is booting fine but when i boot windows 7 it says
error : no such disk press any key to continue......:(

here is log of what i done in terminal....

```
ubuntu@ubuntu:~$ sudo mkdir /media/root
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/root
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/media/root /dev/sda

Installation finished. No error reported.
This is the contents of the device map /media/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb

ubuntu@ubuntu:~$ sudo umount /media/root
```and after doing doning that i rebooted to ubuntu and updated grub. but it gives me few options in blue screen so i chose the 3rd one (may be i done something wrong here :-k ).

here is my grub menu.lst
```


## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        ba71111f-c29d-4ef4-a4e6-4734b22e03b2
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ba71111f-c29d-4ef4-a4e6-4734b22e03b2 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        ba71111f-c29d-4ef4-a4e6-4734b22e03b2
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=ba71111f-c29d-4ef4-a4e6-4734b22e03b2 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        ba71111f-c29d-4ef4-a4e6-4734b22e03b2
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        ba71111f-c29d-4ef4-a4e6-4734b22e03b2
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```here is a log of fdisk if anyone need it. (i put a screen shoot of gparted after creating the partition.)```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09050904

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2041    16394301   83  Linux
/dev/sda2   *        2299        4865    20618240    7  HPFS/NTFS    (windows 7)
Partition 2 does not end on cylinder boundary.
/dev/sda3            4866       19457   117210240    f  W95 Ext'd (LBA)
/dev/sda4            2042        2298     2064352+  82  Linux swap / Solaris
/dev/sda5            4866        9730    39078081    b  W95 FAT32
/dev/sda6            9731       14595    39078081    b  W95 FAT32
/dev/sda7           14596       19457    39053983+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

```please help i need windows 7 for my few but important works ( and i also need ubuntu ).

---

### Post by garvinrick4 on 2010-09-21
Run this so we can just see what your boot looks like. Takes 30 seconds to do.
go to this site and Download to DESKTOP
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Run this code and a text file will pop up on your destop, OPen and copy and paste.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by garvinrick4 on 2010-09-21
This you can keep to see what your grub menu looks like if needed.

```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by websnake on 2010-09-21
> **garvinrick4 said:**
> Run this so we can just see what your boot looks like. Takes 30 seconds to do.
go to this site and Download to DESKTOP
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Run this code and a text file will pop up on your destop, OPen and copy and paste.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

i am a noob in linux.
i downloaded boot_info_script055.sh  from suorceforge.net how do i run it when i run it on terminal it says pemission denid.

EDIT:
oops sorry i forgot to read the instructions on the page.
now running the script

---

### Post by websnake on 2010-09-21
Here is result.txt......

---

### Post by garvinrick4 on 2010-09-21
It shows Windows in the config files. It shows looking for grub in sda1 to /sda. correct.
Still has boot flag on Windows sda2. HMMM.
What boots now Ubuntu/Windows or both?

---

### Post by websnake on 2010-09-21
> **garvinrick4 said:**
> It shows Windows in the config files. It shows looking for grub in sda1 to /sda. correct.
Still has boot flag on Windows sda2. HMMM.
What boots now Ubuntu/Windows or both?

i am currently running ubuntu and when i try to boot windows 7 it says
error : no such disk 
press any key to continue.....

---

### Post by garvinrick4 on 2010-09-21
Okay lets get Windows booting: Then overwrite that with grub2 from sda1.
Use your live CD for ubuntu and.( make sure you have your internet connection on in case it has to fetch it.)
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Now you should be able to boot Windows.
Put live cd back in and.
Then put the grub2 back in from sda1 to sda.
     Code:
     ```
sudo mkdir /media/root
```     Code:
          Code:
     ```
sudo mount /dev/sda1 /media/root
```     Code:
          Code:
     ```
sudo grub-install --recheck --root-directory=/media/root /dev/sda
```     Code:
          Code:
     ```
sudo umount /media/root
```Now reboot take disk out and boot into your hard drive install of ubuntu and:


     Code:
          Code:
     ```
sudo update-grub
```
To update and make sure windows is installed

---

### Post by websnake on 2010-09-21
yep windows 7 is booting now (posting this form windows 7).
now i will try the second step ...

---

### Post by websnake on 2010-09-21
:( after doing the 2nd step now i can't boot to windows 7 it still says no such disk ](*,).

and now i am posting this form ubuntu.

more info:
i am using lenovo y410 and ubuntu 9.10 - the karmic koala released in october 2009.

---

### Post by garvinrick4 on 2010-09-21
After doing the two lines of code that gets Windows booting. What does Ubuntu say if
you try to boot it? We have both grub legacy which was from 9.04 and back and grub2
from 9.10 and up in your boot text file. As of right now I see that we can get Windows booting or Ubuntu booting but not both with same grub. Just need to know after lilo installed that lets Windows boot what ubuntu says when you try to boot with lilo installed.
This is now an offlcial mission that has got to be fixed.

---

### Post by websnake on 2010-09-21
after repeating the second process i booted windows in boot screen i got two option

windows 7 
ubuntu

and when i chose ubuntu it says 

Try (hd0,0): EXT2:

when i do the second step it is show ubuntu and windows because i added ubuntu form EasyBCD when i was unable to boot both operating system at the same time . ( i done this 1 or 2 days ago when i was tired editing grub and still not able to boot windows so i formated my windows 7 partition reinstalled it leaving the ubuntu partition intact and after when i boot windows i added a option to boot ubuntu using EasyBCD but still no luck it says "Try (hd0,0): EXT2:" when i try to boot ubuntu see attachments).

---

### Post by garvinrick4 on 2010-09-21
> **websnake said:**
> after repeating the second process i booted windows in boot screen i got two option

windows 7 
ubuntu

and when i chose ubuntu it says 

Try (hd0,0): EXT2:

when i do the second step it is show ubuntu and windows because i added ubuntu form EasyBCD when i was unable to boot both operating system at the same time . ( i done this 1 or 2 days ago when i was tired editing grub and still not able to boot windows so i formated my windows 7 partition reinstalled it leaving the ubuntu partition intact and after when i boot windows i added a option to boot ubuntu using EasyBCD but still no luck it says "Try (hd0,0): EXT2:" when i try to boot ubuntu). Had to be something different in there it was easyBCD.  Ok so anyway we can boot into either Ubuntu or windows7 with two different boot managers and grub legacy gets in the way
of grub2 to look into the right place for Windows. So lets try to get rid of any grub legacy. While in Ubuntu on hard drive run.
```
sudo upgrade-from-grub-legacy       
```Should say installing grub to your first hard drive
Installation finished no error reported
hdo  /dev/sda

Something real close to that anyway.
Run another
```
sudo update-grub
```should have ubuntu and your windows installs.
Hopefully Windows is pointing towards right spot now.
That is all it is, is windows is pointing where grub legacy pointed it to.
Let me know if this fixes it. If not I will get a user that is effecient in grub legacy
and removing its remnants. Is fixable.

---

### Post by websnake on 2010-09-21
> **garvinrick4 said:**
> So lets try to get rid of any grub legacy. While in Ubuntu run.
```
sudo upgrade-from-grub-legacy       
```Should say installing grub to your first hard drive
Installation finished no error reported
hdo  /dev/sda

Should i run ubuntu form live cd or the one installed on my harddrive???

---

### Post by garvinrick4 on 2010-09-21
> **websnake said:**
> Should i run ubuntu form live cd or the one installed on my harddrive??? Hard drive

---

### Post by websnake on 2010-09-21
when i run the code it says

```

sudo: upgrade-from-grub-legacy: command not found

```

---

### Post by garvinrick4 on 2010-09-21
```
sudo upgrade-from-grub-legacy
```copy and paste just tried and it works.

To sda like usuall and it will say grub legacy removed after 2nd page when it auto runs update-grub
just ran on my machine to test.

---

### Post by websnake on 2010-09-21
> 
     Code:
     sudo upgrade-from-grub-legacy 
copy and paste just tried and it works.

To sda like usuall and it will say grub legacy removed after 2nd page when it auto runs update-grub
just ran on my machine to test.still not working......(see attachments)
somethings wrong (maybe somethings missing :-k ).

---

### Post by garvinrick4 on 2010-09-21
Try this with yes to chainload if asks.

```
sudo apt-get install grub2       
``````
sudo update-grub  
```

---

### Post by websnake on 2010-09-21
your code worked but now i can't boot anything no windows 7 no ubuntu only "Black Screen".


sorry just joking mission accomplished =D> the command worked and now i can boot both operating system tested and working flawlessly.

thanks garvinrick4 for your great support :) .

---

### Post by garvinrick4 on 2010-09-21
That first line was scary!!! 

Your welcome websnake mark as solved please. That one took some time.

---

### Post by websnake on 2010-09-21
> **garvinrick4 said:**
> Your welcome websnake mark as solved please. That one took some time.

Sure ;) .

---

### Post by websnake on 2010-09-21
Ok my problem is solved but can any one explain what was happening with my computer.
 
(it will help me understand if something goes wrong in future.)

---

### Post by garvinrick4 on 2010-09-21
> **websnake said:**
> Ok my problem is solved but can any one explain what was happening with my computer.
 
(it will help me understand if something goes wrong in future.) Answered in the email you sent to me websnake a few moments ago in long version. Short version for here is grub2 and grub legacy do not work together nicely out of the box. Seems to me it went very smoothly from 9.04 to 9.10 on dist-upgrade. 9.10 has grub2 and I did not see the grub legacy in your 9.10 until boot script was run. Should have had you run it earlier in session. All worked out just took more time. That easyBCD is a pain also. Did not know you ran until later in Thread. If anyone is reading this that is going to install a fedora or OpenSuSe  with grub legacy just choose not to install grub when installing those that use legacy instead of grub2. It is a choice I know for certain in fedora and OpenSuse as for others look deeply for the no grub install. Then boot into grub2 install and update-grub as to get your installs into grub config.

---

### Post by websnake on 2010-09-22
Thanks garvinrick4 for explaining and clearing my doubts.

here is another boot script result after the problem is solved.

---

### Post by apverma13 on 2010-09-23
I have installed ubuntu 10.04LTS along with windows 7. but during  startup when i select window 7's entry in grub my computer restarts.

i have tried update-grub but nothing changes.


   ```

                     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1615. But according to the info from fdisk, 
                       sda6 starts at sector 61450240.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             208,894   156,280,319   156,071,426   f W95 Ext d (LBA)
/dev/sda5          20,482,938    61,448,624    40,965,687   b W95 FAT32
/dev/sda6          61,450,240   102,412,287    40,962,048   7 HPFS/NTFS
/dev/sda7         102,414,438   156,280,319    53,865,882   b W95 FAT32
/dev/sda8             208,896    20,482,047    20,273,152  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9468456A68454C64                       ntfs       System Reserved               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        A0C9-1144                              vfat       MOVIES                        
/dev/sda6        58E04887E0486D76                       ntfs                                     
/dev/sda7        0CB3-B441                              vfat       SOFTWARES                     
/dev/sda8        12c1f332-3bd9-4768-adf0-50dde0df15fc   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /media/SOFTWARES         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=12c1f332-3bd9-4768-adf0-50dde0df15fc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 12c1f332-3bd9-4768-adf0-50dde0df15fc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9468456a68454c64
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


   7.1GB: boot/grub/core.img
   7.1GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.32-21-generic
   7.7GB: boot/vmlinuz-2.6.32-21-generic
   7.9GB: initrd.img
   7.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  31 a2 35 85 f6 bc 50 88  fa 7f 50 db 4a 10 83 a6  |1.5...P...P.J...|
00000010  24 ea 02 65 7c 7c 7d 1e  2d 2f da db cc 3c b3 17  |$..e||}.-/...<..|
00000020  39 1c 9a 4e 43 96 ac 8a  f6 48 7d e9 30 c8 9a e0  |9..NC....H}.0...|
00000030  4d 27 d1 60 93 11 c9 18  78 4f 30 66 a6 49 70 d3  |M'.`....xO0f.Ip.|
00000040  c4 40 6e 59 bb 9e ba 5a  f0 13 be ae 8b 4d d9 38  |.@nY...Z.....M.8|
00000050  47 13 45 a1 b0 6b 79 13  f1 a5 85 58 ca 86 07 51  |G.E..ky....X...Q|
00000060  77 7d 9b 27 0b b2 ed 1a  e0 c1 fc 15 f1 8e ef 15  |w}.'............|
00000070  8c c3 48 44 ab 27 26 6c  bd 6a 9e 91 22 67 f9 34  |..HD.'&l.j.."g.4|
00000080  42 a3 25 ed e7 d5 f5 0d  ad 80 e0 c7 36 c6 cf 60  |B.%.........6..`|
00000090  c5 3e 4b dd be c1 8d c7  d6 f4 45 7c ae 1a 14 dc  |.>K.......E|....|
000000a0  41 f4 05 d9 70 63 a3 e3  1c f1 9f 75 35 f7 43 d9  |A...pc.....u5.C.|
000000b0  b7 7d 20 1b 75 1a 7a 34  b1 a5 ae e3 0d 7d 87 d7  |.} .u.z4.....}..|
000000c0  2b fd 3f 7b af d4 53 11  96 1c 42 37 56 9e 9c 5f  |+.?{..S...B7V.._|
000000d0  65 31 0e 16 3e 55 9f d6  21 3d 6b 72 52 40 53 06  |e1..>U..!=krR@S.|
000000e0  5e 9c c6 d1 04 82 5c 91  89 97 af 81 20 d2 cd 77  |^.....\..... ..w|
000000f0  33 21 71 3d 8d 6d 8c 15  6f 2d 9a 79 bb 94 92 50  |3!q=.m..o-.y...P|
00000100  8f 2f 9e 77 22 d1 9e 5b  fa 59 ed 92 d4 2e ec 9b  |./.w"..[.Y......|
00000110  88 bc 9e 08 e8 d5 e8 c2  5d 6e 76 c6 77 cb 9c b7  |........]nv.w...|
00000120  ac 11 6f a3 34 47 9d 80  ca af fb 4a e9 d7 c3 ce  |..o.4G.....J....|
00000130  e1 09 55 7c a0 77 72 8a  82 2e 1c 73 39 8d 29 26  |..U|.wr....s9.)&|
00000140  dd a1 51 8e 08 f8 31 be  95 fe 07 41 ad 58 56 1f  |..Q...1....A.XV.|
00000150  59 1f 8a de 04 71 d5 ff  50 c3 8a 91 f3 60 b7 74  |Y....q..P....`.t|
00000160  23 e5 e9 76 a6 5b b7 49  4a 18 10 07 f7 6c 8f 3e  |#..v.[.IJ....l.>|
00000170  65 3d 2b 74 84 66 08 65  41 83 6f 4a 51 65 c4 e9  |e=+t.f.eA.oJQe..|
00000180  cf 65 ec 99 df e5 93 c3  a8 f6 c4 f0 ac 9d 46 f6  |.e............F.|
00000190  4a 74 db eb 43 a0 2a dd  07 8d 3d d9 91 06 2c 68  |Jt..C.*...=...,h|
000001a0  53 cc 2f ba cb 34 5c 96  c7 97 ef d4 23 16 af c3  |S./..4\.....#...|
000001b0  4b e6 5a d9 26 92 4e 6c  6b 46 6b 63 eb 85 00 df  |K.Z.&.NlkFkc....|
000001c0  d3 ff 0b df d3 ff 7c 5b  35 01 37 16 71 02 00 df  |......|[5.7.q...|
000001d0  d3 ff 05 df d3 ff b3 71  a6 03 4f 0e 71 02 00 00  |.......q..O.q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200 
```


help me out please

---

### Post by arubislander on 2010-09-23
@apverma13: This thread is already marked solved so chances are no one with the know how will see it here. Start a new thread and ask for help there. Good luck.

---

### Post by apverma13 on 2010-09-23
yes i realised that. thank you

---

