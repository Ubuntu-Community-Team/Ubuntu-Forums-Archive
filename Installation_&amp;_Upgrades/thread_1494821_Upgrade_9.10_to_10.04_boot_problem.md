---
title: "Upgrade 9.10 to 10.04 boot problem"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by dkdias on 2010-05-27
I upgraded 9.10 to 10.04 and now it won't boot.  The way 9.10  used to boot was after turning on the computer it would go through the bios screen and then a screen would come up and list both operating systems, Windows Xp and Ubuntu.  XP would be highlighted and would normally boot if I did not change the highlighted area.  If I changed the highlighted area to Ubuntu it would boot into Ubuntu 9.10.  Now after doing the upgrade, it gets to the same screen with the two operating systems listed, but when I change the highlighted to Ubuntu an error message is briefly displayed and then it goes back to the screen that lists both operating systems.  I think the error message says something like couldn't find Ubuntu, or something similiar to that. Windows XP runs fine when I highlight Windows Xp in that first screen, but I want to be able to run Ubuntu. I have Ubuntu on a secondary drive, but shouldn't it have rewritten the upgraded files on that same drive that had 9.10 on it? Please help!

---

### Post by darkod on 2010-05-27
Run the boot info script as explained here and post the content of your results file.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by dkdias on 2010-05-27
> **darkod said:**
> Run the boot info script as explained here and post the content of your results file.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

I will check and see if I can boot the 10.04 cd?  Up to this point I've been unable to boot from cd, except for the 8.04 Ubuntu cd.  All the newer versions won't boot, that is why I did the upgrade rather than a new install. Thank you for your suggestion.  I will post my results after trying this!!  Thanks again!

---

### Post by kansasnoob on 2010-05-27
You can run that info script with the 8.04 CD. I frequently use either an old Knoppix or DSL disc just because they boot quickly and seem to work on almost any hardware.

---

### Post by dkdias on 2010-05-27
> **kansasnoob said:**
> You can run that info script with the 8.04 CD. I frequently use either an old Knoppix or DSL disc just because they boot quickly and seem to work on almost any hardware.

Cool.  Thanks again for the info!!

---

### Post by dkdias on 2010-05-28
> **darkod said:**
> Run the boot info script as explained here and post the content of your results file.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

I ran in terminal and this is what happened?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ root
sudo bash ~/Desktop/boot_info_script*.shThe program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
You will have to enable the component called 'universe'
root: command not found
ubuntu@ubuntu:~$ sudo apt-get install root-system-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package root-system-bin
ubuntu@ubuntu:~$

---

### Post by darkod on 2010-05-28
> **dkdias said:**
> 
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory


Do you have the script downloaded and placed on the desktop? You can't run it if it's not there. You actually have to download the script to run, there is a link in my signature for example. You don't just run the command, that script is not inside ubuntu by default.

---

### Post by kansasnoob on 2010-05-28
> **dkdias said:**
> I ran in terminal and this is what happened?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ root
sudo bash ~/Desktop/boot_info_script*.shThe program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
You will have to enable the component called 'universe'
root: command not found
ubuntu@ubuntu:~$ sudo apt-get install root-system-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package root-system-bin
ubuntu@ubuntu:~$

Is the info script displayed on the desktop? Where did it download to?

What I do is physically find it after downloading it, like mine goes to Downloads, so I actually go to it, double click to open, open terminal, and cd Downloads:

[ATTACH]158540[/ATTACH]

Then the terminal will even tell you where the RESULTS.txt is saved.

---

### Post by dkdias on 2010-05-28
> **darkod said:**
> Do you have the script downloaded and placed on the desktop? You can't run it if it's not there. You actually have to download the script to run, there is a link in my signature for example. You don't just run the command, that script is not inside ubuntu by default.

I downloaded the script, how do I put it in the desktop to run it?

---

### Post by dkdias on 2010-05-28
> **kansasnoob said:**
> Is the info script displayed on the desktop? Where did it download to?

What I do is physically find it after downloading it, like mine goes to Downloads, so I actually go to it, double click to open, open terminal, and cd Downloads:

[ATTACH]158540[/ATTACH]

Then the terminal will even tell you where the RESULTS.txt is saved.

Here is the result at the end of the script. How do I send you this file? Or I could cut and paste all the info? 

echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit

---

### Post by kansasnoob on 2010-05-28
> **dkdias said:**
> Here is the result at the end of the script. How do I send you this file? Or I could cut and paste all the info? 

echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit

Somehow that looks odd, like mine shows:

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ sudo bash boot_info_script055.sh
[sudo] password for lance: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Finished. The results are in the file RESULTS1.txt located in /mnt/sda7

```

My /mnt/sda7 is a symlinked Downloads partition.

I still don't think you're running that right:

> echo Finished. The results are in the file $(basename "$LogFile") located in "$Dir";
exit 

Are you copy-n-pasting commands?

---

### Post by kansasnoob on 2010-05-28
You can use the "ls" command to find things like:

```
lance@lance-desktop:~$ [COLOR="black"]**ls Desktop**[/COLOR]
Screenshot.png
lance@lance-desktop:~$ **ls Downloads**
**[COLOR="Red"]boot_info_script055.sh[/COLOR]**          Peppermint-One.iso
gparted-live-0.4.6-1.iso        pmagic-4.9.iso.zip
KNOPPIX_V6.2.1CD-2010-01-31-EN  RESULTS1.txt
LinuxMint-7.iso                 RESULTS.txt
linuxmint-9-gnome-cd-i386.iso   ubuntu-10.04-desktop-i386.iso
linuxmint-9-gnome-dvd-i386.iso  ubuntu-8.04.4-desktop-i386.iso
lost+found                      ubuntu-9.04-desktop-i386.iso
lubuntu-10.04.iso               ubuntu-9.10-desktop-i386.iso
pclinuxos-gnome-2010.iso

