---
title: "Resized partitions, now splash screen drops to text"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by AirIntake on 2008-04-15
I was so happy with the way Ubuntu 64 (hardy) was running that I decided to give it more room. I booted with the live CD, deleted a spare FAT32 partition, and then resized my Ubuntu's extended, root, and swap partitions to fill the space.

After a reboot, I noticed that the splash screen now drops to text right at "* Reading files needed to boot". When I got into the desktop, I checked GParted and the swap file wasn't being used. I read around, and found out that I needed to update the UUID of the swap in my fstab file. I did that, and now the swap file seems to be enabled properly.

Unfortunately, upon reboot, the splash screen still drops to text at "* Reading files needed to boot".

Did I do something wrong? How can I get the splash to stay up through the entire boot again?

---

### Post by dstew on 2008-04-15
> I booted with the live CD, deleted a spare FAT32 partition, and then resized my Ubuntu's extended, root, and swap partitions to fill the space.When you deleted a partition, you may have disturbed the mapping that grub uses to load the kernel images. Post the output of **sudo fdisk -l** and **cat /boot/grub/menu.lst** so we can have a look.

---

### Post by AirIntake on 2008-04-15
```
brad@Bitchbox7:~$ sudo fdisk -l
[sudo] password for brad: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e709e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14779   118711493+   7  HPFS/NTFS
/dev/sda2           18496       19457     7727265    7  HPFS/NTFS
/dev/sda4           14780       18495    29848770    5  Extended
/dev/sda5           14780       17973    25655773+  83  Linux
/dev/sda6           17974       18495     4192933+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
and
```
brad@Bitchbox7:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage (hd0,4)/boot/grub/splashimages/hpblue.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5c4afccf-0a4c-4168-afc1-7ccf5c2fe379 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04 Hardy Heron 64bit
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5c4afccf-0a4c-4168-afc1-7ccf5c2fe379 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04 Hardy Heron 64bit - Recovery Mode
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5c4afccf-0a4c-4168-afc1-7ccf5c2fe379 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04 Hardy Heron 64bit - memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Home Premium
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		HP Recovery Manager
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by AirIntake on 2008-04-15
Just to clarify, the system still boots and seems to run fine, I'd just like to get rid of the unsightly text that didn't used to be there on startup.

---

### Post by dstew on 2008-04-15
One thought: try updating your initial RAM file system image:```
sudo update-initramfs -u
```Maybe it is lost when it comes to finding the splash image.

---

### Post by AirIntake on 2008-04-15
That command returned:
```
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
```
It doesn't have a problem finding the splash image though. The splash displays and animates for 10 seconds, but then disappears and dumps to text, starting with * Reading files needed to boot [OK] and continuing the rest of the boot in text from there.

---

### Post by dstew on 2008-04-15
I think there are two stages to splash. The first is when grub gets the splash image (from the splashimage line in menu.lst) then the kernel runs the usplash program. But I don't really know what advice to give you at this point. It seems like something from the usplash program. That program has a configuration file, /etc/usplash.conf, you might look at it. If it is absent, maybe you can create one by re-installing usplash. But really, I am out of ideas. Good luck.

---

### Post by AirIntake on 2008-04-15
Yes, it is definitely usplash that's dropping out to text.

---

### Post by AirIntake on 2008-04-16
Is this problem a bug with 8.04, or is it just a normal issue? Should I file a bug report?

---

### Post by dstew on 2008-04-16
One way of finding out is to post a bug report. Sometimes, bugs are specific to hardware, so the forums might not be the best way to find out. To report a possible bug, go to [Launchpad]("https://launchpad.net/ubuntu"). You can also search for the same possible bug.

---

### Post by tj111 on 2008-04-16
Just wanted to say you have the best computer naming scheme ever.  
After a succesful boot, what is the output of `dmesg | tail -n 20` ?

---

### Post by AirIntake on 2008-04-16
I'm at work right now, but I'll try that command when I get home.

You like the naming scheme? Every computer I've ever owned have had this name (though the first 2 were named retroactively :)

