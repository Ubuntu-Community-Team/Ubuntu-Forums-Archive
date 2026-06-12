---
title: "Can't find Ubuntu on Dual Boot"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by bro brian on 2010-12-11
Today, I installed Mandriva 2010 Spring on one of my 2 partitions (both had Ubuntu previously installed on them - Maverick & Lucid). I installed Mandriva on the Lucid partition, I believe. 
  After installing Mandriva on the one existing partition, I don't get any option to boot to the Ubuntu Maverick on the other partition. I get no "dual boot" option. It just goes straight to the Mandriva os.
  I know the Ubuntu Maverick is there, but I can't get to it! Any suggestions? Thanks in advance. Brian

---

### Post by Quackers on 2010-12-11
Please  go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sikander3786 on 2010-12-11
You needed to choose not to install boot loader during the installation of Mandriva. But if you did install it, Mandriva is good at picking other OS. Not sure why it didn't in your case.

Anyhow, as Quackers suggested, boot script output will tell us.

---

### Post by bro brian on 2010-12-11
OK - Thanks! I'm going to study the link, and do as instructed. Hopefully I will be able to get it posted in a short while here. This is all pretty foreign to me, but I should be able to do it. I wish I would've not installed that bootloader for Mandriva! Oh well....

** I Couldn't get the script (results.txt file) to run on the mandriva partition. I used the Ubuntu live cd to do it.[SIZE=2][FONT=Arial Black]
[/FONT][/SIZE]

---

### Post by bro brian on 2010-12-11
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

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
    Operating System:  Mandriva Linux release 2010.1 
                       (Official) for i586 Kernel 2.6.33.7-server-2mnb on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   507,645,109   507,645,047  83 Linux
/dev/sda2         507,645,950   976,768,064   469,122,115   5 Extended
/dev/sda5         953,184,708   976,768,064    23,583,357  82 Linux swap / Solaris
/dev/sda6         507,645,952   935,041,023   427,395,072  83 Linux
/dev/sda7         935,043,072   953,184,255    18,141,184  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        cb233134-df94-4375-95da-37bf522e3c85   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62ad1198-0845-4b15-bef2-80d8d5618eda   swap                                     
/dev/sda6        8aa1fcc1-79aa-4e2b-932d-c4435d607b58   ext4                                     
/dev/sda7        578b21f6-b80f-467c-900b-50371fa78619   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
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
search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=cb233134-df94-4375-95da-37bf522e3c85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cb233134-df94-4375-95da-37bf522e3c85
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cb233134-df94-4375-95da-37bf522e3c85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=62ad1198-0845-4b15-bef2-80d8d5618eda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   6.9GB: boot/grub/grub.cfg
   7.8GB: boot/initrd.img-2.6.31-21-generic
  10.3GB: boot/initrd.img-2.6.32-22-generic
  20.6GB: boot/initrd.img-2.6.32-23-generic
  10.3GB: boot/initrd.img-2.6.32-24-generic
  34.8GB: boot/initrd.img-2.6.32-25-generic
   6.5GB: boot/vmlinuz-2.6.31-21-generic
   8.9GB: boot/vmlinuz-2.6.32-22-generic
  30.2GB: boot/vmlinuz-2.6.32-23-generic
  32.5GB: boot/vmlinuz-2.6.32-24-generic
  33.0GB: boot/vmlinuz-2.6.32-25-generic
  34.8GB: initrd.img
  10.3GB: initrd.img.old
  33.0GB: vmlinuz
  32.5GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,5)/boot/gfxmenu
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 resume=UUID=62ad1198-0845-4b15-bef2-80d8d5618eda splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 resume=UUID=62ad1198-0845-4b15-bef2-80d8d5618eda
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 failsafe
initrd (hd0,5)/boot/initrd.img

title server 2.6.33.5-2
kernel (hd0,5)/boot/vmlinuz-2.6.33.5-server-2mnb BOOT_IMAGE=server_2.6.33.5-2 root=UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 resume=UUID=62ad1198-0845-4b15-bef2-80d8d5618eda splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.33.5-server-2mnb.img

title server 2.6.33.7-2
kernel (hd0,5)/boot/vmlinuz-2.6.33.7-server-2mnb BOOT_IMAGE=server_2.6.33.7-2 root=UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 resume=UUID=62ad1198-0845-4b15-bef2-80d8d5618eda splash=silent vga=788
initrd (hd0,5)/boot/initrd-2.6.33.7-server-2mnb.img

