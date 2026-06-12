---
title: "Ubuntu + Windows 7 dual boot (2 hdds) problem"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by Sicieler on 2010-12-05
Hey guys

I just tried installing Ubuntu 10.10 on my computers extra 250GB hard drive (windows is on a separate 500GB). When I first restarted after installing I got the " boot failure insert system disk and press enter" error. So I went into my bios and changed the default boot drive from the 500GB drive (windows) to the 250GB drive (ubuntu) and it boots up into Ubuntu fine but there was no grub menu to boot into windows. I've tried googling the problem and a little looking through the forums but nothing has worked.

Right now both installs are completely fresh so I can pretty much do anything I need to to fix it. There is also an additional 1 TB hard drive on the computer but it just contains data and documents.

Thanks for your help, 

Sic

---

### Post by Quackers on 2010-12-05
Welcome to UF :-)
When booted into Ubuntu open up a terminal (Applications menu > Accessories > terminal) and type (or copy/paste)
```
sudo update-grub
```
and then press enter and enter your password when required. Then watch the terminal screen as grub.cfg is configured to see whether the Windows Loader is listed. If it is reboot and see if the grub menu appears offering the choice.

---

### Post by Sicieler on 2010-12-05
No its not listed 

This is the result:
```
kyle@Ubuntu:~$ sudo update-grub
[sudo] password for kyle: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by Quackers on 2010-12-05
Please  go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Sicieler on 2010-12-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,520,959   468,518,912  83 Linux
/dev/sda2         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,523,711 1,953,521,664   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,769,086   976,769,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        be81136f-843d-40c8-9ea0-2e0ddcd4feb2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2843278C3F250608                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7A8479328478F1CD                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0d8f6faa-3c76-4da8-8c12-21c2e81bd4e1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=be81136f-843d-40c8-9ea0-2e0ddcd4feb2 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
 202.0GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
 111.8GB: boot/vmlinuz-2.6.35-22-generic
   1.0GB: initrd.img
 111.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

---

### Post by Quackers on 2010-12-05
Grub is not picking up the Windows loader because 2 of Windows boot files appear to be missing. sdc1 is also listed as a Windows XP type boot sector but the operating system is listed as Windows 7. I don't know what happened there. 
You have said that Windows boots ok, I believe. I honestly can't see how it can boot without those files - unless I have missed something :-)
sdc1 is not flagged as bootable either.

And 3 drives seem to be present.

---

### Post by Sicieler on 2010-12-05
Sorry if I was unclear there, but windows does not boot up at all since Ubuntu was installed. When I try to boot from the Windows hard drive i get a "boot failure insert system disk and press enter" error message. 

The 3rd hard drive is a data hard drive that doesn't have anything installed on it.

---

### Post by Quackers on 2010-12-05
Ok, that seems very likely :-)
Do you have a Windows repair/installation disc (not a set of recovery dvd's)?

---

### Post by Sicieler on 2010-12-05
yea, I've tried to use it to repair the startup before (I got some error can't remember what it was), but I can try again.

---

### Post by wilee-nilee on 2010-12-05
So can you clarify which drive windows is on sdb or sdc and what the windows install is and if it was upgraded from another windows OS.

For example vista could do a actual upgrade to windows 7, but XP it had to be a fresh install or a install from XP that left XP in a special old windows file for the data retrieval.

---

### Post by Sicieler on 2010-12-05
> **wilee-nilee said:**
> So can you clarify which drive windows is on sdb or sdc and what the windows install is and if it was upgraded from another windows OS.

For example vista could do a actual upgrade to windows 7, but XP it had to be a fresh install or a install from XP that left XP in a special old windows file for the data retrieval.

Windows is on drive sdc, It is windows 7 and was upgraded from windows XP and it moved the old windows to windows.old.

---

### Post by Quackers on 2010-12-05
So you have Ubuntu on your 250GB drive (sda)
You have Windows 7 on your 500GB drive (sdc)
and you have a data drive of 1TB (sdb) with nothing on it.
Is that correct?

If so, from your Ubuntu desktop please go to Synaptic Package Manager and install Gparted. When it is installed you will find the program in System > Admin > Gparted.
Start Gparted and let it scan your discs for a few seconds. Then in the upper right you will see a box with /dev/sda in it and a little arrow next to it. Click on the arrow and select /dev/sdc. The disc will be re-scanned and any partitions on the disc will be shown in the display.
If you right-click on sdc1 and select "manage flags" and in the box that appears click on "boot" to check that box, then click OK
Please come back at that stage.

---

### Post by wilee-nilee on 2010-12-05
> **Sicieler said:**
> Windows is on drive sdc, It is windows 7 and was upgraded from windows XP and it moved the old windows to windows.old.

Cool, so in sdc as Quackers mentioned your missing these two files I have highlighted.

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:    **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

So lets get them back in eh, you can do this with the command line in the windows repair/recovery booted install or recovery cd or probably just run the auto repair 3 times or more. The key here though is that it is all pointed at the sdc HD.

Lets see what the duck has to say I think they are well qualified here I must say. Argh and he beat me to it I been keelhauled, carry on Quackers.

So do you have a recovery cd or install dvd or thumb?

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> So you have Ubuntu on your 250GB drive (sda)
You have Windows 7 on your 500GB drive (sdc)
and you have a data drive of 1TB (sdb) with nothing on it.
Is that correct?

Yes

> **Quackers said:**
> If so, from your Ubuntu desktop please go to Synaptic Package Manager  and install Gparted. When it is installed you will find the program in  System > Admin > Gparted.
Start Gparted and let it scan your discs for a few seconds. Then in the  upper right you will see a box with /dev/sda in it and a little arrow  next to it. Click on the arrow and select /dev/sdc. The disc will be  re-scanned and any partitions on the disc will be shown in the display.
If you right-click on sdc1 and select "manage flags" and in the box that  appears click on "boot" to check that box, then click OK
Please come back at that stage

Done

---

### Post by Quackers on 2010-12-05
He or she will need a boot flag on sdc1 first :-)

---

### Post by wilee-nilee on 2010-12-05
> **Quackers said:**
> He or she will need a boot flag on sdc1 first :-)

You are correct I gave to much information kind of hoping for a response before acting, which the poster is following your instructions.

"Excellent"
Mr. Burns

---

### Post by Quackers on 2010-12-05
Ok, so now there is a boot flag on sdc1 I would like you to reboot the machine and enter the bios. Please set the boot device order as follows:
1st boot device cd/dvd drive
2nd boot device the Windows hard drive
3rd boot device the Ubuntu hard drive

then reboot with the repair/installation disc in the cd drive.
If you need to press a key to boot from the cd do it. You want to enter the repair console. You will be offered the chance to run the Startup Repair. Please run that up to 3 times. Hopefully on the third run (if not before) it should pick up the Windows system on sdc and offer you the chance to add it to the boot configuration. Answer Y for yes and reboot without the repair cd in the drive. Hopefully Windows will then boot.
Please report back for inspection :-)

---

### Post by Sicieler on 2010-12-05
Ok ran recovery console and 1st time got a message saying:
```
"Startup repair cannot repair this computer automatically

