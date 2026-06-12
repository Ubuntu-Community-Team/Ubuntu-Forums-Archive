---
title: "wont boot"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by jrdbarnhart on 2011-08-27
This is a problem ive had for several months now. I had an issue upgrading to 11.04 from 10.10 i forget which version of 11.04 it was. But I must get it working now to get files off of it at least.

Right now when I boot it up it stops on the screen

error: no such partition.
grub rescue>


What do I do?

---

### Post by dino99 on 2011-08-27
[http://ubuntuforums.org/showthread.php?t=1326991](http://ubuntuforums.org/showthread.php?t=1326991)

---

### Post by jrdbarnhart on 2011-08-27
okay its a link to a link. What do you want me to do with it? There is alot of data there I need specifics not just alot of data thrown at me, I am a novice at best with linux.

---

### Post by jerrrys on 2011-08-27
is this a wubi (ubuntu inside windows) install or dual boot (ubuntu has its own partition)?

---

### Post by bcbc on 2011-08-27
> **jrdbarnhart said:**
> This is a problem ive had for several months now. I had an issue upgrading to 11.04 from 10.10 i forget which version of 11.04 it was. But I must get it working now to get files off of it at least.

Right now when I boot it up it stops on the screen

error: no such partition.
grub rescue>


What do I do?
You've had a computer that hasn't booted for a couple of months? If it's Wubi, see Problem #1 of the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"). Even if it's not Wubi, if you have windows installed, that will get windows booting.

---

### Post by grahammechanical on 2011-08-27
How did you install either 11.04 or 10.10? Or would, try to install be more correct?

If you still have the Live CD whether of 101.0 or 11.04, then may I suggest that you try to boot from the CD in Try Ubuntu mode and rescue your files that way?

Regards.

---

### Post by jrdbarnhart on 2011-08-27
I installed ubuntu 8.04 on a brand new blank hard drive, no windows or osx dual boot. I've booted with the live cd before but was unsuccessful in getting to any of my files. If I can access all my files that way then ill just pull them all off and reinstall. So I need to either get it bootable by itself or access the files and start over. I prefer to fix the issue if possible.

---

### Post by jrdbarnhart on 2011-08-27
And I had 10.10 installed and i tried to upgrade to the last beta version of 11.4 using the internal update and I thought it was going okay when it shutdown on its own but it was never the same....

---

### Post by Hakunka-Matata on 2011-08-27
[LIST]
[*]Can you boot from a liveCD?
[/LIST]
That's one question, answer please?

---

### Post by jrdbarnhart on 2011-08-27
I can boot from the live cd and get into the gui but i am unable to access my files.

---

### Post by Hakunka-Matata on 2011-08-27
When you use the file browser, places, it does not show various partitions, hard drive partitions, as in the attached thumbnail?

---

### Post by kyletstrand on 2011-08-27
Try this step for step (as taken from [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery))

1. Boot into live cd.
2. Press Ctl+Alt+F1
3. Enter 
```
sudo mount /dev/hda1 /mnt
```
4. Enter
```
sudo chroot /mnt
```
5. Enter
```
apt-get update
```
6. Enter
```
apt-get upgrade
```

Is this a laptop?  My instincts are telling me it's a laptop that was not allowed to vent correctly, thus causing it to overheat and shut down mid update.

---

### Post by jrdbarnhart on 2011-08-28
I can see the two hard-drives on that screen, I tried to add a partition to the hdd as one of the early attempts to fix it. Ill dig into that deeper to see if i can access the files that way this afternoon.

and when when i typed
sudo mount /dev/hda1 /mnt

it says
mount: special device /dev/hda1 does not exist

and yes it is a laptop. and that is probably what happened with the overheating....

---

### Post by jrdbarnhart on 2011-08-28
> **kyletstrand said:**
> ```
sudo mount /dev/hda1 /mnt
```

should i be typing sda1 or hda1 ?

---

### Post by Hakunka-Matata on 2011-08-28
```
das@das-System-Product-Name:~$ sudo fdisk -l
[sudo] password for das:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3314    26614752+   7  HPFS/NTFS
/dev/sdb2            4845        9602    38217728   83  Linux
/dev/sdb3            9602        9730     1022976   82  Linux swap / Solaris
``````
sudo fdisk -l
```will list your drives with information on each partition.  You want to mount a Linux System partition - Id 83,  In my case I would mount '**/dev/sdb2**'.

---

### Post by jrdbarnhart on 2011-08-28
Okay I am getting alittle further now. I am able to get to the correct sda now. and when i do the two updates it tells
err [http://.](http://.)........ could not resolve 'archive.ubuntu.com' and W:failed to fetch [http://.](http://.)......

and it is referring to maverick on everything.
I am using a live cd from 10.10. does that make a difference?

---

### Post by jrdbarnhart on 2011-08-28
And i just had a thought. What would happen if i ran update manager on the live cd?

---

### Post by Hakunka-Matata on 2011-08-28
I've lost track, what are you wanting to accomplish now?, What is the goal?

**EDIT:** at this moment i'm burning a liveCD (usb) with 10.04, then I'll boot into it so that I can understand better what you are looking at.  I do not understand why the file browser will not let you access your linux OS and see the data you wanted to copy off.  I won't want to hang around for a long time on the liveUSB system, so if you see this message and it's convenient, get back to me and we'll attempt step through what ever it is you want to accomplish now.

---

### Post by jrdbarnhart on 2011-08-28
LOL.

main objective is to get the computer bootable again and the secondary objective is to access my personal files to just start from scratch. But for some reason I am having a hard time accessing my old desktop where everything i need is saved....

---

### Post by Hakunka-Matata on 2011-08-28
OK, I'm back, and I'm rujnning on liveCD

---

### Post by Hakunka-Matata on 2011-08-28
redacted, totally

---

### Post by Hakunka-Matata on 2011-08-28
some information from your machine is necessary to know where to go and what to do.   Please post output of ```
sudo fdisk -lu
```

---

### Post by Hakunka-Matata on 2011-08-28
> **jrdbarnhart said:**
> LOL.

main objective is to get the computer bootable again and the secondary objective is to access my personal files to just start from scratch. But for some reason I am having a hard time[COLOR=Red] accessing my old desktop where everything i need is saved[/COLOR]....


[LIST]
[*] Yes, that bothers me too, let's do that first, as fixing the boot situation may take longer.
[*]What do you see when you open the file brower (nautilus).  Places?
[*] Do you know how to take a screenshot and post it?
[*]I'm running on an ubuntu 10.10 liveCD, you are also, correct?  **oops, i'm on 10.04.  **
[/LIST]

---

### Post by jrdbarnhart on 2011-08-28
i do not know how to take screenshot.

---

### Post by Hakunka-Matata on 2011-08-28
Applications > Accessories > Take Screenshot
choose 'Select area to grab'
then click on the "Take Screenshot" box, lower right
at that time the you'll be left with a + sign for a cursor, move to one corner,click and hold left mouse button, highlight area of interest, let go of left button, name and save it.  Then when you go to make a reply here, go to the ADVANCED editing, click on the paper clip, choose file, (expand gui so you can see the UPLOAD button, do it)

Once you get that, let's try to find your files,

---

### Post by jrdbarnhart on 2011-08-28
I hope this helps. The 11 gig is what the correct install and the 143 gig as a partition that i did another install of 10.10 on in hopes of correcting this issue which didnt work, i think it only made it worse...

---

### Post by Hakunka-Matata on 2011-08-28
OK, that's great,. good work on the screenshot.
It shows the filesystems, and they are mounted, so you can simply click on them, open them, and navigate to your home directory.

---

### Post by Hakunka-Matata on 2011-08-28
I have to go into town to buy some food soon.  Have you gotten to your data?


[LIST]
[*]To get your machine booting again, first you should download and run [boot_info_script]("http://bootinfoscript.sourceforge.net/")  Link in my signature.
[*]Read and follow directions in the "**How to use the boot info script".  **
[*]After you have created the RESULTS.txt open it by double clicking on it, (it'll be on the Desktop), then highlight and copy the ENTIRE file.
[*]next paste that entire file into a reply, highlight the entire file again, and then click on code tags icon - the **# **icon in the advanced section.  Preview it, then post it.  We'll get important information on how to fix your boot issue from it.
[/LIST]
See you after a while.  Good luck

---

### Post by jrdbarnhart on 2011-08-28
Good news I have not gotten the data yet. And when there's good news then you know there is bad news. Bad news I had to restart due to mouse issues so now it wont boot into the live cd.... It says

```
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

I am going to attempt to burn a 11.04 livecd and see if that will work:confused:

---

### Post by jrdbarnhart on 2011-08-28
Okay the 11.04 live cd now boots, I have no idea what happened with the 10.10 one.

---

### Post by jrdbarnhart on 2011-08-28
here is a screenshot of the fdisk command

---

### Post by jrdbarnhart on 2011-08-28
And finally here is the boot info script results file

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   278,605,455   278,603,408  83 Linux
/dev/sda2         278,605,822   312,580,095    33,974,274   5 Extended
/dev/sda5         300,300,288   312,580,095    12,279,808  82 Linux swap / Solaris
/dev/sda6         278,605,824   299,280,383    20,674,560  83 Linux
/dev/sda7         299,282,432   300,287,999     1,005,568  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        e2ff097b-2830-49af-9483-6e287dbf79d4   ext4       
/dev/sda5        0a50b8a1-fe3e-4ad3-a75d-bbec77722143   swsuspend  
/dev/sda6        8e6d933c-cbaf-4690-a6b6-1cf4a865f51d   ext4       
/dev/sda7        ed58a185-2fdc-45f6-99bd-e747b54f02d6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a50b8a1-fe3e-4ad3-a75d-bbec77722143 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  76.135948181 = 81.750351872   boot/grub/core.img                             1
  76.132854462 = 81.747030016   boot/vmlinuz-2.6.35-22-generic                 1
  76.132854462 = 81.747030016   vmlinuz                                        1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8e6d933c-cbaf-4690-a6b6-1cf4a865f51d ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8e6d933c-cbaf-4690-a6b6-1cf4a865f51d ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8e6d933c-cbaf-4690-a6b6-1cf4a865f51d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e2ff097b-2830-49af-9483-6e287dbf79d4
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1
}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8e6d933c-cbaf-4690-a6b6-1cf4a865f51d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ed58a185-2fdc-45f6-99bd-e747b54f02d6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 133.865032196 = 143.736483840  boot/grub/core.img                             1
 135.174980164 = 145.143029760  boot/grub/grub.cfg                             1
 134.282878876 = 144.185143296  boot/initrd.img-2.6.35-22-generic              2
 133.864280701 = 143.735676928  boot/vmlinuz-2.6.35-22-generic                 1
 134.282878876 = 144.185143296  initrd.img                                     2
 133.864280701 = 143.735676928  vmlinuz                                        1


```

What Can I do now?

---

### Post by Hakunka-Matata on 2011-08-28
OK, good job.  The RESULTS.txt is formatted nicely and easy to navigate, thanks.  Have you tried booting from the hard drive lately?  Or do you want to persue looking for your files using the file browser?  Up to you.

---

### Post by najim on 2011-08-29
Hello, 

Thank you jrdbarnhart, kyletstrand & Hakunka-Matata posting on this thread, i have been having a similar problem for now 2 days i use a laptop that only had ubuntu 10.10 installed and suddenly it could not boot, i have tried several options from threads i find here but none has given me any result only your thread has given me an insight in what could be the problem with my laptop. these are the result on following all your steps **kyletstrand **

sudo mount /dev/sda1 /mnt
gave me this: *looks like swapspace not mounted you must specify file system type*

sudo chroot /mnt
gave me this: *failed to run command "/bin/bash": No such file or directory*

sudo apt-get update
gave me this:* some index files failed to download they have been ignored old one used instead*

sudo apt-get upgrade
gave me this: *0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded*

sudo fdisk -l /dev/sda1 
gave me this: does not contain a valid partition table

i have downloaded and executed the boot_info_script but did not get any results, i think its because none of my partitions is mounted, all it does is hang in between commands. Am really desparate i dont know if anyone has ever solved this before to help me out i have alots to data on this machine that i need and am still a novice in linux only started out with ubuntu at the beginning of this year.

Please Help :confused:

---

### Post by jrdbarnhart on 2011-08-29
When I go to where my files should be there is nothing there, and when I try to boot from the hard disk it still tells me
```
error: no such partition.
grub rescue>
```
lets see if we can get this thing bootable.

---

### Post by Hakunka-Matata on 2011-08-29
I'd like to see you find your data first, or to understand why that operation is not working.
This *should work* for you.  If it doesn't then take a screenshot and show me where it failed.

Boot to live CD, open a Terminal and input this code, things should happen as depicted in the attached Thumbnail 'find_data_sda1.png'.  Everything is Case Sensitive so copying and pasting the commands is the fastest/safest way to run them:  Obviously all lines preceded with # are comments only.  If I've made any mistakes in the code, then look at the thumbnail, the thumbnail has no typos in it.
```

**sudo mount /dev/sda6 /mnt**

**ls /mnt**

# should see folders and files contained in /dev/sda6

**cd /mnt**

**cd home**

**ls**

#should see your username as a folder entry, (folders display as blue entries) I'll use 'jrd' for you only as example.  My username is 'das'

**cd jrd**

[B]ls
[/B] 
#shoud see your data

**cd Downloads**

# should see contents of Download directory

# go about your copying and saving or whatever you need to do now.  'cd ..' moves you back up one directory

**man cp**

# man cp shows how to use the copy command

**cd**

# that switched you back to home directory so you can unmount sda1
sudo umount /dev/sda6

**ls /mnt**

# that last command just to check that you've in fact unmounted sda6
```I've chosen sda6 as the partition of interest but it's only ~ 10 GiB in size, do this again using sda1 instead, it's much larger and may the partition where your data is.

```
Boot with liveCD;
Open Terminal [System > Applications > Terminal]
should see: ubuntu@ubuntu:~$

issue following commands, observe results follow pattern seen in 'find_data_sda1.png' attached thumbnail
any line preceeded by # is a comment line

sudo mount /dev/sda1 /mnt    # (mount appropriate partition, use Gparted to look at your drive layout if needed.  You want to mount a Linux Id                        83 partition.
ls /mnt               # (do you see a bunch of folders listed?, folders appear in light blue bold print
cd /mnt                # (switching working directory to /mnt
cd home                # (switching working directory to /mnt/home, only works if a 'home' directory appeared in /mnt directory
ls                # (listing contents of /mnt/home directory, if you have made than one user account, see multiply usernames
cd das                # (switching working directory to /mnt/home/das  # "das" is my username
ls                # (listing contents of /mnt/home/das directory
cd Downloads            # (switching working directory to /mnt/home/das/Downloads directory
ls                # (listing contents of /mnt/home/das/Downloads directory
cd                # (switching to home directory (a bit confusing because 'home' is a directory itself, we've actually switched to                        the /home/das directory in my case.  The currently logged on user's home directory.
sudo umount /dev/sda1        # (unmount sda1 from /mnt directory
ls /mnt                # (checking to make sure /mnt directory is empty now, (sda1 has been unmounted     
```

---

### Post by jrdbarnhart on 2011-08-29
I was thinking about it today and the sda1 is where the data should be. I ran those commands and there is nothing there, not even my home folder... I never deleted anything so it has to be somewhere. I checked the other drives and nothing was there either

---

### Post by Hakunka-Matata on 2011-08-29
Then use gparted to look at the drives, take a screenshot and post it please.

---

### Post by jrdbarnhart on 2011-08-29
here is the screenshot

---

### Post by jasonrisenburg on 2011-08-29
Last time i got that message i was updating 11.04 on a partial update (i didnt know that was bad) and i had to reinstall... I didnt have another computer to get on the internet and find out how to rescue it.

---

### Post by jrdbarnhart on 2011-08-29
Did you loose any data or was it all still there?

> **jasonrisenburg said:**
> Last time i got that message i was updating 11.04 on a partial update (i didnt know that was bad) and i had to reinstall... I didnt have another computer to get on the internet and find out how to rescue it.

---

### Post by Hakunka-Matata on 2011-08-29
> **jrdbarnhart said:**
> I was thinking about it today and the sda1 is where the data should be. [COLOR=Red]I ran those commands and there is nothing there, not even my home folder[/COLOR]... I never deleted anything so it has to be somewhere. I checked the other drives and nothing was there either

Both sda1 & sda6 have something on them.  You say [COLOR=Red]above[COLOR=Black] you ran those commands and there is nothing there.  What response did you get when you ran *those *commands.  It's hard to progress if you don't provide details on what happened.  All we have established to this point is that you do in fact have *something *on partitions sda1 and sda6.  Show me what happens when you run 
[/COLOR][/COLOR]```
sudo mount /dev/sda1 /mnt
ls /mnt
```[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by jrdbarnhart on 2011-08-29
I did both sda1 and sda 6. And by stroke divine luck, my friend that borrowed my flashdrive that she thought she lost has found it and returned it to me, so I have all of my irreplaceable files again. So if need be we can just reinstall everything at this point

---

### Post by Hakunka-Matata on 2011-08-29
> **jrdbarnhart said:**
> I did both sda1 and sda 6. And by stroke divine luck, my friend that borrowed my flashdrive that she thought she lost has found it and returned it to me, so I have all of my irreplaceable files again. So if need be we can just reinstall everything at this point

Ok, that's great, you have a home directory in both of those partitions.  I'd like to just get to the bottom of this exercise at this point so we both know what's going on.

so let's go farther now. after mounting sda1 or sda6, continue,

```
sudo mount /dev/sda1 /mnt
ls /mnt
cd /mnt/home
ls /mnt/home
```**EDIT: **the last command could have been just 
```
ls
```but that's OK,

---

### Post by jrdbarnhart on 2011-08-29
I did those codes to both again and in sda1 which is the one where I should see my stuff it is empty.

---

### Post by Hakunka-Matata on 2011-08-29
you have to keep going, you're almost there, now you are showing "**[COLOR=Blue]jared[/COLOR]**[COLOR=Blue][COLOR=Black]" as a directory in /home so do the next command,

[/COLOR][/COLOR]```
cd jared
ls
```after that you should see your folders, Downloads, Documents, etc.

GOOD JOB, keep going

---

### Post by jrdbarnhart on 2011-08-29
Its empty....:confused:

---

### Post by I am Lost101 on 2011-08-29
Seems like you may have over wrote your home partition or the update has. Try booting live CD into GUI ( Ubuntu desktop ) . Try Gparted select your system partition and click repair, had a similar scare a while back (not due to upgrade Ill wait for LTS) but this fixed me . 

Good luck

---

### Post by Hakunka-Matata on 2011-08-29
THANK YOU jared, now you've convinced me.  And the same thing is true for sda6 I guess, right? 
If that's the case, and you have your files anyway on the flash drive your friend brought, then do your fresh install as you suggested.  I wanted to make sure we actually got all the way into your home/jared folder to see what was there.  

If you want to do a clean install, then you could/should create your partitions manually, 

Primary  sda1 - Extended (make it as big as needed to hold all the partitions below)
Logical  / (root) Ext 4  - 15 - 20 GiB
Logical  swap - same size as the amount of RAM you have, 2GiB?
Logical  /home Ext 4  -  make it as big as you want

---

### Post by jrdbarnhart on 2011-08-29
I do not see any repair function in gparted, I am using the 11.04 cd

---

### Post by jrdbarnhart on 2011-08-29
Im glad someone else cant find it either. I was starting to loose my marbles thinking I was either blind or stupid. Ill tackle a fresh install when I am more awake. Thank you for your help!

---

### Post by Hakunka-Matata on 2011-08-29
right click on the partition of interest, then select "check" **Edit: Highlight it first**
You'll have to unmount swap, and sda2 before you'll get the check option -  right click, swap-off, and unmount for sda2
**Edit: **maybe you don't have to swap-off,

---

### Post by najim on 2011-08-30
Hello good people, well am also still facing the similar problem, i can't boot the screenshot after running 

```
sudo fdisk -l 

sudo mount /dev/sda1 /mnt

```Am unable to mount any partition of my hard drive 

Please help;

---

### Post by Ciudic on 2011-08-30
hi guys .
i need help , 
i lost my grub menu and cant get it back , tried to reinstall but in live cd i can not mount my ssd hdd . 
please help me out to mount my hdd and get my grub menu back

---

### Post by Hakunka-Matata on 2011-08-30
najim:  The terminal gave you the answer, you cannot mount swap partitions.  You want to mount the partitions of type **Linux 83.  **Instead of mounting sda1, mount any partition that has a type of Linux 83.

So you should be able to mount sda5 --> sda8.  You can mount them all, one after another, then go look in the /mnt folder and you'll see all of them there.

Also, you really should start your own thread, it gets too confusing if more than one OP is asking questions.

Start your own thread and you'll get lots of help.

Good Luck

---

### Post by Ciudic on 2011-08-30
hi , sorry about being confusing . 
i did specified the linux 83 partition ,and still cant do it . 
i am really new to ubuntu and i spent all my day looking for terminal comands 
i still need same ones help

---

### Post by Hakunka-Matata on 2011-08-30
Ciudic:

Please start your own thread, it works best for you and for those helping you.  Give it a subject of something like, "lost Grub menu, please help"

Good luck

---

### Post by jrdbarnhart on 2011-08-30
I reinstalled and used the option to format before reinstall. It appeared to have no problems but when I went to boot it up it now tells me

```
 error: out of disk.
grub rescue>
```

---

### Post by jrdbarnhart on 2011-08-31
Okay I have reinstalled the system and all appears to be working well so i will be marking this thread closed.

---

### Post by Hakunka-Matata on 2011-08-31
jared, Glad to see you got it going.

---