=============================== sda6/etc/fstab: ===============================

# Entry for /dev/sda6 :
UUID=8aa1fcc1-79aa-4e2b-932d-c4435d607b58 / ext4 acl,noatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=62ad1198-0845-4b15-bef2-80d8d5618eda swap swap defaults 0 0
# Entry for /dev/sda7 :
UUID=578b21f6-b80f-467c-900b-50371fa78619 swap swap defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


 290.1GB: boot/grub/menu.lst
 290.1GB: boot/grub/stage2
 260.0GB: boot/initrd-2.6.33.5-server-2mnb.img
 260.1GB: boot/initrd-2.6.33.7-server-2mnb.img
 260.1GB: boot/initrd.img
 260.1GB: boot/initrd-server.img
 290.1GB: boot/vmlinuz
 290.1GB: boot/vmlinuz-2.6.33.5-server-2mnb
 290.1GB: boot/vmlinuz-2.6.33.7-server-2mnb
 290.1GB: boot/vmlinuz-server

---

### Post by Quackers on 2010-12-11
I suggest that you boot into the Ubuntu Live cd and choose "try ubuntu" then when the desktop is loaded run the following commands in a terminal.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot. Ubuntu should then boot directly. Once in Ubuntu open a terminal and run
```
sudo update-grub
``` and watch the terminal screen as grub.cfg is configured to see if Mandriva is detected.

If Ubuntu does not boot up please come back here as the full chroot method may be required.

---

### Post by bro brian on 2010-12-11
Well, Quackers, the Ubuntu showed up, but I guess I formatted the wrong one. LOL...
  I have the Lucid, and the Meerkat was formatted to the Mandriva os. I watched the grub.cfg and it detected the Mandriva as well, but it won't load now. The last 4 or 5 lines at the end of the boot order are the ones for Mandriva. I see the mandriva logos (2 yellow stars and the loading protocol) when I attempt to load it, but it locks up - sometimes with error symbol.
  I don't know at this point. I will post 2 photos of the boot screen. I couldn't get all the lines in the square, so I took 2 pics.
[IMG]http://i245.photobucket.com/albums/gg62/brobri_photos/DSCF0408resized.jpg[/IMG]
[IMG]http://i245.photobucket.com/albums/gg62/brobri_photos/DSCF0409resized.jpg[/IMG]

---

### Post by Quackers on 2010-12-11
I see. So Lucid boots up ok? (even though you thought it should be Meerkat)
What else boots up via the menu?

---

### Post by sikander3786 on 2010-12-11
Are you able to boot Lucid successfully at this point?

---

### Post by bro brian on 2010-12-11
All those lines that say "Ubuntu, with Linux 2.6.31-21, 2.6.32.-22 thru  24". Those are all earlier distros (upgrades of Ubuntu) with the top  ones (ending in 23 & 24) being the last upgrade (Lucid).
 I did a  clean install of Meerkat, but that partition is now the Mandriva. I do  have almost everything from Meerkat backed up on a usb flash, so I guess  I could start all over if need be. I did like the idea of having a dual  boot Mandriva/Ubuntu KDE/gnome laptop, however. At this point, I'm just  about willing to do anything that's within the realms of reason.

**Yes, I can boot Lucid. It's the only one that I can boot up now (which is better than Mandriva at this point). I'd rather be have this problem with Lucid up than Mandriva at this point.

---

### Post by sikander3786 on 2010-12-11
Meerkat can't be restored from the position you are in now.

If you decide to re-install everything, install Mandriva first. Then Ubuntu/Kubuntu and save yourself from all the problems.

---

### Post by bro brian on 2010-12-11
> **sikander3786 said:**
> Meerkat can't be restored from the position you are in now.

If you decide to re-install everything, install Mandriva first. Then Ubuntu/Kubuntu and save yourself from all the problems.

I'm beginning to think that I may be better off doing just that. Or maybe an Ubuntu/gnome, and Kubuntu/KDE. It may end up being more compatible in the long run?

---

### Post by oldfred on 2010-12-11
Without seeing your boot script I think this may be a issue. Grub's osprober often add this to its boot stanza.

initrd (hd0,5)/boot/initrd.img

