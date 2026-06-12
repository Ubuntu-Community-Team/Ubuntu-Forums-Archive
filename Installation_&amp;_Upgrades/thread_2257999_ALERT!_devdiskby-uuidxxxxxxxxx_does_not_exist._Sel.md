---
title: "ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Self Inflicted."
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by RobertoRecordo on 2014-12-24
By self inflicted I mean:

1)   ~~~~ 08:44:25  Monday 22 December 2014 ~~~~ 
Damn. I don't really know what is going on with [edit typo] 14.04. I still see warnings that root only has 0 bytes disk space: is this new since I did an update this AM?

2) ~~~~ 12:54:03  Tuesday 23 December 2014 ~~~~ 
Trying to reduce the size of /, clearing out old kernel remnants seems to be a good idea. The typical caveat is to keep 1-2 kernal version back, but wtf, out with the old.

3) ~~~~ 13:22:12 PM   Tuesday 23 December 2014 ~~~~
I attempted to improvise while following some forum directions to clear out the old kernels 
```
    apt-get purge linux-image-3.13*
    apt-get purge linux-headers-3.13*
```
so I screwed up and deleted linux-image-3.13.0-43-generic  ACTIVE KERNEL!!!

4) ~~~~ 14:12:58 PM   Tuesday 23 December 2014 ~~~~
Before I rebooted (wait, I only restarted from suspend - not out of the woods until I reboot) I did a 
   ```
 sudo apt-get install --reinstall linux-image-3.13.0-43-generic
```
which seems to have restored that which was blown away.

5) ~~~~ 15:36:28 PM   Tuesday 23 December 2014 ~~~~ 
Reboot the system and start damage assesment:
        - Normal boot hangs with a grey screen. 
        - Attemping to boot from the Advanced Boot Options earlier Kernal (3.5) goes as far as displaying the background image.
     I can open a console and look at the filesystem, so the kernal is running.
        - My Ubuntu 14.04 live DVD goes as far as displaying the background image.
        - I can get a system with Ubuntu 12.04.2 desktop amd 64 Live DVD

My filesystem looks like:
```
sudo fdisk -l
[sudo] password for rob: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7151

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1953791      975872   83  Linux
/dev/sda2         1955838   439453695   218748929    5  Extended
/dev/sda5         1955840    17577983     7811072   83  Linux
/dev/sda6        17580032   173828095    78124032   83  Linux
/dev/sda7       173830144   408203263   117186560   83  Linux
/dev/sda8       408205312   439453695    15624192   82  Linux swap / Solaris
```

na dthe UUID's are revealed:
```
sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 12.04.2 LTS amd64" TYPE="iso9660" 
/dev/sde1: UUID="4b2a5548-1adb-49a9-a71e-b9cb04fc4f23" TYPE="ext4" 
/dev/sde5: UUID="98b26601-cad0-4df1-9fb3-e9efcdbc1d65" TYPE="ext4" 
/dev/sde6: UUID="d8116778-908c-4b72-b26d-e915ceae2724" TYPE="ext4" 
/dev/sde7: UUID="1317962a-e829-4e6c-8041-6aa4073398e0" TYPE="ext4" 
/dev/sde8: UUID="e7d189c6-a9d0-4849-bbc2-812a49923b3c" TYPE="swap" 
```

