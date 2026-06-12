---
title: "Unable to hide Grub2 menu at startup"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by tdunk on 2011-04-08
Hi

I have serious problems hiding the Grub menu at startup.

What I want to do is simple boot into the first (and only) item without showing the menu to the user.

I have removed everything on the system so the only option is  "GNU/Linux, with Linux 2.6.32-30-generic" in the menu.

My /etc/default/grub is like this:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
....
```

I have tried with different values in GRUB_TIMEOUT with/without quotes.

I have tried with different values in GRUB_HIDDEN_TIMEOUT with/without quotes.

I have "chmod -x" on 30_os_prober to avoid probing.

After each modification of /etc/default/grub I run "sudo update-grub" without any errors.

No matter what I do I always get the same result:

The menu is shown and no countdown!

It's like grub isn't reading the changes of /etc/default/grub

Could someone please give me a clue of what's going on and why I'm unable to hide the menu?

Thanks!

---

### Post by Rubi1200 on 2011-04-08
Did you run ```
sudo update-grub
``` after making these changes?

---

### Post by tdunk on 2011-04-08
Yes, after every change. I also tried booting after every change, but no changes in boot menu behavior.

My disk is partitioned into one 40GB partiotion with ubuntu and one extended with another partition. Could that be the reason?

---

### Post by Rubi1200 on 2011-04-08
Please do the following so we can get a better overview of the current state of the system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tdunk on 2011-04-08
Thanks. Here is the result:

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372  83 Linux
/dev/sda2          81,915,435   488,392,064   406,476,630   5 Extended
/dev/sda5          81,915,498   488,392,064   406,476,567  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a02a0a55-9828-42e0-8f10-b4c20a907922   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9253b6ac-5ef2-4b46-8f3f-77a82d114d7e   ext3       RestorePart                   
/dev/sda: PTTYPE="dos" 
/dev/sdb         26F2-CE95                              vfat       4GB                           

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

```

---

### Post by Rubi1200 on 2011-04-08
Are you sure this is the whole file?

I wanted to see the grub.cfg parts of the results.

---

### Post by tdunk on 2011-04-08
Sorry gedit isnt coping it all. Here is the reminder:

```

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
search --no-floppy --fs-uuid --set a02a0a55-9828-42e0-8f10-b4c20a907922
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
search --no-floppy --fs-uuid --set a02a0a55-9828-42e0-8f10-b4c20a907922
set locale_dir=($root)/boot/grub/locale
set lang=da
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'GNU/Linux, with Linux 2.6.32-30-generic' --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a02a0a55-9828-42e0-8f10-b4c20a907922
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=a02a0a55-9828-42e0-8f10-b4c20a907922 ro  splash quiet  quiet splash usbhid.quirks=0xeef:0x1:0x40
    initrd    /boot/initrd.img-2.6.32-30-generic
}

### END /etc/grub.d/10_linux ###

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
UUID=a02a0a55-9828-42e0-8f10-b4c20a907922 /               ext3    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


   2.6GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.32-30-generic
    .2GB: boot/vmlinuz-2.6.32-30-generic
    .2GB: initrd.img
    .2GB: vmlinuz


```

---

### Post by tdunk on 2011-04-08
I think I have found the problem.

In 00_headers ${recordfail} is alway 1 causing timeout to be set to -1.

Changing the line "set timeout=-1" to "set timeout=0" causes the system to boot without showing the grub menu. 

```

set locale_dir=($root)/boot/grub/locale
set lang=da
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi

```

I have checked directory /boot/grub/locale and it does not have a "da" locale. Could that be the reason for recordfail=1 ?

There is no reason for "lang" to be set to "da", but I don't know how to change it to "en".

---

### Post by drs305 on 2011-04-08
tdunk,

If you are seeing the menu without a timer it's possible that a 'recordfail' trigger is halting the menu. While it is sometimes difficult to detmine what is triggering the event, we can see if that is what is causing the problem. Even though you don't want to see the timer, it's inablility to count down could be an associated problem.

Open grub.cfg for editing:
```
gksu gedit /boot/grub/grub.cfg
```

Comment out the following section. 
Add the # symbol to each of these lines:
> 
**[COLOR="DarkRed"]#[/COLOR]**if [ ${recordfail} = 1 ]; then
**[COLOR="DarkRed"]#[/COLOR]**  set timeout=-1
**[COLOR="DarkRed"]#[/COLOR]**else
**[COLOR="DarkRed"]#[/COLOR]**  set timeout=0
**[COLOR="DarkRed"]#[/COLOR]**fi

Save the file but do NOT update-grub, as this is only a temporary fix and the update would remove your changes.

Let us know if this allows you to now boot. You might want to first see if you can get a timer. If you want to do that, change the GRUB_TIMEOUT in /etc/default/grub, update-grub and THEN make the changes above.

---

### Post by tdunk on 2011-04-09
Hi

With the section commented out like this I see the menu and there isn't any countdown:

```

#if [ ${recordfail} = 1 ]; then
# set timeout=-1
#else
# set timeout=0
#fi

```

Like below the timeout is always zero and the menu is hidden:

```

#if [ ${recordfail} = 1 ]; then
# set timeout=-1
#else
  set timeout=0
#fi

```

I tried to copy one of the language files and renamed it to da.mo, but I still get recordfail=1.

To allow setting timeout from /etc/default/grub I have changed the section as above in the  00_header file. After a update-grub I can control the timeout. Setting the timeout value to 10 I see the menu and gets a countdown timer of 10s as expected. Setting timeout to zero grub is booting without showing the menu.

I think I'll leave it like this for now. This is ok for my purpose.

Thanks you all for you help. I had tried everything for several days and you guys put me on track within minutes! I can't thank you enough!

Best regards

---

### Post by drs305 on 2011-04-09
tdunk,

Yes, I had an extra comment in the timeout line. As you discovered, leaving the timeout at 0 results in not seeing the menu at all but also means something is triggering the recordfail.

As long as you are happy with it the way it is I'd leave it alone, Just realize that if the Grub2 (grub-pc) package is updated you will need to make the change to 00... once again.

One other thing that might be of interest: If your grub.cfg file  doesn't include a section with a 'keystatus' check you may not be able to call up the menu if you have a problem. You can either manually insert the keystatus check or leave the timeout at 1 so you have a short period of time to stop at the menu. If you need help with the keystatus check let me know.

---

