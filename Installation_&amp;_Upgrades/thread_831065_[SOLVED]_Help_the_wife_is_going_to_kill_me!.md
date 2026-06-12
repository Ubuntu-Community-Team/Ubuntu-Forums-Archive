---
title: "[SOLVED] Help the wife is going to kill me!"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by Jon Williams on 2008-06-16
Hi 

I did I installed ubuntu on my machine, all went well! I currently have XP installed and was hoping for a dual boot. 

When I pop the CD out and try to reboot i get a black screen and the following

Error loading operating system_

I have had a look at the rest of the forums and run the sudo fdisk thingy. here are my results. Does this help.... please help


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99ca99ca

Device Boot Start End Blocks Id System
/dev/sda1 1 14948 120069778+ 7 HPFS/NTFS
/dev/sda2 * 14949 24415 76043677+ 83 Linux
/dev/sda3 24416 24792 3028252+ 5 Extended
/dev/sda5 24416 24792 3028221 82 Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd466

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9729 78148161 7 HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd463

Device Boot Start End Blocks Id System
/dev/hdc1 1 9729 78148161 7 HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd464

Device Boot Start End Blocks Id System
/dev/hdd1 1 9729 78148161 7 HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by meindian523 on 2008-06-16
Where is XP installed,on the 1st,2nd,3rd or 4th HDD?

---

### Post by Jon Williams on 2008-06-16
I think on the first, which I partioned to run ubuntu as well (probably did not need to do this in hinsight!)

J

---

### Post by meindian523 on 2008-06-16
Is there any Error <number> given?

---

### Post by Jon Williams on 2008-06-16
nope

---

### Post by meindian523 on 2008-06-16
Does it wait for some time before putting out that message?If it does,try pressing Esc in that time.That should give you the boot menu,from where you can select the OS to run.I believe the error is for Ubuntu and not XP,coz the default OS after install is Ubuntu in the Grub bootloader configuration.Are you sure you didn't format the C: during installation of Ubuntu?

---

### Post by Jon Williams on 2008-06-16
I will give it a try, I am pretty sure that I have not formatted C: as when I boot from disk I can still see the content from the Places>Computer menu

---

### Post by meindian523 on 2008-06-16
Well,that pretty much means XP is there on your PC.Please try and be back.

---

### Post by lswest on 2008-06-16
Also, I noticed that Linux is the partition that's designated for boot, not the XP partition, not sure if that matters though.  Also can you post the output of ```
cat /boot/grub/menu.lst
``` please, so we can see what the entry is for your XP?

---

### Post by Jon Williams on 2008-06-16
The Esc key did not work

Have i done the next bit right?
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat/boot/grub/menu.lst
bash: cat/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

I tried it with and without a space after cat

---

### Post by meindian523 on 2008-06-16
nopes,you got to get into the partition of your installed system and then do it.The command you ran tried to get the menu.lst of the Live CD,which does not exist.You can run the following series of commands:

```
sudo mkdir /mnt/Linux
```

```
sudo mount /dev/sda2 /mnt/Linux
```

```
cd /mnt/Linux
```

```
cat ./boot/grub/menu.lst
```

---

### Post by imneo on 2008-06-16
here is what you should do:
put your xp cd , boot your pc

when asked press R to Repair windows
you will enter a terminal window

select your oparating system
enter your Administrator password

now write
```
fixmbr
yes
exit

```

now your xp will boot

if you still want to install ubuntu do this:

install a partition manager software (Acronis Disk Director Suite for example)

delete the linux partition and the swap partition
now install ubuntu

select the right HD and when asked select "Largest continues space" at the partitioner section this will install ubuntu on your extended space

that's it you will have dual boot.

---

### Post by Jon Williams on 2008-06-16
ubuntu@ubuntu:~$ sudo mkdir /mnt/Linux
mkdir: cannot create directory `/mnt/Linux': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/Linux
ubuntu@ubuntu:~$ cd /mnt/Linux
ubuntu@ubuntu:/mnt/Linux$ cat ./boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=ee04dd04-2a55-4171-ab85-e647e23d1f2b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ee04dd04-2a55-4171-ab85-e647e23d1f2b ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=ee04dd04-2a55-4171-ab85-e647e23d1f2b ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd3,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd3,0)
savedefault
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1

ubuntu@ubuntu:/mnt/Linux$

---

### Post by Gallienus on 2008-06-16
You might try changing (in the BIOS) the hard disk that your system boots up from. One time I found that the Ubuntu install had put the GRUB boot sector on a hard disk that I incorrectly assumed would have been left untouched, and I think I got exactly the same error message that you reported.

---

### Post by Jon Williams on 2008-06-16
I tried this (with my limited knowledge) however it will not let me select the hard drive, it will only let me select Auto, CD, etc

