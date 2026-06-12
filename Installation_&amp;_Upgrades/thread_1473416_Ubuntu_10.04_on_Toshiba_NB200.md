---
title: "Ubuntu 10.04 on Toshiba NB200?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by i_surf_the_turf on 2010-05-05
Hi

I upgraded recently to the new version of ubuntu on a toshiba NB200 netbook and it didn't work! It just throws me out to a basic shell. I tried installing it "de neuf" but still no luck. The weak atom processor only runs properly on Linux, so I'm currently an unwilling windows user.

Or I could also install the good old 9 version but it's no longer availiable through the site.

HELP!

---

### Post by lechien73 on 2010-05-05
Did you try to install the full version, or Netbook Remix? Do you get any error messages before or after being dumped to the shell?

---

### Post by i_surf_the_turf on 2010-05-05
Hello

I used the full version since I had tried the older netbook remix and I couldn't really use it the way I wanted to. It displays a bunch of I/O errors after installation and then it says when trying to boot:

Gave up waiting for root device. Common problems:
boot args
check rootdelay
check root
missing modules
alert! /dev/disk/by-uuid/..... Does not exist. Dropping to a shell.

Actually I've tried changing the rootdelay parameter but I'm not sure I even did it correctly. I added rootdelay=9 in a line that was pointed out to me.

Any ideas?

---

### Post by lechien73 on 2010-05-05
Did you do the upgrade from a USB stick?

It would be helpful if you were able to boot from a live CD/USB stick, then download and run:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and post the output here.

---

### Post by i_surf_the_turf on 2010-05-05
Thanks for the help! Here is the output:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

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
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *          2,048       821,247       819,200   7 HPFS/NTFS
/dev/sda2             821,248    88,678,344    87,857,097   7 HPFS/NTFS
/dev/sda3          88,678,398   312,580,095   223,901,698   5 Extended
/dev/sda5          88,678,400   283,990,015   195,311,616  83 Linux
/dev/sda6         283,992,064   312,580,095    28,588,032  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1025 MB, 1025507328 bytes
32 heads, 62 sectors/track, 1009 cylinders, total 2002944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     2,001,855     2,001,794   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CA4A54A14A548BD7                       ntfs       SYSTEM                        
/dev/sda2        6EC856B5C8567AF3                       ntfs       WINDOWS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        78d8c5cf-3f88-43d3-a477-00cd311bb5be   ext4                                     
/dev/sda6        82bdf31e-4f5e-414b-a820-a6767f05b864   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B033-A7C4                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
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
search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=78d8c5cf-3f88-43d3-a477-00cd311bb5be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=78d8c5cf-3f88-43d3-a477-00cd311bb5be ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 78d8c5cf-3f88-43d3-a477-00cd311bb5be
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ca4a54a14a548bd7
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
UUID=78d8c5cf-3f88-43d3-a477-00cd311bb5be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=82bdf31e-4f5e-414b-a820-a6767f05b864 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.8GB: boot/grub/core.img
 142.2GB: boot/grub/grub.cfg
  64.8GB: boot/initrd.img-2.6.32-21-generic
  64.8GB: boot/vmlinuz-2.6.32-21-generic
  64.8GB: initrd.img
  64.8GB: vmlinuz

---

### Post by lechien73 on 2010-05-05
Sorry about the delayed reply - it's been a long and not entirely successful day :|

Anyway, your Grub config appears fine to me - maybe some gurus on here could correct me if I'm wrong.

As a test, I would recommend doing the following. This will only make a one-time change, but if it works, then it indicates a problem passing the UUID (long number) to Linux.

1. Use the arrow keys to highlight the Ubuntu entry in Grub.
2. Press 'e' to edit the entry.
3. Delete the 'search' line. Use the up and down arrow keys to place the cursor at the start of the line and hold the "del" key.
4. On the 'linux' line, change 'root=UUID=<long number>' to 'root=/dev/sda5' Leave the rest of the line as it is.
5. Now press CTRL-X to reboot.

Let us know how you get on :)

---

### Post by i_surf_the_turf on 2010-05-05
Sorry to hear about the unsuccessful day... Anyway I did what you said. Unfortunately all it does is to freeze with a blinking terminal cursor on the screen........

Do you know where I can find the previous version?

Many thanks for the help!

---

### Post by i_surf_the_turf on 2010-05-05
Hey!


It actually loaded after a loooongtime!

I;m replying through ubuntu right now!

How do I make this permanent then?

---

### Post by lechien73 on 2010-05-05
Great news...eventually :)

You can run:
```
sudo update-grub
```

and then try rebooting. Hopefully it will stay working!

---

### Post by i_surf_the_turf on 2010-05-05
It does work!

Thank you very much! 

The only problem is that it takes forever to load. And when I say forever, I mean about 7 minutes....

---

### Post by jeroenimo on 2010-05-05
Same thing here..  takes for ages to boot.. must be about 7 minutes here too.
I'm updating kernel and I see there is an update for grub-pc too so I hope it makes a difference

