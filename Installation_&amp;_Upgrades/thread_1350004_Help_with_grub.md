---
title: "Help with grub"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by evworld on 2009-12-08
I am kind of new to linux so bear with me.
 
Here is how I had my system set up and I would like to get it back to the same way.
 
I have two sata hard drives installed. I unplugged one and installed vista onto it. I then unplugged that drive and plugged in the second drive and installed ubuntu on to it.
 
Everything was fine. Which ever system I wanted to use I just booted from the bios. I had the vista drive in the primary slot and my computer booted to it without doing anything.
 
Today I had an update while using Ubuntu. The update was for grub. Not knowing anything would happen I installed it. Now my system is set up as a dual boot the normal way. When I restart my computer Grub loads and I have to pick which sytem to boot into. 
 
If I unplugg the linux drive and restart, grub tries to load and I get some error. No operating system will load. If i plug both drives in and restart grub comes up and I pick which on to run.
 
Before if I had the linux drive unplugged vista would load as normal.
 
What I would like to is get it back to how I had it before. Vista would boot with no grub showing up if I rebooted. If I wanted to run linux I needed to boot to 2nd drive via the bios.
 
Does any one know if I can get it back that way?

---

### Post by presence1960 on 2009-12-08
> **evworld said:**
> I am kind of new to linux so bear with me.
 
Here is how I had my system set up and I would like to get it back to the same way.
 
I have two sata hard drives installed. I unplugged one and installed vista onto it. I then unplugged that drive and plugged in the second drive and installed ubuntu on to it.
 
Everything was fine. Which ever system I wanted to use I just booted from the bios. I had the vista drive in the primary slot and my computer booted to it without doing anything.
 
Today I had an update while using Ubuntu. The update was for grub. Not knowing anything would happen I installed it. Now my system is set up as a dual boot the normal way. When I restart my computer Grub loads and I have to pick which sytem to boot into. 
 
If I unplugg the linux drive and restart, grub tries to load and I get some error. No operating system will load. If i plug both drives in and restart grub comes up and I pick which on to run.
 
Before if I had the linux drive unplugged vista would load as normal.
 
What I would like to is get it back to how I had it before. Vista would boot with no grub showing up if I rebooted. If I wanted to run linux I needed to boot to 2nd drive via the bios.
 
Does any one know if I can get it back that way?

Why don't you just leave it as it is? You don't have to go into BIOS to choose which disk to boot. Turn the computer on and the GRUB bootloader lets you choose whether to boot windows or Ubuntu. This not only makes more sense but is also more convenient.

If you want it back to the way it was I need more info about your setup. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by evworld on 2009-12-08
I looked at the updates that I installed in the history and this is what I installed that changed the way my pc boots.

Commit Log for Tue Dec  8 20:13:12 2009


Upgraded the following packages:
grub-common (1.97~beta4-1ubuntu4) to 1.97~beta4-1ubuntu4.1
grub-pc (1.97~beta4-1ubuntu4) to 1.97~beta4-1ubuntu4.1
ntpdate (1:4.2.4p6+dfsg-1ubuntu5) to 1:4.2.4p6+dfsg-1ubuntu5.1

Can this help someone.  

I guess I can live with the way it boots but with my wife and kids have no idea what linux is.  It was something they didn't need to worry about if they rebooted our computer.

I was thinking if I unplugged my linux drive and tried to fix MBR with vista disc with that drive only plugged in.   My concern is that I am afraid that I will mess up my whole system and maybe I should just leave well enough alone.

If that is my course I guess I just need to figure out how to make vista the primary or first boot because linux is the first boot now.

---

### Post by evworld on 2009-12-08
> **presence1960 said:**
> Why don't you just leave it as it is? You don't have to go into BIOS to choose which disk to boot. Turn the computer on and the GRUB bootloader lets you choose whether to boot windows or Ubuntu. This not only makes more sense but is also more convenient.

If you want it back to the way it was I need more info about your setup. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

[FONT=monospace]When I do

[/FONT]sudo bash ~/Desktop/boot_info_script*.sh
[FONT=monospace]


I get an error saying

bash: /home/evworld/Desktop/boot_info_script*.sh: No such file or directory
evworld@evworld-desktop:~$ 

[/FONT]

---

### Post by presence1960 on 2009-12-08
> **evworld said:**
> [FONT=monospace]When I do

