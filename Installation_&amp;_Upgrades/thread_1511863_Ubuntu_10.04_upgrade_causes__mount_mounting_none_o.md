---
title: "Ubuntu 10.04 upgrade causes:  mount: mounting none on /dev failed: no such device"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by l0uismustdie on 2010-06-17
I posted a similar problem sometime last week...but a little has changed(mainly I can access my files now):

I recently performed the auto upgrade to Ubuntu 10.04 and upon  restart of my machine I am presented with 3 screens.  The first is a  simple "GRUB loading".  The second is "mount: mounting none on /dev  failed: no such device".  The third screen is a series of  initializations, i.e. /dev/sda1: clean, (number of files), (number of  blocks)
*setting preliminary keymap...
and so on until it hits the line:
*checking battery status
at which point it will cease loading until i press the power button.   The next thing that occurs is it kills all the processes it just  initialized and shuts down the computer.

I read that this is likely a problem from loading the wrong kernel and I can get into my files (using a boot 9.10 boot key).  The problem is I don't know what files to change in order to get my system booting the right kernel.

Thanks in advance,
Josh

---

### Post by u01p2109 on 2010-06-17
After Upgrade You should run $sudo grub-install /dev/sda
But You didn`t.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Switching%20to%20ext4%20requires%20manually%20updating%20grub](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Switching%20to%20ext4%20requires%20manually%20updating%20grub)

---

### Post by l0uismustdie on 2010-06-17
Unfortunately this doesn't fix my problem.  Since I can no longer directly log on to my machine I have to boot from a floppy and mount my drive from there.  Upon running the command:
sudo grub-install /dev/sda
I am presented with the error:
grub-probe: error: cannot find a device for /boot/grub

No path or device is specified
When I look at the grub-probe --help it states that grub-install copies GRUB images into the DIR/boot directory.  So, even when I try to mount my drive to / this still doesn't work.  

Any other takers?

---

### Post by leorolla on 2010-06-17
Maybe using the chroot trick from the GRUB2 tutorials will help.

---

### Post by Penguin Guy on 2010-06-17
> **l0uismustdie said:**
> Unfortunately this doesn't fix my problem.  Since I can no longer directly log on to my machine I have to boot from a floppy and mount my drive from there.  Upon running the command:
sudo grub-install /dev/sda
I am presented with the error:
grub-probe: error: cannot find a device for /boot/grub?
That's because you're inside a chroot. Try binding the system folders you need:
```
mount --bind /dev /mnt/chroot/dev
mount --bind /proc /mnt/chroot/proc
```

---

### Post by l0uismustdie on 2010-06-17
I'm still a little confused here what all of you are trying to get at.  So here is what I just tried:
sudo mount /dev/sda1 /mnt 
sudo mount --bind /dev /mnt/chroot/dev
mount: mount point /mnt/chroot/dev does not exists

Which makes sense...what am I trying to bind?
I also tried:
sudo mount --bind /boot /mnt/boot
sudo grub-install /dev/sda

This resulted in the same error.

Thanks for all your replies.

---

### Post by darkod on 2010-06-17
Hold on, stop for a moment.

1. You don't chroot that way, the commands are incomplete.

2. What are you actually trying to do? Obviously you have grub2 because you see the message it's loading and then it tries to load ubuntu. But your root partition doesn't seem to get mounted. So what is the plan after you chroot?

If you want more detailed view of the boot process, download the boot info script, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by l0uismustdie on 2010-06-17
Yeah, I don't have a plan.  What I am trying to do is get my system to boot again without using a usb key and then mounting my hard disk.

Results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa71ba71b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,342,544   112,342,482  83 Linux
/dev/sda2         112,342,545   117,226,304     4,883,760   5 Extended
/dev/sda5         112,342,608   117,226,304     4,883,697  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1058 MB, 1058275328 bytes
2 heads, 63 sectors/track, 16404 cylinders, total 2066944 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00193dca

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     2,066,943     2,066,912   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        14eac46e-1134-4aaa-ad34-bcc3f6c6dfb6   ext4                                     
/dev/sda5        ae2f104b-e67c-40e1-afcd-b962e05a664b   swap                                     
/dev/sdb1        565E-2001                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=14eac46e-1134-4aaa-ad34-bcc3f6c6dfb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ae2f104b-e67c-40e1-afcd-b962e05a664b none            swap    sw              0       0
```

