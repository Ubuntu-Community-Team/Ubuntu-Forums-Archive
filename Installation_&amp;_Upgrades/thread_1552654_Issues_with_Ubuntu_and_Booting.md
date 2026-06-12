---
title: "Issues with Ubuntu and Booting"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Joejo on 2010-08-13
I took a 250gb external hard drive and installed Ubuntu 10.04 onto it. Everything went fine and great, downloaded flawlessly. I go to restart, everything goes fine. I go into the BIOS screen and there was no USB boot...Is there a way i can boot Ubuntu from USB from my computer even though i couldnt find on the BIOS?

Computer:
ASUS G60 series
Intel Quad Core i5
2.27GHz
4GB ram
External:
Hitachi 250gb 

any help would be great.

---

### Post by Joejo on 2010-08-14
....No one can help me?

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> I took a 250gb external hard drive and installed Ubuntu 10.04 onto it. Everything went fine and great, downloaded flawlessly. I go to restart, everything goes fine. I go into the BIOS screen and there was no USB boot...Is there a way i can boot Ubuntu from USB from my computer even though i couldnt find on the BIOS?

Computer:
ASUS G60 series
Intel Quad Core i5
2.27GHz
4GB ram
External:
Hitachi 250gb 

any help would be great.
Is that a G60J, Jx or VX?

---

### Post by Joejo on 2010-08-14
> **MAFoElffen said:**
> Is that a G60J, Jx or VX?


it is the G60JX model.

---

### Post by Joejo on 2010-08-14
Found out hit esc brings me to another boot menu, but now ubuntu will not boot, just a black screen with a flashing underscore...

---

### Post by MAFoElffen on 2010-08-14
For the G60J it's- Get into Bios setup> select "Boot" tab > Go down to "Boot Device Priority" and hit "enter"...  That will open the "Boot Device Priority" screen.  On that screen, hit enter on the first device line.  It will open a selection box with 4 options: Hard Drive, CD/DVD, Removable Device and Network... arrow down to "Removable Device" and press "enter."  Press "esc" once > Goto the "Exit" tab and save your changes.

The G60Jx and Vx should be similar.  "Removable Device" = USB.  Tell me if this gets your going.

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> Found out hit esc brings me to another boot menu, but now ubuntu will not boot, just a black screen with a flashing underscore...
Like a cursor in the upper left hand corner?  When in the boot?  Before the GRUB Menu first or after it?

---

### Post by Joejo on 2010-08-14
> **MAFoElffen said:**
> Like a cursor in the upper left hand corner?  When in the boot?

When I restart i hold 'esc' and it brings up a different menu with boot options, I see the external "Hitachi". I chose that because its what I installed the Ubuntu 10.04 on. Then next thing that happens is the screen goes black and there is only an underscore that blinks, I tried waiting thinking it is only loading up, but after 15 minutes nothing happened. I tried re-installing on the same external thinking maybe the first time something happened and it failed. But, i guess its something with the GRUB, i dont know...I hope someone could help me with it.

---

### Post by MAFoElffen on 2010-08-14
After you select the drive from your "popup" BIOS Boot menu, press F6 and see what happens.  What is the video on that?  I know it's a "gaming" notebook...

---

### Post by Joejo on 2010-08-14
> **MAFoElffen said:**
> After you select the drive from your "popup" BIOS Boot menu, press F6 and see what happens.  What is the video on that?  I know it's a "gaming" notebook...
It has a Nvidia geforce gts 360m 1gb video card on it.

---

### Post by MAFoElffen on 2010-08-14
I have NVidia also... easy.  !st- Are you getting a GRUB Menu at all?

---

### Post by Joejo on 2010-08-14
> **MAFoElffen said:**
> I have NVidia also... easy.  !st- Are you getting a GRUB Menu at all?
No, not at all. In the BIOS set up there isnt even a selection for a USB boot, In the "popup" boot menu that i have to press esc at restart to get, I get the option of the external to boot from. But when i select it the screen just goes black and i get the blinking underscore, i cant even type anything. 

