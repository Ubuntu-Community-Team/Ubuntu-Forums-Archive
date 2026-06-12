---
title: "need some help rebuilding GRUB"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by ubscott on 2010-11-21
hi,
 
through a series of mistakes i have managed to take a working system and make it unable to boot. my two objectives right now are to back up my data, and to make my system bootable. 
 
here's how i got here. i used the Upgrade Manager to upgrade to 10.04 thinking it would solve a problem i was having with my previous installation. when that had completed i found I was unable to boot into 10.04. The system would hang after echoing the message "checking battery state."
 
I attempted to rebuild my grub file, thinking this would solve the 'battery state' problem. this was a mistake. I ended up deleting it, and now there's no menu.lst file in its place.
 
currently when i boot up normally (i.e., with no Live CD) I automatically go into the rescue mode. so far i haven't managed to enter a command that rescue mode recognizes.
 
alternatively, i can boot from the installation CD for Ubuntu 10.04. per this page:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
 
I take these steps:
1. boot from the installation CD.
2. go into terminal
3. type these commands:
 
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
 
 
(the link explains what these commands do.)
 
I receive this error:
 
* * *
warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are unreliable and thier use is discouraged.
Error: if you really want blocklists use --force.
 
* * *
 
so, before i do something that makes my predicament worse, does anyone have some advice about how to rebuild the GRUB? should i use "--force"? Or, is it better to try to rebulid the GRUB from the original installation's rescue mode?
 
also, i must say Ubuntu 10.04 so far is terrifying to this newbie.
 
thanks,

---

### Post by Old_Grey_Wolf on 2010-11-21
10.04 doesn't use Grub or menu.list. It uses Grub2. Look here to see if it helps you [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2).

Edit: OK, I see that you have found another link to the same type of info.

---

### Post by drs305 on 2010-11-21
The command you quote to install Grub2 is correct, assuming you substituted values for X and Y. Users often type it incorrectly. Note that in the first command you list the partition (e.g. sda5, sdb1, etc). In the second command, you only list the drive (sda, sdb, etc). If you mistakenly add the partition to the second command (sda5, sdb1) you will get the error message you mention.

---

### Post by ubscott on 2010-11-21
thanks, drs305. You gave me great advice.  i tried the second command and followed your suggestion about specifying the drive, not the partition.  the grub file has been installed.  when i boot up now i have the options in the grub file to choose from.
 
however, i choose the 'generic' option at the top of the grub menu and i don't get much farther.  the screen goes blank.  "Ubuntu 10.04" appears in small white letters in the center.  below this are four dots.  these dots change from white to red sequentially.  i have left this running for several minutes and Ubuntu never moves beyond this page.
 
does anyone have any suggestions?  thanks.

---

### Post by kansasnoob on 2010-11-21
In order to save everyone time and frustration it would be best if you'd use the Live CD and post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by drs305 on 2010-11-21
> **ubscott said:**
> i have left this running for several minutes and Ubuntu never moves beyond this page.
 
does anyone have any suggestions?  thanks.

If it's a video-related problem, try booting the recovery mode. If the recovery mode isn't displayed on the grub menu, highlight the first entry, press "e" to edit the entry. On the "linux" line, cursor to the end, remove "quiet splash" and add "single". Then CTRL-x to boot. That should boot the recovery mode. From the recovery menu, try selecting the option that deals with video (failsafe x or something like that).

If you don't see the G2 menu at all, hold down the SHIFT key during boot to see if it will appear.

If you are able to boot to the Desktop, you will probably need to install some drivers via System, Administration, Hardware Drivers/Additional Drivers.

---

### Post by BrandonC19 on 2010-11-21
I had the same problem with 10.04 on my laptop, turns out it was a hardware issue, try the 10.10 live cd and see if it works.

---

### Post by ubscott on 2010-11-21
hi Kansasnoob, 

thanks for the suggestion.  here's my results.txt:

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   153,276,164   153,276,102  83 Linux
/dev/sda2         153,276,165   156,248,189     2,972,025   5 Extended
/dev/sda5         153,276,228   156,248,189     2,971,962  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        8cf45f08-6d9e-47d3-969d-ae35a97164b0   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b8f3b82b-372b-4134-9a8f-1d649dd7d3ba   swap                                     
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
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro single 
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8cf45f08-6d9e-47d3-969d-ae35a97164b0
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
UUID=8cf45f08-6d9e-47d3-969d-ae35a97164b0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b8f3b82b-372b-4134-9a8f-1d649dd7d3ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   5.1GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
   2.1GB: boot/initrd.img-2.6.31-22-generic
   2.2GB: boot/initrd.img-2.6.32-25-generic
    .2GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: boot/vmlinuz-2.6.31-22-generic
   1.4GB: boot/vmlinuz-2.6.32-25-generic
   2.2GB: initrd.img
   2.1GB: initrd.img.old
   1.4GB: vmlinuz
    .2GB: vmlinuz.old



