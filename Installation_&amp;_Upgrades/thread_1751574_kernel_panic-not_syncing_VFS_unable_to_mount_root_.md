---
title: "kernel panic-not syncing: VFS: unable to mount root fs on  unknown block(0,0)"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by asynchronous13 on 2011-05-06
After upgrading to 10.04 LTS, I get the following error and the computer does not boot.

```
kernel panic-not syncing: VFS: unable to mount root fs on 
unknown block(0,0)
```

This is an older laptop, a Dell Inspiron 8600. It's been running Ubuntu since 8.xx, with periodic updates. 

The computer boots from a live CD without trouble. The hard drive appears to be completely fine, no problems mounting it while running from the live cd.

I set up a chroot on the existing drive, updated the installed programs (apt-get update && apt-get upgrade), and tried to get grub to install to the drive. grub-install ran and exited with the message that no errors had occurred. 

After reboot:
```
kernel panic-not syncing: VFS: unable to mount root fs on 
unknown block(0,0)
```

So, no change. I noticed that /boot/grub/grub.cfg has "set root='(hd0,1)'", but the only bootable partition is /dev/sda1 . should that correspond to root='(hd0,0)' ?

any tips or ideas would be appreciated.

---

### Post by drs305 on 2011-05-06
The hard drive designation is correct for the way Grub 2 accounts for things.

