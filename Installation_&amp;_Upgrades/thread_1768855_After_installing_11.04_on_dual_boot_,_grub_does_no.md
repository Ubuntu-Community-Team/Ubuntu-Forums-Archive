---
title: "After installing 11.04 on dual boot , grub does not load"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by juanmunoz on 2011-05-27
I have arch installed on my desktop. I have a root , swap ,home partition for it, to install Ubuntu I changed the root partition and split it. There I installed ubuntu on a new partition. After installation I rebooted and grub did not load. On arch I had grub installed on sda

---

### Post by oldfred on 2011-05-27
Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by juanmunoz on 2011-05-27
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63     2,345,489     2,345,427  82 Linux swap / Solaris
/dev/sda2           2,345,490   197,657,989   195,312,500  83 Linux
/dev/sda3         392,965,965   976,768,064   583,802,100  83 Linux
/dev/sda4    *    197,658,624   392,964,095   195,305,472  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e5a4bda7-af04-4866-af32-63d324fb8cae   swap       
/dev/sda2        b6f26bfb-0dfe-4486-be37-fdfe3f0015be   ext4       
/dev/sda3        16bdd8d8-9895-473a-bd81-e13fa5f07446   ext4       
/dev/sda4        a013c585-7c8a-429c-b02c-2ec7a33f8342   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/sda2 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/sda2 ro
initrd /boot/kernel26-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda1 swap swap defaults 0 0
/dev/sda2 / ext4 defaults 0 1
/dev/sda3 /home ext4 defaults 0 1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   3.106431007 = 3.335504896    boot/grub/menu.lst                             1
   3.106648445 = 3.335738368    boot/grub/stage2                               1
   1.274891853 = 1.368904704    boot/kernel26-fallback.img                     1
   1.266564369 = 1.359963136    boot/kernel26.img                              1
   3.108872414 = 3.338126336    boot/vmlinuz26                                 1

=========================== sda4/boot/grub/grub.cfg: ===========================

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
```

---

### Post by juanmunoz on 2011-05-27
Hope  I posted it right . I put it in a new reply.

---

### Post by oldfred on 2011-05-27
You did not post the entire results.txt. On the part you posted, there does not look like anything is wrong.

You have grub2 in the MBR and it is looking at sda4 to boot. You have a grub.cfg in sda4, so it should load that. If grub's os-prober has not found Arch yet, you may be booting thru grub, but then have other Ubuntu issues. When grub only sees one install, it does not show menu. If you hold shift key down from BIOS until menu should appears, do you get menu?

What error message or screen are you getting?

---

### Post by juanmunoz on 2011-05-28
When I press shift, nothing appears it just does the same thing , my monitor says mode not supported. before The grub worked when I just had arch.

---

### Post by oldfred on 2011-05-28
It still sounds like a video issue. Did you hold shift key down the entire time. Or are you booting with grub legacy then it is the escape key.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by juanmunoz on 2011-05-30
now I just saw that it booted after awhile to ubuntu 11.04 , so the problem is that my grub screen does not appear for me to pick between os.Pushing shift or escape did not work . I will try to do the NOMODESET.

---

### Post by juanmunoz on 2011-05-30
problem solved I just opened /etc/default/grub and uncommented the line that says gfxmode=680x480. Then I just updated my grub file from the terminal. 

         Thanks oldfred for the help and giving me those really good threads to look at.

---