I looked all over, i googled to see if im doing anything wrong, i even went to youtube and followed the same exact protocol, step by step, on how to install Ubuntu 10.04 to an external. But at the end of it i do not get a GRUB menu. 

And no one has really helped me other than you. If you can help me fix it to where it works i would be very grateful to you.

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> No, not at all. In the BIOS set up there isnt even a selection for a USB boot, In the "popup" boot menu that i have to press esc at restart to get, I get the option of the external to boot from. But when i select it the screen just goes black and i get the blinking underscore, i cant even type anything. 

I looked all over, i googled to see if im doing anything wrong, i even went to youtube and followed the same exact protocol, step by step, on how to install Ubuntu 10.04 to an external. But at the end of it i do not get a GRUB menu. 

And no one has really helped me other than you. If you can help me fix it to where it works i would be very grateful to you.
First... go back to my post on your BIOS.  ASUS has it as "Removable Device" not USB Boot.  That will set it up in BIOS so you don't have to hit the BIOS Boot Popup each time.

Second, can you run a LiveCD?  If you can, bring it up and look at \boot\grub\grub.cfg by ```
sudo gedit
```in a terminal and then open that file from your removable drive...

Look for the section after "### BEGIN /etc/grub.d/10_linux ###"  In it should be a line similar to this:```
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro   [COLOR=Red]quiet splash[/COLOR]
```edit it to remove "quiet splash" and type in it's place "nomodeset".  Save the file and exit.  Shutdown and reboot. See what it does.  

If you can't boot up from a LiveCD, you can edit it from XP Notepad, but you have to change the file properties beforehand to do it...

If it works, I'll tell you "what" to change "where," to make it permanent in GRUB- otherwise than change is just going to get overwritten when grub does a reconfig...

---

### Post by Joejo on 2010-08-14
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro   nomodeset
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set acd01140d01111e6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

I changed the settings and restarted, i had to boot again from the livecd since the boot menu on the BIOS doesnt have a third option for boot 'removable device'

but, i did change from 'quietsplash' to 'nomdodeset'

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> I changed the settings and restarted, i had to boot again from the livecd since the boot menu on the BIOS doesnt have a third option for boot 'removable device'

That's not in the BIOS Popup that comes up with the ESC key, that's in the BIOS "Setup". (LOL)

> **Joejo said:**
> but, i did change from 'quietsplash' to 'nomdodeset'
And did it boot Ubuntu?

---

### Post by Joejo on 2010-08-14
No, it still doesnt boot Ubuntu.

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> No, it still doesnt boot Ubuntu.
Okay... do this.  When you are booting Ubuntu, hold down the "shift" key.  That should bring up the grub menu. 
- Type "e" on the first menu line.  
- Type "c" which will get you to a grub command line.
- From the command prompt, type "null (hd" then press the "TAB" button. That will autocomplete the info of your available drives.  It should show your 2 drives.  Write the info down and tell me what it says...

Cntrl-c's will get you out of there...

---

### Post by theozzlives on 2010-08-14
It sounds like your GRUB installed on SDA instead of SDB. You need to check your  Windows to see if it boots ok. If you get the GRUB menu, then you need to install GRUB to SDB. And restore your MBR on SDA.

---

### Post by MAFoElffen on 2010-08-14
> **theozzlives said:**
> It sounds like your GRUB installed on SDA instead of SDB. You need to check your  Windows to see if it boots ok. If you get the GRUB menu, then you need to install GRUB to SDB. And restore your MBR on SDA.
But if it installed the Grub Boot to sda it would get a "Miising boot disk" error on booting sdb as the boot drive in BIOS (if it was missing on that disk)...  but the grub menu would come up if he booted from the internal hard disk  (sda) right?

If it did install to sda then everything would work from a Grub2 menu from booting the internal drive.  If it installed to sda1 it would have overwwritten the XP boot sector in that partition and he would be able to start XP...

