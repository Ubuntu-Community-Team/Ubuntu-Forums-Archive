---
title: "Ubuntu installed, but Grub doesn't show up | Keeps booting to windows"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by xarroyo on 2007-09-05
Hey.. 
I have a desktop which came with windows vista home.. I used the Live Cd of ubuntu 7.04 to install it, and everything seems ok.. But when the computer restarts, it doesn't show the grub to pick which OS i want to use, it just goes over windows.. If i insert the live cd and take a glance through Gparted i notice that the ubuntu installation is there... i don't know what's wrong with the grub.. why the grub doesn't show up??? i just can boot to windows and not ubuntu... :S

any thoughts??? 

thanks for the attention,

Xavier

---

### Post by slmclarengt on 2007-09-05
I am having this identical problem and was referred here after I tried my programming forums and eggxpert forums - I just get sick of registering :-). I have tried formatting the partition that contained UBUNTU and reinstalled but the problem stayed. It never loaded Grub; I even tried running through the terminal to install it and looking through the GUI to find any customizations as to how to install Grub. How is this accomplished because there's no point to me to just use UBUNTU because a lot of my programs are unavailable unfortunately on Linux.

Slmclarengt

---

### Post by merlinus on 2007-09-05
Boot from live cd.  Open a terminal (Applications/Accessories/Terminal) and enter these commands one at a time:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).  

For example, root may be (hd0,1) and setup (hd0).

-merlin

---

### Post by xarroyo on 2007-09-06
Hi Merlin..
i followed your steps, when i do the first step i get the following message ```
[ Minimal BASH-like line editing is supported.  For
        the  first  word,  TAB  lists  possible  command
        completions.  Anywhere else TAB lists the possible
        completions of a device/filename. ]

grub>
```

 but when i perform the step 2.. i get the following message ```
find /boot/grub/stage1  --> error 15: File not found
```

what could be the problem??

thanks for the attention,

Xavier

---

### Post by merlinus on 2007-09-06
It may be that grub did not get installed.  How many hdds do you have?

Post results of:

```

sudo fdisk -l

```

-merlin

---

### Post by xarroyo on 2007-09-06
Hey Merlin..

this is the info that i got...

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    c  W95 FAT32 (LBA)
/dev/sda2            5100       10011    39455640    f  W95 Ext'd (LBA)
/dev/sda5            5100       10011    39455608+   b  W95 FAT32

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       12753       48640   288270328+   7  HPFS/NTFS
/dev/sdb2               1       12752   102430408+   f  W95 Ext'd (LBA)
/dev/sdb5               1         263     2112484+  82  Linux swap / Solaris
/dev/sdb6             264         519     2056288+  83  Linux
/dev/sdb7             520       12752    98261541   83  Linux

Partition table entries are not in disk order

```

Thanks for your help..
Xavier Arroyo

---

### Post by merlinus on 2007-09-06
You might try changing the boot order of your hdds in BIOS so sdb boots first.

Also, it looks like you have two linux partitions on sdb.  Do you remember which one is / ?

-merlin

---

### Post by xarroyo on 2007-09-06
Sure, the / is on sdb6
and on the bios, the boot order goes for sdb which also has a windows partition..

Anyway i will check it!! So, what else should i do?

Thanks!

---

### Post by merlinus on 2007-09-06
You might try removing the boot flag on sda1, using gparted live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Another option would be to try this in a terminal:

```

sudo grub-install /dev/sdb

```

Finally, you can try supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by xarroyo on 2007-09-06
Hi Merlin..
From what i read of SGD howto i understand that it just makes media to boot to any OS.. But what i would like to do is to fix the HDD to install the GRUB and choose the OS i want without inserting the CD or USB everytime i want to choose a different OS. Or do i make this cd to start the Ubuntu which was already installed and then insert any code to install the grub! 

Thanks for your help,

Xavier

---

### Post by merlinus on 2007-09-06
The how-to is in my post #3 in this thread.  But it seems this did not work for you.

Supergrub will install grub to the mbr -- did this also not work?

Also, post results of:

```

cat /boot/grub/menu.lst

```-merlin

---

### Post by xarroyo on 2007-09-06
I just tried to boot in the pen drive... but it didn't work.. I will try later with the CD's since i don't have any by the moment.. I hope this fix the GRUB problem.. If i have any problems, i will post!! I hope you can still help me!!

Thanks..
Xavier

---

### Post by rsambuca on 2007-09-06
If you have the liveCD, just plop it in and open a terminal:

sudo grub
root (hd1,5)
setup (hd1)
quit

---

### Post by WiseOdd on 2007-09-09
Thx a bunch for the help in this thread. It just saved my ubuntu install.
Only problem: 
after using Super GRUB to restore my original GRUB, theres no problem booting ubuntu. 
What should i do, if i want to be able to boot the windows partition in GRUB as well? 

If I want to do that now, then I have to use S-GRUB to manually select the windows part. and boot it. Even though i only need the win part. to play games, it would be nice not to have to do all that...

Is it possible to manually configure GRUB to find and recognize the win part., so it will be added?

Again; Thx a bunch. You've already saved me hours of trying to boot my Ubuntu!!!

---

### Post by merlinus on 2007-09-09
Post results of

```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by WiseOdd on 2007-09-09
sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       10699    76172197+  83  Linux
/dev/sda3           10700       10942     1951897+  82  Linux swap / Solaris
/dev/sda4           10943       12161     9791617+   7  HPFS/NTFS

