---
title: "Dual boot problem-no grub menu"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2011-01-01
I have set up dual boot many times. windows/ubuntu.
Today I wiped out the ubuntu partition but I left the windows partition intact. I then reinstalled windows on its old partition and then I ran ubuntu 10.04 setup from a desktop version dvd. 

After installation was finished I rebooted. It goes right into windows. No grub menu. I ran gparted and it shows the ubuntu partition next to the windows partition.

Tried many ways to figure it out. No solution. I then tried to set up wireless internet connection on windows so I could post this. Network setup on windows shows no networks available. 

I reinstalled ubuntu again. I then ran gparted off a cd and it showed my drive as EMPTY. So I installed a livecd and ran its gparted. It shows both operating systems. 

Whats going on?

---

### Post by Idefix82 on 2011-01-01
Wow, this was confusing. So question number one is: is this all one hard drive and several partitions or is it actually several hard drives? How did you install Ubuntu? Did you choose "manual partitioning" or "install Ubuntu next to another OS"?

Can you boot from the Ubuntu Live cd and select "try ubuntu", then, when the desktop is loaded, make sure you have an internet connection and go to [this site]("http://bootinfoscript.sourceforge.net/") and download the boot script to your Desktop. Then, open up a terminal (Applications > Accessories > Terminal) and run

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the content of that file and paste it in your next post between CODE tags.
This will give a full overview of your current system.

If you can't get an internet connection in the live session, then you can download the script beforehand (e.g. from Windows) and save it on a usb stick, then boot the Live session and copy the script from the usb onto the desktop and run the above command.

---

### Post by sofasurfer on 2011-01-02
Well, that didn't go well...
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 


Heres my latest steps...
I have 1 drive.
I wiped it clean.
I installed winxp. Afterwards, winxp actually booted up. I then run a gparted livecd and it shows the ntfs partition but it shows it as empty. So I run gparted off the lucid livecd and it shows the same thing. I clicked on "information" and it says that the partition can not be read. I think it had something to do with clusters. So I used the livecd to access this forum to get help.

Now, before these steps, earlier, I did the same steps and at that time the gparted licecd also did not read the partition, BUT gparted on the lucid livecd DID read it, but now it does not.

Could this be a loose connection? Drive going bad? I doubt that the drive is bad cause everything has been fine for months until today when I tried to reinstall my system.

While I am waiting for your reply I am going to wipe it again and try installing JUST ubuntu and see if it makes a difference with out winxp.

---

### Post by Quackers on 2011-01-02
To run that command, the downloaded boot script needs to be on the Desktop...is it? Or did you download it to Downloads? Copy/paste to the Desktop if necessary, then try running it again.

---

### Post by sofasurfer on 2011-01-02
O crap! I did not download the boot script. Sorry. I'm tired. 
I will make another attempt now.
In the meantime, heres what I did. I now have Lucid only, installed and working. I then installed the gparted livecd and it still shows a empty partition. The error in "information" says "can't find a valid filesystem superblock".

Heres the results of the script...

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   484,245,503   484,243,456  83 Linux
/dev/sda2         484,247,550   490,233,855     5,986,306   5 Extended
/dev/sda5         484,247,552   490,233,855     5,986,304  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        34b0eeb7-513e-469d-8259-320b07a8b422   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        11628694-03da-42ca-b520-27ce84ee069f   swap                                     
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
search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
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
search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=34b0eeb7-513e-469d-8259-320b07a8b422 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=34b0eeb7-513e-469d-8259-320b07a8b422 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34b0eeb7-513e-469d-8259-320b07a8b422
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=34b0eeb7-513e-469d-8259-320b07a8b422 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=11628694-03da-42ca-b520-27ce84ee069f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
 141.8GB: boot/grub/grub.cfg
  25.9GB: boot/initrd.img-2.6.32-21-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
  25.9GB: initrd.img
  25.9GB: vmlinuz


Its real late here. I'll get back to this tomorrow. Thanks for your time and help.

---

### Post by Quackers on 2011-01-02
There is no mention at all of Windows on that drive - only Ubuntu 10.04

---

### Post by sofasurfer on 2011-01-02
I told you up above that I installed only ubuntu this time. If I install windows and ubuntu I can not access ubuntu because there is no boot menu. But I am wondering now why gparted shows my partition as empty and gives me the "can't find a valid filesystem superblock" error.

---

### Post by Quackers on 2011-01-02
Presumably something was wrong with grub, when you couldn't access Ubuntu with Windows installed.
If gparted can't display the partitions, it may think something is wrong with them, or maybe there is a disc problem.

---

### Post by llawwehttam on 2011-01-02
To me it looks like grub is not installed on the MBR.

try ```
sudo grub-install
```

---

### Post by sofasurfer on 2011-01-02
This is rediculous! Now when I boot I get a login prompt. And entering me name and password gets me knowhere.

I blew a lot of dust out of my pc case. Could dust have gotten on the boards and caused this? This is not a bad drive problem and it is not a bad install problem. I did the reinstalls but gefore I did I disconnected my backup drive so I would be sure not to harm the data on it. While I was in there I saw a lot of dust and I blew it out.

---

### Post by Quackers on 2011-01-02
What do you mean, entering your name and password gets you nowhere? Does it log you in? Have you tried startx? Ctrl + Alt + F7 - anything like that, to get to a desktop?

---

### Post by Idefix82 on 2011-01-02
sofasurfer, it is hard to keep pace with your installs and reinstalls. You said before that you had successfully installed Lucid and it worked. The output you provided looks fine to me (llawwehttam, Grub **was** installed). Now, apparently it doesn't work, but it's not clear what you did between then and now.

It is also not clear, what state you actually want to get to. Do you want to dual boot or do you just want Ubuntu or neither? Why were you tinkering with that successful Lucid install?

---

### Post by sofasurfer on 2011-01-02
I suspect that my copy of gparted was not operating properly. When I installed windows gparted was showing I had an empty partition. I downloaded a newer copy and ran it. It showed the partition as being use but said I needed to run chkdsk /f. This corrected my problem because I then install a dual boot with no trouble.

---

