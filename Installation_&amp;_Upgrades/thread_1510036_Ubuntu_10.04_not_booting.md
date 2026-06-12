---
title: "Ubuntu 10.04 not booting"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by sartho on 2010-06-15
Hey, I just installed Ubuntu 10.04 onto an external hdd because my internal just fried, and it won't boot. It just shows error: no usable partition, and shows grub rescue. I installed the alternate cd into a usb to try to reinstall grub, but it won't install. It says, failed to install grub, exit code 1. I can't erase the external because it has data on it that I need, so I resized it and created a partition to boot ubuntu from.

If anyone can help me, I'd greatly appreciate it.

---

### Post by sartho on 2010-06-15
Ok, I found a tutorial on how to install grub2 from a live cd and followed that. It said everything installed correctly, but when I rebooted, it said:

> error: unknown filesystem
grub rescue >

I've been searching around these forums and using google, but everyone else who has this problem has a dual boot system. I only want to install ubuntu on an external hard drive that already has important data on it formatted to ntfs.

---

### Post by darkod on 2010-06-15
From live mode run the boot info script and post the content of the results file as explained:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by sartho on 2010-06-15
Ok, I did everything it siad in the post you linked, but when I try to execute it in the terminal, it says:

```
bash: /home/ubuntu/desktop/boot_info_scriptO55.sh: No such file or directory
```I have the file on my desktop and everything. Idon't know why it is saying that.

---

### Post by darkod on 2010-06-15
Is the filename you used in the command exactly the same? Try again.

---

### Post by sartho on 2010-06-15
Ok, I tried it again. I even copied the name of the file into a txt editor to see if I was spelling it wrong, and pasted it into the terminal. It still says the same thing.

---

### Post by darkod on 2010-06-15
You did write Desktop in the command, not desktop right? As it says in the instructions. Linux is case sensitive even for file and folder names, not like windows. desktop is not the same as Desktop.

sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by sartho on 2010-06-15
Sorry, you're right, I did type desktop with lower case. I'm a relative noob in linux, so sorry.

Here is what the file says:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,523,892,545 1,523,892,483   7 HPFS/NTFS
/dev/sda2       1,523,894,272 1,531,705,343     7,811,072  82 Linux swap / Solaris
/dev/sda3       1,531,707,390 1,590,298,623    58,591,234   5 Extended
/dev/sda5       1,531,707,392 1,590,298,623    58,591,232  83 Linux
/dev/sda4    *  1,590,298,624 1,953,523,711   363,225,088  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        064C0DFB4C0DE671                       ntfs       LaCie                         
/dev/sda2        dac26d48-3f26-43a3-ba61-a396fb695bff   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        806859bc-797b-4075-9b23-31b57fa1fca2   ext4                                     
/dev/sda5        273dd919-4f94-4ff0-8494-d9f56801cde1   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/LaCie             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/273dd919-4f94-4ff0-8494-d9f56801cde1 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda4        /media/806859bc-797b-4075-9b23-31b57fa1fca2 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
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
search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
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
    search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=273dd919-4f94-4ff0-8494-d9f56801cde1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=273dd919-4f94-4ff0-8494-d9f56801cde1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 273dd919-4f94-4ff0-8494-d9f56801cde1
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
UUID=273dd919-4f94-4ff0-8494-d9f56801cde1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=806859bc-797b-4075-9b23-31b57fa1fca2 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=dac26d48-3f26-43a3-ba61-a396fb695bff none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 786.5GB: boot/grub/core.img
 800.2GB: boot/grub/grub.cfg
 786.5GB: boot/initrd.img-2.6.32-21-generic
 786.5GB: boot/vmlinuz-2.6.32-21-generic
 786.5GB: initrd.img
 786.5GB: vmlinuz

=================== sda4: Location of files loaded by Grub: ===================


 827.2GB: boot/grub/core.img
```I posted the whole thing, like it said in your post.

---

### Post by darkod on 2010-06-15
You have grub2 on the MBR of the disk but it seems it's looking at the wrong partition.

Don't use the alternate cd image for reinstalling grub2. Can you use the standard desktop image, liveCD?

Either on cd or usb stick, doesn't matter.

Boot with the Try Ubuntu option in live mode and in terminal execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should sort it out. Can't see much wrong with the results otherwise. See if it helped first.

---

### Post by sartho on 2010-06-15
Ok, I did that and it said it installed correctly so I rebooted without the live cd in, and it still wouldn't boot. It showed this error:

```
Error: no such partition
grub rescue >
```
I entered ls to see what it had as the directories, and it showed these:

```
(hd0) (hd0,4) (hd0,2) (hd0,1)
```

I tried it again and got the same result.

---

### Post by darkod on 2010-06-15
Hmmm... it saw partition #5 to install grub without errors, but it's not seeing it in your ls results.

I wonder if sda5 is corrupted somehow. Maybe if you were resizing it to make space for sda4, I don't know.

From live mode, without sda5 mounted, you can try:

sudo fsck /dev/sda5

Lets see what the check will say.

---

### Post by sartho on 2010-06-15
Ok, Here is what it said:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 137751/1831424 files, 692121/7323904 blocks

```

---