---

### Post by meindian523 on 2008-06-16
Do this:
```
sudo gedit ./boot/grub/menu.lst
```
Then edit the default 0 line to > default 4,save and exit.Reboot.

---

### Post by Jon Williams on 2008-06-16
Hi tried this, rebooted nothing happened

checked that i had saved it and yes it is still there, is it in the right place?

default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4


P.S. thanks for all the help so far

---

### Post by meindian523 on 2008-06-16
Ok,I lost my connection,and this is the last idea I have.And yes,the edit is in the right place.If this doesn't work,I'm afraid I can't help further.Repeat the series of commands I gave earlier about sudo mkdir...mount...etc then do ```
sudo gedit ./boot/grub/menu.lst
```then place a > # sign in front of the line > map (hd3) (hd0)Save and exit.Reboot.

---

### Post by meierfra. on 2008-06-18
Try this:


Step 1) Reinstall Grub

Boot from the Ubuntu Live CD. Open a terminal and type

```
 sudo grub
```

and at the grub prompt 

```
find /boot/grub/stage2
```

The output will be of the form "(hd3,1)", but the first number might be different. 

Still at the grub prompt:

```
root (hd3,1)    (use the output from "find /boot/grub/stage2)
setup (hd3)           (use the first number from the output)
quit
```

Step 2 Edit menu.lst

```
sudo mkdir /mnt/Linux
sudo mount /dev/sda2 /mnt/Linux
gksudo gedit  /mnt/Linux/boot/grub/menu.lst
```

Change

"# groot=(hd3,1)" to "# groot=(hd0,1)"

(so change the first number to 0, do not change anything else)

change "root (hd3,1)" to "root (hd0,1)"  in the Ubuntu, Ubuntu recovery and  memtest items"

change the  Windows Item to

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

(do not use the map lines)

Save the file and reboot.

This will only work  if the computer is  booting  from then Windows/Ubuntu drive.
If this is not the case,  let me know which drive the computer is booting from, and I'll give you modified instruction.

---

### Post by Jon Williams on 2008-06-19
WOW!!!

Thanks I get the dual boot menu!

I have tried ubuntu and it works (no more CD)

Ahh 

Windows xp reports an error

NTLDR is missing
Press ctrl+Alt+Del to restart

any ideas?

Thanks for saving my bacon thus far!!

---

### Post by meierfra. on 2008-06-19
Could be a numbers of things. Let's try this first:

Put all of this on menu.lst

title Microsoft Windows XP Professional 
root (hd1,0)
map  (hd0) (hd1)
map  (hd1) (hd0)
savedefault
makeactive
chainloader +1

title Microsoft Windows XP Professional 
root (hd2,0)
map  (hd0) (hd2)
map  (hd2) (hd0)
savedefault
makeactive
chainloader +1

title Microsoft Windows XP Professional 
root (hd3,0)
map  (hd0) (hd3)
map  (hd3) (hd0)
savedefault
makeactive
chainloader +1


Save the file. Reboot and see which one works.  Of course remove the wrong ones afterwards.

---

### Post by bigken on 2008-06-19
> **Jon Williams said:**
> Hi 

I did I installed ubuntu on my machine, all went well! I currently have XP installed and was hoping for a dual boot. 

When I pop the CD out and try to reboot i get a black screen and the following

Error loading operating system_

I have had a look at the rest of the forums and run the sudo fdisk thingy. here are my results. Does this help.... please help


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99ca99ca

Device Boot Start End Blocks Id System
/dev/sda1 1 14948 120069778+ 7 HPFS/NTFS
**/dev/sda2 * 14949 24415 76043677+ 83 Linux**
/dev/sda3 24416 24792 3028252+ 5 Extended
/dev/sda5 24416 24792 3028221 82 Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd466

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9729 78148161 7 HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd463

Device Boot Start End Blocks Id System
/dev/hdc1 1 9729 78148161 7 HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdacfd464

Device Boot Start End Blocks Id System
/dev/hdd1 1 9729 78148161 7 HPFS/NTFS
ubuntu@ubuntu:~$


your boot flag is set for the **/dev/sda2 * 14949 24415 76043677+ 83 Linux **where it should be set for** /dev/sda1 1 14948 120069778+ 7 HPFS/NTFS**

---

### Post by meierfra. on 2008-06-19
Just to make sure. You used exactly

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


So you changed the 3 to a 0 and removed the two map lines?

---

### Post by meierfra. on 2008-06-19
> your boot flag is set for the /dev/sda2 * 14949 24415 76043677+ 83 Linux where it should be set for /dev/sda1 1 14948 120069778+ 7 HPFS/NTFS

1)  The "makeactive"  in menu.lst already put the boot flag on "/dev/sda1" 

2)  There is no reason for the boot flag to be on /dev/sda1, since Grub does not use boot flags.

---

### Post by bigken on 2008-06-19
> **meierfra. said:**
> 1)  The "makeactive"  in menu.lst already put the boot flag on "/dev/sda1" 

2)  There is no reason for the boot flag to be on /dev/sda1, since Grub does not use boot flags.


I thought windows did when you run gparted windows always has boot flag

---

### Post by meierfra. on 2008-06-19
Windows needs the boot flag if Windows is in charge of the MBR  (In this case the MBR looks for the partition with the boot flag, and then boots it) 

So then Windows is installed,   the boot flag is always  put on the  Windows partition  and it  just stays there.
In addition "menu.lst" usually has the "makeactive" statement, which also  puts  the boot flag on the Windows Partition.

For these two reasons, the boot flag almost always is on the Windows partition. But as far as I know it isn't necessary for Windows to boot.

---

### Post by bigken on 2008-06-19
so to fix windows he needs to try the repair console with **chkdsk**  & **chkdsk /p /r**

---

### Post by meierfra. on 2008-06-19
> so to fix windows he/she needs to try the repair console with chkdsk & chkdsk /p /r

That will be one of the next moves.. So lets plan ahead: 

If my posts 21 and 23 didn't solve the problem:

Boot from the Windows CD, press "r" to enter the  repair console and 

then  (I edited this according to bigken  suggestions)

```

chkdsk

chkdsk /p /r   (only if chkdsk returned an error)

fixmbr

fixboot

```

After reboot you should boot directly into Windows.
So you will have to reinstall Grub. See Step 1 in post #19

---

### Post by bigken on 2008-06-19
personally I would go this way 

chkdsk

chkdsk /p /r

fixmbr

fixboot

---

### Post by meierfra. on 2008-06-19
Fine with me (although fixmbr doesn't really accomplish anything, and then one has to reinstall grub)


Why the extra "chkdsk"?

---

### Post by bigken on 2008-06-19
> **meierfra. said:**
> 1)  The "makeactive"  in menu.lst already put the boot flag on "/dev/sda1" 

2)  There is no reason for the boot flag to be on /dev/sda1, since Grub does not use boot flags.


you were right about the boot flag just unchecked mine and was still able to boot in vista

---

### Post by bigken on 2008-06-19
if chkdsk finds errors no need to run the other commands


thats if it fixes them

---

### Post by meierfra. on 2008-06-19
But if your run "chkdsk  /p /r" and there are no errors, isn't that the same as running "chkdsk" ?

---

### Post by bigken on 2008-06-19
> **meierfra. said:**
> But if your run "chkdsk  /p /r" and there are no errors, isn't that the same as running "chkdsk" ?



chkdsk is very fast so I run it 1st and might not find any errors were as chkdsk /p /r can take hours and might find errors 

personally I can see a repair install needed

---

### Post by meierfra. on 2008-06-19
> chkdsk is very fast so I run it 1st and might not find any errors were as chkdsk /p /r can take hours and might find errors


O.k so one would run "chkdsk" as a routine check. But when one is worried that something is wrong, wouldn't one run "chdsk /p/r"  even if "chkdsk" did not return any errors?

Edit:  I don't really think anything is wrong  with the file system. So you are right, no reason to run "chdsk /p /r" if "chkdsk" doesn't return an error.

---

### Post by bigken on 2008-06-19
ok run chkdsk /p /r dont forget the spaces

---

### Post by Jon Williams on 2008-06-19
Wow!

just got home from work and read the latest, sorry to have caused problems, but thanks for getting involved.

I think i need to re-read this in order to work out what to do and maybe have a cup of tea first!
but thankyou!

---

### Post by meierfra. on 2008-06-19
I edited my post 28 according to my discussion with bigken.

So all you really need to read is in post 21, 23, and 28.  But do them in this  order:

23  21  28

 > sorry to have caused problem

You didn't cause any problems. Bigken and me just had a friendly discussion on what to do next, we both learned something and then came up with a strategy we both agree on.

---

### Post by meindian523 on 2008-06-19
Thanks to meierfra for jumping in.

@Jon
I directed meierfra to this thread in a PM,coz I felt I was going wrong somewhere.Learnt something too.

---

### Post by Jon Williams on 2008-06-19
Thanks to you all for the help and support, I am now writing this through windows and everything works ok.

It was my fault as last night i did not delete the maps ssection properly.

Thanks again for all the support you have saved my bacon big time!!!!!!!

very grateful 

Jon Williams

---

### Post by meierfra. on 2008-06-19
> I am now writing this through windows and everything works ok.

Good. 

> Thanks again for all the support you have saved my bacon big time!!!!!!!

You are welcome. Glad to be of help.

Could you mark the thread as solved (Go to thread tools).

---

