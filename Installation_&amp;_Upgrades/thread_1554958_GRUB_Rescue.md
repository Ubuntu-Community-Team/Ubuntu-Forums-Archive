---
title: "GRUB Rescue"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Shelton2142 on 2010-08-17
A couple months ago I ordered a CD and installed Ubuntu 10.4 alongside Windows XP. I had some issues with multiple incorrect bootloader menus and sought some help, but unfortunately I ended up being an idiot and not reading instructions correctly.

I tried to use this command.

sudo grub-install --root-directory=/media/sda5 /dev/sda

Now I am stuck in GRUB rescue with "file not found". Fairly sure I had just wiped my hard drive, I tried to boot Ubuntu from the CD. However, when I put the CD in the drive, the disk does not read, nor does the drive even spin up.

After looking around for other posts on this issue, I found my way to [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode). I attempted some of the commands that it said only work in GRUB rescue, but every command I try is met with "unknown command".

---

### Post by Cavsfan on 2010-08-17
First try  entering  **insmod normal**

Then if you can post results of:

sudo fdisk -l

---

### Post by Shelton2142 on 2010-08-17
unknown command 'sudo'

That's what I get. Apparently GRUB rescue does not recognize spaces. Also, is that an I or a 1?

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> unknown command 'sudo'

That's what I get. Apparently GRUB rescue does not recognize spaces. Also, is that an I or a 1?

Were you able to enter **insmod normal** and get the regular grub command?

sudo fdisk -l is with a small letter L

---

### Post by Shelton2142 on 2010-08-17
When I do that it repeats "file not found".

---

### Post by Cavsfan on 2010-08-17
You need **drs305** to help. He could fix this in a matter of minutes.
I'll see if I can find him.

---

### Post by Cavsfan on 2010-08-17
Hopefully he will stop by in a few. Then after he fixes you up, you can check out the tutorial in my signature.

But, we have to get you able to boot up first.

I wish I knew more about fixing grub when it's messed up!  ](*,)

---

### Post by drs305 on 2010-08-17
From the LiveCD, please download and run the *boot info script* from this site:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

It will generate a file called "Results.txt" and give us a good idea of what is happening. Post the contents of the file in this thread, between "code" tags. You generate the tags by pressing the **#** icon in the post's menu.

---

### Post by Shelton2142 on 2010-08-17
I'm currently not able to make my computer run from the CD. I've had the CD in the drive the whole time I've been in this conversation, but so far the disk drive doesn't spin up. Maybe I just don't understand exactly what I'm being told to do.

---

### Post by Cavsfan on 2010-08-17
Thanks **drs305**! I hope I did not bug you! I will watch, take notes and hopefully learn this time.

---

### Post by drs305 on 2010-08-17
> **Shelton2142 said:**
> I'm currently not able to make my computer run from the CD. I've had the CD in the drive the whole time I've been in this conversation, but so far the disk drive doesn't spin up. Maybe I just don't understand exactly what I'm being told to do.

Does the CD work in another computer?

If it's not spinning at all, you may have to change the BIOS settings to allow the CD to boot first. How to enter BIOS setup varies by system, but it's usually it is by pressing the DEL key or one of the function F** keys as the computer starts. If you can get into BIOS, find the boot options and set the system to boot from the CD drive first.

Added: I'm going to be away for a bit but will check in a few hours. There are a number of helpers on here who are excellent at interpreting the Results.txt contents who may reply before then.

---

### Post by Shelton2142 on 2010-08-17
The CD has run in both the computer I broke and the laptop I am currently using to post here. I just don't install it on the laptop because there isn't enough space.

Okay, I managed to get into BIOS. I have 3 options in the menu under Boot.

Boot Device Priority
Boot Settings Configuration
Security

In Device Priority, there are 3 listed devices.

floppy drive
sata:3m-wdc wd3200
cdrom: pm-atapi ihd

I switched the CD to first priority and now the computer is running from the disk. That first hurdle is finally fixed.

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> The CD has run in both the computer I broke and the laptop I am currently using to post here. I just don't install it on the laptop because there isn't enough space.

Okay, I managed to get into BIOS. I have 3 options in the menu under Boot.

Boot Device Priority
Boot Settings Configuration
Security

In Device Priority, there are 3 listed devices.

floppy drive
sata:3m-wdc wd3200
cdrom: pm-atapi ihd