---

### Post by darkod on 2010-06-17
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

You don't have the /boot/grub folder and any of the boot files. I wonder whether grub2 was installed at all, or simply the boot files are missing. Because it's different fix.

Lets first try to recreate grub.cfg by chroot into the install:

sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-mkconfig
update-grub
grub-install /dev/sda
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

Restart and see what happens.

---

### Post by l0uismustdie on 2010-06-17
Thanks for replying so quick.

Everything works until:
grub-mkconfig
This gives me a familiar error: grub-probe: error: cannot find device for /boot
So I tried one more step:
mount --bind /boot /mnt/boot
no luck here either.

---

### Post by darkod on 2010-06-17
I was afraid of that, grub2 doesn't seem to be installed at all. It's more complicated to install with chroot but I'll try to do it.

Kansasnoob, are you around? You're the guy for this. :)

Lets see first if you have any kernels at all, because they are also in the /boot folder which doesn't seem to exist.

Once you do the first four commands to mount the system, what does it show with:

ls /mnt/boot

If you can see the kernels like vmlinuz-2.6.32-xx then it's fine. Either way, continue with:

sudo chroot /mnt /bin/bash
apt-get install grub-pc (I'm not sure this line will work, but it's my best shot, sorry)
update-grub
grub-install /dev/sda

then continue exiting the chroot and the umount commands from the previous try.

---

### Post by l0uismustdie on 2010-06-18
Well, it looks like I don't even have the right kernels.  The last kernel in /mnt/boot is vmlinuz02.6.31-22-generic.
My terminal:
sudo chroot /mnt /bin/bash
apt-get install grub-pc 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

Which I did...and corrected nothing.  I'm wondering if I just get the right kernel in the boot directory if it won't fix somthing?

---

### Post by Penguin Guy on 2010-06-18
You get into a chroot like this:
```

#Make the directory:
sudo mkdir -p /mnt/chroot

# Mount the system:
sudo mount /dev/sda1 /mnt/chroot

# Bind /dev and /proc (to allow editing of partitions):
sudo mount --bind /dev /mnt/chroot/dev
sudo mount --bind /proc /mnt/chroot/proc

# Enter chroot:
sudo chroot /mnt/chroot

```
You can then run any commands you want. Try:
```

update-grub
grub-install /dev/sda

```

---

### Post by darkod on 2010-06-18
> **Penguin Guy said:**
> You get into a chroot like this:

Which is the same as my commands, the chroot is not the issue here, we need fresh ideas, the OP already managed to chroot.

> 
You can then run any commands you want. 

Not really, and that's the point. But I still haven't figured out the solution, I think it was the /bin/bash because it sort of allowed the OP to try installing things. Although an error appeared.

But just

sudo chroot /mnt/chroot

will not allow you to install with apt-get, try it.

To the OP, did you try running the install command again after trying what the message suggested. Even if there was no notification, maybe something got fixed.

Since it's complaining about dpkg and you have no 2.6.32 kernels, it's clear the upgrade to 10.04 had a hiccup.

That's why it didn't install any 2.6.32 kernel and is not even allowing you to run apt-get install now.

Try again the chroot and the dpkg --reconfigure -a as suggested. That is also the command to run to try to repair upgrade process went bad, and your obviously did.

---

### Post by Penguin Guy on 2010-06-18
[@darkod]("http://ubuntuforums.org/showthread.php?p=9479320#post9479320"): Pacman works fine for me using the chroot instructions I posted, so I see no reason why apt-get wouldn't work.

OP: Do you have a [FONT="Courier New"]/boot[/FONT] partition? Please post back the results of [FONT="Courier New"]sudo fdisk -l[/FONT] , [FONT="Courier New"]sudo blkid[/FONT] , and the contents of your [FONT="Courier New"]/etc/fstab[/FONT] file.

---

