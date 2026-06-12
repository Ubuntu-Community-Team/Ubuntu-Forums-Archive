---
title: "HELP - just upgraded to 10.04 and it killed my computer"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by LutraMan on 2010-06-28
it doesn't load, it's just stuck on that screen:
```

GRUB loading.
error: the symbol 'grup_puts_' not found
grub rescue>
```

---

### Post by Rubi1200 on 2010-06-28
Hi,
do you have the CD you used to install Ubuntu?

If you have a CD you can boot the computer and then use the script in my signature. Follow the instructions and post back here so that we can help you resolve this.

---

### Post by LutraMan on 2010-06-28
I have the karmic koala cd
(and right now I'm on Fedora live CD)

I had karmic for about 6 month to a year (I think) and now I just clicked the "upgrade now" button on the ubuntu update window.

---

### Post by Rubi1200 on 2010-06-28
Ok, so you have an Internet connection; great!

Click on the link in my signature and follow the instructions there. Post back here and please wrap the text with the code tags.

---

### Post by LutraMan on 2010-06-28
one problem.
I see that in the instructions I need to use the sudo command on something.
last time I tried it in Fedora livecd, I got this message:

```
We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

liveuser is not in the sudoers file.  This incident will be reported.

```

do you know of anyway to get around it?

---

### Post by LutraMan on 2010-06-28
actually, nevermind...
kept on reading and found it myself

---

### Post by LutraMan on 2010-06-28
RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 450623 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ba40ba3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,072,529   613,072,467  83 Linux
/dev/sda2         613,072,530   625,137,344    12,064,815   5 Extended
/dev/sda5         613,072,593   625,137,344    12,064,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   976,771,518   976,771,485 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/dm-0        51e0bdfc-1a89-45e0-b993-9953dc69e6b8   ext3       F10-i686-Live                 
/dev/dm-1        51e0bdfc-1a89-45e0-b993-9953dc69e6b8   ext3       F10-i686-Live                 
/dev/loop0                                              squashfs                                 
/dev/loop2                                              squashfs                                 
/dev/loop3       51e0bdfc-1a89-45e0-b993-9953dc69e6b8   ext3       F10-i686-Live                 
/dev/sda1        5514bbc3-367a-48c9-b4f7-1eba3879a3a0   ext4                                     
/dev/sda5        9363c7ff-c67a-41fa-bf27-74d9364de52f   swap                                     
/dev/sdb1        72467e01-decf-4afa-aa91-cda9491e7b42   ext4                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
live-osimg-min
live-rw

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/live-rw /                        ext3       (rw,noatime)
/dev/sr0         /mnt/live                iso9660    (ro)


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
search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
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
search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5514bbc3-367a-48c9-b4f7-1eba3879a3a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=5514bbc3-367a-48c9-b4f7-1eba3879a3a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=5514bbc3-367a-48c9-b4f7-1eba3879a3a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=5514bbc3-367a-48c9-b4f7-1eba3879a3a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5514bbc3-367a-48c9-b4f7-1eba3879a3a0
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=5514bbc3-367a-48c9-b4f7-1eba3879a3a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9363c7ff-c67a-41fa-bf27-74d9364de52f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# 1 line added by user (Tom)
UUID=72467e01-decf-4afa-aa91-cda9491e7b42 /storage ext4 defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
  25.4GB: boot/initrd.img-2.6.31-22-generic
  25.3GB: boot/initrd.img-2.6.32-22-generic
  18.0GB: boot/vmlinuz-2.6.31-22-generic
  19.3GB: boot/vmlinuz-2.6.32-22-generic
  25.3GB: initrd.img
  25.4GB: initrd.img.old
  19.3GB: vmlinuz
  18.0GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file
```

---

### Post by LutraMan on 2010-06-29
bump?

---

### Post by Rubi1200 on 2010-06-30
I see that nobody has answered your post yet so I will try and get it more attention.
First, a question: what do you have on sdb1; an external HDD and is the drive bootable?

Your bootscript results indicate a problem with GRUB, but it would be better if you wait for one of the experts to come along and lead you through this.

Hang in there!

---

### Post by tommcd on 2010-06-30
Well, I am not an expert, but I will try to help.
Try reinstalling grub2 to the MBR of /dev/sda (your first hard drive, which has Ubuntu installed to /dev/sda1).
See this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
You will do this from the Ubuntu live CD, not the Fedora live CD.
The Fedora live CD may have some method of reinstalling grub as well; but I am not familiar with Fedora.

---

### Post by LutraMan on 2010-07-01
ok, followed the instructions on method 1 from the link you gave me. mostly it went ok, except for one error, here is the output:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ba40ba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38162   306536233+  83  Linux
/dev/sda2           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386583+  ee  GPT
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
[B]ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.[/B]

ubuntu@ubuntu:~$ 

```

I'm restarting the computer now, I'll let you know if it worked.

---

### Post by LutraMan on 2010-07-01
first of all tnx! (but I still need more help)

ok, so there is some progress, I got my system back, but with heavy damage.

the facts are these:
 - when grub is loading, I'm getting an error, but it disappears to quickly for me to read. (any log that I can access to view it?)
 - the screen flickers when ubuntu is loading and when it loads, it gives me an error message that ubuntu is running on low graphics mode. 
 - when the computer is actually loading, I see that there is no window manager and I can't load compiz, I'm getting an error message if I try: "desktop effects could not be enabled"

should I try to reinstall NVIDIA?

---

### Post by tommcd on 2010-07-01
> **LutraMan said:**
> 
 - when grub is loading, I'm getting an error, but it disappears to quickly for me to read.
After you boot the system, try running:
```
sudo update-grub
```
If it reports errors, post them here.
> **LutraMan said:**
> 
 - the screen flickers when ubuntu is loading and when it loads, it gives me an error message that ubuntu is running on low graphics mode. 
 - when the computer is actually loading, I see that there is no window manager and I can't load compiz, I'm getting an error message if I try: "desktop effects could not be enabled"
should I try to reinstall NVIDIA?
I would disable compiz until you get the graphics problem sorted out.
What nvidia card do you have? You could try reinstalling the nvidia driver?
Question: How did you install the nvidia driver in the first place? Did you install the driver from the Ubuntu repos (the preferred method) or did you install the driver from nvidia.com?

---

### Post by LutraMan on 2010-07-02
ok, I ran the command "sudo update-grub" and here is the output:
```
sudo tom@tom-desktop:~$ sudo update-grub
[sudo] password for tom: 
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
tom@tom-desktop:~$ 

```

I'm restarting now and I'll fill you in.


about Nvidia, I have 8600 (if I remember correctly, but I'm sure it's 8 series) and I installed it automatically using ubuntu - I received a message in the upper-right corner of the screen that there are restricted drivers available and I approved the installation.

---

### Post by LutraMan on 2010-07-02
ok... so... uhmmm...
well, some change (very small though). The error in the grub was replaced by a little bit more friendly info message that says something about the linux image.
However, besides that, not much of an improvement. The screen still flickers on loading and loads without a window manager.

but this might help! this is the error message regarding the NVIDIA problem (it's not copy-paste, so there may be some typing mistakes): ```
The following error was encountered. you may need to update your configuration to solve this.
(EE) jul 02 20:35:46 NVIDIA(0): failed to initialize NVIDIA kernel module. Please see the system kernel log for additional error messages and consult NVIDIA README for detailes
(EE) NVIDIA(0): *** Aborting ***
(EE) screens found but none have a usable configuration.
```

BTW: as I typed the error message to this post I recalled that I encountered this error in the past and got a black screen (the first time I tried ubuntu and fedora) formatting and/or reinstalling the system didn't help. I eventually fixed this problem by physically replacing the graphic card and the replacing it back, though I don't think that what actually fixed the problem, I did a whole other bunch of crazy things to try and fix it.

(there is a post of mine of this error somewhere in the ubuntu and fedora archive, both unsolved because I couldn't figure out what the h$ll I did)

---

### Post by LutraMan on 2010-07-02
another update:

when I go to "System > Administration > Nvidia X server settings" I get an error message:
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

I typed in:
```
sudo nvidia-xconfig
```

it created a new xorg.conf file:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

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

```

but that didn't fix the problem, or did anything for that matter.

plzzzzz help

---

### Post by LutraMan on 2010-07-02
SOLVED!
first of all, tnx tommcd and rubi for the great help and education on grub.

and now, for anyone who happens to run into the same problem in the future and stumble on this thread in a google search, here is a step by step on the nvidia problem.

basically, what I did, is installed it manually. (this is NOT recommended and I suggest it only as a last resort if the ubuntu repository auto installation fails you)

1) download the driver from the NVIDIA website and remember where you saved it.
1.a) right click on the file and give make it executable (I'm not sure it's necessary but it doesn't hurt)
2) restart the computer, and hold down shift as before the GRUB loads, so it will throw you to the menu.
3) choose the recovery mode
4) drop to root shell
5) CTRL+ALT+F2 and log in (a clean way to get from runlevel 1 to 3 as required by the NVIDIA installation file)
6) cd to the directory where you saved the driver
7) type in ```
sudo ./*NVIDIA-Linux-x86-256.35.run*

``` (please notice that your file name may be different)
8 ) follow the NVIDIA instruction and when it asks whether to create a new xorg.conf file, let it.

