---
title: "Grub/boot issues after 10.10 install from USB drive"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by residualbit on 2011-01-15
I am setting up ubuntu on a new(ish) HP desktop and it has been pretty painful. My issues up until now are in this thread: [http://ubuntuforums.org/showthread.php?t=1666634](http://ubuntuforums.org/showthread.php?t=1666634)

I marked that one as solved and am starting a new one as the initial issue for starting that thread was indeed solved.

Here is where I am at now:
[http://img703.imageshack.us/i/img20110114090757.jpg/](http://img703.imageshack.us/i/img20110114090757.jpg/)

I've found that I can just type exit, sometimes, once sometimes 10 times, and ubuntu will eventually boot. My main concern is that the grub menu only appears intermittently at boot. If I hit ESC to specify a boot device, it will show up after I pick, but if I just turn the PC on, it seems to be hit or miss. Also, as an aside, when I do get the grub menu, it is version 1.9.xxxxx. Should I be using 2? 

Once in a grub menu, I follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)
and that lets me fully boot without getting the above 'gave up waiting...'error. The only problem is that this seems to only be temporary. When I reboot and get to a grub menu again, hit e to edit, it's back to what it was before....

Any insight, help, etc would be very much appreciated!

---

### Post by kansasnoob on 2011-01-15
Once you're booted into Ubuntu try just running:

```
sudo update-grub
```

> when I do get the grub menu, it is version 1.9.xxxxx. Should I be using 2? 

That's OK, grub2 is 1.9X +.

---

### Post by residualbit on 2011-01-15
When I run update-grub, it spits this out:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I'll try to reboot and see what happens...

---

### Post by residualbit on 2011-01-15
That didn't seem to make any difference. I am still having the same original problem.

---

### Post by kansasnoob on 2011-01-15
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That may provide the info needed for us to figure out what's wrong.

---

### Post by residualbit on 2011-01-15
Here is the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,905,518,591 1,905,516,544  83 Linux
/dev/sda2       1,905,520,638 1,953,523,711    48,003,074   5 Extended
/dev/sda5       1,905,520,640 1,953,523,711    48,003,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d000b731-d3ec-45fd-8377-ab21adae9455   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f1eb83dd-4b9d-451c-bfb5-4d1bcdc9c4d7   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d000b731-d3ec-45fd-8377-ab21adae9455 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d000b731-d3ec-45fd-8377-ab21adae9455 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d000b731-d3ec-45fd-8377-ab21adae9455 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d000b731-d3ec-45fd-8377-ab21adae9455 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=d000b731-d3ec-45fd-8377-ab21adae9455 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f1eb83dd-4b9d-451c-bfb5-4d1bcdc9c4d7 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 856.9GB: boot/grub/core.img
 809.8GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
   1.3GB: boot/initrd.img-2.6.35-24-generic
   1.1GB: boot/vmlinuz-2.6.35-22-generic
 856.9GB: boot/vmlinuz-2.6.35-24-generic
   1.3GB: initrd.img
    .9GB: initrd.img.old
 856.9GB: vmlinuz
   1.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by Ad@m on 2011-01-15
I have gone through your other thread and this may seem to have no logic behind it but can you set the BIOS back to raid and see what happens?

---

### Post by dino99 on 2011-01-15
as i feel you might thanks HP for their tatooed hardware: some hidden bytes inside MBR that conflict with grub. The only solution i know is a low level format to get rid of these spywares.

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by residualbit on 2011-01-15
> I have gone through your other thread and this may seem to have no logic behind it but can you set the BIOS back to raid and see what happens?

That didn't seem to make a difference. Same problem.

> as i feel you might thanks HP for their tatooed hardware: some hidden bytes inside MBR that conflict with grub. The only solution i know is a low level format to get rid of these spywares.

That's sort of what I was thinking. Their bloat-ware knows no bounds. How would I go about doing that?

---

### Post by dino99 on 2011-01-15
> **nkirk1 said:**
> That didn't seem to make a difference. Same problem.



That's sort of what I was thinking. Their bloat-ware knows no bounds. How would I go about doing that?

see the link given into the previous post, or if you have hdd tools from western digital (good one)

---

### Post by kansasnoob on 2011-01-15
I'd prefer you be patient and try some "custom" entries in "/etc/grub.d/40_custom" so we can actually troubleshoot this instead of just getting slap-happy :D

But I can only type so fast ;)

Ultimately, after some testing, we could either upgrade you to a newer version of grub2 or try downgrading you to grub legacy. I'd hope the latter would not be necessary.

I do need to see the output of this command from your installed Ubuntu if you want to try upgrading grub2:

