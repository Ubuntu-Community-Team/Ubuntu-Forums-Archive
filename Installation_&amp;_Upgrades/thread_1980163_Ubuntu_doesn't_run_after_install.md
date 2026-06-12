---
title: "Ubuntu doesn't run after install"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by antsco on 2012-05-14
Hi
I installed ubuntu 12.0.4 on a dell inspiron 6000 laptop, with Windows XP already as the main OS
I had a free partition of 86GB which apparently ubuntu has detected and utilized for its installation (from a CD Rom)
After install, which apparently wnet well, the booting process remains stuck on a command prompt and it doens't boot at all, neither with ubunto nor with windows.
The only thing I can do is booting with ubuntu from the CD rom.
Any ideas on how I can successfully install ubuntu (or unistall for that matter)?
Thanks
Antonio:confused:

---

### Post by oldfred on 2012-05-14
Welcome to the forums.

You can download this into the liveCD/USB or download a bootable repairCD.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by antsco on 2012-05-15
btw, the message I get when booting is:

error no such partition
grub rescue>

hope this can help targeting the problem.
Also since I am quite new to linux/ubuntu I am still not quite sure how to install and run boot-repair-disk, any help appreciated
Thanks
Antonio

---

### Post by darkod on 2012-05-15
That link has the procedure to run the boot-repair from live mode. It's under the 2nd option: Install Boot Repair in Ubuntu.

Boot with the cd in live mode, open Terminal and in terminal run the two lines of code from that section, Install Boot Repair in Ubuntu.

When Boot Repair opens, you can do the Recommended Repair if you want to, or you can only do the Create BootInfo summary. That will give you a link where the summary is. Post that link and we can see the details of the system and maybe find the problem.

---

### Post by antsco on 2012-05-15
Hi darko
eventually running boot disk succeded. Not the first time though.
After the first trial the system message said that th ebooting had been repaired but when rebooting the same problem appeared.
Next I re-run boot-disk-repair changing one advanced option, I guess it was the ata support box and when I rebooted it still gives the following message:

error: no device connected

but after less than a minute the dual loader appears. and then I can boot either windows or linux.
I wonder why this error appears and how can I avoind it form happening
any clues?
Thanks for your help 
Antonio

---

### Post by darkod on 2012-05-15
Unfortunately without more details that the boot info script results produce, we can't know what exactly is going on.

It sounds like you need to check the BIOS settings too, this doesn't sound like ubuntu issue.

---

### Post by antsco on 2012-05-16
Hi Darkrod
are you suggesting that I run the bootinfoscript after ubuntu is loaded?
BTW why do you think it is a BIOS issue, I have not manipulated the BIOS at all while trying to install UBUNTU
Does Ubuntu manipulate the bios during the installation process?
Cheers
Antonio

---

### Post by darkod on 2012-05-16
Yes, you can run the script after it's loaded and post the results.

No, ubuntu doesn't manipulate the BIOS but there are possibilities you are booting from another disk if you have more than one, etc. The boot process is controlled by BIOS too, the order of the devices and of the HDDs, so depending on the setup it can have a role.

---

### Post by antsco on 2012-05-29
Hi
I just  run  bootinfoscript and this is the output (see below). There seems something wrong in sda6
but dunno how to interpret that nor what to do.
Any clue is appreciated
Thanks
Antonio

> 
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   245,762,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda2         245,762,048   450,558,989   204,796,942   7 NTFS / exFAT / HPFS
/dev/sda3         450,559,051   625,141,759   174,582,709   f W95 Extended (LBA)
/dev/sda5         450,559,053   489,628,982    39,069,930   7 NTFS / exFAT / HPFS
/dev/sda6         489,629,696   620,949,503   131,319,808  83 Linux
/dev/sda7         620,951,552   625,141,759     4,190,208  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E83455A134557392                       ntfs       
/dev/sda2        C0A42DBCA42DB5B6                       ntfs       Dati
/dev/sda5        4C4C70424C7028BA                       ntfs       UBUNTU
/dev/sda6        4f9b0dbd-dc2c-43e9-9992-74389831e69e   ext4       
/dev/sda7        8e183875-3689-40f2-ac8c-22b3ebe7c3ac   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=4f9b0dbd-dc2c-43e9-9992-74389831e69e ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=4f9b0dbd-dc2c-43e9-9992-74389831e69e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 4f9b0dbd-dc2c-43e9-9992-74389831e69e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root E83455A134557392
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4f9b0dbd-dc2c-43e9-9992-74389831e69e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8e183875-3689-40f2-ac8c-22b3ebe7c3ac none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 261.610439301 = 280.902070272  boot/grub/core.img                             1
 261.607429504 = 280.898838528  boot/grub/grub.cfg                             1
 239.859340668 = 257.547005952  boot/initrd.img-3.2.0-23-generic-pae           2
 261.606685638 = 280.898039808  boot/vmlinuz-3.2.0-23-generic-pae              1
 239.859340668 = 257.547005952  initrd.img                                     2
 261.606685638 = 280.898039808  vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Los datos comprimidos están corruptos