**and now, a note for any ubuntu developer that may stumble on to this post:**
It is the forth time in a row, that right after a new ubuntu installation I have to sit in front of the computer and the ubuntu forums for days to fix endless problems, created by the "upgrade". Now it may work smoothly for most, but for me, this upgrade took 13 hours (because it kept stopping and waiting for me to answer questions when I wasn't around) and another 4 days to fix all the problems it created (and I'm still not sure I covered them all). I know you work hard over there, but PLZZZZZZZZZZZZZZ QA a little bit more thoroughly before you release your upgrades. It is a NIGHTMARE!

---

### Post by tommcd on 2010-07-03
> **LutraMan said:**
> SOLVED!
**and now, a note for any ubuntu developer that may stumble on to this post:**
It is the forth time in a row, that right after a new ubuntu installation I have to sit in front of the computer and the ubuntu forums for days to fix endless problems ...
1. Glad you got it fixed. I would have recommended upgrading to the latest driver in the Ubuntu 10.04 repos, but if the driver from nvidia.com is working for you then I would leave that alone. My nvidia 8600GT works just fine with the *nvidia-current* driver from the 10.04 repos.
Just remember that when there is a kernel upgrade for Ubuntu you may need to reinstall the nvidia driver. Just do it the same way you described in your last post and you should be fine.

2. FYI: The Ubuntu devs don't read this forum. If you want to post a bug or something you have to go to Launchpad. The Ubuntu devs do read and respond to  Launchpad posts.

3. FYI #2: This is why I always do clean installs of Ubuntu. I (almost) always do clean installs of every distro that I use. You start from a clean slate and avoid all the *residual detritus and sludge*, for lack of a more "technical" term, that can be left behind from a dist-upgrade.

---

### Post by Rubi1200 on 2010-07-03
> **LutraMan said:**
> SOLVED!
first of all, tnx tommcd and rubi for the great help and education on grub.

More than welcome! I hope your experiences with Ubuntu will be easier in the future.

:)

---