Sending more information to microsoft can help Microsoft create solutions.

(options to send or not to send (I chose send))

Details:

Problem signature:
Problem event name: StartupRepairOffline
Problem Signature 01: 0.0.0.0
Problem Signature 02: 0.0.0.0
Problem Signature 03: unknown
Problem Signature 04: 0
Problem Signature 05: unknown
Problem Signature 06: 1
Problem Signature 07: unknown
OS Version: 6.1.7600.2.0.0.256.1
Locale ID: 1033"
```

After choosing send I got a message that once again told me startup repair could not fix the problem and that if I had recently attached a device to the computer to detach it and try again.

I then detached everything not keyboard, mouse or monitor, rebooted, and went for the second attempt. Same error, same results. Interesting thing I noticed this time was at the top of the System Recovery Options window there was a message that said "Operating system: Unknown on (Unknown) Local Disk" as if it didn't even know windows was installed. Time for third try...

Exact same thing. At the end of each run their was a more details option that opened a box with some stuff in it, but its quite long so I'll post what I have now and type up the message while you digest all this.

Also if it helps I did make a image of the sdc drive (saved to 1TB data Drive) before I installed ubuntu.

---

### Post by Sicieler on 2010-12-05
Diagnosis and repair details:
```
Startup Repair diagnosis and repair log
------------------------------
Number of repair attempts: 1

Session details
------------------------------
System Disk = \Device\Harddisk0
Windows directory = 
AutoChk Run = 0
Number of root causes = 1

Test Performed:
------------------------------
Name: Check for updates
Result: Completed Successfully. Error code = 0x0
Time taken: 0 ms

