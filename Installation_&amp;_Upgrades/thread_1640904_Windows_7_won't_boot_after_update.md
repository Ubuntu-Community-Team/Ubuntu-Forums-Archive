---
title: "Windows 7 won't boot after update"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by shibazz on 2010-12-08
I've been successfully running dual boot with Ubuntu 10.04 and Windows 7 for a few months.

After a batch update in Ubuntu my Windows won't boot.

When I select Windows Loader in grub it initiates the Windows loading screen then after a beat the computer restarts.

I ran "repair computer" from the Windows 7 disk, and it says something like "can't repair, please contact administrator/manufacturer."

I'm in over my head with this problem. I'm afraid my newbie self needs assistance in even diagnosing the problem :/

I hope I don't have to reinstall everything. If it wasn't for Adobes bias I wouldn't even have a Windows partition.

Some basic info:
3 partitions
1. Ubuntu 10.04 64bit
2. Windows 7 64bit
3. Shared File System

Windows has the boot flag in gparted.

I don't know what update broke my system, but I do remember seeing a grub update on there. So that's probably it.

I know the information given is not adequate to diagnose the problem. When requesting information if you could provide details on how to acquire it, that would be much appreciated.

---

### Post by Rubi1200 on 2010-12-08
Hi and welcome to the forums :)

Use a LiveCD to boot the computer and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

EDIT: you don't say whether you can still boot Ubuntu. If yes, you can run the script in Ubuntu rather than from the CD.

---

### Post by shibazz on 2010-12-08
Thanks Rubi! :)

Sorry, my Ubuntu is fully operational.

I also did make a super nifty bootable USB, Linux is so cool like that. :)

I'll jump on this when I get home from work.

Thanks again.

---

### Post by Rubi1200 on 2010-12-08
No problem.

Let us know if you need anything else.

---

### Post by shibazz on 2010-12-08
Here's the results.txt generated from boot info script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   409,593,239   409,593,177  83 Linux
/dev/sda2    *    409,593,240   716,788,169   307,194,930   7 HPFS/NTFS
/dev/sda3       1,917,655,038 1,953,523,711    35,868,674   5 Extended
/dev/sda5       1,917,655,040 1,953,523,711    35,868,672  82 Linux swap / Solaris
/dev/sda4         716,788,170 1,917,646,919 1,200,858,750   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b52da3e3-ca77-4f6e-965b-6dd5116995e0   ext4                                     
/dev/sda2        6441D15A0A9C2074                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        4F4BFFB11E39A4DF                       ntfs                                     
/dev/sda5        fcd2f09a-5968-4d89-8e3c-1ebb6842deb1   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b52da3e3-ca77-4f6e-965b-6dd5116995e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6441d15a0a9c2074
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b52da3e3-ca77-4f6e-965b-6dd5116995e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fcd2f09a-5968-4d89-8e3c-1ebb6842deb1 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.7GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.9GB: boot/initrd.img-2.6.32-22-generic
  38.9GB: boot/initrd.img-2.6.32-23-generic
  40.8GB: boot/initrd.img-2.6.32-24-generic
  39.0GB: boot/initrd.img-2.6.32-25-generic
  39.0GB: boot/initrd.img-2.6.32-26-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
    .3GB: boot/vmlinuz-2.6.32-22-generic
   7.9GB: boot/vmlinuz-2.6.32-23-generic
  40.8GB: boot/vmlinuz-2.6.32-24-generic
 179.4GB: boot/vmlinuz-2.6.32-25-generic
  39.0GB: boot/vmlinuz-2.6.32-26-generic
  39.0GB: initrd.img
  39.0GB: initrd.img.old
  39.0GB: vmlinuz
 179.4GB: vmlinuz.old

```

---

### Post by Rubi1200 on 2010-12-09
Thanks for posting the results.

It seems, as you suspected, that GRUB is not picking up the Windows install.

First try this command:

```
sudo update-grub
```
If that does not add it to the menu, then try this:

```
sudo os-prober