He could run bootscritpt to locate and verifiy where the boot records are... and to verify what the MBR's have.

---

### Post by Joejo on 2010-08-14
> **MAFoElffen said:**
> Okay... do this.  When you are booting Ubuntu, hold down the "shift" key.  That should bring up the grub menu. 
- Type "e" on the first menu line.  
- Type "c" which will get you to a grub command line.
- From the command prompt, type "null (hd" then press the "TAB" button. That will autocomplete the info of your available drives.  It should show your 2 drives.  Write the info down and tell me what it says...

Cntrl-c's will get you out of there...

When i booted Ubuntu and held shift it only brought me to another loading screen that asked if i wanted to install, try and not install. But nothing that had to do with a grub menu. 
Everything was installed onto the External. I have no problems booting Windows.

---

### Post by MAFoElffen on 2010-08-14
> **Joejo said:**
> When i booted Ubuntu and held shift it only brought me to another loading screen that asked if i wanted to install, try and not install. But nothing that had to do with a grub menu. 
Everything was installed onto the External. I have no problems booting Windows.From that menu you should be able to get to a "Boot Options" screen that you can edit, but no matter. 

OK... Try this first:
> **oldfred said:**
> Just to confirm what is installed where, from LiveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's  menu and then paste the contents between the generated [ code][ /code]  tags.
And post the results here...

---

### Post by Joejo on 2010-08-14
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    40,965,749    40,963,702  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,750   976,771,119   935,805,370   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sdb2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sdb5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        ACD01140D01111E6                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2863f089-84b9-4f70-aee3-d38b1d7cb2da   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f027579a-95aa-48b2-b566-b6d93499e48e   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        687C074D7C07160A                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro   nomodeset
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set acd01140d01111e6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f027579a-95aa-48b2-b566-b6d93499e48e none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
  86.0GB: boot/grub/grub.cfg
  86.0GB: boot/initrd.img-2.6.32-21-generic
  86.0GB: boot/vmlinuz-2.6.32-21-generic
  86.0GB: initrd.img
  86.0GB: vmlinuz



this is the results of what you gave me, downloaded and used on the LiveCD

---

### Post by MAFoElffen on 2010-08-14
Hmm- Everything looks good on sda for XP and sdb for Ubuntu...  That confirmed that the Windows MBR is Ok on your first drive.  It also confirmed that the Grub2 bootloader installed to the MBR of your second drive and that it is correctly looking in your Ubuntu partion for the "grug,cfg".  The grub.cfg looks good.

With "quiet splash" taken out, on Ubuntu boot, it should be echoing all it's doing before it "freezes" to the screen.  Didn't you say the current error is "what"?  On a device init or on a mount?  I think I saw a mount error, but that was after an interupt 15, which would be a user shutdown...

---

### Post by Joejo on 2010-08-14
Well, i Installed twice to the same hard drive and followed the instructions but the same issue keeps coming up as just a black screen with a blinking underscore. I dont know what the issue could be if everything i coming out correctly...sould i re-install a third time but inside the LiveCD instead of a straight install...I dont know what else it could be.

---

### Post by MAFoElffen on 2010-08-14
EDIT: From your posted results, the system "install" is good... I think the graphics mode is stopping you.  Installing again is not getting you anywhere.

Please post (cut and paste) what these two files say (text) from your sdb1:
/etc/X11/Xsession.d/xorg.conf
/var/log/Xorg.0.log

Please, this time post them within some "code" tags.  If you post in advanced mode, press the "#" icon and cut/paste between the tags...

---

### Post by Joejo on 2010-08-14
Where would i find those files?

I went into my external that has the Ubuntu installed and it has the etc/x11/xsession.d and when i go into that file there is no xorg.conf

same with var/log
there is no file with xorg.0.log


on the LiveCD its obviously there is that the one you want

---

### Post by MAFoElffen on 2010-08-15
> **Joejo said:**
> Where would i find those files?