```
uname -m
```

In fact that may be a better route than trying custom entries.

---

### Post by residualbit on 2011-01-15
haha that's fine. I'm in no rush. I will just keep the low level formatting in my back pocket as a last resort. Here's the output:

```
x86_64

```

Thanks again for your help.

---

### Post by residualbit on 2011-01-15
Also, what about the intermittently showing grub menu at boot?

---

### Post by kansasnoob on 2011-01-15
> **nkirk1 said:**
> Also, what about the intermittently showing grub menu at boot?

With only one OS the menu should always be hidden by default. I imagine the "errors" cause it to show up.

Regardless I just tried to repeat a test upgrading to the latest Natty grub2 packages and - well - there are just too many complexities!

So I'm going to type a custom menu entry for you to try and we'll go from there.

Give me a few minutes to get this right.

---

### Post by kansasnoob on 2011-01-15
Hmmm, proxy errors keep shutting me down.

Anyway, upgrading to the Natty packages is too complex ATM so try adding this entry to "/etc/grub.d/40_custom":

```
menuentry 'Custom entry' {
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d000b731-d3ec-45fd-8377-ab21adae9455
	linux	/vmlinuz root=UUID=d000b731-d3ec-45fd-8377-ab21adae9455 ro quiet splash
	initrd	/initrd.img
}
```

Do you know how to do that?

It's like:

```
gksudo gedit /etc/grub.d/40_custom

```

Then below the existing text (do not edit any existing text) copy-n-paste the above entry. Then click on Save and exit.
Then be sure to run:

```
sudo update-grub
```

That entry will end up at the bottom of the grub menu. Hopefully it will boot OK.

---