```
Let me know what happens please.

---

### Post by shibazz on 2010-12-09
I ran both those lines, no change.

"Sudo os-prober" does list Windows 7.

However, the Windows 7 Loader was/is already present in the Grub menu as stated in line 3 of 1rst post. 

Although I did not give good detail to Windows failure booting process.

In Grub when I select Windows 7 Loader it starts to load then feeds me this error.

Status: 0xc0000225
Info: The boot selection failed because a required device is inaccessible.

Searching this error brings up two main scenarios;

1. Problems after installing Ubuntu
2. Partition problems/"corruption"

Mine occurred after the update.

On this error page I have two options (paraphrased);

1. Repair Computer 
2. Start Windows Normally.

If I try to start windows normally that's when the computer restarts.

When I try to repair from the Windows 7 disc it tells me it can't fix it.

I tried again just now to see if maybe the other repair attempt was being moody.

Nope, failure.

I hope this is solvable. Thanks so much for your help.

---

### Post by shibazz on 2010-12-10
I just found an inconsistency.

At the top of my boot info script it says Grub2 is installed in the MBR, but my grub menu when I boot up at the top says 1.98

I don't know if this means anything, thought I'd throw it out there :)

---

### Post by Rubi1200 on 2010-12-10
I am not quite sure what is going on because the results look normal.

The boot flag which Windows needs is on sda2 where it should be.

GRUB2 is installed to the MBR and points to the Ubuntu partition sda1 as it should.

(note: GRUB2 is 1.98; nothing to be concerned about there)

And, GRUB correctly identifies the Windows partition on sda2.

Moreover, all the correct boot files for Windows are also in place.

So, my conclusion?

Let's first try and purge then reinstall GRUB just in case there was some kind of glitch during the update.

You need to use the chroot method outlined in this fantastic guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If this does not get Windows booting again, there are some other options we can try, but first things first.

---

### Post by sikander3786 on 2010-12-10
Grub2 is the code-name. The current version is actually 1.98. No problem ;-)

I would recommend to boot a Windows recovery disc and perform startup repair from command line instead.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once you are able to boot Windows successfully, re-installing Grub is just a matter of 2 commands.

---

### Post by shibazz on 2010-12-11
I tried purging and reinstalling grub.

The system was exactly how it was before (Ubuntu = Boot, Windows 7 loader present in Grub, but won't boot.

Then I tried restoring the Windows 7 MBR, it was successful.

Unfortunately, Windows 7 still doesn't boot.

It gives the same error as when it tried to boot from Grub.

Neither Operating System loads now.

Can I reinstall Grub from Windows Command Prompt so I can get back into Ubuntu? Code?

Otherwise, I'll have to go to the office tomorrow to pick up my Ubuntu USB installation.

Windows 7 failing to boot on it's own can't be good.

Is this thread still relevant to Ubuntu Forums now? Can ya'll still help me? :)

---

### Post by wilee-nilee on 2010-12-11
It may be that you have a corrupted boot set up and maybe need a chkdsk as well.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

It sounds like reloading the mbr worked to boot W7 but Ubuntu if there is a setup needing a fix wont recognize it at times. Neither would the recovery disc you may have to point it at the C partition from the command line.

---

### Post by shibazz on 2010-12-11
"BootRec.exe /fixmbr" Command Prompt yields:

```
The operation completed successfully.
```When I run "chkdsk /r" Command Prompt says:

```
The type of the file system is NTFS.
Cannot lock current drive.
Windows cannot run disk checking on this volume because it is write protected.
```I am unsure whether to continue all Willie Nillie like, because of the error from "chkdsk /r". :)

Or, should I be addressing this "write protection"?

Standing by for illumination. :)

---

### Post by shibazz on 2010-12-11
Willie Nillie, I ran the rest of the code here was the Command Prompt output:

```
BootRec.exe /fixboot
The Operation completed successfully.

BootRec.exe /ScanOs
Scanning all disks for Windows Installations.

Please wait, since this may take a while...

Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation completed successfully.

BootRec.exe /RebuildBcd
Scanning all disks for Windows Installations.

Please wait, since this may take a while...

Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation completed successfully.
```No change. I tried to go down the "Write Protection" trouble shooting path here [http://forums.whirlpool.net.au/archive/1229012](http://forums.whirlpool.net.au/archive/1229012) .

I don't see any Permission problems from these Detail Volume logs for both C: (Windows Partition) and D: (NTFS Storage Partition).

```
Disk 0 Online 931 GB 0b
Read-only : No
Hidden : No
No Default Drive Letter: No
Shadow Copy: No
Offline : No
BitLocker Encrypted : No
Installable : Yes

Volume Capacity : 146 GB
Volume Free Space : 86 GB

Disk 0 Online 931 GB 0b
Read-only : No
Hidden : No
No Default Drive Letter: No
Shadow Copy: No
Offline : No
BitLocker Encrypted : No
Installable : Yes