I went into my external that has the Ubuntu installed and it has the etc/x11/xsession.d and when i go into that file there is no xorg.conf

same with var/log
there is no file with xorg.0.logSorry- My fault. ::embarrassed:: "xorg,conf" is in "/etc/X11/" Mine looks like this: 
[HTML]# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/HTML]Yours (a fresh install) is going to look more like this:
```
###           This is my failsafe xorg.conf            ###
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Then each time you boot it will create other logs into "/var/log/"  For Xorg, it creates an Xorg.x.log, with "x" being "0" for current or last and +1 (or 1, 2, 3, 4, 5) to each older- each time it boot., it also appends/renames the past files as  xorg.x.log.old to older logs.  Here is an example of my xorg.0.log:
[HTML]X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux maf-ubuntu-01 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 14 18:57:01 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:3:0:0) 10de:00f9:1682:2120 nVidia Corporation NV45 [GeForce 6800 GTO] rev 162, Mem @ 0xd7000000/16777216, 0xb0000000/268435456, 0xd6000000/16777216, BIOS @ 0x????????/131072
(--) PCI:*(0:6:0:0) 10de:00f9:1682:2120 nVidia Corporation NV45 [GeForce 6800 GTO] rev 162, Mem @ 0xdf000000/16777216, 0xc0000000/268435456, 0xde000000/16777216, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 06@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Aug 14 18:57:01 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 14 18:57:01 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 14 18:57:01 NVIDIA(0):     enabled.
(II) Aug 14 18:57:03 NVIDIA(0): NVIDIA GPU GeForce 6800 Ultra (NV40) at PCI:6:0:0 (GPU-0)
(--) Aug 14 18:57:03 NVIDIA(0): Memory: 262144 kBytes
(--) Aug 14 18:57:03 NVIDIA(0): VideoBIOS: 05.40.02.36.08
(II) Aug 14 18:57:03 NVIDIA(0): Detected PCI Express Link width: 0X
(--) Aug 14 18:57:03 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 14 18:57:03 NVIDIA(0): Connected display device(s) on GeForce 6800 Ultra at
(--) Aug 14 18:57:03 NVIDIA(0):     PCI:6:0:0:
(--) Aug 14 18:57:03 NVIDIA(0):     HSP LM02 (DFP-0)
(--) Aug 14 18:57:03 NVIDIA(0): HSP LM02 (DFP-0): 165.0 MHz maximum pixel clock
(--) Aug 14 18:57:03 NVIDIA(0): HSP LM02 (DFP-0): External Single Link TMDS
(II) Aug 14 18:57:03 NVIDIA(0): Assigned Display Device: DFP-0
(==) Aug 14 18:57:03 NVIDIA(0): 
(==) Aug 14 18:57:03 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Aug 14 18:57:03 NVIDIA(0):     will be used as the requested mode.
(==) Aug 14 18:57:03 NVIDIA(0): 
(II) Aug 14 18:57:03 NVIDIA(0): Validated modes:
(II) Aug 14 18:57:03 NVIDIA(0):     "nvidia-auto-select"
(II) Aug 14 18:57:03 NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) Aug 14 18:57:03 NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) Aug 14 18:57:03 NVIDIA(0):     option
(==) Aug 14 18:57:03 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 14 18:57:05 NVIDIA(GPU-1): NVIDIA GPU GeForce 6800 Ultra (NV40) at PCI:3:0:0 (GPU-1)
(--) Aug 14 18:57:05 NVIDIA(GPU-1): Memory: 262144 kBytes
(--) Aug 14 18:57:05 NVIDIA(GPU-1): VideoBIOS: 05.40.02.36.08
(II) Aug 14 18:57:05 NVIDIA(GPU-1): Detected PCI Express Link width: 0X
(--) Aug 14 18:57:05 NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) Aug 14 18:57:05 NVIDIA(GPU-1): Connected display device(s) on GeForce 6800 Ultra at
(--) Aug 14 18:57:05 NVIDIA(GPU-1):     PCI:3:0:0:
(--) Aug 14 18:57:05 NVIDIA(GPU-1):     none
(II) Aug 14 18:57:05 NVIDIA(0): Initialized GPU GART.
(II) Aug 14 18:57:05 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Aug 14 18:57:05 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 14 18:57:05 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
(**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Found relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)[/HTML]If for some reason there is none.  It either means that your install was never started or it never got to an xorg init.  In that case, post your "boot.log" which is located in the same directory "/var/log"  Then we can see if there is an error happening before the xorg init.

Is that enough directions for you to get that information?

EDIT/ADD:  This info should tell just where your PC is erroring out/hanging.  Go ahead and post the "boot.log" so we don't have to go another post in case it's needed.  

My thoughts on this are:  Like I said, the system itself looks good as far as GRUB and Ubuntu is concerned (the basic files and layout/whats installed where).  This seems more a hardware/driver type of problem, where I need to see what the problem is and see if we can use a startup option to get around it in order for you to get going long enough to install the driver you need -- that will correct it in the long run.  For instance if it's the graphics driver, to get it going so you can install the specific graphics driver for your hardware...

---

### Post by Joejo on 2010-08-15
ok, i went into the ect/x11 there is nothing containing xorg
you can see in the picture if it attached

i also went into the var/log file but there was nothing there with xorg also

i did find the boot file and when i opened it there was nothing in it

"Nothing has been logged yet."

---

### Post by MAFoElffen on 2010-08-15
> **Joejo said:**
> ok, i went into the ect/x11 there is nothing containing xorg
you can see in the picture if it attached

i also went into the var/log file but there was nothing there with xorg also

i did find the boot file and when i opened it there was nothing in it

"Nothing has been logged yet."
Strange... Wait one, I'm on my desktop- bringing up my laptop on a generic Ubuntu 10.04.

---

### Post by Joejo on 2010-08-15
ok im still here on the LiveCD

---

### Post by MAFoElffen on 2010-08-15
OK... Lets back up a bit.  Take a screenshot of the "disk utility" window (gparted) when you are displaying your external disk, with your Ubuntu system's partition highlighted... example:

---

### Post by Joejo on 2010-08-15
Ok. here it is.

---

### Post by MAFoElffen on 2010-08-15
Let's see, the drive is bootable- the partition is marked bootable.  The  Bootinfoscript reports that Grub2 is installed in the MBR of sdb and is pointed to your Ubuntu system partition to where the grub.cfg is present... But the grub menu "never" boots.  I guess you could reinstall/recover the Grub2 boot...

Okay, so from your LiveCD session, goto Places> and select your "240GB Filesystem"... That will mount it.

Open a terminal session and type:
```
mount | tail -1
``` Should come out with output such as:
```
/dev/sda1 on /media/[COLOR=Red]2863f089-84b9-4f70-aee3-d38b1d7cb2da[/COLOR] type ext4 (rw,nosuid,nodev,uhelper=udisks)
```Which i edittted with your UUID... so it should be resulting in that "2863f089-84b9-4f70-aee3-d38b1d7cb2da"... [COLOR=Red]If you get a different UUID when you type the "Mount" command, STOP immediately (don't go on with the other instructions!!!) and tell me!!![/COLOR]
Next type in ```
ls /media/2863f089-84b9-4f70-aee3-d38b1d7cb2da/boot
```and you should see a directory listing of your external drives boot directory, with a highlighted "grub" in it.
Next, type in: ```
sudo grub-install --root -directory=/media/2863f089-84b9-4f70-aee3-d38b1d7cb2da /dev/sdb
```That should reinstall Grub2 to your external drive.  I added in all your info from previous.  IF all goes well, shut down the LIveCD Session and try to boot up on your External Drive.

---

### Post by Joejo on 2010-08-15
Is this what i am supposed to see?

---

### Post by MAFoElffen on 2010-08-15
Yes, except I had a space-typo in the last command.  Try this (cut and paste into a terminal session):
```
sudo grub-install --root-directory=/media/2863f089-84b9-4f70-aee3-d38b1d7cb2da /dev/sdb
```

---

### Post by Joejo on 2010-08-15
eh, im still getting the blinking "_" behind a black screen when i try to boot from that external.

---

### Post by MAFoElffen on 2010-08-15
Reboot.  I'm assuming your still using the BIOS popup or not.  After you select your drive and it starts to boot, press "ESC".  See if that brings up your GRUB menu...   If grub is set with the menu "display" off, it sometimes echos "press any key..." or "press ESC to display the grub menu."  

(a) If it does, press "e" on the first line and replace the "nomodeset" with "single" and then ctrll-x to boot...  Go on to step (c)

(b) If it doesn't, Boot up on the LiveCD and re-edit the grub.cfg to change the "nomodeset" to single.  Exit LiveCD and reboot into the external drive.

(c)  Should come up in a single user mode in TTY console (simple text graphics, command line prompt).  If it does, at the prompt, type in ```
startx
```(which would be the same as typing in "init 5") ...and see if that starts your GUI.  

Tell me if that works...  
Edit: If the GUI doesn't start and stays at the prompt for some reason (knowing we're working with a suspect system config) you can shut down the machine by the command "reboot".

---

### Post by Joejo on 2010-08-15
its still not letting me boot from and it also will not let me type anything in when i get the "_" when i try to boot into the external

---

### Post by MAFoElffen on 2010-08-15
Still not even booting grub?  (Darn)  

Go here and download SuperGRUB2Disk:
 [http://www.supergrubdisk.org/wiki/SuperGRUB2Disk](http://www.supergrubdisk.org/wiki/SuperGRUB2Disk)
After creating a disk, boot up from it and use the "[FONT=Verdana][SIZE=1]Detect any GRUB2 installation (even if mbr is overwritten)[/SIZE][/FONT]" option.  See if you can boot from the grub menu it finds on your external drive...

Oh change "single" back to "nomodeset".

---

### Post by Joejo on 2010-08-15
ok, i went in, i changed back the original setting back to 'nomodeset'
i downloaded the supergrub2disk
i booted with it, took me straight to a GRUB menu
The first on the list was Ubuntu GNU/Linux and i highlighted and tried to boot into it
i got this

"loading
ERROR: Kernel not detected'

"press any key"

pressed enter got back to main menu

highlighted the 
'[FONT=Verdana][SIZE=1]Detect any GRUB2 installation (even if mbr is overwritten)'
took me back to the main menu


[/SIZE][/FONT]

---

### Post by MAFoElffen on 2010-08-16
From the screen shot you sent me of your .\boot directory, the kernel files were there... So then to get this message:
> "loading... ERROR: Kernel not detected'It started going through the menu and errored on the kernel load.  So the [COLOR=Green]root entry[/COLOR] here:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    [COLOR=Green]set root='(hd1,1)'[/COLOR]
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro   nomodeset
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2863f089-84b9-4f70-aee3-d38b1d7cb2da
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2863f089-84b9-4f70-aee3-d38b1d7cb2da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

```...Has changed physically on your laptop... Which it will, if you have "*MULTIPLE*" removable USB drives.  When you ran the "boot info script" you had an additional USB "free agent" external drive connected, didn't you.  And you still have that drive connected, but you've booted a few times since then...  So it may be that your USB Ubuntu external drive is now coming up to grub2 as "(hd2," instead of "hd1,"...

Ubuntu can adapt to that dynamic change because it goes off the device UUID, but grub is not...  When you get this fixed, remember to boot with your Ubuntu as the Only USB attached external drive... until after you boot.  USB drives are "removable media" - meaning they can be mounted and unmounted "hot," with the right precautions.

Okay:
Disconnect your "Free Agent" drive and try it again with the SuperGRUB2Disk...

---