Test Performed:
------------------------------
Name: System Disk Test
Result: Completed Successfully. Error code = 0x0
Time taken: 0 ms

Test Performed:
------------------------------
Name: Disk metadata test
Result: Completed Successfully. Error code = 0x0
Time taken: 0 ms

Root cause found:
------------------------------
System volume on disk is corrupt.

Repair action: File system repair (chkdsk)
Result Failed. Error Code = 0x1f
Time taken = 0 ms

--------------------------------
--------------------------------

```

---

### Post by Quackers on 2010-12-05
Unusual for Windows 7. Is it the Vista upgrade disc you are using?
You could try going in again and this time choose the command prompt (on the next page to startup repair - maybe advanced options) and enter
```
bootrec.exe /fixmbr
```
Note the space between bootrec.exe and /fixmbr (not sure whether it matters) and then reboot without the disc in and see what happens.

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> Unusual for Windows 7. Is it the Vista upgrade disc you are using?
You could try going in again and this time choose the command prompt (on the next page to startup repair - maybe advanced options) and enter
```
bootrec.exe /fixmbr
```
Note the space between bootrec.exe and /fixmbr (not sure whether it matters) and then reboot without the disc in and see what happens.

No its the windows 7 disk, after using bootrec.exe /fixmbr i get an error that says:
 ```
