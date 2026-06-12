---
title: "Installing 10.04"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Kamaladi on 2010-06-07
Dear all,

This my first ever post. I recently decided to install Ubuntu 10.04 as a dual boot along with my existing XP Pro OS. I have a old Dell XPS laptop with 2 GB RAM, 2.1 GHz CPU, and 60 GB HD. My intentions were to have 15 GB allocated for Ubuntu and rest for the Windows.

After reading the instructions, which seemed like fairly easy,I created 10.04 Live CD. I booted through the CD, but I can only get the initial screen and then the computer will shut down. Thinking that I might have burnt the Cd wrong way, I tired with 3 different CD burn with lowest possible speed, but no success.

I then used the flash drive instead, and downloaded the netbook edition. This lead me to install screen. After clicking on install, nothing happened and computer shut down after couple of minutes.

I then created alternate CD, with that I could go as far as the partition section, where I had to shrink the hard drive to allocate space for Ubuntu. After the partition, the computer shutdown in same way like in above situation.

I am surprised why it is being this hard. I reinstalled XP all over again. created a new partition for Ubuntu before hand and tried every steps like in above. But the results were similar.

Unless I can get an answer that helps the installation, I plan to install 9.10 to see if that will work.

I would greatly appreciate if I can get any direction from this forum. 
PS: This is the first time ever I am playing with Linux. I just have basic computer skills.

Thanks,

K.

---

### Post by dandnsmith on 2010-06-07
Sounds to me as if there is a hardware problem.
Causing the system to shut down is fairly extreme.
Was there any problem in running XP?
I suggest that testing your RAM might be the place to start - a failure can have odd effects.
Installing 9.10 might also throw light - especially if it installs successfully.

---

### Post by Kamaladi on 2010-06-07
Thanks for you reply.

XP runs fine, and I also checked memory, there is no issue with it. However, I found a link via an earlier post in the forum that might be of help to me, I will give it a shot tonight.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)


K.

---

### Post by oldfred on 2010-06-07
You did not mention what video card you have. That makes a difference on what settings work or work best.

On my nvidia the monitor shutdown but the USB key kept flashing so I could tell it was still loading.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings

Other settings may be required for other video cards.

---

### Post by Kamaladi on 2010-06-07
Finally got Ubuntu installed but ran into another problem, plz help :(

Used live CD (10.04) to install. Where I was stuck before, all I needed was to press a space bar and the installation went forward...BIG SURPRISE. But after 95% installation, Computer shut down. There were some issues ( no clue what they were) when I re-started Ubuntu. I had use Synaptic Package Manger, and do something in Terminal (based on instruction I found in the forum). After that it seems that Ubuntu is up and running.

BUT, XP doesn't start. It goes to blue screen showing error and asking me to run check disk. I can't seem to go any further than that blue screen to do any check disk.

I have 60 GB hard drive. Where I had existing partition for XP and intentionally left space of abt 15-17 GB for future Ubuntu install. I used the option of "Use the most available free space" while installation of Ubuntu.

I feel great that I got the Ubuntu to install, but I am equally sad that I can't use XP. For novice like me, today was a very overwhelming day with computer terms. PLZ Help me get XP run again.

Thanks.
K

---

### Post by oldfred on 2010-06-07
After windows gets resized it wants to run checkdisk chkdsk. You may have to run it from you windows install/recovery disk.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

Run chkdsk several times, until no more errors are detected.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Kamaladi on 2010-06-08
Thanks for your help so far oldfred. My issues are still there, below is the recap of my problem after installing ubantu 10.04, and the issues.

When loading XP from the option in GRUB, it goes to a blue screen. The blue screen says following:
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.
Technical Information:
***STIO: 0x0000007B (0xBACCB528, 0xC0000034, 0x00000000, 0x00000000)

When I enter the recovery console through the installation CD I get a message, “The path or file specified is not valid”. It does not ask me Admin password or anything. It goes straight to C:\>
When I type CHKDSK C: /F I get message “The parameter is not valid. Try /? For help”
If I just type chkdsk, I get message “The specified drive is not valid, or there is no disk in the drive”
If I type fixboot, I get message “FIXBOOT cannot find the system drive, or the drive specified is not valid”
If I type fixmbr, nothing happens, it goes to next C prompt (C:\>) in next line.

I would love to keep playing, but I need XP for other stuffs. I can’t even reinstall XP from boot menu as it can’t access the drive. When I “enter” to install XP, I get a message “55797 MB Disk 0 at ID 0 on bus 0 on atapi <setup cannot access this disk.> 

I then tried Ubuntu through Live CD and tested some suggestions in the forum like:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)
or
[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)
But these did not help either 

In a worst case scenario, can I use Gpart from Live CD and wipe out everything thing and then try reinstalling the XP. Shall I just delete the Ubuntu partition of 17 GB (plz refer to attached picture) or everything in my drive before reinstalling XP (hopefully it can then allow me to reinstall). I want to be absolutely sure about this, because I don’t want to end up without any OS.

For people with my level of expertise, which is basically no expertise, I felt it will be wise to familiarize first with the system much-much longer (through the Live CD or USB) before jumping into installation.
 
I appreciate any help in this matter from all the Ubuntu Guru's.

Thanks, K.

---

### Post by oldfred on 2010-06-08
Just be careful of older threads as now with grub2 things have changed. Windows repairs should be the same. Do you have the boot flag on the windows partition. when you run this it should show a * or from the disk utility it should show check mark next to bootable on the windows partition.

sudo fdisk -l