### Post by kansasnoob on 2011-01-16
Sorry to just disappear :(

I kept getting proxy errors when I was trying to post, although I do see that my last post including the sample "custom entry" did go through. Did you have a chance to try that?

Regardless I'm going to post my testing results in case it might help you or anyone else. However, *[COLOR="Red"]this is only meant as general instruction![/COLOR]* I'd hope that anyone who's unfamiliar with package management and boot-loaders would ask for specific help if any of this is even slightly confusing :)

I was too tired to do anymore yesterday after playing around in the snow and the mud but this AM I did figure out how to install the newest Natty grub2 packages in Maverick. It's a bit more complex than in the past because now when you install the "grub-common" package individually it insists on installing either "grub" or "grub-pc".

BTW in Ubuntu the package "grub" = legacy grub, and the package "grub-pc" = grub2.

Anyway I didn't want to reinstall any packages from Maverick sources but rather use only the Natty packages I downloaded here:

[http://packages.ubuntu.com/natty/grub-common](http://packages.ubuntu.com/natty/grub-common)

[http://packages.ubuntu.com/natty/admin/grub-pc](http://packages.ubuntu.com/natty/admin/grub-pc)

NOTE: It's very important that a person use the proper packages for their architecture, that's why I asked for the output of "uname -m". (64 bit users should see x86_64 and 32 bit users should see i686). I'd think it goes almost without saying that a person should normally select a mirror close to them, but these are very small downloads, I always use "mirrors.us.kernel.org/ubuntu/". I should also mention that I'm only able to test this on i686!

Anyway to work-around the dependency issue I created a folder on my desktop named "Natty_grub" and downloaded both the "grub-common" and "grub-pc" to that folder as you can see here:

```
lance@lance-desktop:~$ **ls ~/Desktop**
820-7799.pdf                  Screenshot-3.png
default.pa                    Screenshot--dev-sda - GParted.png
**Natty_grub**                    Screenshot.png
Natty updates packgs removed  sol-11-exp-201011-live-x86.iso
Screenshot-1.png              ubuntu-docs_10.10.4ubuntu0.1~ppa2_all.deb
Screenshot-2.png
lance@lance-desktop:~$ **ls ~/Desktop/Natty_grub**
[B][COLOR="Red"]grub-common_1.99~20110112-1ubuntu1_i386.deb
grub-pc_1.99~20110112-1ubuntu1_i386.deb[/COLOR][/B]

```

Clear as mud so far? I just used Firefox to download and I have it's preferences set to always ask where to plant my downloads.

From thereon the upgrade to the Natty packages went like this, first backing up and creating a new /boot/grub directory, and purging the Maverick packages:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get purge grub-pc grub-common
```

Then I changed directories (cd) to the folder containing the Natty .debs:

```
cd Desktop/Natty_grub
```

Note: you can use the "ls" command to be certain you're in the right place (example):

> lance@lance-desktop:~$ cd Desktop/Natty_grub
lance@lance-desktop:~/Desktop/Natty_grub$ ls
grub-common_1.99~20110112-1ubuntu1_i386.deb
grub-pc_1.99~20110112-1ubuntu1_i386.deb
lance@lance-desktop:~/Desktop/Natty_grub$ 


Then simply let dpkg work it's magic with a wildcard "*":

```
sudo dpkg -i *
```

Example:

> lance@lance-desktop:~/Desktop/Natty_grub$ sudo dpkg -i *
Selecting previously deselected package grub-common.
(Reading database ... 213786 files and directories currently installed.)
Unpacking grub-common (from grub-common_1.99~20110112-1ubuntu1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from grub-pc_1.99~20110112-1ubuntu1_i386.deb) ...
Setting up grub-common (1.99~20110112-1ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-pc (1.99~20110112-1ubuntu1) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu 10.10 (10.10) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu natty (development branch) (11.04) on /dev/sda17
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda3
Found Ubuntu 10.10 (10.10) on /dev/sdb1
done


Of course during the process a number of debconf messages will appear, for instance - during removal of the Maverick packages you'll be asked if you want to remove all grub packages, of course you do, so you'd use the Tab key to select Yes and then hit Enter.

While installing the new packages you'll see a number of these "messages" like, "Linux command line" which is where you'd enter any special boot parameters if needed, and "Linux default command line" which will normally show "quiet splash". Generally with both of those you'd accept the defaults and just use the Tab key to select OK and Enter to proceed.

Then you'll see a window that explains where to install grub and again you'd just use the Tab key to select OK, and Enter to proceed. The next screen will give you the choice of where to install grub, typically that will be the MBR of the drive like "/dev/sda", selections can be made using the "space bar" on the keyboard, then Tab to select OK, and Enter to proceed.

Have I confused anyone yet? Doing things myself and trying to explain them to others is obviously two very different things.

---

### Post by residualbit on 2011-01-16
I tried the custom grub entry to no avail. After that, I tried tinkering around with some other settings in grub, also to no avail. In the face of overwhelming defeat, I decided to go with the low level reformat/nuke of the drive. 16.5 hours later, I tried to reinstall 10.10 64bit from the thumb drive. Install went fine then on reboot, of course, I get the same damn error. FML.

---

### Post by residualbit on 2011-01-16
It honestly seems like grub or whatever makes the busybox message come up isn't waiting long enough for something at boot. For instance, when the initramfs prompt comes up, typing exit will get me to the login screen eventually. If I power up, get the busy box screen, and wait (maybe 15-20 seconds), i can type exit once and get right to the login screen. If I start typing exit as soon as I get to the busybox screen, I end up typing it like 15 times before it moves along to the login window. Also, like I said in the first post, when I do this:[http://ubuntuforums.org/showpost.php...68&postcount=2](http://ubuntuforums.org/showpost.php...68&postcount=2)
It boots fine, but that seems to be only temporary. Is there anyway to make that change stick?

On a side note, I noticed that if I opt to 'restart' the PC, I am having an issue there too. It shuts down, but when it powers back up, it just hangs at the intro/bios screen. If I turn it off and back on, it boots fine (until it gets to the error.) This issue doesn't happen if i just shut down and then turn it back on.

---

### Post by residualbit on 2011-01-16
I did this:
[http://www.uluga.ubuntuforums.org/showpost.php?p=9790840&postcount=4](http://www.uluga.ubuntuforums.org/showpost.php?p=9790840&postcount=4)
and now I can boot just fine. If anyone can explain the specifics of this to me, I would greatly appreciate it.

Thanks.

---

### Post by residualbit on 2011-01-16
Marking solved. This also seemed to solve my aforementioned restart issue as well. Can anyone tell why the above 'fix' actually did fix my problem(s)/what it did?

Thanks.

---

### Post by Quackers on 2011-01-16
It appears to me that you have stopped the system looking for the UUID of your /root system. Presumably it just now looks for /dev/sda1 instead. It's possible that this was causing your problem. I may be wrong though :-), maybe somebody else could confirm this - or not!
Either way, I'm glad that your problem is solved :-)

---

### Post by Quackers on 2011-01-16
This is from drs305's guide
"#GRUB_DISABLE_LINUX_UUID=true
Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
Update: A bug requires quotation symbols be added for this option to be enabled. Change true to "true" and uncomment the line to eliminate UUIDs for linux entries."

at
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by residualbit on 2011-04-08
FYI. I had the same issue after a fresh install of Natty beta 1 on the same machine. Same fix.

---

### Post by residualbit on 2011-09-04
FYI again. Same issue in 11.10. Same fix.

---