### Post by l0uismustdie on 2010-06-18
So I was able to get apt-get working with Penguin Guy's suggestions.  My machine will now boot on its own but is booting the old kernel (probably because there is no new one).  I made and installed the 10.04 kernel with no luck.

SO here are the results you asked for:
```

josh@josh-hp:~$ sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa71ba71b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6993    56171241   83  Linux
/dev/sda2            6994        7297     2441880    5  Extended
/dev/sda5            6994        7297     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 1058 MB, 1058275328 bytes
2 heads, 63 sectors/track, 16404 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00193dca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16405     1033456    b  W95 FAT32

``````

josh@josh-hp:~$ sudo blkid
/dev/sda5: UUID="ae2f104b-e67c-40e1-afcd-b962e05a664b" TYPE="swap" 
/dev/sdb1: UUID="565E-2001" TYPE="vfat" 
/dev/sda1: UUID="14eac46e-1134-4aaa-ad34-bcc3f6c6dfb6" TYPE="ext4" 

``````

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=14eac46e-1134-4aaa-ad34-bcc3f6c6dfb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ae2f104b-e67c-40e1-afcd-b962e05a664b none            swap    sw              0       0

```

---

### Post by l0uismustdie on 2010-06-18
Upon reboot now I am faced with a ton of configurations which end in the machine being hung up on:
```

[117.9412511] [<c1050327>] kernel_thread_helper+0x7/0x10

```

---

### Post by darkod on 2010-06-18
I would suggest to boot the kernel from 9.10 if it boots OK (2.6.31-xx) and then in terminal run the:

sudo dpkg --reconfigure -a

If the upgrade went wrong and stopped half way trough, that should make it finish up. I guess it should even install the 10.04 kernel (2.6.32-xx).

Remove the kernel you tried to install manually first if it doesn't work.

---

### Post by Penguin Guy on 2010-06-19
Remove the kernel you tried to manually install, then run:
```

sudo dpkg --configure -a
sudo apt-get update

```
If all goes well, you should have a working up-to-date system.

---

### Post by kansasnoob on 2010-06-19
> Kansasnoob, are you around? You're the guy for this.

@ Darko, 

Sorry I was unavailable but I'll check back a few times this weekend and see what's up when the OP posts again.

---

### Post by l0uismustdie on 2010-06-19
So upon issuing the last two commands and following a reboot I'm looking at:
```

error: file not found.
error: you need to load the kernel first
    Failed to boot both default and fallback entries
Press any key to continue...

```

Pressing a key just brings the message again.

---

### Post by kansasnoob on 2010-06-20
OK lets try reinstalling grub 2 completely, packages and all. Please copy-n-paste the following commands because some are incredibly long, and also post the full terminal output back here so we can see exactly what might be failing:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
apt-get update
```

Either of the following two commands may return errors that could be very helpful to us:

```
apt-get -f install
```

```
dpkg --configure -a
```

Regardless of errors continue:

```
apt-get install --reinstall grub-pc
```

You can accept all of the default options as that installs, just continue:

```
update-grub
```

Be sure and wait for it to say done, and continue:

```
grub-install /dev/sda
```

If that returns any errors then also run:

```
grub-install --recheck /dev/sda
```

Now be sure to copy-n-paste the full terminal output here, then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Hopefully that will at least provide us some helpful info, or maybe even get you booting.

---

### Post by darkod on 2010-06-20
I can't be sure, but I think the OP doesn't even have kernels. I guess that would give back the error that a kernel has to be loaded.

Can you just install one in chroot?

---

### Post by l0uismustdie on 2010-06-20
First line:
```

josh@josh-hp:~$ sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for josh: 
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file

``````

josh@josh-hp:~$ sudo dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'

``````

josh@josh-hp:~$ sudo ln -s /bin/true /sbin/initctl
josh@josh-hp:~$ sudo apt-get update
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com lucid/partner Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com lucid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Ign http://us.archive.ubuntu.com lucid/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com lucid/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                       
Ign http://security.ubuntu.com lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://archive.canonical.com lucid Release                       
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://archive.canonical.com lucid/partner Packages              
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done

