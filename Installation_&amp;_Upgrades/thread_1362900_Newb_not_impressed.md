---
title: "Newb not impressed"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by robbielint on 2009-12-23
ok, installed Ubuntu, logged-in, it told me it had updates, i told it to update, it said it needed to reboot, i said ok, it tried to reboot and broke. It broke itself? 
 
Says it got tired of waiting for root? and dumps me to some cryptic command line. tried the recover option at boot with even worse results.
 
a complete newb and not impressed with the touted 'stability'. shoot. this thing breaks itself. should i stay or should i go?
 
is this an easy fix?
 
tia. robbie

---

### Post by presence1960 on 2009-12-23
What type of install did you do, wubi (inside windows) or did you boot off the Live Cd and do an install to a dedicated partition? What are your specs of the machine?

While you are at it do this also:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by robbielint on 2009-12-23
Thanks for the quick response, I've installed on a Lenovo T60p, Core 2 Duo, 4 gb, ATI graphics...i installed on it's own partition. It worked great until I chose to do the update.

Here's the Results.txt:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   147,458,047   147,251,200   7 HPFS/NTFS
/dev/sda3         147,465,360   195,365,519    47,900,160   5 Extended
/dev/sda5         147,465,423   193,294,079    45,828,657  83 Linux
/dev/sda6         193,294,143   195,365,519     2,071,377  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9a6a9a6a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C2647B0E647B0507" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="128C93F08C93CC9B" TYPE="ntfs" 
/dev/sda5: UUID="72513e1c-d180-4420-8e67-3af719fafa51" TYPE="ext4" 
/dev/sda6: UUID="b7664e64-06d3-4c50-ad69-f97582004ec4" TYPE="swap" 
/dev/sdb1: UUID="A6BEF8C2BEF88BD5" LABEL="VirtualVolume" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 72513e1c-d180-4420-8e67-3af719fafa51
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 72513e1c-d180-4420-8e67-3af719fafa51
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=72513e1c-d180-4420-8e67-3af719fafa51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 72513e1c-d180-4420-8e67-3af719fafa51
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=72513e1c-d180-4420-8e67-3af719fafa51 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 72513e1c-d180-4420-8e67-3af719fafa51
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=72513e1c-d180-4420-8e67-3af719fafa51 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 72513e1c-d180-4420-8e67-3af719fafa51
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=72513e1c-d180-4420-8e67-3af719fafa51 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set c2647b0e647b0507
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=72513e1c-d180-4420-8e67-3af719fafa51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b7664e64-06d3-4c50-ad69-f97582004ec4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  75.5GB: boot/grub/grub.cfg
  75.5GB: boot/initrd.img-2.6.31-14-generic
  75.5GB: boot/initrd.img-2.6.31-16-generic
  75.5GB: boot/initrd.img-2.6.31-16-generic.dpkg-bak
  75.5GB: boot/initrd.img-2.6.31-16-generic.new
  75.5GB: boot/vmlinuz-2.6.31-14-generic
  75.5GB: boot/vmlinuz-2.6.31-16-generic
  75.5GB: initrd.img
  75.5GB: initrd.img.old
  75.5GB: vmlinuz
  75.5GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-12-23
> I found that adding all_generic_ide to the /boot/grub/menu.lst stanza was an OK workaround, but I do not know
if this affects performance, reliability, etc. Here's the change I made:

kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=1e3fbd55-5dfa-4cee-b9c7-8bc8bd3982ff [COLOR="Red"]ro splash all_generic_ide[/COLOR]

see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003") for the solution quoted above. That problem was the subject of the bug report to which I linked. The poster found a solution that works for him.

A simple google search turned this up for me.

P.S. GRUB2 does not use menu.lst. See here to edit GRUB2 to create a custom entry so you can try that solution: [https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)

