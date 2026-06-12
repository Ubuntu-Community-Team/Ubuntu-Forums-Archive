---
title: "No rootfile system"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by goreyduke on 2011-01-10
Trying to re-install Ubuntu 10.10, it says "no root file system is defined. Please correct this from the partitioning menu".

In GParted, I have a 16gb partition ready for it, formatted as ext4. Is this not the filing system? Do I have to format this as NTFS?  

What is a rootfile system?

---

### Post by matt_symes on 2011-01-10
Hi

Select the partition and hit edit on the Ubuntu install partition screen and select / as the mount point.

[http://www.linfo.org/root_filesystem.html](http://www.linfo.org/root_filesystem.html)

Kind regards

---

### Post by Hippytaff on 2011-01-10
there is a drop down menu when edtiting the patition in gparted with options such as /home /swap. The / (forward slash on it's own) is the root partition. Select this for the root partition

---

### Post by cgroza on 2011-01-10
Just edit that ext4 partition you want to install Ubuntu on and there is a field like: "mount point". Just put a "/" in there and you should be fine.

---

### Post by goreyduke on 2011-01-10
Thanks, everyone. That did the trick. I'm now installed and up and running in Ubuntu 10.10!

But there's a new problem in my quest to "dual boot in perfect harmony". Windows 7 has dropped off the bootloader menu.

I can see the partition in GParted but, even though I kept it formatted as NTFS, it is showing up as "unallocated".

Previously, it was showing up as mostly white (i.e. with spare capacity) and yellow where W7 was loaded. Now it is all grey, with no hint that there is an OS in there.

Can I recover W7 undamaged, or is my only option to re-loaded it, losing the programs, files, etc?

---

### Post by Quackers on 2011-01-10
In Ubuntu, open up a terminal and run ```
sudo update-grub
``` then watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and try selecting Windows from the grub menu to see if it boots ok.
If this doesn't happen boot Ubuntu then go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by goreyduke on 2011-01-20
Here's what's happening now. Have reloaded W7 and Ubuntu 10.10 but W7 has dropped off the bootloader.

See:

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2    *        206,848   419,432,447   419,225,600   7 HPFS/NTFS
/dev/sda3         419,432,448   480,872,447    61,440,000  83 Linux
/dev/sda4         480,874,494   976,771,071   495,896,578   f W95 Ext d (LBA)
/dev/sda5         480,874,496   976,771,071   495,896,576   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A070991F7098FCEA                       ntfs       System Reserved               
/dev/sda2        9A1C20591C203325                       ntfs       Hard Disc                     
/dev/sda3        048bdec1-7491-4384-ac10-3ca62d75e3db   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2256EE9656EE6A4D                       ntfs       Stuff                         
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=048bdec1-7491-4384-ac10-3ca62d75e3db ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=048bdec1-7491-4384-ac10-3ca62d75e3db ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=048bdec1-7491-4384-ac10-3ca62d75e3db ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=048bdec1-7491-4384-ac10-3ca62d75e3db ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 048bdec1-7491-4384-ac10-3ca62d75e3db
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 217.0GB: boot/grub/core.img
 232.4GB: boot/grub/grub.cfg
 215.6GB: boot/initrd.img-2.6.35-22-generic
 215.9GB: boot/initrd.img-2.6.35-24-generic
 217.0GB: boot/vmlinuz-2.6.35-22-generic
 217.0GB: boot/vmlinuz-2.6.35-24-generic
 215.9GB: initrd.img
 215.6GB: initrd.img.old
 217.0GB: vmlinuz
 217.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde #

Thanks

---

### Post by Quackers on 2011-01-20
Have you, at some time, tried to repair the mbr with a Windows XP repair disc?
Have you also had a wubi install at some time?

---

### Post by goreyduke on 2011-01-21
I have done a fair bit of repairing with Windows, yes. This last was an image re-install, then some partitioning to create space for Ubuntu and separate storage folders.

I haven't used Wubi at all. I have run U10.10 off the disc several times.

---

### Post by psusi on 2011-01-21
> **Hippytaff said:**
> there is a drop down menu when edtiting the patition in gparted with options such as /home /swap. The / (forward slash on it's own) is the root partition. Select this for the root partition

You mean in the installer ( ubiquity ), not gparted.

---

### Post by psusi on 2011-01-21
It looks like your Windows is in sda2, so if you need to boot it, hit escape at the grub menu to get the command line, and enter this:

set root=(hd0,2)
chainload +1
boot

Running update-grub should detect it and add it to the menu.  If it doesn't, then you might need to add it to /etc/grub.d/40_custom.

---

### Post by goreyduke on 2011-01-21
Hello, I've tried that but it rejects the word "chainload".

The set root=(hd0,2) works ok, but it says chainload (or chainload+1 or chainload +1) is not a command.

So the boot instruction comes up as "no kernel".

Is there an alternative to chainload?

---

### Post by psusi on 2011-01-22
Err, chainloadER.

---

### Post by Hippytaff on 2011-01-22
> **psusi said:**
> You mean in the installer ( ubiquity ), not gparted.

  thanks for pointing that out ;-)

---

### Post by goreyduke on 2011-01-23
You star! That did the trick. It booted straight into W7.

But there were problems the next time I booted. It didn't pick up W7 the next time around.

But "add it to /etc/grub.d/40_custom" is a bit beyond me. What do I have to do next?

---

### Post by psusi on 2011-01-23
Edit the file and add the following lines:

```

menuentry "Windows" {
set root=(hd0,2)
chainloader +1
boot
}

```

---

### Post by goreyduke on 2011-01-24
Hmmm. Again, that works, but again it does not remember it the next time around.

I made a note of what version of Grub I'm using, if that's any help. Grub 1.98, it says.

---

### Post by psusi on 2011-01-24
You put that in /etc/grub.d/40_custom and ran sudo update-grub?

---

### Post by goreyduke on 2011-01-24
No, that's the bit I don't understand.

Is "/etc/grub.d/40_custom" a line in a terminal, something to write before "update grub", etc?

And "edit the file"? Forgive me for not picking up on this but, er, what file? Where?

I don't want to go charging about in the terminal if I don't know that that's what I should be doing. "Put" is confusing me a bit, too. 

I can get into what I think is the Command line (by pressing C when the grub options appear, without W7). And the menu entry stuff/chainloader stuff works a treat.

But once I press Esc to load W7, there is no time to write anything else.

So do I write or add "/etc/grub.d/40_custom" and then "update grub", etc, before I press Esc?

Just checking! Thanks for you help, by the way. I wouldn't have got this far without your patience and indulgence.

---

### Post by matt_symes on 2011-01-24
Hi

> Is "/etc/grub.d/40_custom" a line in a terminal, something to write before "update grub", etc?

And "edit the file"? Forgive me for not picking up on this but, er, what file? Where?

I don't want to go charging about in the terminal if I don't know that that's what I should be doing. "Put" is confusing me a bit, too.

This is what psusi is trying to get you to do.

Boot into Ubuntu normally.

Press the ALT and F2 keys at the same time to display the run dialog. Into it enter (copy and paste if you want)

```
gksudo gedit /etc/grub.d/40_custom
```

Enter your password as normal. This will open the file /etc/grub.d/40_custom with root privilages. At the end of the file add this (you can copy and paste from here)

```
menuentry "Windows" {
set root=(hd0,2)
chainloader +1
boot
}
```

Save the file as normal and then close it.

Open a terminal (Applications->Accessories->Terminal) and type (exactly as typed below)

```
sudo update-grub
```

Enter you password when prompted. You will not see it echoed to the screen. This should recreate you grub.cfg file. When it is finished reboot your PC to check a new menu entry called Windows is available.

Kind regards

---

### Post by goreyduke on 2011-01-24
Thanks Matt, that worked... to an extent.

I found the run dialogue box (something new to me) and cut and pasted everything ok.

But I wonder if I blundered when I began the menuentry line on the same line as the text in the run box.

What has happened is that now the pc just boots straight into Windows! I am now writing this in W7 because I can't get back into Ubuntu, the boot stage does not offer up anything.

What's occurring?

---

### Post by matt_symes on 2011-01-24
Hi

> But I wonder if I blundered when I began the menuentry line on the same line as the text in the run box.

Yes. That does not sound right. Lets have a look at your 40_custom file.

Press ALT and F2 again. Type

```
gedit /etc/grud.d/40_custom
```

Notice there is no gksudo at the front this time as you don't want to edit the file (you can't save it). 

Copy and paste the contents back in your next post so we can see where you are.

Kind regards

---

### Post by goreyduke on 2011-01-25
How would I do that? I can't boot into Ubuntu as the pc now boots straight into W7.

I tried booting off the disc but when I paste gedit /etc/grud.d/40_custom into the run box, it comes up blank.

So if W7 can't read anything in Linux and I can't boot into my U10.10 set up, I can't see how this isn't going to leave me stuck with just W7 and an unuseable linux partition.

Thanks

---

### Post by goreyduke on 2011-01-25
That wasn't an ironic thanks, by the way! It was a does-what-it-says-on-the-tin thanks. I'm grateful that you and psusi and others have been able to get me this far.

---

### Post by matt_symes on 2011-01-25
Hi

> How would I do that? I can't boot into Ubuntu as the pc now boots straight into W7.

Hmmmm. Sorry about that. Was 3 in the morning when i made that last post. I guess my brain had given up for the day ;)

