---
title: "Vista/Ubuntu -Boot mess (Grub)"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by gek0 on 2010-06-21
Hi all,

Skip to ################## to miss out my life story and introduction :P

I have been running Vista and Ubuntu for quite some time now.  I Think I was using Wubi but it never occurred to me that this was the "wrong" way to install Ubuntu.  Regardless I had fun for around half a year after taking a childhood ambition to run Linux(Sad I know).

So once school was finished and I had some free time I booted ubuntu and ran the update manager as it had been a while since i used it.  I was given an option to upgrade to Lucid so I took it - obviously.  

#########################
During the upgrade/installation it asked me to where grub2 was to be installed, and if my memory serves me correctly it said "if you are unsure, select all", so I selected all and proceeded, as boot loaders is not something I have ever spent any time on.

At the restart i was faced with grub rescue, it was from here I struggled.  However, always impressed by how many errors can be fixed by Google I proceeded and made my Live CD, both Vista recovery and ubuntu Live.

It has been a week since this began and I have come a long way since and changed many settings as per every post and thread I came across, I will do my best to try and note the changes I made.

Live CD boot and changed grub2 install to /dev/sda, somehow.
Ran update-grub
Windows Recovery Environment appeared on grub2 menu.
Managed to install grub legacy? Certainly a different version than grub2
When I tried to boot to boot to vista on grub2 menu it hung for 3 seconds then restarted my computer back around to grub2 after bios.

I then found the fix if you used WUBI which I believed at the time I had, so I copied the files wublder and so on. Didn't work.

Then I found a post about using testdisk.  The instructions were well written and I got to the point were you "backupBS" only to found no such option and everything reading "OK", suggesting nothing was wrong and this route would fail.  I tried the other options of rebuilding and so on, dead ends also.