---

### Post by darkod on 2012-05-29
You can try reinstalling grub2 to the MBR. Boot with the CD in live mode and in terminal do:
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Restart and see if it helped.

One reason might be that the core.img and the other grub2 files are very far back on the disk, beyond 250GB or 280GB. Sometimes boards don't recognize boot files beyond 137GB on the disk.

If that it the issue here, I am not sure how to resolve it except making a separate /boot partition as much at the front of the disk as you can. That will assure the boot files are not so back.

---

### Post by antsco on 2012-06-11
Hi Darkrod

I guess I misunderstood your directions: I rebooted with the Ubuntu installation disk (clicking on the trial version button of ubuntu, the alternative was clicking on the install ubuntu button)

and performed the sudo commands as suggested but....the message I get is:


cannot find /dev/sda6/mnt in /etc/fstab or /etc/mtab

Do I really have to do this by booting with the CD?
Thanks
Antonio

---

### Post by darkod on 2012-06-11
You mistyped it, it's not /dev/sda6/mnt together. There is a space between the two.

It's:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by antsco on 2012-06-11
Hi,
thanks for clarifying.

Anyhow, what would happen if I run the commands from the installed ubuntu instead than fron the installation CD?
Thanks
Antonio

---

### Post by darkod on 2012-06-11
I thought you can't boot the installed ubuntu. If you can, it's even easier, you only need to run the grub-install command and little different:
```
sudo grub-install /dev/sda
```

It depends where you run it from, there are differences.

---

### Post by antsco on 2012-06-11
Hi
well..I run the command following your advice and..I've got a problem now

When rebooting I get:

error: partition doesn't exist
grub rescue>

What shall I do now????
Any help appreciated
Antonio

---

### Post by antsco on 2012-06-11
I just run bootinfoscript and what I got was (just first few lines)

> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

It looks as if there is something missing in "(, msdos6)/boot/grub" I wonder whether the command you suggested me to run was complete, I mean if some other sudo command needed to be issued to complete the process.

BTW the initial bootscriptinfo log header (right after install afew weeks ago) was like this:
> => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.Cheers
Antonio

---

### Post by oldfred on 2012-06-11
I do not think that is the issue. 

I have several drives and get the same style MBR output you have. Except your original style I do have with bootinfoscript v.61 and the grub1.99 with Ubuntu 12.10. So it is a minor difference in updates to boot script and/or grub1.99.

From grub rescue can you manually boot or is partition not seen?

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg
OR - and again change this example from hd0,2 and sda2 to your partition:
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

### Post by antsco on 2012-06-11
Hi
thanks for your hints but I am still not 100% sure about what to do.

I run boot-repair-disk as explained in the support materials but the result is still the same
even though boot-repair said that it has been fixed.
So I still find the "grub rescue >" prompt and before that an error saying that no partition is found.
This is the url generated in case it can be of help understanding what's up: [http://paste.ubuntu.com/1035969](http://paste.ubuntu.com/1035969)

When I run "ls" from the "grub rescue>" I get the following:
(hd0) (hd0,msdos2) (hd0,msdos1) (hd1)

how can I use that info to do what you suggest to doing?
what is the relationship between (hd0), (hd0,x), (hd1), etc and sda, sda1, sda5, etc?
Cheers
Antonio

---

### Post by darkod on 2012-06-11
When you tried 'ls' it didn't show something like (hd0,msdos6) listed? That would be your ubuntu partition /dev/sda6.

Even if it doesn't list it, at the grub rescue prompt try something like:
```
configfile (hd0,msdos6)/boot/grub/grub.cfg
```

---

### Post by antsco on 2012-06-11
tried that but "configfile" is not recognized as a valid command......

After I also run the "set" command and what I got is:
> prefix=(hd0,msdos6)/boot/grub
root=hd0,msdos6

So, is this similar to what you wanted me to achieve by using the *configfile* command?

Cheers
Antonio

---

### Post by darkod on 2012-06-11
OK, try this, one by one command:
```
set root=(hd0,6)
linux (hd0,6)/vmlinuz
initrd (hd0,6)/initrd.img
boot
```

Can that boot it?

---

### Post by oldfred on 2012-06-11
If Darko's suggestion does not work, is this an older computer with a newer larger hard drive? Some old BIOS only boot from the first 137GB. Script show boot files at about 280GB point on drive.

