---
title: "[SOLVED] I'm set up w/ Dual Boot on two seperate drives. Need help w/ grub."
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by SloYerRoll on 2008-03-06
I've read a few threads on this. But need a bit more advise than they gave. 

Background:
I wanted to try out Ubuntu and set it up on a small (10GB) partition on my "main" drive and found out I wanted to have two separate OS's so when I finally pull the trigger on dumping Vista for good, I don't have to muck around w/ partitions. I know gparted is good stuff, but why mess it when you don't have to? :)

SO:
I have two internal drives (both 250GB)
I have Ubuntu installed on one drive (drive is dedicated to Ubuntu) and Vista and Ubuntu set up on the other drive in dual boot configuration. 

What I'd like to do is remove the Ubuntu that's on the Vista drive. Give that partition back to Vista. Then create a GRUB that gives me the option to boot from either drive when I fire the machine up. 

So at the end of the day, I'd have vista on one 250GB drive and Ubuntu on the other 250GB drive and be able to pick which OS I need at boot. 

Any links, help or advise is greatly appreciated. 

Best,

---

### Post by Pumalite on 2008-03-06
How do you boot? Who owns the Grub?

---

### Post by SloYerRoll on 2008-03-06
Good question. I'm sure this is where the "problem" lays. 

Right now, neither drive knows the other exists. I wanted to do a clean install on the Ubuntu drive, so I disconnected the Vista drive, ran gparted to partition accordingly for Ubuntu and installed. 

So I only have the Ubuntu drive connected now. When it loads, it doesn't give me all the options a typical GRUB dual boot would. It just tells me it's loading in 3 seconds and then runs. 

The Vista drive w/ the dual boot of Ubuntu that I want to get rid of boots directly to Vista. 

So each drive "owns" it's own boot setup. 

The thing I'm unsure about is how to set it up so I can have both drives attached and get GRUB. 

Both drives are SATA. 


The following is a second priority:
The only other thing is I'd like to "give back" the partitions to Vista. But I want it to be allocated NTFS space so I don't have to jump through Vista hoops to find it.

---

### Post by Pumalite on 2008-03-06
Obviously Vista has the boot loader in the drive that has Vista on. I'm not a Windows user, but I'd assume you could just resize your Vista drive with the Vista partitioner. In case you go ahead and do it, don't forget to backup all important data first. It's a matter of good practice. I also assume that Ubuntu is installed in the second half of that drive. After you do that we could discuss the rest.

---

### Post by SloYerRoll on 2008-03-06
> **Pumalite said:**
> After you do that we could discuss the rest.All important data is backed up daily on a seperate external drive. Feel free to commence!:)

---

### Post by Pumalite on 2008-03-06
Go into your Vista and check your partitioner and see if you can expand your partition.

---

### Post by SloYerRoll on 2008-03-06
I can't expand the main drive. But I can remove the existing files and format as one big chunk of free space. I'll just format it to NTFS and make it some kind of data drive. So I'm happy w/ that for now. 

The only time I plan on being in Vista anyway is when I'm using my Adobe CS3 apps anyway. Other than that. I'm going to live in Ubuntu!

BTW: I'm doing some graphics work tonight. So there may be a bit of lag in my responses since I'll be in windoze.

---

### Post by vgrisham on 2008-03-06
Jon,

I'm in the same boat. My main hard drive has Ubuntu (Ext3) with which I do 99% of my work. The second hard drive has Vista (NTFS) and I use that exclusively for gaming. My third drive I use as a backup (Ext3). Right now, I literally unplug my ext3 drives when I want to use Vista. The rest of the time, the Vista drive is unplugged. Grub has no idea the Vista drive exists, but I've been wanting to set it up to where Grub lets me choose my OS at boot time. 

I'm keenly interested in this thread and I'll be throwing in questions as well. 

Thanks for creating this thread.

Vaughn

---

### Post by SloYerRoll on 2008-03-06
Feel free to jump in whenever Vaughn:KS

Happy I could incidentally help :)

The main reason I need to do this is because I can get an end of the world convert these graphics, if you don't I'll start shooting people email. 

I'm looking into virtualbox and others but I'm opening and closing 100+MB photoshop files, so I need all the memory my machine has. (Just like yours for gaming)

---

### Post by confused57 on 2008-03-06
Here's how I have my system set up:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You need to run:
```
sudo fdisk -l
```
-l is a lowercase "L"
This will show if Vista is on the first partition...the Windows entry in the above link will work if this is the case.

If it's on the 2nd partition, root would need to be (hd1,1)...if you have 3 hard drives, the Vista drive may be recognized as (hd2):
```
tltle  Vista
root (hd2,0)
makeactive
map  (hd0) (hd2)
map  (hd2) (hd0)
boot
```

---

### Post by SloYerRoll on 2008-03-07
OK so when I was trying to expand the partition on the Vista HD. I formatted the Ubuntu data. Nothing critical lost but I didn't see Confused's post until after the fact...

So the key players are now two SATA HD's. 

1 drive exclusively Ubuntu. 
1 drive exclusively Vista. 

Neither of them have ever talked to each other. How do I make them get along at boot time?