What seems noteworthy ( although  I don't understand it) is that the UUID starting with 98b26601 is the one that the boot process claimed to be non existent. After booting the live CD I was able to see the partitions using gparted, and in a terminal I could mount and access sde[1,5,7] - I didn't try the others. Does this tell us something about how far the boot process got?

The good news is the computer is not my main system and is backed up well enough and so I am not freaked out. I actually see this as an opportunity because I am working to get up the learning curve after 4 years of being a Linux user. So I am willing to spend more time trying to learn while I rescue this system, rather than wiping it and starting over.

I have spent most of the day trying various fixes ( and carefully following [http://askubuntu.com/questions/516217]("http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell")  ) while trying to discover why the system won't boot, but most of the posts are a result of installation problems not sabotage by the system administrator. 

Can anyone give me some ideas of what may be missing, or that nees to be updated/re-installed/purged ?

Thanks -Rob

---

### Post by Bucky Ball on 2014-12-24
Forget 10.04 LTS. No longer supported. Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730"). 

Excuse my ignorance, but what is your actual support question? There is a lot of information, but to me at least, it is not clear what you want help with. Are you trying to install 14.04 LTS, 12.04 LTS? ;)

---

### Post by RobertoRecordo on 2014-12-24
I am trying to recover from accidentally purging my active kernal. I did a typo when I wrote 10.04: the system is 14.04 - I am editing the original.

I can not get the live dvd for 14.04 to boot - (video problem), I am using 12.04 for diagnostics.

My support question is "please help me debug this" Please tell me what diagnostics can be used to discover if this is a grub problem or .. what? 

Thank you - Rob

---

### Post by oldfred on 2014-12-24
I would rather you had a working live installer of 14.04. Always best practice to have working repair DVD or flash drive of the current version of every system you have installed.

Can you add nomodeset or other boot parameter to get  14.04 to boot? I have nVidia card and always had to use nomodeset on live installer and first boot or until I install nVidia driver.

Have you tried waiting a few seconds and press enter after error?

But best to see details. While the auto fix from Boot-Repair ususally works, it occasionally makes things worse.
So better if someone reviews summary report before running fixes.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What brand/model system and what video card/chip do you have? How much RAM?
Is BIOS set to boot in AHCI mode for drive not IDE nor RAID?

        SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=2255888](http://ubuntuforums.org/showthread.php?t=2255888)
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

---

### Post by RobertoRecordo on 2014-12-24
Mr. OldFred -

Thank you for the detailed "to do " list. Yes, the issue with the 14.04 live DVD is no doubt a video issue, I will pursue that.
I have seen references to "LVM, GPT, separate /boot and UEFI" but I do not know anything - I will do some research.
The drive is sata, and I think the disk is being read because the boot process gets far enough along to display my custom background.
Trusty Tahr
AMD Athlon 64 x2 Dual Core 4800+
Asus M2N-MX SE
NVidia 430 GForce 6100
4Gb memory

I think I went over most of "SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist " (gate this thread a similar title), but it is worth going over again.
Finally  &#8220;apt-get upgrade&#8221; did not seem to solve all of my problems: are there files I should purge before attempting it again?

This being Christmas Eve, I am planning family time in the next day, so it will probably be Friday before I report back.

Regards,
Rob

---

### Post by oldfred on 2014-12-24
The reference to LVM, gpt, etc is just that Boot-Repair works with all those configurations. You do not need to worry about those unless you have it.

If using nVidia you need nomodeset in most cases on Live installer and first boot after install.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by RobertoRecordo on 2014-12-27
After booting with my 14.04 live DCD (setting nomodeset in bootloader) I ran boot-repair the results are in [http://paste.ubuntu.com/9628089/](http://paste.ubuntu.com/9628089/)


The system does not boot with the latest kernel  3.13.0-43-gneric, but does boot as far as the user login when I run 13.5.0.51-generic.




I am still bothered by the error message that appears when boot fails
"Alert! /dev/disk/by-uuid/98b26601-cad0-4df1-9fb3-e9efcdbc1d65 does not exist.
Dropping to shell!"
 
This is the root directory (sda5 on my sywtem) and it can be found by fdisk, mounted and read in the console.


I am going to move on to reading and the links that oldfred suggested  regarding "How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot"


Please let me know if the boot-repair the results suggest a solution.


-Rob

---

### Post by Bucky Ball on 2014-12-27
> **RobertoRecordo said:**
> 
"Alert! /dev/disk/by-uuid/98b26601-cad0-4df1-9fb3-e9efcdbc1d65 does not exist.


Looks like the UUID for that partition in fstab is wrong. Maybe try:

```
sudo blkid
```

... and check.

---

### Post by oldfred on 2014-12-27
When you have a separate /boot partition, the set root entry or search default in fstab is the /boot partition and the linux line root= is the UUID of the / (root) partition. Your UUIDs look correct.

Because you also have a /usr partition, I am not sure if boot repair works correctly. All system partitions must be mounted when reinstalling grub. But not sure if yours is critical to reinstall or not.  And Boot repair mounts / (root) and if checked will also mount /boot. But any other special configuration with added partitions will not work. You then have to chroot into install and manually mount all system partitions.
Generally better to just have / (root) for most desktop installs.

Do you have BIOS set to AHCI? not IDE, nor RAID nor any other setting?

Sometimes just a simple entry works. We can just try adding a very simple boot stanza to 40_custom and see if it boots. It will be at bottom of grub menu. Since you have several kernels which should be housecleaned out, your may have to scroll down to see new entry. Just copy into 40_custom:

 gksudo gedit /etc/grub.d/40_custom

```
menuentry "Test boot " {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
```

---

### Post by RobertoRecordo on 2014-12-30
Forum Reply 20141230
~~~~ 10:03:55 AM   Tuesday 30 December 2014 ~~~~ 

Thank you Bucky Ball & oldfred for your suggestions. I have been slow to get back to you, but have been working on this problem, reading about the boot process and getting more familiar with grub.

From my notes:
"Today I followed some links sent by oldfred. In
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)   #3
Stewart said "You should be able to boot using the old kernel and then run the sudo update-initramfs –u -k command. Then run sudo dpkg –reconfigure."

First, this system is now running Grub 2.02 ~ Beta2-9ubunt1. I don't know if it was always so, or if it got changed during this endless debug exercise.
Kernels 3.43 and 3.11 will not boot, they error out. But 3.5 boots (I do not have to set "nomodeset") to login, and I can open a console ctrl-alt-F1
So, I tried the suggested "fix".
F1$ update-initramfs –u -k all
F1$ sudo dpkg –reconfigure -a

Kernel 3.-13.0-43 complains that "ca-certificates is broken or not fully installed".** No drives are mounted.**

Kernel now 3.11.0-22 boots to login prompt, but I could not enter any password. I selected "guest session", but decided to power down and retry.
 Booted kernel 3.11.0-22, got to the login prompt, I entered my password, and it goes to my normal background. I can't open a terminal with Ctrl-alt-t or Ctl-Shift-T, and Unity is not running. **All drives are mounted.**
I am able to open a console, so I think that I can make more progress using it."

I also tried ```
sudo service lightdm restart
``` but that didn't do anything for me.

What do you suggest I do next? Post the contents of /etc/fstab ?
In one of the links oldfred commented "When you chrooted into system, did you do a full un-install/reinstall of grub and update kernel?"
No, I have not done that. Grub is working enough to get me to log in, should I try
```
sudo apt-get update sudo apt-get install ubuntu-desktop
```

Regards,

Rob

---

### Post by RobertoRecordo on 2014-12-30
I tried oldfreds suggestion

gksudo gedit /etc/grub.d/40_custom 

     Code:
     ```
menuentry "Test boot " {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
```

I have no gui;) so I did this in nano, I noticed that sda5 was mounted. Also, the newest kernal still will not get to login during boot: I am using an older kernal that will go through login, and let me use ctrl+alt+F1 .

This did not change anything. BTW, why do we want "quiet splash" when we are debugging?

Now I have to go cut wome firewood -It's cold in California!

-Rob

---

### Post by oldfred on 2014-12-30
I think the reference to older kernel is still in the same version of Ubuntu or versions of 3.13.xx. You should have housecleaned out previous versions of kernels after you have upgraded. They may have other conflicts with the rest of system being newer.

Yes better without quiet splash, I just happened to post a standard entry.

---

### Post by RobertoRecordo on 2014-12-30
oldfred -
Yes, I am booting Ubuntu 14.04 when I select kernel 3.5.x-x 

Also, I forgot to mention that six months ago when I upgraded 12.10 => 13.10 I was greeted with a black screen and a message: ubuntu ext4-fs error (device dm-0): hdtree_dirblock_to_tree:920
Fixed by
 ```
sudo dpkg-reconfigure -a
```

I will not be surprised if I have to repeat that. But for now  I do not have a blank screen, just no Unity.


Can you please comment on my questions at the bottom of #10 in this thread?

-Rob

---

### Post by oldfred on 2014-12-30
You should not need to reinstall desktop as that is the entire GUI system and all the programs.

But you can totally uninstall grub and reinstall it. Boot-Repair can help with that.

Or you can chroot into your system.
       drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Include this when chrooted:

 # uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

---

### Post by RobertoRecordo on 2015-01-06
I continue to work on this problem, even as I spend time trying to get  familiar with grub and doing everything from the command line.

> **oldfred said:**
> 

Sometimes just a simple entry works. We can just try adding a very simple boot stanza to 40_custom and see if it boots. It will be at bottom of grub menu. Since you have several kernels which should be housecleaned out, your may have to scroll down to see new entry. Just copy into 40_custom:

 gksudo gedit /etc/grub.d/40_custom

```
menuentry "Test boot " {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
```

The above creates a new menuentry, but when I select it from the grub boot menu, it immediately goes to a gray screen, ctl-alt-del does not even work! I suppose that it is diagnostic, but I don't understand what I have learned. How would I know if the problem is not a typo in the script?


-Rob

---

### Post by oldfred on 2015-01-07
remove quiet splash and perhaps add nomodeset since you have an old nVidia.

With my nVidia cards I always had to use nomodeset until I installed the proprietary nVidia driver. You will need a legacy driver. Which should be in Ubuntu repository. Look in system settings, either drivers with 12.04 or other Software and drivers tab.

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by RobertoRecordo on 2015-01-08
Progress? maybe... Update Follows:

I followed the procedure in 
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And I didn't see anything unusual when I went through the steps. At the end, when I ran update-grub, I saw the files listed for the 3 kernels that I have in my system. 
I rebooted, and now can only get a grub CLI, so back to the 14.04.1 and64 desktop DVD live session to investigate.

I am still trying to use a separate boot partition ( I intend to put two more distros on this system).
I found the familiar files on sda1:
```
$ ls /media/ubuntu/4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
abi-3.11.0-22-generic         lost+found
abi-3.13.0-43-generic         memtest86+.bin
abi-3.5.0-51-generic          memtest86+.elf
config-3.11.0-22-generic      memtest86+_multiboot.bin
config-3.13.0-43-generic      System.map-3.11.0-22-generic
config-3.5.0-51-generic       System.map-3.13.0-43-generic
grub                          System.map-3.5.0-51-generic
grub_backup                   vmlinuz-3.11.0-22-generic
initrd.img-3.11.0-22-generic  vmlinuz-3.13.0-43-generic
initrd.img-3.13.0-43-generic  vmlinuz-3.5.0-51-generic
initrd.img-3.5.0-51-generic
```
But I did find a boot partition on sda5, which was not there before.
```

sudo ls /media/ubuntu/98b26601-cad0-4df1-9fb3-e9efcdbc1d65/boot
grub  initrd.img-3.13.0-43-generic
```

I am posting the results of bootinfoscript, hoping it will be useful.



```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 368480 of the same hard drive for 
                       core.img. core.img is at this location and looks in 
                       partition 112 for .
    Operating System:  
    Boot files:        /grub/grub.cfg

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,953,791     1,951,744  83 Linux
/dev/sda2           1,955,838   439,453,695   437,497,858   5 Extended
/dev/sda5           1,955,840    17,577,983    15,622,144  83 Linux
/dev/sda6          17,580,032   173,828,095   156,248,064  83 Linux
/dev/sda7         173,830,144   408,203,263   234,373,120  83 Linux
/dev/sda8         408,205,312   439,453,695    31,248,384  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4b2a5548-1adb-49a9-a71e-b9cb04fc4f23   ext4       
/dev/sda5        98b26601-cad0-4df1-9fb3-e9efcdbc1d65   ext4       
/dev/sda6        d8116778-908c-4b72-b26d-e915ceae2724   ext4       
/dev/sda7        1317962a-e829-4e6c-8041-6aa4073398e0   ext4       
/dev/sda8        e7d189c6-a9d0-4849-bbc2-812a49923b3c   swap       
/dev/sr0                                                iso9660    Ubuntu 14.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/4b2a5548-1adb-49a9-a71e-b9cb04fc4f23 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda5        /media/ubuntu/98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda6        /media/ubuntu/d8116778-908c-4b72-b26d-e915ceae2724 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda7        /media/ubuntu/1317962a-e829-4e6c-8041-6aa4073398e0 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  98b26601-cad0-4df1-9fb3-e9efcdbc1d65
else
  search --no-floppy --fs-uuid --set=root 98b26601-cad0-4df1-9fb3-e9efcdbc1d65
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    else
      search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    fi
    linux    /vmlinuz-3.13.0-43-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.13.0-43-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /vmlinuz-3.13.0-43-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /vmlinuz-3.13.0-43-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-22-generic-advanced-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.11.0-22-generic ...'
        linux    /vmlinuz-3.11.0-22-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-22-generic-recovery-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.11.0-22-generic ...'
        linux    /vmlinuz-3.11.0-22-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-51-generic-advanced-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.5.0-51-generic ...'
        linux    /vmlinuz-3.5.0-51-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.5.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-51-generic-recovery-98b26601-cad0-4df1-9fb3-e9efcdbc1d65' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        else
          search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
        fi
        echo    'Loading Linux 3.5.0-51-generic ...'
        linux    /vmlinuz-3.5.0-51-generic root=UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.5.0-51-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    else
      search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    else
      search --no-floppy --fs-uuid --set=root 4b2a5548-1adb-49a9-a71e-b9cb04fc4f23
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_oldfred ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry  "Test Boot (oldfred)" {
    set gfxpayload=keep
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda5 ro nomodeset
        initrd /initrd.img
}


### END /etc/grub.d/40_oldfred ###

### BEGIN /etc/grub.d/40old_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry  "Test boot" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}


### END /etc/grub.d/40old_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=98b26601-cad0-4df1-9fb3-e9efcdbc1d65 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
#UUID=4b2a5548-1adb-49a9-a71e-b9cb04fc4f23 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=d8116778-908c-4b72-b26d-e915ceae2724 /home           ext4    defaults        0       2
# /usr/local was on /dev/sda7 during installation
UUID=1317962a-e829-4e6c-8041-6aa4073398e0 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=e7d189c6-a9d0-4849-bbc2-812a49923b3c none            swap    sw              0       0
UUID=4b2a5548-1adb-49a9-a71e-b9cb04fc4f23    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e3 d5 69 94 1f 6c 49 0e  ad 7f 0c f9 aa af 64 4d  |..i..lI.......dM|
00000010  dc 84 93 03 ef 2b f3 0e  b3 bb 2f 9e b3 49 08 9e  |.....+..../..I..|
00000020  ad 9b 32 ee c9 40 5f e5  5e 6c fb 41 f6 87 f1 1e  |..2..@_.^l.A....|
00000030  d0 ca db f4 b2 b3 ef f8  d1 4b 1d 66 0c 77 dd 92  |.........K.f.w..|
00000040  c7 33 1d 78 e4 04 fd 7a  b0 c6 e8 ec 37 8e 3e ac  |.3.x...z....7.>.|
00000050  a3 00 65 70 25 41 f5 c3  ac 86 f9 fb 8b f3 14 56  |..ep%A.........V|
00000060  72 4a f9 ce e6 35 cd 29  f8 13 fa e9 ed 86 2d 19  |rJ...5.)......-.|
00000070  bb 3d 07 5c 7e b7 dc 42  5e 08 d7 49 1f 74 75 82  |.=.\~..B^..I.tu.|
00000080  5c 00 00 00 00 4e dc 07  00 00 ba 2a 00 00 00 00  |\....N.....*....|
00000090  01 00 00 00 00 00 00 00  ff ff ff ff ff ff ff ff  |................|
000000a0  ff ff ff ff ff ff ff ff  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 5a 09 00 00  d5 00 69 01 00 00 00 00  |....Z.....i.....|
000000c0  00 00 00 00 00 00 00 00  41 00 00 00 00 00 00 80  |........A.......|
000000d0  00 00 01 00 dc 07 0d e6  36 1f 70 50 84 62 d5 d8  |........6.pP.b..|
000000e0  fd fe 27 5a c9 87 28 f5  3e d5 9e 02 da b9 f5 c2  |..'Z..(.>.......|
000000f0  b4 e6 c7 b9 f7 3f ee a6  c9 1e 4f 7b d3 ef b2 38  |.....?....O{...8|
00000100  d6 ff 1c b0 bb 90 5e c0  6a c4 ea ac 9b f4 ec b1  |......^.j.......|
00000110  8c df 28 4d e8 13 ff 43  3a d9 6e 46 bc de d8 6a  |..(M...C:.nF...j|
00000120  d5 9b 70 bb 7f 29 d0 bd  f2 71 eb 34 f8 70 0e 27  |..p..)...q.4.p.'|
00000130  5c 6c db ed bf 0b ba 00  55 1b e6 e9 30 fc 22 b3  |\l......U...0.".|
00000140  e2 dc 5f b9 ed f9 5b af  0e 55 35 fa e1 ed 80 35  |.._...[..U5....5|
00000150  19 f7 cd f6 fd b3 73 87  de 64 0a f2 50 6e 3d 4d  |......s..d..Pn=M|
00000160  f6 12 ab 40 09 c9 5d 96  a5 9f f2 af 5c 01 a9 79  |...@..].....\..y|
00000170  1f ba d9 4f c4 3d cf d5  ee 8f 5c 7c b1 5b 27 2d  |...O.=....\|.['-|
00000180  ff 5f e3 eb 8a 64 23 a7  6c b3 05 ab 35 c6 4f d8  |._...d#.l...5.O.|
00000190  37 2f a8 89 76 4a d9 2a  51 3e e1 46 b9 6d e2 b8  |7/..vJ.*Q>.F.m..|
000001a0  47 d9 bf dd 2f 75 11 c9  7c f6 19 dc 89 6d 2d 1c  |G.../u..|....m-.|
000001b0  94 bd f2 4e ea 1c d6 e0  18 86 27 a3 ee fb 00 be  |...N......'.....|
000001c0  06 79 83 fe ff ff 02 00  00 00 00 60 ee 00 00 fe  |.y.........`....|
000001d0  ff ff 05 fe ff ff 02 60  ee 00 00 30 50 09 00 00  |.......`...0P...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-TC9WyJpx/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-TC9WyJpx/Tmp_Log: No such file or directory
  No volume groups found
```

I don't know what to do next, except to look on the forums for solutions to "grub boots to command line interface"

**edit Post: **tried this from grub CLI```
grub> set root=(hd0,1)
grub> linux /vmlinuz-3.13.0-43-generic 
grub> initrd /initrd.img-3.13.0-43-generic
grub> boot
```

failed 
"cant read '/etc/fstab' "
"mount: mounting /def or /root/dev failed : no such file or directory"
"Target filesystem doesn't have requested /sbin/init"
"Try passing init=bootarg"

Regards,

-Rob

---

### Post by oldfred on 2015-01-09
If you really want separate /boot partitions, you must have one for each install, otherwise you get massive conflicts.

With manual boot better to use links. If you use the specific kernel it is in /boot not /.

 Separate /boot on sda1, / on sda5:
grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,5)
grub> linux (hd0,1)/vmlinuz-3.13.0-43-generic root=/dev/sda5 ro
grub> initrd (hd0,1)/initrd.img-3.13.0-43-generic
grub> boot


If you have boot files in a /boot folder in the / , then one update was done without mounting the /boot partition. When you chrooted, did you also mount the /boot?

Better to use this or Boot-Repair's Summary report which also uses this version:
 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