Then found a post from Oldfred (who I hope will spend the time with my post and help me ultimately put this being me so I can figure out what actually went wrong...") suggesting the use of the Vista recovery CD, I ran it no problem after a few failed attempts of writing it to CD, found my Vista OS and I went off to recovery it using the fixboot, scanos, rebuildbcd, which did something.  Note I didnt run .fixmbr as I had spent alot of time(2 days) fixing grub to boot me to an OS...  This didnt work either, either did chkdsk, i realise now I didnt run chkdsk /r properly, i guess it wasn't pointed to the correct drive or something I don't know.

So in my wisdom I booted from live CD and used Gparted to format my Linux partition and resize Vista to take up the existing room, with the idea of reinstalling lucid from CD and creating a fresh partition and hopefully rewriting grub correctly(Ambitious but I was tired and stuck).  After reading some more on Gparted I realise it's not the best tool to use for Vista.....  Too late now though.

This changed the outcome of trying to boot to Windows Recovery Environment to achieving a flashing underscore, something which seemed common, great, I'm almost there.

Ran testdisk again, no luck.

Decided to relaunch Recovery CD to just /fixmbr and be done with it and try to reinstall Ubuntu again.  It was slow to load and also didn't locate my Vista OS, I tried the LOAD DRIVERS option, but it was late and I decided to give up and sleep.

Now, were I am at now.

Recovery CD boot caused Blue screen - irq_not_less_or_equal.

I realise I need to run chkdsk /r but I cannot reach a prompt to do so when booted to Windows CD, as it crashes.

I can continue and go down the repair MBR routes with boot cds and so on but I am going to ask for help before my computer goes on fire.

Time for the important details then.

 ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 10935296 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda4: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,084,160   566,162,147   545,077,988   7 HPFS/NTFS
/dev/sda4         566,163,454   625,141,759    58,978,306   5 Extended
/dev/sda5         566,163,456   622,616,575    56,453,120  83 Linux
/dev/sda6         622,618,624   625,141,759     2,523,136  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0606                              vfat       DellUtility                   
/dev/sda2        2ED2EF36D2EF0147                       ntfs       RECOVERY                      
/dev/sda3        CE60F48660F47695                       ntfs       Windows Vista                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        36917c93-81d1-45fc-a492-71d7357cde3a   ext4                                     
/dev/sda6        ea654c7d-54e3-405d-9c61-596d1f6b5a3f   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
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
search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=36917c93-81d1-45fc-a492-71d7357cde3a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=36917c93-81d1-45fc-a492-71d7357cde3a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36917c93-81d1-45fc-a492-71d7357cde3a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07d7-0606
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set ce60f48660f47695
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
UUID=36917c93-81d1-45fc-a492-71d7357cde3a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ea654c7d-54e3-405d-9c61-596d1f6b5a3f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 305.0GB: boot/grub/core.img
 292.1GB: boot/grub/grub.cfg
 305.3GB: boot/initrd.img-2.6.32-22-generic-pae
 305.1GB: boot/vmlinuz-2.6.32-22-generic-pae
 305.3GB: initrd.img
 305.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```Thank you for taking the time to read and I hope you can get my out of this and back into my dual boot.

---

### Post by darkod on 2010-06-21
To cut a long story short:

You seem to have full ubuntu installation on sda5, not wubi.

1. Do you get a grub boot menu at start and can you boot ubuntu successfully?

2. Can you boot vista from it successfully?

---

### Post by gek0 on 2010-06-21
I get a grub boot menu with Linux then Linux Recovery, memtest, dell utility, windows recovery environment.

Linux boots fine, Windows Recovery goes to the flashing underscore until I press the button to turn my computer off.

So I cannot boot vista successfully.

Sorry for the long opening post but I just wanted to get as much listed as to what I have done to give you an idea as to were I might be.

---

### Post by darkod on 2010-06-21
No problem with giving lots of info, I just couldn't figure out what you can and can't boot.

Because you don't seem to have wubi, the wubildr files you put there might create confusion, not sure. But lets not delete them straight away, just move them temporarily. If it turns out you need them, we can put them back.

Boot ubuntu and in Places open your vista partition, /dev/sda3. It will probably just be called 260GB filesystem.

Move the files wubildr and wubildr.mbr for example to your ubuntu home folder.

Restart and see whether it helped.

---

### Post by gek0 on 2010-06-21
I wasn't sure whether or not to remove them earlier in my attempt to fix it.

I did as you suggested and windows recovery still hangs at the blinking curser.

---

### Post by darkod on 2010-06-21
The vista boot files seem messed up.

Boot with the vista repair cd you made, and follow the instructions here to manually try to fix the boot files in command prompt:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Note: Try just the bootrec.exe /fixboot first. Run it three times.

Running the /fixmbr will overwrite grub2 on the MBR but even that is no problem if that helps you get vista booting. Reinstalling grub2 back to the MBR is easy with the ubuntu cd.

Try just /fixboot first, if it doesn't help, try both commands, if that still doesn't help try also the automated process, not just the manual.

If vista manages to boot on its own, I guess you will have no problems booting it from grub2 too.

---

### Post by gek0 on 2010-06-21
When I use the boot cd I get to system recovery options and it can't find my vista install. It used to until I gparted. I have searched on how to use load drivers to locate it but not finding anything. Posting this on my iPod I'm currently looking at the system recovery options screen.

---

### Post by darkod on 2010-06-21
Uhhh... we are running out of options.
Sometimes you can force chkdsk from ubuntu. It can't really fix ntfs errors but it can schedule a check the next time you try to boot windows.

From ubuntu try:

sudo ntfsfix /dev/sda3

After it finishes, restart and select to boot vista. Hopefully it will start a check.

---

### Post by gek0 on 2010-06-21
I went on without selecting vista and went to command prompt. I executed fix boot a few times and restarted. It didn't change anything. Still flashing underscore. It's maybe worth mentioning I get the same flashing underscore before what I belive ubuntu loads my graphics card when I boot if from grub. I scheduled chkdsk using ubuntu. Booted windows recovery and same underscore. Should I try fix mbr? Or wait for more user input?  I'm in no rush I'd just like to get it fixed.

---

### Post by darkod on 2010-06-21
The problem is if the vista repair process can't find the partition, as it seems according to what you say, it won't try to fix anything.

Like for example if you run the vista repair cd on a computer where there is no windows at all. What is it going to fix?

Without finding the partition, it ignores everything like you never had vista on there.

I'm not sure what's best to do right now honestly. You can try the automated process of the vista repair cd, as I said, reinstalling grub2 on the MBR later is easy. Provided the repair process overwrites it.

---

### Post by gek0 on 2010-06-21
Erm I tried the recovery disk and got a new menu I pressed f8 to view advanced options. Now I see the 3 safe mode options and a list of others. Enable boot logging. Low res video. Last known good config. Directory services restore mode. Debugging mode. Disable auto restart on failure. Disable driver signature enforcement. And  start windows normally.  Lol tempting to press the last. Any ideas from here?  I have to go shopping soon so I may not reply for an hour. But just know your a hero for helping

---

### Post by gek0 on 2010-06-21
Quick update.  I performed bootrec.exe /fixmbr, restarted and faced with flashing cursor again.  It seems to be linked with corrupt video?

Not sure whether I am any further on now, or if I should try to reinstall grub to mbr?

---

### Post by darkod on 2010-06-21
> **gek0 said:**
> Quick update.  I performed bootrec.exe /fixmbr, restarted and faced with flashing cursor again.  It seems to be linked with corrupt video?

Not sure whether I am any further on now, or if I should try to reinstall grub to mbr?

/fixmbr installed windows mbr on the disk and now it's trying to boot vista directly. It ends up with a flashing cursor, the same as trying vista from the boot menu.

However, you can try this: start the computer and after the POST finishes start hitting F8 for the advanced windows menu. And don't ask how it looks for vista because I've never seen it. :)

But hopefully there might be Recovery Console or similar in that advanced menu, and again hopefully, it might allow you to run chkdsk. Not sure if it recognizes the vista partition correctly, but if there is such console, at the command prompt try

chkdsk c: /r /f

---

### Post by oldfred on 2010-06-21
It sounds like Darko & you have gone though ust about everything. It may be just too many changes especially resizing a Vista partition with errors is too much to fix.

I have also seen this but never used it.
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by gek0 on 2010-06-21
Chkdsk is running... When I ran it before I didn't direct it to c: maybe that's why it didn't run before. Anywhere I looked it didn't say to add c:  it makes sense to though lol.  I don't want to reformat I want to fix this!

I saw this issue with booting to windows on another post but can't find it sigh. Is it possible that the bios got changed at some point conflicting my video driver causing this?

---

### Post by gek0 on 2010-06-21
Sigh chkdsk and every other tool i have used doesn't recall any errors on my Vista.  I reinstalled grub2 to sda and I am going to proceed to remove any useful files I had on Vista.  Have you two never seen this problem were Vista loads to a flashing underscore after a serious battering of the mbr? lol.. Once I copy any useful files to an external HD I will start looking at the BIOS and device manager as I see theres quite a bit documented on it.

If you know anything can you chirp up now before I go in with my sleeves rolled up? :)  Also, say I do reinstall my Windows vista, how can I be sure this won't happen again when Lucid goes back on another partition?  Please refrain from telling me to read instructions properly lol.

---

### Post by darkod on 2010-06-21
I don't want to say "It's your fault" but it's probably your fault. :)

I can't bother to quote your exact words but during this thread you said something along "I formatted my ubuntu partition, extended vista to use the space..."

You probably meant deleted the ubuntu partition otherwise you can't expand vista to take that space. In which case, if that really happened, you have a new installation of ubuntu which in turn shrinked vista again to make space for the new ubuntu.

You can't just resize the windows partition back and forth like that. Remember, this is windows we are talking about.

If this really happened, the resizing probably corrupted it. On top of that, even vista repair process is useless... :)

The moral of the story is, don't resize windows too much, especially not back and forth. If you make a new vista install I'm 99% sure it will work out fine. It is not ubuntu who did the damage, although it might seem like that.

Of course installing vista will overwrite grub2 on the MBR so you need to reinstall it from live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Because the vista partition will be formatted when reinstalled (you should select to format it), after booting ubuntu run:

sudo update-grub

because the partition will have a new UUID.

It should be fine after that. It's vista that can't boot and can't repair itself, ubuntu can't help here.

---

### Post by gek0 on 2010-06-21
lol you see I had gotten quite far doing just about everything you and oldfred posted in other threads and so on to a point where Vista would not even boot at all.

The reason I formatted the 30gig partition that included Linux was because I was trying to rewrite grub properly as I clearly didn't do it the first time.  It seemed like the logic route to follow at the time, repart the drive to expand Vista to take where I had Linux, then reinstall Linux and part the drive using Gparted.  Again I thought I was onto a winner lol... I figured as the space I was resizing was empty I couldnt do much harm, so let that be a warning to people  in future.

I'm not blaming Linux at all, rather my missuse of the tools it has.

Its a shame although I havnt had to reinstall windows Vista in the 4 years its been on this PC and I have recovered it from some serious problems.

I think I initially had a wubi install then I managed to remove it and install Lucid.

I have learned quite a bit about booting though so thats a plus.

Shame on you pair for not fixing this!

---