I figure I'll go into BIOS tonight and have my puter boot to the Ubuntu drive so one of you guys can show me how to get GRUB to help out. 

Thanks again for any help or ideas. 

Best,

---

### Post by SloYerRoll on 2008-03-07
I'm all set up and have both hard drives plugged in and BIOS boots to my Ubuntu Drive. 

What's next? :)

---

### Post by confused57 on 2008-03-07
> **SloYerRoll said:**
> I'm all set up and have both hard drives plugged in and BIOS boots to my Ubuntu Drive. 

What's next? :)
If you're unsure if Vista is on the first partition, you can run:
```
sudo fdisk -l
```
-l is a lowercase "L"

Then open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

for Vista on the first partition, add this to the very end of the menu.lst file:
```
title  Windows Vista
rootnoverify  (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
quit & save

Vista on 2nd partition would be "rootnoverify (hd1,1)"

You should be able to just copy & paste the commands in a terminal.

---

### Post by SloYerRoll on 2008-03-07
Hey Confused. Thanks!

When you posted w. your link last time. My Vista Hard drive wasn't plugged in since I didn't have BIOS set up. 

I'll follow your instructions and let you know the results!

Thanks for the awesome tuts too!

---

### Post by SloYerRoll on 2008-03-07
I'm a bit confused though. 
Neither of my OS's are on a partition. Easch OS is on it's won seperate hard drive:

So I ran ```
sudo fdisk -l
``` and came up w/ this:

```
jon@ish:~$ sudo fdisk -l
[sudo] password for jon:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       28737   220292096    7  HPFS/NTFS
/dev/sda4           28738       30394    13309852+   5  Extended

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e55a717

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       27977   224725221   83  Linux
/dev/sdb2           27978       30401    19470780    5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris
/dev/sdb6           27978       29164     9534514+  82  Linux swap / Solaris

Partition table entries are not in disk order
jon@ish:~$ 

```

---

### Post by confused57 on 2008-03-08
Looks like Vista is on partition #3(/dev/sda3), so try this entry:
```
title  Windows Vista
rootnoverify  (hd1,2)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

sda1 is Dell's utility partition(I have one on my Dell Dimension 4550) and sda2 is probably a restore partition?

---

### Post by SloYerRoll on 2008-03-08
OK so I did that and rebooted. It booted sstraight to the Ubuntu disk w/o GRUB asking me anything. It did the exact same thing as it normally does..

menu.lst:
```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=37dcaded-3e3e-4c31-81b9-05e775ed7b00 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# howmany=all

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=37dcaded-3e3e-4c31-81b9-05e775ed7b00 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=37dcaded-3e3e-4c31-81b9-05e775ed7b00 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title  Windows Vista
rootnoverify  (hd1,2)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by confused57 on 2008-03-08
You probably need to comment the line with hiddenmenu & increase the timeout...change:
```
hiddenmenu
```
to
```
# hiddenmenu
```

and change timeout from 3 to 10:
timeout  10

Also, place your Vista entry after the line ###END DEBIAN AUTOMAGIC KERNELS  LIST...

---

### Post by SloYerRoll on 2008-03-08
Sweet!
GRUB is doing what it should. 

I haven't tested GRUB booting Vista. but the config file makes sense and I'm sure it will work!

Thanks confused!

---

### Post by vgrisham on 2008-03-08
Jon & Confused,

Let me complicate this one step further. I have three drives. SDA holds my Ubuntu OS drive. It has three partitions: SDA1 is swap, SDA2 is root, SDA3 is home. SDB is a backup drive and it has one partition, SDB1. Drive three is my Vista drive and it has one partition SDG1. 

Before I start messing with grub, I'm a little concerned by the bootflag field. For some reason, partition sdb1 is flagged as boot. This partition contains no operating system and is not bootable. Should I clear the flag? If so, is that something I can change in fstab?

Here's my fdisk profile:
> 
vaughn@vaughn-desktop:~$ sudo fdisk -l
[sudo] password for vaughn:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d512bfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     4000153+  82  Linux swap / Solaris
/dev/sda2   *         499        5373    39158437+  83  Linux
/dev/sda3            5374       38913   269410050   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   83  Linux

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf063c921

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       19458   156288000    7  HPFS/NTFS


So I'm guessing my Vista grub entry is going to be:

> 
title  Windows Vista
rootnoverify  (hd2,1)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

I'm not sure what goes in the brackets in the map section; what's in there now is just a guess. Also, what do I need to make any changes to the chainloader line?

Thank you both very much.

---

### Post by confused57 on 2008-03-08
vgrisham,
    Here's probably the best grub guide you'll find:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
you may want to check the section for how grub recognizes partitions.

You can check how grub designates your drives with:
```
gedit /boot/grub/device.map

Your Vista entry would probably be:
[code]title Windows Vista
rootnoverify (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

The boot flag being on your storage drive won't hurt nor effect booting the other drives.

---

### Post by vgrisham on 2008-03-08
Thanks Confused! That worked perfectly. :guitar:

---

### Post by confused57 on 2008-03-08
> **vgrisham said:**
> Thanks Confused! That worked perfectly. :guitar:
You're welcome...glad to hear it worked.

---