OR try this:
   ```
 * Manual Editing of grub.cfg (Not encouraged)
      Manual editing of /boot/grub/grub.cfg is not encouraged. Think of grub.cfg as a result, not as an initiator. The files that should be edited are contained in the /etc/grub.d folders and the /etc/default/grub file.

      In order to discourage its editing, grub.cfg is read-only. Even attempting to open, edit and save this file using root privileges cannot be done until the 'read-only' status is changed. If you must edit this file:
      Code:

      sudo chmod +w /boot/grub/grub.cfg
      gksudo gedit /boot/grub/grub.cfg

      Note: This file is returned to 'read-only' status anytime the update-grub command is run.
```
from [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by robbielint on 2009-12-26
Thanks for looking at this for me...but I'd have no idea where to type:
 
sudo chmod +w /boot/grub/grub.cfg
gksudo gedit /boot/grub/grub.cfg
 
Linux is still too hard and buggy for the rest of us. I'll try again in a few years

---

### Post by darkod on 2009-12-26
> **robbielint said:**
> Thanks for looking at this for me...but I'd have no idea where to type:
 
sudo chmod +w /boot/grub/grub.cfg
gksudo gedit /boot/grub/grub.cfg
 

In Terminal (Applications-Accessories).

---

### Post by phillw on 2009-12-26
> **robbielint said:**
> 
 
Linux is still too hard and buggy for the rest of us. I'll try again in a few years


I'm saying nothing on that, except to point you over to an explanation --> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Please take the time to read it.

Regards,

Phill.

---

### Post by bimalc on 2009-12-26
> **phillw said:**
> I'm saying nothing on that, except to point you over to an explanation --> [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Please take the time to read it.

Regards,

Phill.

I know you're trying to avoid the holy cultural war that ensues when windows users come to linux and complain its too [complicated, un-user-friendly, not-windows, etc.] and the link you post is fairly good on the whole topic, but, especially for Ubuntu, the expectations ARE different [take this up with Canonical if you think its bogus].  Ubuntu's promise, explicit or not, is Linux for the rest of us.  Inherent in that promise (at least in the minds of many windows users who might be listening) is that, at a bare minimum, 

1) the product installs on the bulk of standard (read mass market) hardware configurations with minimal low level work by the end user [no sending people in the manually edit boot/installation files, no dumping them into a console and expecting anything more than one or two simple commands].  The corollary to this is that where there are known issues with specific bits of (popular) hardware, various graphics drivers on laptops come to mind, instead of sending noobs to the four corners of the earth, the community has a vested interest in making it EASIER for these people to join the community by leveraging that these new users are good at it.  If the sad reality is that new users are NOT savvy about BASHing their way through problems the process needs to be automated as much as possible on the install end.  Once you give new users a gui to live in, you;d be surprised at how rapidly they'll become adept as moving from the gui to the terminal and back.  But if they never get the gui running, they'll never invest in learning enough to competently use the terminal and participate in the community.

and 2) When the product does something in an automated fashion it should, at the very least not make things that used to work stop working.  The update might fail, it might tell you to go do the update manually, but it shouldn't take things that worked (like say booting into a gui) and make them not work.  The link you posted essentially argues that since Linux is FOSS and most devs are uncompensated we should expect things to not work as expected.  This line opf argument is completely broken for a distro which is supposed to appeal to the masses.

---

### Post by ElSlunko on 2009-12-26
Sounded like an easy fix to me! Sorry you didn't stay around long enough. See you in a few years.

---

### Post by phillw on 2009-12-26
> **bimalc said:**
> I know you're trying to avoid the holy cultural war that ensues when windows users come to linux and complain its too [complicated, un-user-friendly, not-windows, etc.] 

To be free - as in totally free, it is also required that people learn a little. If you wish your hand to be held and told what to do, then Windows is the better OS. If, however, you are inquisitive ... have a play with Linux and excercise the brain cells. Whilst some of the answers we give requiring copy & paste may seem like complete gobbly-gook, we all had one bean on our count when we started here.

Regards,

Phill.

---

### Post by presence1960 on 2009-12-26
> **robbielint said:**
> Thanks for looking at this for me...but I'd have no idea where to type:
 
sudo chmod +w /boot/grub/grub.cfg
gksudo gedit /boot/grub/grub.cfg
 
Linux is still too hard and buggy for the **_rest of us_**. I'll try again in a few years

who are the rest of us? Do you have turds in your pockets or something? Don't speak for others. What you meant to say it is too hard for you!

If you had problems with 9.10 you could have tried the Long Term Support release 8.04 hardy heron, but since your mind is already made up...

---

### Post by recluce on 2009-12-27
Chalk this guy up as an id*ot. 

- Not because he had trouble installing Ubuntu. It happens to all of us. 