Here's what you need to do. Follow these instructions. Take your time and if you are unclear as to what i am asking you to do post back here first for clarification from someone.

Put a Ubuntu LiveCD (or USB) into the PC, boot up and select 'Try Ubuntu'. When that has booted up.

Open up a terminal (Application->Accessories->Terminal) and type

```
sudo mount -t ext4 /dev/sda3 /mnt
```

Enter your password when prompted. You will not see it echoed to the screen. This is normal. 

Press ALT and F2 together as before and type

```
gksudo gedit /mnt/etc/grub.d/40_custom
```

This will open 40_custom from you hard drive.

Edit it so it looks like this

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows" {
set root=(hd0,2)
chainloader +1
boot
}
```

Save the file.
 
Back in the terminal type

```
sudo grub-install --root-directory=/mnt /dev/sda
```

If required, enter your password again. Remove CD and boot back into Ubuntu open a terminal and type

```
sudo update-grub
```

EDIT:If i have missed something can someone else speak up.

Kind regards

---

### Post by goreyduke on 2011-01-25
No luck, I'm afraid. It booted straight back in to Windows. 
There were a couple of points en route that may be of relevent, though.

Firstly, I wasn't asked for my password after sudo mount -t ext4 /dev/sda3 /mnt so I didn't put it in.

Then when pasting... menuentry "Windows" {
set root=(hd0,2)
chainloader +1
boot
}         ...I took the liberty of changing "Windows" to "Windows 7" though that can't have made any difference, surely?

And finally, back in the terminal I again wasn't asked for my password, but put it in anyway, thinking it might be needed.

This was the outcome after re-doing the grub install:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$

From memory / might well be the Ubuntu partition created as part of the original set up, as recommended in "Dual Boot Windows 7 and Ubuntu 7 in Perfect Harmony". I can check in Disk Utility/GParted, etc, if necessary.

---

### Post by matt_symes on 2011-01-25
Hi

Yes... update-grub did not work. I did wonder about that. So what you will need to do is detailed in this web page. Have a good read and if you have any questions post back. I might not be able to answer tonight though.

[http://www.robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd](http://www.robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd)

This is the part you need to do (not the first part). Notice below i have changed what was on the web page to use sda3 (your partition) and not sda5. You wil not need to create /mnt as well

```
mount **/dev/sda3** /mnt &&
mount -o bind /dev /mnt/dev &&
mount -o bind /proc /mnt/proc &&
chroot /mnt bash &&
sudo update-grub &&
reboot;
```

Here is another link

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Search for the section **METHOD 3 - CHROOT** where all these are bound and mounted

```
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
```

so if the first method does not work try this method.

Kind regards

---

### Post by goreyduke on 2011-01-25
No worries, Matt. It'll be a day or two but I'll piece my way through it. Thanks.

---

### Post by goreyduke on 2011-01-26
Hello Matt,

It's not quite there but it's not far away, I reckon. I'm running off the disc, to I think that's why it said:

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ mount /dev/sda3 /mnt &&
> mount -o bind /dev /mnt/dev &&
> mount -o bind /proc /mnt/proc &&
> chroot /mnt bash &&
> sudo update-grub &&
> reboot;
mount: only root can do that
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

So how would I begin that command with "sudo"? 

I'm fine at cutting and pasting the answer but am not that Linux literate that I can translate it myself. 

I'd rather give this option a go as far as possible than move straight on to the second idea you pitched. Cheers.

---

### Post by psusi on 2011-01-26
You need to run sudo -s first so that all of those commands will then be run as root.  Just prefixing it with sudo will only run the first command ( up to the && ) as root.

---

### Post by goreyduke on 2011-01-26
Still no luck. Am I doing this right? I entered sudo -s then pressed return and then entered the rest of the commands on the line that follow.

Hence:

> ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mount /dev/sda3 /mnt &&
> mount -o bind /dev /mnt/dev &&
> mount -o bind /proc /mnt/proc &&
> chroot /mnt bash &&
> sudo update-grub &&
> reboot;

After that, I got:

> root@ubuntu:/#

So I put in my password, thinking that was what was required.

But instead, it said:

> command not found
root@ubuntu:/# sudo -s
sudo: unable to resolve host ubuntu

---

### Post by Quackers on 2011-01-26
When the terminal prompt changes from ubuntu@ubuntu to root@ubuntu you are to then enter
```
sudo update-grub && reboot;
```
did you do that? (although the sudo probably isn't required, not sure about the ; at the end )

---

### Post by psusi on 2011-01-26
After sudo -s and the prompt changes, just enter these commands, one at a time:

mount /dev/sda3 /mnt
for f in dev sys proc ; do mount --bind /$f /mnt/$f ; done
chroot /mnt
update-grub

If all goes well, reboot.

---

### Post by goreyduke on 2011-01-26
Blimey. It worked! It has offered up W7 three boots in a row!! Thanks everyone.

Now if someone can please tell me how to delete this other stuff that's clogging up the bootloader...

> Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin

...so I can reduce the options to just Maverick and W7 (and how to swap the order of those two around) then I believe I can skip my way merrily home. 

And again, thanks y'all for the continued help and patience.

---

### Post by psusi on 2011-01-26
Open synaptic and search for linux-image and remove the older versions.  It is usually a good idea to keep one previous version as a backup.

---

### Post by Quackers on 2011-01-26
Aha! Success! Excellent :-)

---