---

### Post by ubscott on 2010-11-21
hi Drs305,
 
> From the recovery menu, try selecting the option that deals with video (failsafe x or something like that).
 
i choose the first recovery mode from the GRUB, and eventually i get to the Recovery Menu. the choices are:
 
resume (resume normal boot)
clean (try to make free space)
dpkg (repair broken package)
failsafeX (run in Failsafe graphic mode)
grub (update the grub bootloader)
netroot (drop to root shell prompt)
 
"resume" is highlighted. however, i can't select 'failsafeX'. just as i hit the arrow down key for the first time the screen goes blank and the familiar "Ubuntu 10.04" shows up with the four small dots below it.
 
i don't know how to select an option from this menu. i thought arrow-down was the way. help is much appreciated. Thanks.

---

### Post by drs305 on 2010-11-22
Normally you should be able to just cursor down to the recovery selection you want. 

In the same way you added single to the end of the line, you could try to add various kernel options. The first one I'd probably try is **nomodeset**

If that doesn't work, do a Google search for other kernel options for your particular computer. One of those regarding acpi, lapic, ahci, etc added to the end of the 'linux' line may work. Try to find a reference for one of those that is a known issue for your computer first.

---

### Post by ubscott on 2010-11-22
drs305, appreciate the replies. i changed my keyboard to a USB, and after a few reboots, i could select the failsafe mode from the recovery menu. it was wierd how the problem went away.
 
i also edited my grub file, putting 'single' in there.
 
however, when i boot in failsafe mode i get lines of output. in the output is reference to an error log. i get the lines of output only the first time i run failsafe. subsequent tries causes control to immediately return to the recovery menu.
 
the error log has this message:
"Add**Screen/ScreenInit** **failed** for driver 0"
 
according to this page, the culprit is my old monitor and old graphics card:
**[http://tinyurl.com/283vash](http://tinyurl.com/283vash)**
 
i switch to my good monitor; i.e., a ViewSonic that is about 6 years old. i chose normal boot from the recovery menu. the boot hangs with the command "checking battery state."
 
from this page:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)
 
i have created a new XOrg.config file. however, when i now choose failsafe from the recovery menu, the screen goes absolutely dark. there are no error messages to brigthen the mood.
 
it seems i have several ways to go. i could try BrandonCD's suggestion of getting a 10.10 live CD. however, i don't know what i would do with it that i'm not already doing with my 10.04 live CD.
 
i could try to edit the XOrg.config file. (this doesn't sound like fun.) i can try to put kernel commands in my grub, ala drs305's suggestion. i could also try a newer graphics card.
 
does anyone have any suggestions? thanks in advance.

---

### Post by ubscott on 2010-11-23
> If it's a video-related problem, try booting the recovery mode. If the recovery mode isn't displayed on the grub menu, highlight the first entry, press "e" to edit the entry. On the "linux" line, cursor to the end, remove "quiet splash" and add "single". Then CTRL-x to boot. That should boot the recovery mode...
 
> In the same way you added single to the end of the line, you could try to add various kernel options. The first one I'd probably try is nomodeset
 
hi,
 
i'm trying to modify the grub2 file to add 'nomodeset'. however, i can't seem to do this.
 
from the grub menu items i choose the first "recovery" item. Then when i press "e" to edit the file, i enter an editing interface that doesn't seem to have a way to save. I try CTRL-x to boot, see lots of verbiage and finally reach the "battery state" line that hangs the boot. I usually reboot again, and when i press "e" to edit the file, it doesn't have the 'nomodeset' instruction.
 
i've searched for the answer to this question for more than an hour. however, how does one save changes when you've pressed 'e' from the grub2 menu? CTRL-x performs the boot; but it doesn't seem to save.
 
the other way i've tried to edit the file is by:
cd /boot/grub
gksudo edit menu.lst
 
i get: 
Gtk-WARNING **: cannot open display:
 
nothing follows the colon at the end of that line.
 
the other way i've tried to edit the file is by:
sudo nano menu.lst
 
the file is empty. then i look for the file and it isn't there.
 
a visit to this page:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
tells us:
No ''/boot/grub/menu.lst''. It has been replaced by ''/boot/grub/grub.cfg''.
The main menu file, ''/boot/grub/grub.cfg'' is not meant to be edited, even by 'root'.
 
 
...so, does anyone have any suggestions about how i can modify the menu.lst file so that 'nomodeset' is included?
 
Also, should 'single' be retained; i.e., '...single nomodeset...' ?
 
thanks,

---

### Post by oldfred on 2010-11-24
You do not edit grub.cfg. If you know what setting you need to make system work you can change /etc/default/grub. drs305's signature line has links to all the important grub2 explanations including editing of the grub parameter file.

gksudo gedit /etc/default/grub


What video card do you have? That determines the settings to add to grub and normally you do not have to edit the grub parameter file but add a driver. Some have found the generic setting works for many older systems.

On first boot after install, press e on getting the GRUB bootloader. Use shift from BIOS if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by drs305 on 2010-11-24
> **ubscott said:**
> hi,
 
i'm trying to modify the grub2 file to add 'nomodeset'. however, i can't seem to do this.
 
from the grub menu items i choose the first "recovery" item. Then when i press "e" to edit the file, i enter an editing interface that doesn't seem to have a way to save.

Just for clarification. The changes you make by editing the menuentry during boot are non-persistent. This means that they last only for that one boot - you won't see them the next time you boot unless you make the changes permanent by other means. That can be a good and bad thing - good in that a change that doesn't work isn't remembered. Bad in that if you are trying lots of modifications you have to remember which one worked so you can then make it permanent.  ;-)

At the end of his post, *oldfred* gave you several options to try at the end of the 'linux' line if the problem is video-related. If one of them works, you would edit /etc/default/grub (gksu gedit /etc/default/grub), add the phrase to the end of the "linux" line after 'quiet splash' and then update the grub menu (sudo update-grub).

---

### Post by ubscott on 2010-11-24
thanks for the info Oldfred and drs305. regarding the non-persistent nature of editing via 'e', i wish there was some message at the bottom indicating it. Something like "changes are not saved permanently." that would save newbies some time trying to figure out the changes aren't retained.
 
i ran these two commands:
lspci 
lshw -short
 
they return:
VGA Compatible Controller Intel Corp 82865G Integrated Graphics Controller (rev 02)
 
however, when I edit the grub file as Oldfred suggests, i still can't get it to get past the 'checking battery state' line. Here's the page that I followed:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
 
where the grub file says ”quiet splash" I made it:
a.) "quiet splash i915.modeset=1&#8243;
b.) ”quiet splash i915.modeset=0&#8243;
 