You should be able just to reinstall windows to the exisiting NTFS partition. But if it is having problems the installer may also not see it. You do not have to uninstall Ubuntu but will have to reinstall grub2 from the liveCD. Just be sure to follow directions for correct version of grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

If something is missing from windows this will output the entire boot of your system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by Kamaladi on 2010-06-09
Hi oldfred,

I am so grateful for your help so far.

I ran the Boot info script, and following is the result. 

Also, I have a XP SP2 CD, I recently had upgraded to SP3, can that be a reason why i can't work fixmbr (plz refer to my previous post) through recovery console? If it's too much trouble and technical, I would just like to format the drives through Gpart in Live CD, and hopefully then able to install XP.
Thanks.
K

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,971,754    83,971,692   7 HPFS/NTFS
/dev/sda2          83,972,094   117,209,087    33,236,994   5 Extended
/dev/sda5          83,972,096   115,726,335    31,754,240  83 Linux
/dev/sda6         115,728,384   117,209,087     1,480,704  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7CB82098B8205346                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee   ext4                                     
/dev/sda6        d97bf0b8-4655-4368-b0b8-a2cca5e84c56   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
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
search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
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
    search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7cb82098b8205346
    drivemap -s (hd0) ${root}
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
UUID=2028c3e0-5d3e-41ef-ac83-f2e4e847a7ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d97bf0b8-4655-4368-b0b8-a2cca5e84c56 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  51.7GB: boot/grub/core.img
  50.0GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.32-21-generic
  51.7GB: boot/vmlinuz-2.6.32-21-generic
  51.8GB: initrd.img
  51.7GB: vmlinuz
```

---

### Post by oldfred on 2010-06-09
I do not see anything obviously wrong in the boot script listing. Everything looks like it should boot.

You can install a windows style boot loader from Ubuntu. But if windows does not boot it will not be any better.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

It may give error messages about the rest of the lilo boot loader missing but that is ok, we just want the bootloader part that goes into the MBR as it works the same as windows.

You can download a Vista repair disk. It will not repair your XP but you can use it to run chkdsk.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Use Vista CD to repair XP  - meierfra. Post 15
[SOLVED] New Dual Boot setup causes XP to BSOD 
[http://ubuntuforums.org/showthread.php?t=1392524&page=2](http://ubuntuforums.org/showthread.php?t=1392524&page=2)

Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Kamaladi on 2010-06-09
The lilo option didn't help.

I created the Vista CD.I followed all the instruction there. When I used **diskpart** followed by **list volume** command as suggested. It does not show the C dive. Only thing shown there is the vista recovery CD.

It seems that system is not finding C :(

Shall I delete everything and format using Live Cd and then re install XP. Then be extra careful next time when installing Ubuntu. I apologize if I sound impatient, but I had to do some stuff in windows :( 

Thanks,

K.

---

### Post by oldfred on 2010-06-09
There are a few more things that may work but they all take extra time and I do not know details as I have not run them. testdisk has some things. If you have data you also may want to recover that, if you do not have good backups.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

But if you need windows now you may want to just reinstall. You may find the installer does not see the NTFS partition either as it is corrupted. I would think reformating with gparted may reset it, but am not sure. You should not have to remove the Ubuntu install.

---

### Post by Kamaladi on 2010-06-10
Hi Oldfred,

Once again, I would like to express my gratitude for sticking around to help me solve my problem :)

I have no issues with loosing any data. I had just formatted my computer and reinstalled XP SP2, then updated to SP3. Then I immediately started on installation of Ubuntu. So, I don't have any data in there to lose :D

My biggest fear is, even if I clean current windows installation through Live CD, or even completely remove/wipe out absolutely everything from the hard disc, the XP installation CD still might not see the the hard drive for installation.

I have borrowed a computer from my buddy to finish off my pending work, so I can relax a bit :)

The whole process, starting from reinstalling XP, then trying to figure out why Ubuntu is not installing - and my computer is shutting down in the middle (which BTW I found out was because of the heating of the computer, Ubuntu likes it best when I start fresh in a cooler computer), finally installing Ubuntu, then XP not starting, then trying to work around it, etc, was mentally draining.

I will take a break this week, watch couple of World Cup Soccer matches and try refreshed next week :) I will post the outcome then.

Again, thanks a lot.

K.

---

### Post by Kamaladi on 2010-06-15
Used Live CD to wipe out the whole disk, took no chances. The installation of XP went smooth :D

I have created Ubuntu in my USB Flash drive, I will be using that rather than installing in the computer. After getting more familiar with Ubuntu, through USB, hopefully one day I can completely replace XP :P

Thanks,

K.

---

### Post by Madmonkykungfu on 2010-06-15
I had a similar problem when i installed Ubuntu on a second partition. It refused to install as NTFS and afterwords actually changed the file system on both partions preventing Vista from booting. Luckily i had a Acronis CD and was able to reformat back to NTFS and reinstall Vista. 
 
Im going to re-install Ubuntu on the second partion but im afraid of history repeating itself. Does anybody have any ideas what went wrong?

---

### Post by oldfred on 2010-06-15
Madmonkykungfu, Welcome to the forum. 

It would be better for you to start a new thread as your question is not directly related to the OP's issues. If you want to install inside a NTFS partition for better testing than just running the liveCD that is a wubi install. It still uses the windows boot loader (shows grub menu but does not install grub) and is inside a root.disk file inside the windows partition.

A full install need two partitions / (root) & swap. Both can be logical, windows needs primary, so you can use one of the 4 primary partitions and put as many logical partitions for linus or NTFS data (only) in the extneded partition.

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

Vista or 7 use the windows tools in MMC to resize the c: partition.

---