Bitchbox1 - 386SX 16 1MB RAM 40MB HD
Bitchbox2 - 486DX2/66 16MB RAM 420MB HD
Bitchbox3 - P133 48MB RAM 1.6GB HD
BitchboxIV - PIII 500 384MB RAM 18.2GB HD
Bitchbox5 - Athlon 1500+ 512MB RAM 30GB HD (Laptop)
Bitchbox6 - Athlon 64 3800+ 2GB RAM 250GB+500GB HD
Bitchbox7 - Core 2 Duo 1.66 2GB RAM 160GB HD (Laptop)

---

### Post by mjfowler on 2008-04-16
I've been getting exactly the same thing as AirIntake, ever since I upgraded my laptop to a larger hard disk, about 5 days ago. I've got a Dell Inspiron 1300, and I'm running Hardy beta, which I've been updating regularly - it could be that I upgraded to kernel 2.6.24-15 at about the same time.

To do the hard disk upgrade, I backed up my root and /home directories to a USB disk (using tar), partitioned the new hard disk with the same partitions as the old disk (but larger), then copied the root and /home directory contents back - basically following this very detailed howto: 

[http://linuxmint.com/forum/viewtopic.php?t=3969]("http://linuxmint.com/forum/viewtopic.php?t=3969")

One thing I specifically did in the backup / restore (as recommended in the above howto) was to replace UUIDs in /etc/fstab and menu.lst with device names, i.e., /dev/sda1 instead of UUID=xxxx... 

Partitions on new disk all OK, and I can confirm that my swap partition is being used.

Interested to know if others have experienced this, and possible solution.

Mike

---

### Post by AirIntake on 2008-04-17
I get:
```
brad@Bitchbox7:~$ dmesg | tail -n 20
[   74.057809]   groups: 01 02
[   74.057813]   domain 1: span 03
[   74.057814]    groups: 03
[   74.057816] CPU1 attaching sched-domain:
[   74.057818]  domain 0: span 03
[   74.057820]   groups: 02 01
[   74.057822]   domain 1: span 03
[   74.057824]    groups: 03
[   74.992419] NET: Registered protocol family 17
[   78.260004] wlan0: Initial auth_alg=0
[   78.260014] wlan0: authenticate with AP 00:04:e2:98:61:10
[   78.263779] wlan0: RX authentication from 00:04:e2:98:61:10 (alg=0 transaction=2 status=0)
[   78.263784] wlan0: authenticated
[   78.263788] wlan0: associate with AP 00:04:e2:98:61:10
[   78.266189] wlan0: authentication frame received from 00:04:e2:98:61:10, but not in authenticate state - ignored
[   78.267203] wlan0: authentication frame received from 00:04:e2:98:61:10, but not in authenticate state - ignored
[   78.268265] wlan0: RX AssocResp from 00:04:e2:98:61:10 (capab=0x11 status=0 aid=1)
[   78.268270] wlan0: associated
[   78.273564] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   94.185051] wlan0: no IPv6 routers present

```
I don't think that helps...

---

### Post by AirIntake on 2008-04-17
@mjfowler

How do you check if your swap is actually being used? I've checked in system monitor, and the swap usage is 0, but that doesn't mean it's not working necessarily, because I do have 2Gigs of ram.

---

### Post by tj111 on 2008-04-17
Ok, after a reboot, try looking through the contents of /var/log/boot.log (I *think* thats where it is in Ubuntu, at work now), and look for any error messages.  Or alternatively, you can run:
```

grep -i -e 'error' -e 'failed' /var/boot.log

```

Give me the output of that (delete any personal info, if there is any, which I doubt).

---

### Post by mjfowler on 2008-04-17
AirIntake,

If you enter

```
sudo swapoff -a
sudo swapon -a
```

and then

```
free -m

```

it will show total / used / free number of swap blocks, and total & free at least should be non-zero. (If you enter 'free - m' after 'sudo swapoff -a', this should show 0 / 0 / 0).

I think this shows whether swap is available - although it doesn't prove it's being used.

Mike

---

### Post by wkulecz on 2008-04-17
What's the reasoning behind the einstein who thinks changing to UUIDs instead of device names is a good idea?

I sure don't see an upside, and they sure do make the system more fragile, greatly hindering diaster recovery efforts.   

I see  them as  an unreadable version of disk/partition labels which themselves are a band-aid over the real problems caused by dynamically changing device name assignments.

--wally.

---

### Post by AirIntake on 2008-04-17
```
brad@Bitchbox7:/var/log$ sudo grep -i -e 'error' -e 'failed' /var/log/boot.log
grep: /var/log/boot.log: No such file or directory

```
I don't seem to have a boot.log. I've checked /var and /var/log. There is a file /var/log/boot, but its contents say "(Nothing has been logged yet.)"

---

### Post by AirIntake on 2008-04-17
Upon last reboot, Ubuntu ran an fsck on sda5. The check somehow failed, but I can't seem to locate a log of why. Help!

---

### Post by AirIntake on 2008-04-17
Ok, I've found /var/log/fsck/checkroot. Its contents are:
```
Log of fsck -C -a -t ext3 /dev/sda5 
Thu Apr 17 17:14:56 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda5 was not cleanly unmounted, check forced.
/dev/sda5: 163843/1605632 files (0.9% non-contiguous), 1086092/6413943 blocks
fsck died with exit status 1

Thu Apr 17 17:16:22 2008
----------------
```
Is this something useful?

---

### Post by tj111 on 2008-04-17
The fsck man pages say that exit status 1 means that the errors were corrected.  So thats nothing to worry about.

I was replying earlier from work, and actually was going through some boot logs on a CentOS server to figure out some error messages.  I used that exact grep command and got an output like this::
```

Apr 17 00:01:09 host exim: clamd shutdown failed
Apr 17 00:01:18 host clamd: ERROR: Parse error at line 299: Unknown option ArchiveMaxCompressionRatio.
Apr 17 00:01:18 host clamd: ERROR: Can't open/parse the config file /etc/clamd.conf
Apr 17 00:01:18 host exim: clamd startup failed
Apr 17 12:37:15 host exim: clamd shutdown failed
Apr 17 12:37:16 host clamd: clamd shutdown failed
Apr 17 12:37:54 host clamd: ERROR: Parse error at line 299: Unknown option ArchiveMaxCompressionRatio.
Apr 17 12:37:54 host clamd: ERROR: Can't open/parse the config file /etc/clamd.conf
Apr 17 12:37:54 host clamd: clamd startup failed
Apr 17 12:37:56 host exim: Starting clamd: 
Apr 17 12:37:56 host clamd: ERROR: Parse error at line 299: Unknown option ArchiveMaxCompressionRatio.
Apr 17 12:37:56 host clamd: ERROR: Can't open/parse the config file /etc/clamd.conf
Apr 17 12:37:56 host exim: ERROR: Can't open/parse the config file /etc/clamd.conf
Apr 17 12:37:56 host exim: clamd startup failed

```

Unfortunately dmesg doesn't provide this nice output, and from what I can find there's  a lot of issues with enabling logd in Ubuntu.  See this [bug report](https://bugs.launchpad.net/upstart/+bug/98955).  If I had an output like that, I could be of alot more help.

---

### Post by AirIntake on 2008-04-18
Just for kicks I a complete removal and reinstall of usplash, usplash-theme-ubuntu, and ubuntu-desktop in Synaptic. No luck.

I'm going to do some searching around for the next couple days, but after that I think I'm going to fix this problem the Windows way...with a format and reinstall :)

---

### Post by AirIntake on 2008-04-23
Bah, I give up. After a reinstall the usplash problem was fixed, but then I couldn't get Flash to work the same way as last time (or any other way, for that matter). I guess I'll wait a bit until they have the kinks worked out.

---

### Post by tj111 on 2008-04-23
You have to install the 32-bit version of Firefox and Flash to get flash support.  There currently is no 64-bit versions available.  So make sure you got the 32-bit versions before giving up.

---

### Post by AirIntake on 2008-04-26
I've got Ubuntu 8.04 installed with no problems now! Did a reinstall with the release version with no usplash issues. Then instead of using that script to install Flash I just went to youtube.com and let Firefox suggest that I install flash. I did, and it worked perfectly!

---

### Post by tj111 on 2008-04-28
Good to hear :)

---

### Post by sefs on 2008-04-29
[http://ubuntuforums.org/showthread.php?t=766806](http://ubuntuforums.org/showthread.php?t=766806)

This thread may have been what you were experiencing if you had done an upgrade to hardy instead of a clean install.

The thread contains a problem description and the fix.

---