[/FONT]sudo bash ~/Desktop/boot_info_script*.sh
[FONT=monospace]


I get an error saying

bash: /home/evworld/Desktop/boot_info_script*.sh: No such file or directory
evworld@evworld-desktop:~$ 

[/FONT]
is the file on the desktop? The error is saying there is no file by that name on desktop. You must have downloaded it to another directory. Move it to desktop.

---

### Post by evworld on 2009-12-08
I don't believe it downloaded it anywhere,  If it did I can't find it.

---

### Post by presence1960 on 2009-12-08
> **evworld said:**
> I looked at the updates that I installed in the history and this is what I installed that changed the way my pc boots.

Commit Log for Tue Dec  8 20:13:12 2009


Upgraded the following packages:
grub-common (1.97~beta4-1ubuntu4) to 1.97~beta4-1ubuntu4.1
grub-pc (1.97~beta4-1ubuntu4) to 1.97~beta4-1ubuntu4.1
ntpdate (1:4.2.4p6+dfsg-1ubuntu5) to 1:4.2.4p6+dfsg-1ubuntu5.1

Can this help someone.  

I guess I can live with the way it boots but with my wife and kids have no idea what linux is.  It was something they didn't need to worry about if they rebooted our computer.

I was thinking if I unplugged my linux drive and tried to fix MBR with vista disc with that drive only plugged in.   My concern is that I am afraid that I will mess up my whole system and maybe I should just leave well enough alone.

If that is my course I guess I just need to figure out how to make vista the primary or first boot because linux is the first boot now.

I can help get it back to the way it was but I need that info so I can tell you what you need to do.

My seven year old daughter has been dual booting Ubuntu and XP for about a little over a year now. So she was 6 when she started dual booting. She was able to understand that to boot windows you scroll down the menu to highlight Windows then hit enter. I think if you explain this to your wife and kids they will be ok. 

If not like I said give me that info and we'll get it back to the way it was. I just want to be certain before I tell you to alter your system.

P.S. In school she is learning Mac OSX. In the not distant future the roles of me as teacher and her as student will most likely be reversed.

---

### Post by evworld on 2009-12-08
I can't get that script to run...  I past it into the terminal and this is what shows up.


evworld@evworld-desktop:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for evworld: 
bash: /home/evworld/Desktop/boot_info_script*.sh: No such file or directory
evworld@evworld-desktop:~$ 



I new to all this so I would at least like to learn to get that script to run.

---

### Post by presence1960 on 2009-12-08
> **evworld said:**
> I don't believe it downloaded it anywhere,  If it did I can't find it.

to see if it downloaded in firefox go Tools > Downloads and the window on left of below pic will open. if it is listed you downloaded it.

to see where it was downloaded go Edit > Preferences > Main tab. You will see a download section. There you will see what directory it was downloaded to. When you find it move it desktop and run that command

---

### Post by evworld on 2009-12-09
It didn't download it to firefox.    Tools > downloads there is nothing in the box.

The directory for firefox to download in   "Downloads"  It is not in there.   I just copied your script and pasted into the terminal.  I post what showed when I hit enter.   It appears to me that the command didn't run..??

---

### Post by evworld on 2009-12-09
Should I download that boot scrip link you have?

---

### Post by presence1960 on 2009-12-09
> **evworld said:**
> It didn't download it to firefox.    Tools > downloads there is nothing in the box.

The directory for firefox to download in   "Downloads"  It is not in there.   I just copied your script and pasted into the terminal.  I post what showed when I hit enter.   It appears to me that the command didn't run..??

you need to click on the link in my signature line Boot Info Script and download it. Then make sure that file is on desktop. That is the "script". Once file is on desktop then run that "command" ```
sudo bash ~/Desktop/boot_info_script*.sh
``` in terminal.

The command will execute the script.

---

### Post by evworld on 2009-12-09
Sorry for being stupid   :D

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37cd37cc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35713571

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   468,728,504   468,728,442  83 Linux
/dev/sdb2         468,728,505   488,392,064    19,663,560   5 Extended
/dev/sdb5         468,728,568   488,392,064    19,663,497  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D69C17C39C179CD5" LABEL="Vista64" TYPE="ntfs" 
/dev/sdb1: UUID="c76d3cb0-5081-4a1c-b348-0566421f6cb1" TYPE="ext4" 
/dev/sdb5: UUID="50c6942a-048d-4c5b-8231-0934b90a3d78" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/evworld/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=evworld)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set c76d3cb0-5081-4a1c-b348-0566421f6cb1
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c76d3cb0-5081-4a1c-b348-0566421f6cb1
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c76d3cb0-5081-4a1c-b348-0566421f6cb1
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c76d3cb0-5081-4a1c-b348-0566421f6cb1
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c76d3cb0-5081-4a1c-b348-0566421f6cb1
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d69c17c39c179cd5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c76d3cb0-5081-4a1c-b348-0566421f6cb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=50c6942a-048d-4c5b-8231-0934b90a3d78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