Volume Capacity : 572 GB
Volume Free Space : 413 GB
```

---

### Post by wilee-nilee on 2010-12-11
> **shibazz said:**
> "BootRec.exe /fixmbr" Command Prompt yields:

```
The operation completed successfully.
```When I run "chkdsk /r" Command Prompt says:

```
The type of the file system is NTFS.
Cannot lock current drive.
Windows cannot run disk checking on this volume because it is write protected.
```I am unsure whether to continue all Willie Nillie like, because of the error from "chkdsk /r". :)

Or, should I be addressing this "write protection"?

Standing by for illumination. :)

Not sure about write protected, usually it is volume in use and a do you want to run it at next start up Y/N.

---

### Post by wilee-nilee on 2010-12-11
Is there any little yellow triangles by the NTFS partitions in gparted right click them anyway and look in the information.

You can do a check on the same popup, but It is not the same as a ckdsk, exactly.

I think you had a borked W7 to begin with that needed some work, theoretically, the Ubuntu update isn't on the NTFS partitions and should have no effect unless it changed the bootloader.

---

### Post by shibazz on 2010-12-12
There are no yellow triangles in Gparted.

I went back to post #9 to bring grub back to life with a USB Live Ubuntu.

So I'm back at that point now (Ubuntu = Boot, Windows = No Boot).

It is very strange that W7 is this messed up after a Linux update, but it was working for months before.

I still have no idea how to fix this except to reinstall Windows7. Which would be unfortunate, and would it work for sure?

Any more ideas before I start erasing my labors?

---

### Post by keithnerin on 2011-01-30
I have almost the same problem. I just installed Ubuntu (and grub) on my comp that had Windows 7. Ubuntu boots and works fine, but can't boot in Windows now. Same as said above, it starts loading, then stops and restarts. Same messages when recovery disk tried. I need help please! I'm new to all this. I'm open to re-installing Windows, but don't even know how to do that at this point. You don't get "installation discs" anymore with Windows 7. I have the recovery disk, I can make a back up from my other Windows 7 machine (if that would work), and I have a downloader for Windows 7 Professional free from my school. I don't know how to proceed with that though. I can't open it in Ubuntu even to unzip, and don't know how to do that from the prompt commands. I tried booting from the USB but it won't, I believe because it is still compressed.

---

### Post by Crim_Ferret on 2011-01-31
I had this happen at one point going from Karmic to Lucid. I used my system recovery disk to re-write the Windows MBR which got rid of grub and Windows booted fine. Then I created a live cd, and used that to re-install grub paying particular attention to where it installed. It worked fine after that.

---

### Post by donSchoe on 2011-02-11
Hello, i have almost the same problem.

I have Windows 7 (x64) on my machine and installed Ubuntu 10.10 Desktop edition using a live CD.

My disk looks like this:

```
/dev/sda1 NTFS Windows 7 system partition  (~100MB)
/dev/sda2 NTFS Windows 7 main partition    (~100GB)
/dev/sda3 SWAP                             (~  4GB)
/dev/sda4 EXT4 Ubuntu 10.10 main partition (~ 50GB)
```After installing Ubuntu 10.10 using the live CD I can still select Windows 7 in GRUB menu but after selecting it it wont boot and I'll get back to the GRUB menu after a few seconds. What's wrong?

I've run the boot script posted above, here are my results.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 543338 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 280373920 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,802,047   204,595,200   7 HPFS/NTFS
/dev/sda3         204,802,048   212,971,519     8,169,472  82 Linux swap / Solaris
/dev/sda4         212,971,520   312,580,095    99,608,576  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
222 heads, 30 sectors/track, 146662 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FA706AB6706A7971                       ntfs       System-reserviert             
/dev/sda2        DED87704D876D9EB                       ntfs                                     
/dev/sda3        c465b75c-b0ef-492d-9437-d7097c834bfb   swap                                     
/dev/sda4        bbe1fbaf-f46c-47af-abca-e8f21bde9b45   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FC36BADE36BA995A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3E785D97785D4EB1                       ntfs       Afri 931GB                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr1         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdc1        /media/Afri 931GB        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set bbe1fbaf-f46c-47af-abca-e8f21bde9b45
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set fa706ab6706a7971
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=bbe1fbaf-f46c-47af-abca-e8f21bde9b45 /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 143.5GB: boot/grub/core.img
 139.3GB: boot/grub/grub.cfg
 139.8GB: boot/initrd.img-2.6.35-25-generic-pae
 143.5GB: boot/vmlinuz-2.6.35-25-generic-pae
 139.8GB: initrd.img
 143.5GB: vmlinuz
```I've tried using the Windows 7 recovery disk but it just tells me "Everything is fine with your system."

Any help is appreciated.
Thanks :)


EDIT: OKAY, I just tried spending some time to understand the log above:

```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
[COLOR=Red]    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr[/COLOR]

```[COLOR=Red]
[COLOR=Black]This looks like I screwed up something. How should it look like? How can I fix this? Note: I had a WUBI (Ubuntu inside Windows) installation first but removed it and installed a "real" Ubuntu. Not sure why it points to a WUBI directory....[/COLOR]
[/COLOR]

---