---

### Post by antsco on 2012-06-12
Hi
it doesn't work either. The *linux* command is not recognized either
So the actual configuration is:
> 
prefix = (hd0,msdos6)/boot/grub
root=hd0,6
the command boot is also NOT recognized

This is actually an older computer (2005) with a new hard drive that has partitions
smaller than 130 Gb

:confused:
Cheers
Antonio

---

### Post by darkod on 2012-06-12
oldfred wasn't referring to the partition size, but to the disk size and the location where the boot files are. The disk is 320GB, much larger than the 137GB limitation some older BIOS-es have to find the boot files.

From your boot info results in post #18:
```

=================== sda6: Location of files loaded by Grub: ====================
             GiB - GB             File                                 Fragment(s)
   261.633880615 = 280.927240192  boot/grub/core.img                             1
  261.633499146 = 280.926830592  boot/grub/grub.cfg                             1
  239.859340668 = 257.547005952  boot/initrd.img-3.2.0-23-generic-pae           2
  261.606685638 = 280.898039808  boot/vmlinuz-3.2.0-23-generic-pae              1
  239.859340668 = 257.547005952  initrd.img                                     2
  261.606685638 = 280.898039808  vmlinuz                                        1

```

The boot files are beyond the 137GB, they are at 280GB on the hdd.

It looks like this is what's blocking it to boot correctly.

Or the ubuntu partitions are somehow corrupted. When you tried the 'ls' you said it listed only the two ntfs partitions. It should have listed all partitions as found.

---

### Post by antsco on 2012-06-12
Hi
sooo.....what do you suggest I could do to change the location where the boot partition
is? is there a way to put the boot sectors before the 137 Gb limit (without reinstalling everything)? Or alternatively how do I know if the ubuntu partitions are corrupted?
The boot-repair-disk that I run yesterday said that everything was ok.

On the other hand, I had managed to boot and use the Ubuntu OS before I tried to solve that particular problem (see earlier posts), when at  start-up I received that error message saying "device not found". Do you think that all the I did after could have corrupted the ubuntu partitions?
 
Thanks
Antonio

---

### Post by darkod on 2012-06-12
The only way to "move" the boot files before the 137GB mark is to create a small partition, separate /boot partition. But your first two ntfs partitions take all this space, the first is approx 120GB and the second 100GB.

I was reading the whole thread again from the start, and noticed when you ran the first boot-repair automatic repair that it reported FlexNet which interferes with the boot process. Not sure what that is, how and when were you using it, but it might have something to do with your boot problems.

Try running the recommended repair of boot-repair again, see if it helps.

Otherwise, according to the latest boot info results, all looks fine, except if the problem is the location of the boot files, but that can't be checked until you move them towards the beginning of the disk which is takes by your windows partitions right now.

---

### Post by YannBuntu on 2012-06-12
Hello
In the log we can see that FlexNet was removed (after user confirmation), so i would rather bet for the 137GB problem.

Remark: the FlexNet can come back after Windows use.

---

### Post by antsco on 2012-06-13
Hi
I eventually managed to revert to the original condition, where I have dual boot at start up but the first thing I see upon switching on my laptop is is "error: device not found"
after which the dual boot menu is presented and I can choose which OS to use.

I managed to do this by running boot-repair-disk and clicking on the ATA disk advanced option, which apparently solves the problem that some of you have hinted at, that of using a disk whose size goes beyond the 137GB, the boot sector being installed beyond that limit.

Still do not understand why this error at start up occur, which  is not problematic per se, but delays somewhat the booting time.
In case you guys have any other suggestions on how to tackle this, please let me know
In the meanwhile I just want to thank you all for the time you have dedicated to this issue of mine. It has made a difference since I am a complete beginner with Ubuntu and wouldn't have known what to do if this forum hadn't existed and you hadn't replied to my queries.
Best regards
Antonio

---

### Post by antsco on 2012-06-13
...sorry, what?

---

### Post by YannBuntu on 2012-06-13
As the "ATA disk" option is not enough, you will probably need to [create a separate /boot partition close from the start of your disk (inside the first 137GB of your disk).]("http://ubuntuforums.org/showthread.php?t=1998257")
To perform this, use a Windows tool to reduce either sda1 or sda2 (if sda2, reduce it from the start), in order to leave a 1Go free space before or after sda1 partition. Then via gParted, create a new partition (Primary, 1Go, Ext4) in this free space. Then simply run Boot-Repair, update it, click "Advanced options" -> "GRUB location" tab, select the "Separate /boot partition: sdaX" option (sdaX must be your new 1Go partition) to setup your Ubuntu so that it uses this new partition.

---