``````

josh@josh-hp:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1288 not upgraded.

``````

josh@josh-hp:~$ sudo dpkg --configure -a
josh@josh-hp:~$ sudo apt-get install --reinstall grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1288 not upgraded.
Need to get 0B/607kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 233187 files and directories currently installed.)
Preparing to replace grub-pc 1.98-1ubuntu6 (using .../grub-pc_1.98-1ubuntu6_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.98-1ubuntu6) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

``````

josh@josh-hp:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

``````

josh@josh-hp:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
josh@josh-hp:~$ sudo grub-install --recheck /dev/sda
Installation finished. No error reported.

```I think darko is right...it doesn't even look like the 10.04  kernel was downloaded.  Also, the 1288 packages not upgraded concerning...
Rebooting normally...doesn't seem like anything has changed.  Still booting in 9.10.
Thanks guys.

---

### Post by kansasnoob on 2010-06-20
Do exactly the same as in post #22 only right after running:

```
apt-get update
```

Run:

```
apt-get dist-upgrade
```

That could take a while to complete but then run all other commands!

Then we'll know what your internet connection is like.

---

### Post by kansasnoob on 2010-06-20
Excuse my "duh" moment, but this:

> Still booting in 9.10.

Tells me you can still boot into the OS without using a chroot???????????????

Can you boot the old kernel without using a Live CD?

If so what happens when you run:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

I feel a bit like a doggy chasing it's tail.

---

### Post by l0uismustdie on 2010-06-22
Yeah...I can understand your last sentiments.  It seems like all the pieces of the puzzle where in the posts but hadn't been put together in the right order yet.  Alas, I am up and running with only the slight disturbance that the button that registers if the laptop lid is closed seems to be temperamental now.  I am greatly indebted to you all.  

The funny thing about this is that I asked my computer science advisor about it and he goes "Oh yeah, easy fix.  Find you menu.lst file and just add the new kernel."  Little did we realize I not only didn't have the menu.lst file(GRUB 2)...I didn't have the new kernel either.  C'est la vive.  Thanks again for all your help. 

Josh

---

### Post by neo unplugged on 2010-08-11
[UPGRADE TO LUCID ERROR]

mount: mounting none on /dev failed no such device
mknod: /dev/tty3 file exists
usb_id[333] unable to access '/devices/pci0000:00/0000:00:1d.1/
.
.
.
Checking battery [OK]
And then it just waits forever.


SOLUTION that worked for me:

sudo apt-get update
sudo apt-get install grub2 (this is important. you have to get this installed no matter what)
sudo apt-get install grub-pc
sudo apt-get install grub-common

sudo grub-mkconfig && update-grub (if you get a message that "you have to be logged in as root to run grub-mkconfig" then login as root and run the command)

reboot. select the recent kernel. it will still give you the message mount: mounting /dev failed ...(something like that) but dont worry. it should load everything fine and finally the xserver
Maybe there's a simpler solution but the above did work for me.

---

### Post by ssd27 on 2010-09-17
Hello,
    I used to have a fc6 until recetnly 2 weeks back I installed ubuntu 10.04 LTS on top of virtual box and vista home premium(I know its a blunder but I desperately needed at that moment to practice on visual studio) . Now the actually problem . The system froze and I have to perform a forceful shutdown which resulted in a crash. Next time I booted I went into initramfs.
1. boot failed because it couldn't find anything in /root. I have my ext4 installed in /dev/sda1. For performing mount /etc/fstab does not exist. I could n,t even get to a terminal operation failed
2. I tried using Live cd which I used to install ubuntu but it keeps on going with red and white dots. when i tried to get into menu and go to "try ubuntu without installing" even that didnot panout. I was able to check disk and memory through live cd those are fine.
Please don't tell me to do a fresh install I have tons of imp data on it. Is there anyway to recover it. Please help

---

### Post by narcisgarcia on 2010-10-28
To install kernel acording to Ubuntu current version (in this case, 10.04):
```
sudo apt-get update
sudo apt-get install linux
```
On the next boot, you should have Linux kernel 2.6.32 available to boot on.

---