Yes, you want to make the cdrom first. I have mine that way normally.
That is the problem, right now it is taking the HD option.

---

### Post by Shelton2142 on 2010-08-17
Well, now I have the boot info script and I'm in the Terminal about to use the command 

sudo bash [path/to/the/download_folder]/boot_info_script*.s

I'm not familiar with Ubuntu enough for this. What is the name of the default path to the download folder in a LiveCD session?

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> Well, now I have the boot info script and I'm in the Terminal about to use the command 

sudo bash [path/to/the/download_folder]/boot_info_script*.s

I'm not familiar with Ubuntu enough for this. What is the name of the default path to the download folder in a LiveCD session?

Where did you download it? If it went to home then it would be ~/home/**your user goes here**/boot_info_script*.s

---

### Post by Shelton2142 on 2010-08-17
Would the user of a LiveCD be named "ubuntu"? because that's the parent folder of my downloads.

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> Would the user of a LiveCD be named "ubuntu"? because that's the parent folder of my downloads.

Yes, try plugging that in place of **your user goes here **and see if that does the trick.

---

### Post by Shelton2142 on 2010-08-17
okay, I seem to keep mistyping the path, because I keep coming up with "no such directory exists". should the path be 

file_system/home/ubuntu/downloads/boot_info_script

---

### Post by drs305 on 2010-08-17
Most likely the command will be:
```
sudo bash ~/Desktop/boot_info_script*.sh
or 
sudo bash ~/Downloads/boot_info_script*.sh
```

since most downloads are either to the Desktop or the user's Downloads folder.

---

### Post by Shelton2142 on 2010-08-17
Got it!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /media/sda5/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,020   447,304,905   178,890,886   7 HPFS/NTFS
/dev/sda3         447,305,726   625,141,759   177,836,034   5 Extended
/dev/sda5         447,305,728   617,814,015   170,508,288  83 Linux
/dev/sda6         617,816,064   625,141,759     7,325,696  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        14A48F43A48F25F8                       ntfs       Local Disk                    
/dev/sda2        506CD7DA6CD7B8C4                       ntfs       New Volume                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        baaf6d96-6112-4a47-9206-6885c352dc08   ext4                                     
/dev/sda6        8d2d7718-c09c-4219-a553-dce7ee34ff77   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\ubnldr.mbr="UNetbootin" 
C:\wubildr.mbr = "Ubuntu" 

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
search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
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
search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=baaf6d96-6112-4a47-9206-6885c352dc08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=baaf6d96-6112-4a47-9206-6885c352dc08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=baaf6d96-6112-4a47-9206-6885c352dc08 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=baaf6d96-6112-4a47-9206-6885c352dc08 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set baaf6d96-6112-4a47-9206-6885c352dc08
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 14a48f43a48f25f8
    drivemap -s (hd0) ${root}
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
UUID=baaf6d96-6112-4a47-9206-6885c352dc08 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d2d7718-c09c-4219-a553-dce7ee34ff77 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 308.6GB: boot/grub/core.img
 259.5GB: boot/grub/grub.cfg
 308.6GB: boot/initrd.img-2.6.32-21-generic
 308.6GB: boot/initrd.img-2.6.32-22-generic
 308.6GB: boot/vmlinuz-2.6.32-21-generic
 308.6GB: boot/vmlinuz-2.6.32-22-generic
 308.6GB: initrd.img
 308.6GB: initrd.img.old
 308.6GB: vmlinuz
 308.6GB: vmlinuz.old 
```

Maybe now I can figure out just how stupid I was with all of this.

---

### Post by drs305 on 2010-08-17
Things look normal in Results.txt.  It looks like you have/had Wubi installed at one point, but now you are trying to use a regular Ubuntu installation.

Since things look ok, what I normally recommend is removing and reinstalling Grub2 just to 'reset' everything. Reviewing this thread from the beginning, I see the command you used to install included "/media/sda5".

Had you previously mounted /dev/sda5 on /media ?  I ask because most of the examples we use here are for /mnt.  /media is ok, if that is where you mounted it before running the command in the first post.

If you aren't sure, I'd suggest trying to run the install command again from the LiveCD, since that is the easiest way to do it. Use these commands from the LiveCD Desktop:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note it is **sda5** in the first command, and only **sda** in the second.

If this still doesn't work, then we can use *chroot* and remove and reinstall grub-pc into your real partition from the LiveCD. It involves a few more commands but it isn't difficult. But first try the above.  In the meantime, I'll prepare the chroot instructions.  ;-)

---

### Post by Shelton2142 on 2010-08-17
I don't think I had it previously installed on /media, but to be honest I don't know anymore. That command was not used to install the OS. It was used after the OS was already installed, because I had that multiple boot menu problem and I thought it was supposed to fix it and move everything into one menu. Unfortunately, I wasn't paying close enough attention to the instructions, and was supposed to use an XP installation CD and use that to repair the menus.

I'm an extreme novice when it comes to terminal commands. I wasn't sure if I was supposed to use that command one line at a time. This is what I got.

mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt sda
/usr/sbin/grub-probe: error: cannot stat `sda'.
Invalid device `sda'.
Try `/usr/sbin/grub-setup --help' for more information.