---

### Post by presence1960 on 2009-12-09
should be a fairly simple fix. You have GRUB installed on MBR of both hard disks. You want to keep GRUB on the Ubuntu disk (sdb). So you want to put Vista's bootloader on MBR of windows disk (sda). You will need your Vista or Windows 7 install DVD. You want to boot off that DVD, but first go in BIOS and set the sda disk with windows on it as first in the hard disk boot order. Save changes to CMOS and continue booting off the Windows DVD. You want to follow the instructions for Vista/7 on this [link]("http://ubuntuforums.org/showthread.php?t=1014708").

Reboot when complete and you should boot into windows. Then change disk order in BIOS and make sure Ubuntu boots too.

---

### Post by evworld on 2009-12-09
presence1960

Thanks for your help......    If you see anything that might help me thanks,   I will read in the morning.   I need to sleep.  If I screw my comp up tonight I never get to work in the am.  I will check thread in am.

Thanks.

Ev

---

### Post by evworld on 2009-12-09
I not sure of the bios changes.   Can I just unplug the linux hd and put to my vista cd with only the vista hd plugged in....


Ev

---

### Post by presence1960 on 2009-12-09
> **evworld said:**
> presence1960

Thanks for your help......    If you see anything that might help me thanks,   I will read in the morning.   I need to sleep.  If I screw my comp up tonight I never get to work in the am.  I will check thread in am.

Thanks.

Ev

I need to sleep also. Should be an easy fix, I posted the directions in post #14.

If you don't have your Vista/win 7 install DVD you can download an iso and burn to CD a way to access recovery console only. Get it [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

### Post by presence1960 on 2009-12-09
> **evworld said:**
> I not sure of the bios changes.   Can I just unplug the linux hd and put to my vista cd with only the vista hd plugged in....


Ev

That should work. Just be aware that to boot either OS you wanted to control booting thru BIOS- at least I understood that as the reason we are doing this. Once you plug both disks in you will then be able to choose in BIOS which disk to boot.

---

### Post by evworld on 2009-12-09
I am afraid of screwing my system up so I leaning towards leaving the way it boots.  Is there a way I can have vista be the default  or first boot.  
 
Right now when grub loads I see two ubuntu kernels then vista on the bottom.  If I do nothing ubuntu will load on a restart.   
 
Is there a way I can have Vista start and need to choose linux when I boot my computer

---

### Post by darkod on 2009-12-09
> **evworld said:**
> I am afraid of screwing my system up so I leaning towards leaving the way it boots.  Is there a way I can have vista be the default  or first boot.  
 
Right now when grub loads I see two ubuntu kernels then vista on the bottom.  If I do nothing ubuntu will load on a restart.   
 
Is there a way I can have Vista start and need to choose linux when I boot my computer

The easiest way is to open in terminal:
sudo gedit /etc/default/grub

and change the GRUB_DEFAULT value. If vista is third in your menu, you want value 2 (always one less than the position in the menu). Save and close the file. Run
sudo update-grub

and that should be it. Note, if new kernels are added during update you will need to adjust this value again but this is the easiest way.

---

### Post by presence1960 on 2009-12-09
> **darkod said:**
> The easiest way is to open in terminal:
sudo gedit /etc/default/grub

and change the GRUB_DEFAULT value. If vista is third in your menu, you want value 2 (always one less than the position in the menu). Save and close the file. Run
sudo update-grub

and that should be it. Note, if new kernels are added during update you will need to adjust this value again but this is the easiest way.

That will work, but if you want a GUI solution install startupmanager from synaptic or by running in terminal ```
sudo apt-get install startupmanager
```

personally I prefer the method darko described. But I had installed startup manager and took some screenshots for those who aren't comfortable with the command line.

Below is a screenshot of startup manager on the tab that controls the default OS to boot.

---

