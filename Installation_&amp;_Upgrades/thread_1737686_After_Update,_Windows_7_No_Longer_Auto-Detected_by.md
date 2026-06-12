---
title: "After Update, Windows 7 No Longer Auto-Detected by GRUB2"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Gas Addict on 2011-04-23
I'm using Maverick Meerkat, 10.10, 64bit. I'm a pretty basic user but am trying my best to learn.

My background:
I have a laptop on which I installed Win7 Ulimate on one partition. After installing Win7 I then installed Ubuntu on a separate partition. GRUB2 found both Win7 and Ubuntu perfectly. I could choose to boot into either one and the ability for GRUB2 to "remember" which OS I booted into last worked properly. I then did a kernel update a couple days ago via Ubuntu's Update Manager. After that, GRUB2 could no longer see Win7. I added a custom boot entry in /etc/grub.d/ so that Win7 would show up in GRUB2.

However once Win7 did show up in GRUB2 I kept having a problem with the Windows bootloader being missing. I used the Win7 Recovery DVD to get into Windows and then installed EasyBCD for Win in which I was able to create a Win7 boot entry and get the Win7 bootloader back. I set EasyBCD to skip the bootmenu so my current configuration now is that on bootup I see GRUB2, which shows Maverick Meerkat & Win7. If I select Win7 then Win7 loads via EasyBCD and it works fine. 

The problem though is that GRUB2 does not auto-detect Win7 AND it no longer remembers the last OS that I booted into. I would rather not use EasyBCD if I can help it and would like to just use GRUB2 for everything.

**My question is this: **How can I get GRUB2 back to controlling Ubuntu & Win7 properly without the need for anything else in between.  I have asked in the Freenode Ubuntu channel but haven't received any help besides "sudo update-grub" which I have done and it hasn't helped.

If anyone could help, I would appreciate it so much. Thank you so much to the helpful Ubuntu community! :KS

---

### Post by oldfred on 2011-04-23
Welcome to the forum.

A kernel or grub update should not have changed the windows boot.

Lets see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Gas Addict on 2011-04-23
Thank you so much for responding!

Here is my output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   955,799,551   955,592,704   7 HPFS/NTFS
/dev/sda3         955,801,598   976,771,071    20,969,474   5 Extended
/dev/sda5         955,801,600   976,771,071    20,969,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        A638CB6038CB2E5D                       ntfs       Enterprise                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4327abda-28ae-4c0c-894d-d40ca872912d   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda1: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sda2        /media/Enterprise        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
insmod tga
if background_image /usr/share/images/grub/02510_home_1920x1080.tga ; then
  set color_normal=white/black
  set color_highlight=light-blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_Windows_proxy ###
menuentry "Microsoft - Windows 7 Ultimate" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/10_Windows_proxy ###

### BEGIN /etc/grub.d/11_linux_proxy ###
menuentry "Ubuntu - Maverick Meerkat" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4327abda-28ae-4c0c-894d-d40ca872912d ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/11_linux_proxy ###

### BEGIN /etc/grub.d/20_os-prober ###
### END /etc/grub.d/20_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=4327abda-28ae-4c0c-894d-d40ca872912d    /    ext4    errors=remount-ro,user_xattr    0    1
#Entry for /dev/sda2 :
UUID=A638CB6038CB2E5D    /media/Enterprise    ntfs-3g    defaults,uid=1000,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda1 : (System Reserved Win 7)
UUID=5ED26389D263646D    /dev/null/    ntfs    noauto,nosuid,nodev,nls=utf8,umask=0222    0    0



=================== sda5: Location of files loaded by Grub: ===================


 498.2GB: boot/grub/core.img
 498.4GB: boot/grub/grub.cfg
 492.1GB: boot/initrd.img-2.6.35-28-generic
 490.5GB: boot/vmlinuz-2.6.35-28-generic
 492.1GB: initrd.img
 490.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
```

---

### Post by Hedgehog1 on 2011-04-23
It looks like the Windows 7 boot partition has been damaged:

```