---

### Post by oldfred on 2010-08-17
I do not think I have ever seen /media reported in the MBR as the boot script shows.

The commands I have are

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I think drs305 left off the /dev/ in the last command. I cut and paste from a text file to try to avoid memory errors (note oldfred), but still sometimes try updating to specific examples and mistype something.

---

### Post by Shelton2142 on 2010-08-17
When running

sudo grub-install --root-directory=/mnt /dev/sda

It reported no errors and that installation was fine. I do warn that when I ran the command that broke the computer in the first place, it also stated that no errors were detected. I'm not sure what's going to happen when I restart the computer. In fact, I'm very reluctant to restart until I get another response from drs305.

Also, another question. When I restart to check if the bootloader is fixed, do I have to go back to BIOS to change the boot order back to the default, or do I just remove the CD prior to restarting?

---

### Post by Cavsfan on 2010-08-17
> **oldfred said:**
> I do not think I have ever seen /media reported in the MBR as the boot script shows.

The commands I have are

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I think drs305 left off the /dev/ in the last command. I cut and paste from a text file to try to avoid memory errors (note oldfred), but still sometimes try updating to specific examples and mistype something.

Glad to see you **oldfred** and thanks for helping! I knew that between you and **drs305**, you'd be able to get this fixed.

BTW, someone asked me about making the Grub2 font size bigger and I didn't think there was a way.
But, I found on **drs305**'s GRUB 2 tutorial a forum member that goes by **Riskable **was able to figure that out.
So, I added a step 7 to my tutorial that makes the font larger.

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> When running

sudo grub-install --root-directory=/mnt /dev/sda

It reported no errors and that installation was fine. I do warn that when I ran the command that broke the computer in the first place, it also stated that no errors were detected. I'm not sure what's going to happen when I restart the computer. In fact, I'm very reluctant to restart until I get another response from drs305.

Also, another question. When I restart to check if the bootloader is fixed, do I have to go back to BIOS to change the boot order back to the default, or do I just remove the CD prior to restarting?

Just remove the CD. That is what I always do. No need to jack with the Bios this way.
If you want to boot up on CD, put it in, if not, take it out. Works well from my perspective.

---

### Post by Shelton2142 on 2010-08-17
SUCCESS! Woo!

That command fixed everything. I just restarted and now I can boot back into windows and Ubuntu without any issues, and all of the stuff in my hard drive is still there. Thanks guys!

---

### Post by drs305 on 2010-08-17
> **oldfred said:**
> 
I think drs305 left off the /dev/ in the last command.

Yep, did it again! I guess I'm going to just have to cut/paste from now on; or else submit all my posts through *oldfred*!  By the way, I could probably use *olddrs305* but it would be an understatement...

Just a note on the original mountpoint. It doesn't really matter where the partition is mounted as long as the same mountpoint is repeated in the root-directory part of the second command. But since /media isn't what is normally used, I suspected that might be the problem.

Shelton2142:  :-)

---

### Post by Cavsfan on 2010-08-17
> **Shelton2142 said:**
> SUCCESS! Woo!

That command fixed everything. I just restarted and now I can boot back into windows and Ubuntu without any issues, and all of the stuff in my hard drive is still there. Thanks guys!

I wasn't much help, but I am very glad they got you fixed up! The last time I messed something up, instead of 
taking the safe route like you did, I just did a clean install and lost a bunch of stuff I did not really want to loose.

Be sure and check out the tutorial in my sig. as it makes it a lot easier and you can make it look pretty cool too.
Better than just black and white or blue and white, whatever the default is.

---