```

---

### Post by dkdias on 2010-05-28
I compressed the file to make it so the forum would allow the size of the file?
Ive got to get ready to go to work now.  I will mess with this later.  Thank you for all your help......if i did not do it right still, I will mess with it later tonight. it is 6:50 am here......thanks again!!

---

### Post by kansasnoob on 2010-05-28
That's not the results, it's just the content of the script itself. Where did you find it?

---

### Post by kansasnoob on 2010-05-28
Just being a cheerleader here :)

Never give up, I chose the moniker "kanasnoob" for a good reason 2 1/2 years ago. I couldn't do anything right :(

Since you're working in the Live environment if you've rebooted you'll need to download the Boot Info Script again, but if you're using Firefox first go to Edit > Preferences > General and be sure it's set to download to Desktop. So after doing that just download:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then when the download is complete just copy-n-paste (double click to highlight, right click to copy, then right click to paste in terminal):

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Then go to the Desktop and you should see the RESULTS.txt. Just right click on it and choose compress, then use the attachment "paper clip" at the top of this forum reply box to attach the RESULTS.txt.tar.gz :)

---

### Post by dkdias on 2010-05-28
> **kansasnoob said:**
> Just being a cheerleader here :)

Never give up, I chose the moniker "kanasnoob" for a good reason 2 1/2 years ago. I couldn't do anything right :(

Since you're working in the Live environment if you've rebooted you'll need to download the Boot Info Script again, but if you're using Firefox first go to Edit > Preferences > General and be sure it's set to download to Desktop. So after doing that just download:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then when the download is complete just copy-n-paste (double click to highlight, right click to copy, then right click to paste in terminal):

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Then go to the Desktop and you should see the RESULTS.txt. Just right click on it and choose compress, then use the attachment "paper clip" at the top of this forum reply box to attach the RESULTS.txt.tar.gz :)

So basically I am downloading the script to my desktop and then cutting and pasting it inside the terminal then I am entering the "sudo bash ~/Desktop/boot_info_script*.sh" into the terminal? Is this correct?

---

### Post by darkod on 2010-05-28
No, not cutting and pasting the script. Leave the script on the desktop, open the terminal and just type:

sudo bash ~/Desktop/boot_info_script*.sh

That should run it and create the results.txt also on the desktop where the script is.

Then open the results.txt file, and copy-paste the content here.

---

### Post by dkdias on 2010-05-28
> **darkod said:**
> No, not cutting and pasting the script. Leave the script on the desktop, open the terminal and just type:

sudo bash ~/Desktop/boot_info_script*.sh

That should run it and create the results.txt also on the desktop where the script is.

Then open the results.txt file, and copy-paste the content here.

Okay, so after running the script and it is still open in its own box, then open a terminal box and run the sudo bash command given... then locate and open the results.txt file and copy-paste it here........ I'm slow but at some point I can learn, maybe.. ](*,)

---

### Post by wilee-nilee on 2010-05-28
Just for a little more help I hope paste into the reply using code tags, here is how.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by kansasnoob on 2010-05-28
> **dkdias said:**
> Okay, so after running the script and it is still open in its own box, then open a terminal box and run the sudo bash command given... then locate and open the results.txt file and copy-paste it here........ I'm slow but at some point I can learn, maybe.. ](*,)

Aaah, I think I may have confused you with the screenshot back in post #8. You don't have to "open" the script at all.

I just do it because I don't have the command to run it memorized so I open the script and there's the command:

> #to use this script:
#
#     sudo bash boot_info_script055.sh

Of course that doesn't tell you to select the location of the script, that's why I just "cd Desktop" or wherever it's at, but the "~/Desktop/" part of this:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

does exactly the same thing as "cd Desktop" in terminal :)

With Linux there are generally several ways of getting to the same outcome.

---

### Post by dkdias on 2010-05-29
> **kansasnoob said:**
> Aaah, I think I may have confused you with the screenshot back in post #8. You don't have to "open" the script at all.

I just do it because I don't have the command to run it memorized so I open the script and there's the command:



Of course that doesn't tell you to select the location of the script, that's why I just "cd Desktop" or wherever it's at, but the "~/Desktop/" part of this:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

does exactly the same thing as "cd Desktop" in terminal :)

With Linux there are generally several ways of getting to the same outcome.

I think I did it this time?  I've attached the results.txt file.  Thanks again.  I'm a shortimer with Ubuntu!!
In recap of my computer issues.. I did try the wubi in the past but it didn't work.  So I partitioned my 200g drive on this computer and installed 9.10 Ubuntu on it. I then upgraded 9.10 to 10.04 and upon reboot 10.04 didn't boot. I would like to dual boot windows xp and Ubuntu 10.04. Thank you everyone for your help!!

---

### Post by kansasnoob on 2010-05-29
You did great :)

I need to run some errands and I'll give it a thorough look when I get back. I know some folks prefer having it in CODE tags so here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x784e7b6b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   216,693,244   216,693,182   7 HPFS/NTFS
/dev/sda2         216,696,830   398,295,039   181,598,210   5 Extended
/dev/sda5         216,696,832   395,319,295   178,622,464  83 Linux
/dev/sda6         395,321,344   398,295,039     2,973,696  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x093d6fca

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3952438c-f0b0-44f4-85e5-b408ed19d9da   ext4                                     
/dev/sda1        20B01C32B01C1140                       ntfs       200 Gig HD (New)              
/dev/sda5        09babe05-6a49-4e90-a494-f3870dfe4513   ext4                                     
/dev/sda6        3a54d8fe-a8ea-47cf-9946-4913f5e20ffb   swap                                     
/dev/sdb1        027CCAE97CCAD717                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=09babe05-6a49-4e90-a494-f3870dfe4513 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=09babe05-6a49-4e90-a494-f3870dfe4513 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 09babe05-6a49-4e90-a494-f3870dfe4513
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ccc878bbc878a57c
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a0ab6d58-3377-4eda-9a08-f935ba78f7f5
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=a0ab6d58-3377-4eda-9a08-f935ba78f7f5 ro quiet splash
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a0ab6d58-3377-4eda-9a08-f935ba78f7f5
	linux /boot/vmlinuz-2.6.27-7-generic root=UUID=a0ab6d58-3377-4eda-9a08-f935ba78f7f5 ro single
	initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set a0ab6d58-3377-4eda-9a08-f935ba78f7f5
	linux /boot/memtest86+.bin 
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
# / was on /dev/sdb5 during installation
UUID=09babe05-6a49-4e90-a494-f3870dfe4513 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=3a54d8fe-a8ea-47cf-9946-4913f5e20ffb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 149.7GB: boot/grub/core.img
 119.7GB: boot/grub/grub.cfg
 119.9GB: boot/initrd.img-2.6.32-21-generic
 111.3GB: boot/vmlinuz-2.6.32-21-generic
 119.9GB: initrd.img
 111.3GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"
```

Thanks for sticking with it.

---

### Post by oldfred on 2010-05-29
Since you have 2 drives you should leave windows in sdb's MBR and install grub to sda. Then in BIOS make sure you are booting from sda. If you ever have a problem with sda you can then select sdb to boot.

Did you at some point change drive order? Ubuntu thinks it is on hd1 and windows thinks it is on hd0 which is the opposite of sda & sdb.