- Not even because he has no idea what a command shell is - and thus will not be able to rescue a shot Windows installation either.

- Do so because he came here with a sense of entitlement, wasted the time of all the people replying to him, refused to learn or even use Google on his own. That he just quit the scene whining about how hard Linux is and how unfair life is in general, just rounds off the picture.

The community does not need people like him, really.

---

### Post by robbielint on 2010-01-05
> **presence1960 said:**
> who are the rest of us? Do you have turds in your pockets or something? Don't speak for others. What you meant to say it is too hard for you!

 
Dude, I really appreciate you for your help, but it began to get too deep for me. I *really* want to use Linux. I'm totally in-sync with the whole "free" (not as in "free beer") philosophy, and besides, I hate Windows and Ballmer.
 
Look: Ubuntu marketing claims to be "Linux for the rest of us..." The only turd I have right now is, sadly, Ubuntu. 
 
Ubuntu claims: "Once installed your system is immediately **ready-to-use**. On the desktop you have a full set of productivity, internet, drawing and graphics applications, and games."
 
I took the marketing bait. The claim worked for 27.347 seconds, I was fully stoked, then Ubuntu prompted me to update and it broke itself.
 
Now...one guy here called me an 'idiot'...too rare. I suggest that I'm an idiot for beleiving the same old corperate marketing bs that's spewing out of Ubuntu...and, of course, whomever wrote that buggy-*** update code.
 
What's the difference between Ubuntu and Microsoft? Both have a marketing machine that lures users in with minor untruths. Dude-man...If you say in your advertising that your system will install and be "immediately ready-to-use" then you'd better not screw it up and blame the user. This whole blame-the-user thing is a dud.
 
I have no doubt that one day Linux will be the OS of choice. But it's got to get better at not breaking itself. If I broke it it'd be one thing...but the damn thing broke itself.
 
Again, a bucket-load of thanks for stepping in to help. To those of you hiding behind your flame-throwers: You're weak, evolution will eventually weed-out your strain.

---

### Post by robbielint on 2010-01-05
Ok, I fixed it. Reinstalled Ubuntu, unchecked all of the updates related to the Linux Kernel Updates (2.6.31-16). Everything installed updated nicely. Somehow, the kernal updates broke the boot loader last time.

---

### Post by robbielint on 2010-01-06
My apologies for some of the comments I made about Ubuntu and the team that wrote the updater: It's not too badly broken and everything is working very nicely now.

The core of the original problem was that after I let the updater do the installs, the kernel updates changed by grub.cfg by adding another entry for the new version, the minor bug is that is did not remove the previous version from the boot list even though it had replaced it.

So, grub was trying to launch the old kernel by default and, thus, the "root not found" error. Now that I'm becoming more proficient, looking back at the .cfg and log file i posted, this is a very simple problem with a very simple solution: Choose the correct version from the grub list at boot time. 

Now I'm going to fix the grub.cfg to remove the extra entry. There should be a gui for this, perhaps I'll write one if it doesn't already exist. How hard can it be?

Happy now to be using Linux

---

### Post by presence1960 on 2010-01-06
> **robbielint said:**
> My apologies for some of the comments I made about Ubuntu and the team that wrote the updater: It's not too badly broken and everything is working very nicely now.

The core of the original problem was that after I let the updater do the installs, the kernel updates changed by grub.cfg by adding another entry for the new version, the minor bug is that is did not remove the previous version from the boot list even though it had replaced it.

So, grub was trying to launch the old kernel by default and, thus, the "root not found" error. Now that I'm becoming more proficient, looking back at the .cfg and log file i posted, this is a very simple problem with a very simple solution: Choose the correct version from the grub list at boot time. 

Now I'm going to fix the grub.cfg to remove the extra entry. There should be a gui for this, perhaps I'll write one if it doesn't already exist. How hard can it be?

Happy now to be using Linux
To get rid of the kernels you don't want remove linux-image-2.6.31-xx & linux-headers-2.6.31-xx in terminal or Synaptic Package Manager. It is recommended that you leave the two most recent kernels and their recovery options that way if one kernel borks you can boot into the other. Once you have removed unwanted kernels open a terminal and run ```
sudo update-grub
```
to refresh grub.cfg & the GRUB menu.

---