### Post by sartho on 2010-06-15
Ok, I hate double posting, but I tried reinstalling Ubuntu, and redoing the partitions, but I still get  the same error.

I retried what you said and got:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 137741/1525920 files, 673003/6103296 blocks
```

---

### Post by darkod on 2010-06-15
I'm running out of ideas. Are you sure you are booting from the usb hdd?

Did you also have dual boot on your int hdd and maybe it's trying to boot from it and reporting that error? Or the int hdd is removed completely?

The results looked good, I don't know what to say.

---

### Post by confused57 on 2010-06-15
Here's an older thread I had bookmarked for installing on an external drive:
[http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263)

It's possible the hard drive isn't spinning up fast enough, or necessary modules aren't be loaded, etc?  The instructions may not work for you, but maybe something to explore.

---

### Post by sartho on 2010-06-15
@darkod:  Yeah, I am booting from usb. I don't have any internal installed because it's messed up.

@confused57: I tried following your guide, but when I get to step 5, it asks for a password. I'm assuming it's the password I created, but when I enter it, it says "authentication failure."

---

### Post by confused57 on 2010-06-15
> **sartho said:**
> @darkod:  Yeah, I am booting from usb. I don't have any internal installed because it's messed up.

@confused57: I tried following your guide, but when I get to step 5, it asks for a password. I'm assuming it's the password I created, but when I enter it, it says "authentication failure."

The live cd shouldn't really need a password for sudo?  I believe step 5 should be:
```
sudo mount -t proc proc /mnt/ubuntu/proc
```

---

### Post by sartho on 2010-06-15
Sorry, I was mistaken. It was step 7 that asked for a password.

---

### Post by confused57 on 2010-06-15
For step 7, try using "sudo su", since you're chrooted into your Ubuntu, the password you set when you installed should work.

---

### Post by sartho on 2010-06-15
Ok, I've made it to step 9, but I'm not sure how to edit the file. Do I edit in the terminal, and if so, where do I make the edit? Sorry if this is a stupid question, but I'm pretty much a noob when it comes to linux.

---

### Post by confused57 on 2010-06-15
> **sartho said:**
> Ok, I've made it to step 9, but I'm not sure how to edit the file. Do I edit in the terminal, and if so, where do I make the edit? Sorry if this is a stupid question, but I'm pretty much a noob when it comes to linux.

Don't worry, I remember how it was when I was starting Ubuntu, I was totally lost(confused?).

Yes, you would use the terminal:
```
nano /etc/mkinitramfs/initramfs.conf
```
Then at the top of the page put:
```
WAIT=10
```
Ctrl+X, then y to save

Now you need to re-create the initrd file:
```
mkinitramfs -o /boot/initrd.img-`uname -r` /lib/modules/`uname -r`
```

The rest of the instructions were written for legacy-grub, you shouldn't need to follow them, since you're using Lucid with grub2.

I've never done the above, but you might give it a try.

---

### Post by sartho on 2010-06-16
For the third initrd file, should I copy it exactly as you have it, or substitute something for uname?

Also, I'm reinstalling Ubuntu to better follow your guide, and I was wondering where I should install the bootloader. Before I installed it on sda, but I have the option to install it on sda, sda1(ntfs data partition, sda5(root), or sda4 (home).

---

### Post by confused57 on 2010-06-16
> **sartho said:**
> For the third initrd file, should I copy it exactly as you have it, or substitute something for uname?

Also, I'm reinstalling Ubuntu to better follow your guide, and I was wondering where I should install the bootloader. Before I installed it on sda, but I have the option to install it on sda, sda1(ntfs data partition, sda5(root), or sda4 (home).

Copy & paste it exactly as I have it.  Only install the bootloader to sda.

---

### Post by sartho on 2010-06-16
I've done everything in your guide, with your additions at the end, and it still shows up, "no such partition."
The only thing I've done differently, is that in step 4 I put:

```
sudo mount /dev/sda5 /mnt/ubuntu
```

I did this because you had sdb1 as your root, and that is my root. Should I have changed it to something different? Also, when I put in what you told me in step 10, nothing happens, except that it takes a few seconds to go to the next prompt.

---

### Post by confused57 on 2010-06-16
> **sartho said:**
> I've done everything in your guide, with your additions at the end, and it still shows up, "no such partition."
The only thing I've done differently, is that in step 4 I put:

```
sudo mount /dev/sda5 /mnt/ubuntu
```

I did this because you had sdb1 as your root, and that is my root. Should I have changed it to something different? Also, when I put in what you told me in step 10, nothing happens, except that it takes a few seconds to go to the next prompt.

You're correct to change it to /dev/sda5, about the only other thing you could try is to increase the WAIT to something like 20.

If you have another computer handy, you could burn a copy of Super Grub Disk:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
I'm out of ideas on anything to try, but if increasing the WAIT doesn't work, I definitely recommend trying Super Grub Disk.

Also, you might start a new thread & place something like "Can't boot 10.04 external usb install" in the subject line, with a reference to this thread.  Maybe someone who's had the problem & was able to find a solution will see it.

Added:  You could also try plugging your usb drive into another usb port on your pc.  I know this sounds pretty "off-the-wall", but won't hurt to try.

---