Install from LiveCD terminal Best to copy & paste to avoid errors :
Find linux partition - fidsk should show sda5 as linux:
```
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

If it does not boot it is because the drives are reversed. You then will have to chroot into your system and kansasnoob is better than I at that. I have copied his instructions for my use several times.

You also still show wubi in your windows. You may want to in windows houseclean that out after everything else is fixed.

---

### Post by darkod on 2010-05-29
> **oldfred said:**
> 

Did you at some point change drive order? Ubuntu thinks it is on hd1 and windows thinks it is on hd0 which is the opposite of sda & sdb.



Not only that, fstab says:
/ was on /dev/sdb5 during install

and now it's reported on /dev/sda5. Can that make confusion? Should anything be done and what?

Also, what's with the OS being reported as Ubuntu Lucid (development release) instead of Ubuntu 10.04 LTS?

---

### Post by kansasnoob on 2010-05-29
> **oldfred said:**
> Since you have 2 drives you should leave windows in sdb's MBR and install grub to sda. Then in BIOS make sure you are booting from sda. If you ever have a problem with sda you can then select sdb to boot.

Did you at some point change drive order? Ubuntu thinks it is on hd1 and windows thinks it is on hd0 which is the opposite of sda & sdb.

Install from LiveCD terminal Best to copy & paste to avoid errors :
Find linux partition - fidsk should show sda5 as linux:
```
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

If it does not boot it is because the drives are reversed. You then will have to chroot into your system and kansasnoob is better than I at that. I have copied his instructions for my use several times.

You also still show wubi in your windows. You may want to in windows houseclean that out after everything else is fixed.

If I recall correctly dkdias has only a Hardy Live CD so won't that foul things up (trying to recover grub 2 with a legacy grub disc)? 

I've been working on something that's reliant only on the installed OS's package management so we avoid that scenario:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

So far 2 out of 3 people I've asked to follow that have trouble though so I need to write it better :(

Knowing how to do something and being able to explain it are worlds apart, but I'd appreciate any feedback from you or darkod :)

---

### Post by kansasnoob on 2010-05-29
> Also, what's with the OS being reported as Ubuntu Lucid (development release) instead of Ubuntu 10.04 LTS?

That shouldn't matter too much, I mean it should update to final OK, other than checking for this:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Security%20Issue%20when%20upgrading%20from%20Lucid%20Alpha%202](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Security%20Issue%20when%20upgrading%20from%20Lucid%20Alpha%202)

> Security Issue when upgrading from Lucid Alpha 2

If you installed Lucid prior to Alpha 3, you may have libmysqlclient16 7.0.9-1 installed. This package was present in the Ubuntu archive by mistake and was retracted, but because it has a later version number than the real libmysqlclient16 package, the real package will not be installed automatically on upgrade. To ensure that you have the official package installed on your Lucid system and will receive security support for it throughout Ubuntu 10.04 LTS, it is important that you run sudo apt-get install libmysqlclient16/lucid and follow the instructions. (522225) 

But we can check the version of that package after we get Lucid booted.

I need to study this real good now.

---

### Post by oldfred on 2010-05-29
Yes if the OP does not have a current liveCD the shortcut install will not work and he will have to do a full chroot to update it. 

I would like to know if it is a removeable drive or why the drive order seems to have changed.

kansasnoob - I think I saw one thread where a user had trouble with your thread. Even though you clearly list drives and partitions at the top and then your command was sdX the user typed sda5 not sda. I think more examples. I understand the X & Y for drive & partition, but it seems almost all users are not familar with the difference. After sdX or and sdXY example it may help to have specific entries for drives like sda or sdb (and say not sda5) and for partitions sda5 or sdb5 as correct style entries. I think your thread is good and I understand it as it is, but we see how new users do not understand MBR systems.

---

### Post by darkod on 2010-05-29
Agree. And just because of that, to make it even more easier to follow for anyone, I would use more splitting into sections. For example, after checking which grub packages are installed, when starting the commands to reinstall grub2, group the commands in a section, with a clearly stated name that it's for grub2. Maybe even saying something along the lines: if the previous results showed you have the grub package installed, skip this section...

People will still make mistakes. :) Most you can do is to try to minimize that.

---

### Post by kansasnoob on 2010-05-29
I'm getting kind of tired (up late with sick animals) so I'm just going to review things. I need to know if you've tried anything since posting that RESULTS.txt too. It could make a difference.