### BEGIN /etc/grub.d/10_Windows_proxy ###
menuentry "Microsoft - Windows 7 Ultimate" {
**[COLOR="Red"]set root=(hd0,1)[/COLOR]**
chainloader +1

...

**[COLOR="red"]sda1[/COLOR]**: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
```

**Gas Addict** - Windows Vista and Windows 7 use two partitions minimum, a small 100 meg one to boot from, and then the main Windows Vista/7 partition (typically /dev/sda1 & dev/sda2) - also called HD0,1 and HD0,2.

The Windows boot partition will need to be rebuilt.


***The Hedge***

:KS

p.s. If you don't have your windows a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by Gas Addict on 2011-04-23
Thank you for responding!

I actually changed (hd0,2) to (hd0,1) on my own after some advice from someone in #Ubuntu because when it was on (hd0,2) it kept giving me the error "BOOTMGR is missing". Once I switched it to (hd0,1), Win7 started booting again normally.

When I go into Win7 Recovery DVD and try "Startup Repair" it says that everything is normal. Are there any command line methods to accomplish what I need to do? What is it exactly that needs to be done? My boot partition needs to be rebuilt? Does that mean I need to format my windows partition and start over? (Would really really like to avoid this if possible).

Thank you again for taking the time to help so much. Really appreciate it!

---

### Post by oldfred on 2011-04-23
You can move the boot flag with gparted or Disk Utility to sda2 and then run the command line repairs which should fix the windows install. It will then obsolete sda1.

But if sda1 has corruption or a bad entry in the partition table it may still prevent everything from working.

You may want to try chkdsk on the sda1 partition.

I copied a lot of the windows commands into this post:

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by Gas Addict on 2011-04-24
Thank you again for your help!

Chkdsk /R C: reported no errors. 
Chkdsk /R D: reported no errors. 

Is my Win7 100MB system partition on 'C' or 'D'? Chkdsk took a lot longer on 'D' than it did on 'C' but whenever I would go into My Computer in Win7 I would see it being on 'C'. 

When you say I will obsolete sda1 does that mean I will be messing up the Win7 system partition? Is there any alternative to that? Is there a way to "restore" the sda1 win7 system partition if Chkdsk finds no errors on it? I saw the commands you linked to--the bootrec /FixMBR part says it will mess up GRUB2. Is this what I should do?

Thanks for putting up with my lack of experience. Much appreciated.

---

### Post by Gas Addict on 2011-04-24
An update, I followed the steps here: [http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

What has happened now is that GRUB2 is once again seeing Windows 7 automatically (although for some reason it thinks Windows 7 is actually Windows Vista) and I am able to boot into Win7 and Ubuntu.

My question is regarding the boot sector recovery. When I was following the instructions listed on the link above I was not able to copy the boot files over to the Win7 System Reserved 100MB partition (dev/sda1). It kept saying access denied so instead I copied them over to my main Win7 partition (dev/sda2) and now I have a C:\BOOT folder on /dev/sda1.  What I am wondering is, did I do this correctly? Even though it works right now am I setting myself up for some problem in the future (i.e. next time I do an Ubuntu kernel update)?  Is the boot supposed to be installed in the 100MB Win7 System Reserve partition instead? And if that is how it is supposed to be, how can I go about doing this?

THANK YOU!

Here is an updated boot info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /BOOT/bcd /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   955,799,551   955,592,704   7 HPFS/NTFS
/dev/sda3         955,801,598   976,771,071    20,969,474   5 Extended
/dev/sda5         955,801,600   976,771,071    20,969,472  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        A638CB6038CB2E5D                       ntfs       Enterprise                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4327abda-28ae-4c0c-894d-d40ca872912d   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda1: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)
/dev/sda2        /media/Enterprise        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
insmod tga
if background_image /usr/share/images/grub/02510_home_1920x1080.tga ; then
  set color_normal=white/black
  set color_highlight=light-blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/11_os-prober_proxy ###
menuentry "Microsoft - Windows Ultimate 7" {
    savedefault
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set a638cb6038cb2e5d
    chainloader +1
}
### END /etc/grub.d/11_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry "Ubuntu - Maverick Meerkat" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 4327abda-28ae-4c0c-894d-d40ca872912d
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4327abda-28ae-4c0c-894d-d40ca872912d ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/20_linux_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=4327abda-28ae-4c0c-894d-d40ca872912d    /    ext4    errors=remount-ro,user_xattr    0    1
#Entry for /dev/sda2 :
UUID=A638CB6038CB2E5D    /media/Enterprise    ntfs-3g    defaults,uid=1000,nodev,locale=en_US.utf8    0    0
#Entry for /dev/sda1 : (System Reserved Win 7)
UUID=5ED26389D263646D    /dev/null/    ntfs    noauto,nosuid,nodev,nls=utf8,umask=0222    0    0



=================== sda5: Location of files loaded by Grub: ===================


 498.2GB: boot/grub/core.img
 498.3GB: boot/grub/grub.cfg
 492.1GB: boot/initrd.img-2.6.35-28-generic
 490.5GB: boot/vmlinuz-2.6.35-28-generic
 492.1GB: initrd.img
 490.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
```

---

### Post by samacaster on 2011-04-24
AH YES! System Reserved. 100 MB of nothing important. Windows will not let you into it. It is primarily used for Bitlocker if enabled. It can be removed via Disk Management. Like your recovery partition it has no drive letter assigned.

At to root of your C: drive (They should be hidden) is your BCD. Removing system reserved will not affect startup.

BUT! If everything works now simply make Ubuntu the default OS with EasyBCD.

---

### Post by Gas Addict on 2011-04-24
> **samacaster said:**
> AH YES! System Reserved. 100 MB of nothing important. Windows will not let you into it. It is primarily used for Bitlocker if enabled. It can be removed via Disk Management. Like your recovery partition it has no drive letter assigned.

At to root of your C: drive (They should be hidden) is your BCD. Removing system reserved will not affect startup.

BUT! If everything works now simply make Ubuntu the default OS with EasyBCD.

So if everything is working and I'm booting Windows from /dev/sda2 instead of /dev/sda1 is that the same way a default Win7 install would be setup?  Thank you.

---

### Post by oldfred on 2011-04-24
The default for win7 is the two partitions. They added the new 100MB boot/recovery partition so you could encrypt the main partition as the boot cannot be encrypted. Possibly also if main partition has issues you could still boot into recovery and run repairs. If you have repair CD then even that is not something you need now.

Win7 overinstalled over Vista only uses the one partition. Or if you create partitions in advance it will install to just one partition.

---