---------

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=63c4f6ed-128c-4cc9-afc2-73f7206f769a ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=63c4f6ed-128c-4cc9-afc2-73f7206f769a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=63c4f6ed-128c-4cc9-afc2-73f7206f769a ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=63c4f6ed-128c-4cc9-afc2-73f7206f769a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=63c4f6ed-128c-4cc9-afc2-73f7206f769a ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2007-09-09
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#[/COLOR]hiddenmenu

Make this change in the file, for starters, so the grub menu will appear.

Then add after this line:

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR=Red] title        Microsoft Windows XP
root        (hd0,3)
savedefault
makeactive
chainloader    +1
[/COLOR]
```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by WiseOdd on 2007-09-09
soooo, i should gedit the menu.lst to smt like this?:

title           Windows Xp
root            (hd0,3)
kernel          ?
quiet

---

### Post by WiseOdd on 2007-09-09
kk, done that :)

testing

---

### Post by merlinus on 2007-09-09
Our posts crossed.

Add the lines in red.

---

### Post by WiseOdd on 2007-09-09
Yessir!!!

That just did it!!!!!

IT WORKS!

Who ever said Microsoft couldnt be beaten?

Thx Alot! That will save me a lot of pain!

---

### Post by computersly on 2007-09-09
> **xarroyo said:**
> Hey.. 
I have a desktop which came with windows vista home.. I used the Live Cd of ubuntu 7.04 to install it, and everything seems ok.. But when the computer restarts, it doesn't show the grub to pick which OS i want to use, it just goes over windows.. If i insert the live cd and take a glance through Gparted i notice that the ubuntu installation is there... i don't know what's wrong with the grub.. why the grub doesn't show up??? i just can boot to windows and not ubuntu... :S

any thoughts??? 

thanks for the attention,

Xavier

Try partitioning it with patition magic, and make a swap file too.
I always use partition magic, works awsome for me.
Let me know if that works,
computersly

---

### Post by merlinus on 2007-09-09
> **WiseOdd said:**
> Yessir!!!

That just did it!!!!!

IT WORKS!

Who ever said Microsoft couldnt be beaten?

Thx Alot! That will save me a lot of pain!

Excellent news!  Glad I could help.

---

### Post by xarroyo on 2007-09-26
Hi.. Sorry for the delay.. i've been busy..
now i am back to solve the problem.. i have tried by delete the ubuntu partion and re-install it again.. but nothing happened!! the grub didn't show up-- so i followed the steps :

```
sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit
```

this appear on the 
```
grub> find /boot/grub/stage1
 (hd1,2)
```

and i replaced them.. finally i got root(hd1,2) and finally on setup(hd1)

when i did this the grub appear, i was glad until i selected any OS.. it direct me to an error..

If i select to boot to Ubuntu i get the following message:

Error 22
No such partition

If i select to boot to Windows i get the following message:
Starting up..
Invalid system disk


here i add my new fdisk


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    c  W95 FAT32 (LBA)
/dev/sda2            5100       10011    39455640    f  W95 Ext'd (LBA)
/dev/sda5            5100       10011    39455608+   b  W95 FAT32

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       12753       48640   288270328+   7  HPFS/NTFS
/dev/sdb2               1         498     4000153+  82  Linux swap / Solaris
/dev/sdb3             499       12752    98430255   83  Linux

```


So, what do i have to correct on the menu.lst ???? how can i modify it!

---

### Post by merlinus on 2007-09-26
```

gksudo gedit /boot/grub/menu.lst

```

will allow you to edit the file.  But you may wish to post it here first.

---

### Post by merlinus on 2007-09-26
Info on grub error 22:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by xarroyo on 2007-09-26
> **merlinus said:**
> ```

gksudo gedit /boot/grub/menu.lst

```

will allow you to edit the file.  But you may wish to post it here first.

if i do it outside the grub> i get the menu.lst empty... no code..
if i do it inside the grub> i get the message Error 27: Unrecognized command

---

### Post by merlinus on 2007-09-27
Are you running from the live cd?  If so, you will have to mount ubuntu first.

```

sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb3 /media/ubuntu

```

Then post results of:

```

cat /media/ubuntu/boot/grub/menu.lst

```

---

### Post by xarroyo on 2007-09-28
thanks.. here is the grub

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=6015e276-ab2f-4aa9-8b4d-675ae82ce6bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6015e276-ab2f-4aa9-8b4d-675ae82ce6bd ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6015e276-ab2f-4aa9-8b4d-675ae82ce6bd ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by merlinus on 2007-10-01
What is the boot order of your hdds in BIOS?

Also, you might get rid of the boot flag on sda1, and the map statements in the windows lines in menu.lst.

---

### Post by merlinus on 2007-10-01
You might also check what grub lists for root.  Press e at the opening menu to make sure it says (hd1,2).

---

### Post by xarroyo on 2007-10-09
Now it is finally solved.. the grub was installed.. but the real problem was that i was doing this on a Desktop PC which has two HDD.. The problem was that one Disk has a IDE socket and the other HDD has a SATA.. The OS (windows and Ubuntu) were installed on the SATA.. and on the BIOS the boot order was to go first with the SATA. So the solution was replace on the bios the order boot and make it to boot first with the IDE.. then i restarted and the Grub finally appear.

It seems that IDE has a priority to boot.. I read it in some spanish site, so he mentioned to do this, and it finally worked!

Thanks Merlin for your help and your advices!!

---