NTLDR is missing
Press Ctrl+alt+del to Restart
```

---

### Post by Quackers on 2010-12-05
If it's looking for ntldr it must be a Windows XP repair disc.
Do you have Win 7 installed on a different machine in your house?

---

### Post by Sicieler on 2010-12-05
Yea I have it on a few others.

Also just to clarify that ntldr error came after I rebooted.

---

### Post by Quackers on 2010-12-05
If you boot one up and go to Start > Control Panel and select Backup and Restore Centre a new window will open up and on the left hand side it offers the chance to make a Windows recovery cd (it's actually the repair cd). It only takes a minute or so.
Then you can try to boot from that in your other machine and run Startup Repair 3 times (if necessary) with that disc.

---

### Post by Sicieler on 2010-12-05
Made system repair disk, and got exact same results as I got with the installation disk.

---

### Post by Quackers on 2010-12-05
Hmm I must admit I didn't like your last error. It was asking for a chkdsk, but I put that down to having no boot files.
Did you try Startup repair 3 times and/or bootrec.exe /fixmbr?
You could also try bootrec.exe /rebuildbcd
but if it really does want a chkdsk it should probably be run.
I think it can be done from a command prompt with chkdsk /r  with a space in between them
The /r is to repair any bad sectors found.

EDIT chkdsk should be run until no errors are reported!

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> Hmm I must admit I didn't like your last error. It was asking for a chkdsk, but I put that down to having no boot files.
Did you try Startup repair 3 times and/or bootrec.exe /fixmbr?
You could also try bootrec.exe /rebuildbcd
but if it really does want a chkdsk it should probably be run.
I think it can be done from a command prompt with chkdsk /r  with a space in between them
The /r is to repair any bad sectors found.

I did Startup repair 3 times and bootrec.exe /fixmbr.

chkdsk /r said: 
```
The type of this filesystem is NTFS.
Cannot lock current Drive.
Windows cannot run disk checking on this volume because it is write protected.
```

Bootrec.exe /rebuildbcd found the windows installation in D:\Windows, but when I tried to add it to the boot list it gave the error:```
The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted.
```

---

### Post by Quackers on 2010-12-05
The D: error would be expected because there is no operating system. However the fact that it picked something up may indicate that there is some sort of boot file in that partition - possibly. I don't know what that means though.

I wonder if the write-protected error would change if you just ran chkdsk - without the /r
In all honesty I haven't had to do a chkdsk in a long time and things may have changed since then.
I'm scrambling about for ideas and coming up empty I'm afraid.

It is usual for Win 7 to repair itself very easily with the startup repair. I'm struggling to find reasons for yours not doing so.

Maybe somebody else could come up with more ideas. There are many here more knowledgable than me in this area.

At least with a change in the bios you can use Ubuntu in the meantime.

I'll continue to think about this and if I come up with anything you'll be the second to know! :-)  Good luck.

---

### Post by Quackers on 2010-12-05
You mentioned a backup image earlier. With what program was that made?

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> You mentioned a backup image earlier. With what program was that made?

It was made with windows, in the create a system image portion of the control panel.

I just tried to use the image to restore with the installation disk, and told it to exclude the drive that ubuntu is on. When i did that it gave me an error about a drive being excluded that shouldn't have been so I unexcluded Ubuntu's drive and it worked. I restarted and got an error don't remember what it was :(, so I rebooted and tried to get into ubuntu by booting from its HD instead of windows' HD. However when it finished booting I was in windows and the 250GB HD Ubuntu ?was/is? installed on is back to how it was before Ubuntu was installed with 100MB of system partition (from a previous Ubuntu install attempt) and 230GB of unformatted space. 

I'm at a loss of how restoring the image of one drive also restores a drive that didn't even have an image created for it happened, but it did...

I guess now I need to once again try and install ubuntu on the 250GB HD? Any Suggestions?

---

### Post by Quackers on 2010-12-05
That may be because the Ubuntu drive is the first hard drive. Windows likes to be on the first drive.
It may be that just the first small partition that Win 7 uses has been restored.
I'm guessing.
Maybe if you boot from the Ubuntu Live cd and select "try ubuntu" and when the desktop loads make sure you've got an internet connection and go to the site below and download and run the bootscript again we will be able to see more clearly what has happened and what is installed where.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Sicieler on 2010-12-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
224 heads, 19 sectors/track, 114754 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,523,711 1,953,521,664   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,769,086   976,769,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D6183378183356A9                       ntfs       System Reserved               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2843278C3F250608                       ntfs       Data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7A8479328478F1CD                       ntfs       Windows                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

How this is right is beyond me the only drive that should have windows on it is sdc...

Also to clarify windows currently boots only when I tell it to boot from the 250GB HD that it is not installed on...

---

### Post by Quackers on 2010-12-05
Lol, the 2 missing Windows boot files return! :-) Sadly they are on sda and the rest of Win 7 is on sdc.
It seems that Windows 7 was originally on sda then.
Now I am stuck :-)
I don't know how to get that 200MB partition over to sdc.
Alternatively that will be the only partition showing on sda now and if you re-install Ubuntu on the remaining part of that drive (which may now be shown as unallocated space) would that be ok? 
From the live cd desktop can you run Gparted and post a screenshot of the /dev/sda drive please?

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> Lol, the 2 missing Windows boot files return! :-) Sadly they are on sda and the rest of Win 7 is on sdc.
It seems that Windows 7 was originally on sda then.
Now I am stuck :-)
I don't know how to get that 200MB partition over to sdc.
Alternatively that will be the only partition showing on sda now and if you re-install Ubuntu on the remaining part of that drive (which may now be shown as unallocated space) would that be ok? 
From the live cd desktop can you run Gparted and post a screenshot of the /dev/sda drive please?

Yes you are correct windows previously resided on the 250GB hard drive. And yea I'd be fine missing out on the whole 200 MB of that partition in the Ubuntu install. :)

---

### Post by Quackers on 2010-12-05
To be honest it's not the 200MB it's what grub may or may not do to it. Nothing I think!
Just so there is no doubt about the unallocated space on sda I would suggest you create a partition on sda using the whole remaining space and format it in whatever system you choose. Click on the green tick in the toolbar to apply the action.
Then when it's run delete that partition again, clicking the green tick to apply the changes. This should ensure that nothing is left behind from the previous install.
It won't take long. Just a couple of minutes.
Then, I think it will be good to re-install Ubuntu in that free space. I think :-) I hope :-)

---

### Post by Sicieler on 2010-12-05
> **Quackers said:**
> To be honest it's not the 200MB it's what grub may or may not do to it. Nothing I think!
Just so there is no doubt about the unallocated space on sda I would suggest you create a partition on sda using the whole remaining space and format it in whatever system you choose. Click on the green tick in the toolbar to apply the action.
Then when it's run delete that partition again, clicking the green tick to apply the changes. This should ensure that nothing is left behind from the previous install.
It won't take long. Just a couple of minutes.
Then, I think it will be good to re-install Ubuntu in that free space. I think :-) I hope :-)

Yes!! It's finally working:D:D

Thanks so much for your help man, your awesome :)

---

### Post by Immahazmacookie on 2010-12-06
Maby if u have the time, back up your data and then wipe both drives, install Ubuntu, the restore the Window$ drive.

---

### Post by Quackers on 2010-12-06
Lol, wooohooo, nice one :-)
About 15 minutes after I fell asleep watching The Ashes :-)
Could you mark the thread as solved please by using the Thread Tools near the top of the page. Thanks.

---