At the Grub menu (hold SHIFT if you don't see it), press 'c' to get to the command prompt. Type the following to see what Grub2 can find:
```
ls # Should show your drives and partitions hd0,1=sda1
ls (hd0,1)/ # Should include 'vmlinuz' and 'initrd'
ls (hd0,1)/boot/grub # Should see a lot of *.mod files

```

From a LiveCD, if you can download the boot info script from the following site it can tell us a lot about your boot files. Run the script, then post the contents of RESULTS.txt.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

PS. The next time you boot, you might want to check the BIOS to see what size it reports for your hard drive. If it displays something considerably less than your actual drive size, that could be a problem.

---

### Post by asynchronous13 on 2011-05-06
> **drs305 said:**
> The hard drive designation is correct for the way Grub 2 accounts for things.

At the Grub menu (hold SHIFT if you don't see it), press 'c' to get to the command prompt. Type the following to see what Grub2 can find:
```
ls # Should show your drives and partitions hd0,1=sda1
ls (hd0,1)/ # Should include 'vmlinuz' and 'initrd'
ls (hd0,1)/boot/grub # Should see a lot of *.mod files

```

From a LiveCD, if you can download the boot info script from the following site it can tell us a lot about your boot files. Run the script, then post the contents of RESULTS.txt.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

PS. The next time you boot, you might want to check the BIOS to see what size it reports for your hard drive. If it displays something considerably less than your actual drive size, that could be a problem.

Here's the RESULTS.TXT
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   617,611,263   617,609,216  83 Linux
/dev/sda2         617,613,310   625,141,759     7,528,450   5 Extended
/dev/sda5         617,613,312   625,141,759     7,528,448  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c96227eb-1464-41db-bba1-867e0ceed96d   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0ec0e0b6-d685-41e6-921c-4d453a0ecb47   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/c96227eb-1464-41db-bba1-867e0ceed96d ext4       (rw,nosuid,nodev,uhelper=udisks)

```

I'll check the BIOS on the next reboot -- seems odd that an upgrade would change bios settings though. Will also try the grub menu. thanks for the ideas.

---

### Post by drs305 on 2011-05-06
Try this. Grub is looking in /boot/boot/grub instead of /boot/grub. If the files are intact, this might be all that is required.

From a LiveCD:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not put the partition number in the second command.
Reboot.

Note: the upgrade wouldn't have changed the BIOS, but for some older motherboards it could move the boot files outside the disk area seen by BIOS and Grub. I don't think that is your situation.

---

### Post by asynchronous13 on 2011-05-06
> **drs305 said:**
> Try this. Grub is looking in /boot/boot/grub instead of /boot/grub. If the files are intact, this might be all that is required.

From a LiveCD:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not put the partition number in the second command.
Reboot.

Note: the upgrade wouldn't have changed the BIOS, but for some older motherboards it could move the boot files outside the disk area seen by BIOS and Grub. I don't think that is your situation.

Progress! sort of. That time I got a grub menu prompt automatically instead of the previous error.

all of the "ls" commands checked out appropriately.

BIOS indicates 130GB or so. It is a 320GB drive (it's been running like this for a couple of years now)

You might have found my mistake, I'm pretty sure I used --root-directory=/mnt/boot last time. Will try again!

---

### Post by asynchronous13 on 2011-05-06
Holy cow, I think this whole thing could be summarized with "I didn't know to use <shift> to get the grub menu." 

Ran grub-install again and after reboot got back to the same error as before. Shift key on bootup brought up the grub menu immediately. My computer chokes on kernel 2.6.32-29. Now that I can get the boot menu, it's easy to pick an older one that works. It turns out that I could have done that at any time. Ugh.

(and wouldn't you know it, update manager wants to install a new kernel!)

thanks for the help! will mark solved.

---

### Post by drs305 on 2011-05-06
> **asynchronous13 said:**
> BIOS indicates 130GB or so. It is a 320GB drive (it's been running like this for a couple of years now)

The RESULTS.txt was incomplete, but that could be because it couldn't find the files in /boot. It's only important in that if your BIOS only sees 137GB and your /boot files end up past that point, your boot will fail. If I could have seen the normal RESULTS.txt I would have checked to see if your Ubuntu partition is within the first 137GB of the disk. That's the easiest way to ensure the BIOS limitation never affects your Ubuntu boot.

---

### Post by jiapei100 on 2013-01-04
I met exactly the same issue.
I'm actually building a system using LFS. However, I've got no idea how to produce a initrd, but I've already built a vmlinuz ... Is it a must to build my own initrd? How to produce such a file?


Cheers
Pei

---

### Post by drs305 on 2013-01-05
Pei,

It would be best to start your own thread, as this one is pretty old and you probably won't get many viewers of your post. 

I'm not sure exactly what you are asking, but in general you can rebuild an initrd.img by running the following command, replacing the [COLOR="DarkRed"]kernel version[/COLOR] with the one you want to update:

```
sudo update-initramfs -c -k [COLOR="DarkRed"]3.2.0-35-generic[/COLOR]
```

---

### Post by ager-wick on 2013-01-07
I know this is an ancient thread, but I just got this error message today upon rebooting a server. For the benefit of others who may have gotten it for the same reason, the cause was very simple: the /boot partition was out of disk space!

So all I did to fix the problem was:
- hold down shift while booting so the grub menu shows up
- boot using another kernel (not the first one)
- check if you're out of disk space on /boot using
```
df
```
Look for the line that ends in "/boot". Mine said something like this:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
...
/dev/sda1               233191    233191         0 100% /boot
```
- check which linux images are installed using:
```
dpkg --get-selections | grep linux-image-
```
- chech which one you're using now: ```
uname -a
```
- uninstall a bunch of the oldest ones (but leave a few just in case - including the one you used to boot!). You can do this using ```
sudo apt-get remove linux-image-
``` then just press tab to get a list of the installed images, type the next digit(s) and press tab again to autocomplete.
- also uninstall the last one (the one that failed) and install it again after all the old ones have been uninstalled)
- before uninstalling make absolutely sure you're not uninstalling the one you're currently using! The reason is that you may want to boot again using that kernel, if everything doesn't work out.
- reboot and see if it works (it did for me).

---

### Post by da_g_bomb on 2013-01-27
Nice solution ager-wick,

I got the same error from the boot partition being full.

In the past I have free'd up some space, by manually deleted images or moving them out of the boot partition, but using apt-get to remove them seems much better.

When I checked the images I had, still had a lot of 2.6.28 and 2.6.31 images, which I got rid of.

I still have about 15 2.6.32 images which I should clear out at some point, but getting rid of the oldest ones free'd up enough space for the system to boot again.

---

### Post by OldestUbunterFr45 on 2013-06-29
One simpler solution
If you use grub before grub2, go in /boot/grub/device map  : change  (hd0) /dev/hda in /dev/sda
and so  on for hd1 
go in /boot/grub/menu.lst : change every line which  contains hda1 in sda1 , and so on, save the file

This solution comes from using vmlinuz in Puppy 4.3.1  which works with sda and PartedMaic which works with hda
when configuring  by grubconfig so When I  restart the linux Puppy I got the error message:)
 You  can also  change these values when entering "e" on grub line at boot

It was a pleasure and no reinstall neither kernel version in my  case

---

### Post by lejf-rossi on 2014-03-19
Sorry to keep this going, but I'm having the same issue as above, I checked the disk usage and its on the order of 8% used for the boot drive.

I did the boot info scrypt, and I that I have no grub.

Here is a link to the full results file (no sign in required): [https://drive.google.com/file/d/0B7y25NiPomFuajk0cE9JQVduZTA/edit?usp=sharing](https://drive.google.com/file/d/0B7y25NiPomFuajk0cE9JQVduZTA/edit?usp=sharing)

On the top it says this:

[COLOR=#000000][FONT=Courier New]=> No boot loader is installed in the MBR of /dev/sda.[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]=> No known boot loader is installed in the MBR of /dev/sdb.
[/FONT][/COLOR]

I've been in grub, so its there, why isn't it showing up?

Thanks in advance for any help.

---