change to
initrd /boot/initrd.img

But the hd0,5 is wrong(for grub2) and unnessary. You should be able to copy the boot stanza from your grub.cdf to 40_custom and edit it. If it works then you can delete the osprober version by turning off the prober.

Copy the mandriva entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by bro brian on 2010-12-11
My apologies, Oldfred, but I don't understand what you are saying here. It sounds like it's worth a try, but my knowledge is far too limited to grasp an understanding of what you have laid out. I am persistent, but quite illiterate yet. Argh!

Can I do this all from the Ubuntu konsole, or am I navigating to another place?

---

### Post by oldfred on 2010-12-11
Yes, just open up a terminal session and run 
gedit /boot/grub/grub.cfg
That should show the grub.cfg file (that you do not edit) and scroll to the bottom. It looks like grub's os prober has added the new boot stanzas at the end.
You copy those stanzas.
Then run this:
gksudo gedit /etc/grub.d/40_custom
Paste into this file below the few lines in it. Edit as discussed to remove the errors. save & run the update to add then to your grub.cfg menu.
sudo update-grub

Note when you reboot you will still have the old not correct entries, then your edit entries. You will have to scroll down as the grub menu box probably will not show all the entries.

If the edited entries work then we can turn off the osprober to eliminate the wrong entries.

If it does not work, rerun the boot script so we can see what is where.

---

### Post by bro brian on 2010-12-12
Holy Toledo, Oldfred - IT WORKED!!!!
I just can't believe I pulled that off... :roll:... I have 2 additional lines at the bottom of the bootload sequence. The old ones are still there, but the 2 new lines both load Mandriva. The Ubuntu loads as well.
  I don't think that I'll remember how to do this again, so I'd better print this thread out, and stay subscribed to it. Oldfred, many thanks for your expanded instruction as well as to Quackers & the other's input. This is one of those stumbling blocks that makes me think about giving up, but somehow keep going. I will have to reflect on this lesson for a few days.
  Here is a picture showing the end result - showing the 2 lines on the bottom of the boot order. I will also try to mark this thread as solved.

[IMG]http://i245.photobucket.com/albums/gg62/brobri_photos/Bootloadafterconfigeditresized.jpg[/IMG]

---

### Post by oldfred on 2010-12-12
You now can turn off the osprober. If you ever update system you can turn it back on temporarily if you want. This will remove the "wrong" entries.

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

then
sudo update-grub

I find the best way to document boot configuration & partitions is the bootinfo script. I run it before & after I make system or partition changes and I have now added it to my backup script to rerun it and include it in my backup of /home.  Link to script in quackers post #2.

---

### Post by bro brian on 2010-12-12
And what is the command for turning the osprober back on, may I ask?

---

### Post by oldfred on 2010-12-12
Why would you ever want to turn it back on, you know how to manually add entries.:)

Oh.
Just reverse the turn off entry (you only do one or the other). Change to false or add # to make it a comment. Or with the chmod command +x so it is executable. chmod is a command to change a file from execute to not execute among others. See man chmod for details.

GRUB_DISABLE_OS_PROBER=False
or
sudo chmod a+x /etc/grub.d/30_os-prober

---

### Post by bro brian on 2010-12-12
Oldfred, you so funny. I have no idea why I would want to turn it back on, but thanks for explaining that to me. You've got to admit that I'm getting one heck of a schooling! lol...

---

### Post by bro brian on 2010-12-14
This is my System76 Pangolin Performance (P-5) laptop with the finished result.
Left side: Ubuntu 10.04 (Lucid Lynx) os with Gnome desktop
Right side: Mandriva 2010.1 (Spring) os with KDE desktop

  I just can't thank you all enough for your input. I am really happy with the end result. I really wanted a dual-boot where I had the option of using applications native to either the KDE or Gnome. I probably should've went with the Kubuntu, and probably wouldn't have run into the problems I encountered had I done so, but I am very happy with the Mandriva as well. Mandriva was the first Linux operating system I learned, so I am somewhat comfortable with it - except for the booting issue. Having said that, I love the Ubuntu as well for it's "user-friendly" properties. With your help, and a little persistence, I ended up with a pretty sweet laptop, ya think?

[IMG]http://i245.photobucket.com/albums/gg62/brobri_photos/DualBootscreensDec2010.png[/IMG]

---