The first time I set modeset=1. the next time I set it to zero. I make a change and reboot. eventually i get to the "battery state" line and boot hangs. i know my changes were saved because the grub file is just as I left it upon the subsequent boot.
 
i haven't been able to get to where i'm logging into Ubuntu and seeing a GUI interface since I upgraded to 10.04. all of my efforts to fix this video problem need to be shell commands. 
 
so, i'm wondering if I am better off trying to download an old Intel driver for my card. Or, should i try to install a new graphics card and try to get a driver for it via a shell command. Are there any alternatives to "i915.modeset= X" that I can try?
 
thanks for the help.

---

### Post by oldfred on 2010-11-24
Did you try the generic also.

[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

Not sure if any of this may apply:
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by ubscott on 2010-11-26
thanks for the reply, oldfred.
 
> Did you try the generic also
 
i tried most of the stuff on the page in the startup file (i.e., where you hit the 'e' when looking at the grub file options.)
 
I also tried to put the 'blacklist=vga16fb' line by editing the grub file. however, nothing came of it. 
 
btw, those are nvidia commands. my graphics card is Intel. i tried substituting 'Intel' for 'nouveau' at one point; e.g., intel.modeset=0. However, this did nothing.
 
> Not sure if any of this may apply:
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions) 
 
i can boot into the Live CD fine. i see the Linux menu, can go into System/Administration/Additional Drivers. it tells me that i have no proprietary drivers in use on the system.
 
i don't understand why the Live CD boots, since it is using the same video card as the Ubuntu 10.0.0.4. there must be an instruction it is following that i need to have in my local installation. 
 
i looked at the grub file in the Live CD's file system area. i saw no special instructions. i think they are just about the same as what my local installation's grub file has. for both, this command exists:
#GRUB_GFXMODE=640x480
 
it sure would be nice if the Live CD could just fix the local installation. or, if the local installation would just do what the Live CD does.
 
all help appreciated. thanks.

---

### Post by ubscott on 2010-11-27
i'm glad to say that i can now boot 10.04!  these threads saved me:
[http://ubuntuforums.org/showthread.php?t=1361205](http://ubuntuforums.org/showthread.php?t=1361205)
[http://ubuntuforums.org/showthread.php?t=1334740](http://ubuntuforums.org/showthread.php?t=1334740)
[http://ubuntuforums.org/showthread.php?t=114578](http://ubuntuforums.org/showthread.php?t=114578)
 
i tried this:
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
 
it gave me an error.  then i tried this:
sudo dpkg-reconfigure gdm
 
this reconfigured my gdm.  once i had done this i could boot again.
 
what a relief!  thanks for the help.

---