---

### Post by lechien73 on 2010-05-05
Try going into your BIOS settings and change the **SATA Controller Mode**, it's probably set to *AHCI*, so set it to *Compatibility*.

If that solves it, please mark the thread as [Solved] by using the "Thread Tools" option at the top of the page. And enjoy!!! :D

---

### Post by i_surf_the_turf on 2010-05-05
I'll try that, but probably tomorrow, I cant wait another slow load.....
Thanks again!

By the way, [jeroenimo]("http://ubuntuforums.org/member.php?u=913909") I just used your guide for bluetooth for the 12th time or something! Thanks again to you too!

---

### Post by jeroenimo on 2010-05-05
> **lechien73 said:**
> Try going into your BIOS settings and change the **SATA Controller Mode**, it's probably set to *AHCI*, so set it to *Compatibility*.

If that solves it, please mark the thread as [Solved] by using the "Thread Tools" option at the top of the page. And enjoy!!! :D
That my friend was the trick, it boots in 15 seconds now ;-)

---

### Post by lechien73 on 2010-05-06
Great...glad to hear it. Have fun :)

---

### Post by pete2222 on 2010-05-07
Can you guys advise whether your Ubuntu 10.04 is now running fine, including sound and WiFi on the toshiba NB200.  I am thinking of installing it on mine, and need some guidance on whether it's worthwhile trying.

---

### Post by antoinef on 2010-05-11
Hey folks, 

Same question as Pete2222 - can you confirm that the UNR 10.04 now works fine ?

I initially upgraded from the Update Manager from Karmic to Lynx, and had the same issues, so rolled back to 9.10. Just want to make sure it's worth upgrading again !

---

### Post by lechien73 on 2010-05-11
It might be a good idea to start a new thread and ask these questions. Now that this thread is marked as solved, it probably doesn't get checked that often.

---

### Post by pete2222 on 2010-05-11
> **antoinef said:**
> Hey folks, 

Same question as Pete2222 - can you confirm that the UNR 10.04 now works fine ?

I initially upgraded from the Update Manager from Karmic to Lynx, and had the same issues, so rolled back to 9.10. Just want to make sure it's worth upgrading again !

 In my case I am using the netbook version from a usb stick. It seems to be working fine, except sound, which is working  from the headphones only.

---

### Post by Myronas on 2010-05-11
Hi to all, this is my first post on this forum, and I really need your guidance and advice.

I'm really interested in this netbook nb200-10z and in this afternoon I went to the shop to see it. I booted from my usb flash drive where I had installed the ubuntu 10.04 (normal distro). It booted perfectly and then I checked some things:


[LIST]
[*]The touchpad was detected as supposed with scrolling working fine
[*]the wifi card was detected correctly (i think) as I executed the command iwconfig and saw the card detected. By the way this card is b/g/n !! N is supported and the manufacturer keeps it secret!?!?!
[*]Bluetooth was not detected.
[*]Sound wasn't tested as I didn't know before that may were issues with that
[/LIST]
So, please tell me have you tried ubuntu 10.04 on this netbook and what systems don't work out of the box? Your opinion is crutial as I would like to make a decision till tomorrow and go buy it.

---

### Post by pete2222 on 2010-05-11
> **Myronas said:**
> Hi to all, this is my first post on this forum, and I really need your guidance and advice.

I'm really interested in this netbook nb200-10z and in this afternoon I went to the shop to see it. I booted from my usb flash drive where I had installed the ubuntu 10.04 (normal distro). It booted perfectly and then I checked some things:


[LIST]
[*]The touchpad was detected as supposed with scrolling working fine
[*]the wifi card was detected correctly (i think) as I executed the command iwconfig and saw the card detected. By the way this card is b/g/n !! N is supported and the manufacturer keeps it secret!?!?!
[*]Bluetooth was not detected.
[*]Sound wasn't tested as I didn't know before that may were issues with that
[/LIST]
So, please tell me have you tried ubuntu 10.04 on this netbook and what systems don't work out of the box? Your opinion is crutial as I would like to make a decision till tomorrow and go buy it.

The wifi card works fine on mine as does the mousepad. Speakers don't though. 
 I don't have bluetooth on my nb200 so can't comment.

---

### Post by Myronas on 2010-05-12
> **pete2222 said:**
> The wifi card works fine on mine as does the mousepad. Speakers don't though. 
 I don't have bluetooth on my nb200 so can't comment.

The function keys are working properly? The hibernation? Have you noticed reduced working times or excessive power consumption?

For your problem with the sound you can find many solutions in this forum.

---

### Post by tsixlas on 2010-06-10
My 10.04 ubuntu installation has the following problem. Whenever i leave my laptop alone for a couple of seconds, the system hung. No refresh is happening to the screen (the time is stuck) and if i have music playing it stuck too. If I move the mouse pointer everything return to normal. If i stop moving the mouse, after a while it happens again.

---