Going clear back to post #3 you can only use an 8.04 CD, eh? That's OK but folks need to know that :)

What I see from the script:

You have a Windows MBR on both drives.

Lucid is on sda5.

Win XP is on sdb1.

The 200GB drive is /dev/sda.

The 40GB drive is /dev/sdb.

I should know if both drives are IDE, particularly if they're on one cable as Master and Slave.

As Darkod said Lucid's fstab says:

> # / was on /dev/sdb5 during installation

So I guess the drive order changed at one time, eh? Regardless the UUID is correct so we won't worry about it for now.

Anyway, if the 200GB drive is set to boot first in BIOS I'd just run the following commands from the Live Hardy desktop. Some commands are horribly long so please copy-n-paste all commands.

Also you'd be doing me a huge favor if you'd copy-n-paste the full terminal output back here whether or not this works. That's the only way I can see what's happening on your end :)

It might also be helpful if you spent just a few minutes to get some understanding how my chroot procedure works:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

So, when you're ready, from your Hardy Live Desktop:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

```
grub-mkconfig -o /boot/grub/grub.cfg
```

```
grub-install /dev/sda
```

Note: if that shows any errors also run:

```
grub-install --recheck /dev/sda
```

Then exit the chroot and unmount like this:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Hopefully that'll get you booting again. If not that's where I'll really need to have seen the full terminal output pasted back here.

---

### Post by kansasnoob on 2010-05-29
@ darkod and oldfred,

I'm too tired to mess with that right now, but I appreciate your thoughts.

When I'm not so tired I need to pick your brains about dealing with separate /boot partitions.

That's just something I've avoided like the plague :)

Maybe you could, at your leisure, post some comments at my "revert to legacy grub" thread:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Time for a nap :)

---

### Post by dkdias on 2010-05-30
> **kansasnoob said:**
> I'm getting kind of tired (up late with sick animals) so I'm just going to review things. I need to know if you've tried anything since posting that RESULTS.txt too. It could make a difference.

Going clear back to post #3 you can only use an 8.04 CD, eh? That's OK but folks need to know that :)

What I see from the script:

You have a Windows MBR on both drives.

Lucid is on sda5.

Win XP is on sdb1.

The 200GB drive is /dev/sda.

The 40GB drive is /dev/sdb.

I should know if both drives are IDE, particularly if they're on one cable as Master and Slave.

As Darkod said Lucid's fstab says:



So I guess the drive order changed at one time, eh? Regardless the UUID is correct so we won't worry about it for now.

Anyway, if the 200GB drive is set to boot first in BIOS I'd just run the following commands from the Live Hardy desktop. Some commands are horribly long so please copy-n-paste all commands.

Also you'd be doing me a huge favor if you'd copy-n-paste the full terminal output back here whether or not this works. That's the only way I can see what's happening on your end :)

It might also be helpful if you spent just a few minutes to get some understanding how my chroot procedure works:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

So, when you're ready, from your Hardy Live Desktop:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
apt-get update
```

```
apt-get install --reinstall grub-pc
```

```
grub-mkconfig -o /boot/grub/grub.cfg
```

```
grub-install /dev/sda
```

Note: if that shows any errors also run:

```
grub-install --recheck /dev/sda
```

Then exit the chroot and unmount like this:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Hopefully that'll get you booting again. If not that's where I'll really need to have seen the full terminal output pasted back here.

40 gig is a sata drive, the 200 gig is a ide drive. I tried wubi before I installed the 200 gig drive, but wubi did not work for some reason.  The 200 gig was a recent install on this computer. Actually it was 9.10 Ubuntu that I upgraded from. For some reason prior to installing the 200 gig drive, 8.04 Ubuntu was the only Ubuntu cd that booted, but after installing the 200 gig drive 9.10 booted so I installed it. I haven't tried anything yet.  I was gone to the coast soon after I posted the results.txt this morning.  Thank you all again for all you assistance with this. I will try one of your solutions tomorrow, my wife wants me to watch a movie with her right now!  Thank you all again!!

---

### Post by dkdias on 2010-06-01
The computer also boots first to the Sata 40 gig drive, will this effect the fix you gave me?  Sorry I have not replied recently, my home internet has been acting very strange, no matter which computer I'm on.  Whether I'm on Ubuntu / Windows Xp or Windows Vista?  Anyway, I was gone for most of the holiday weekend, so I will try your fixes tonight.  Thank you again for all your help!!

---

