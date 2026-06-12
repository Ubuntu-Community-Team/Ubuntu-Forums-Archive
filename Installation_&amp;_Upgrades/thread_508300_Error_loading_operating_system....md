---
title: "Error loading operating system..."
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by meyou on 2007-07-24
Ok, a little background. I had WinXP installed on a 36gb raptor and I used Acronis Disk Director to move the partition to my new drive, a 150GB raptor. After doing this Windows would only boot if I had the WinXP CD in, otherwise I'd get the above error message. I knew this had something to do with the MBR/partition tables, but I figured installing Ubuntu for dualboot would solve this. It didn't.

 I get the same message now that Ubuntu is installed, and putting an XP cd or the Ubuntu CD(and choosing boot first hard disk) allows me to load GRUB and choose what to boot.

How can I fix this?

---

### Post by meyou on 2007-07-24
bump

---

### Post by dannyboy79 on 2007-07-24
could be the boot flag is not set on the hard drive. do you have the correct partition being active? ALso, are you sure that the bios is pointing to the correct device? When you installed Ubuntu, did you chose to install Grub to the MBR or a boot slice patition? (or whatever it's called) Pop in the Ubuntu live cd and then open gparted. there should be a pull down for boot flag.

it sometimes means that the mbr needs to be trashed and then recreated. it sometimes means that the BIOS needs to be changed from Auto to LBA for the hard drive detection.

the gparted livcd has TestDisk on it which can rewrite your boot sector and or MBR if need be. that livecd is invaluable and I suggest anyone who dual boots or knows anything about computers (win/linux) has it at their side!!!

---

### Post by meyou on 2007-07-24
Well at the advice of someone else I've just installed gparted and was about to check that. Do I need to run it from the LiveCD or could I just run it from my installed copy of Ubuntu?

---

### Post by meyou on 2007-07-24
Well doing a little investigating in gparted shows that HDA had the bootflag on, but that's not my boot drive. SDA is my bootdrive.

SDA1 = NTFS = /media/WINXP
SDA2 = EXT3 = / (BOOT)
SDA3 = Extended
SDA5 = linux-swap

I removed the bootflag from HDA hoping that might help, would it?

---

### Post by dannyboy79 on 2007-07-24
you need to set sda to have the boot flag and make sure that your bios is booting the sda drive first before the hda drive.

---

### Post by meyou on 2007-07-24
SDA2 currently has the bootflag, do I need to set it on SDA1 also?

The BIOS is already set to boot the SDA drive first.

---

### Post by meyou on 2007-07-24
here is a screenshot of gparted

[img]http://m3j.adsyp.net/gpartedss.png[/img]

---

### Post by dannyboy79 on 2007-07-25
> **meyou said:**
> SDA2 currently has the bootflag, do I need to set it on SDA1 also?

The BIOS is already set to boot the SDA drive first.

no you shouldn't have to IF you actually have the files that grub is looking for located within /boot/grub/ which is contained within sda2. Are you sure you installed Grub to the MBR? You could try that again following this procedure:
BOOT WITH LIVE CD
OPEN TERMINAL WINDOW
```
sudo fdisk -l
```
this should list all ur Hard disk's
(your main ubuntu partition should be /dev/sda2 as you have already told me)
```
sudo grub
```
grub> ```
find /boot/grub/stage1
```
this will return something like (hd0,1) {this means that it found grub's file within the first hard drive and on the second partition as grub starts at zero)
grub> ```
root (hd0,1)
```
grub> setup (hd0)
grub> quit


If that still doesn't work, it sounds like your MBR is messed up and isn't accepting anything to be written to it. You'll need to only wipe out the first 446 bytes of your MBR which will LEAVE your partition tables alone!!! You can do that with this command from within a live cd:
dd if=/dev/zero of=/dev/sda/ bs=446 count=1
(where hda is the actual drive that you want to remove the first 446 of the MBR from)

Let me know how it goes.

---

### Post by meyou on 2007-07-26
> **dannyboy79 said:**
> no you shouldn't have to IF you actually have the files that grub is looking for located within /boot/grub/ which is contained within sda2. Are you sure you installed Grub to the MBR? You could try that again following this procedure:
BOOT WITH LIVE CD
OPEN TERMINAL WINDOW
```
sudo fdisk -l
```
this should list all ur Hard disk's
(your main ubuntu partition should be /dev/sda2 as you have already told me)
```
sudo grub
```
grub> ```
find /boot/grub/stage1
```
this will return something like (hd0,1) {this means that it found grub's file within the first hard drive and on the second partition as grub starts at zero)
grub> ```
root (hd0,1)
```
grub> setup (hd0)
grub> quit


If that still doesn't work, it sounds like your MBR is messed up and isn't accepting anything to be written to it. You'll need to only wipe out the first 446 bytes of your MBR which will LEAVE your partition tables alone!!! You can do that with this command from within a live cd:
dd if=/dev/zero of=/dev/sda/ bs=446 count=1
(where hda is the actual drive that you want to remove the first 446 of the MBR from)

Let me know how it goes.

well, before reading this post, I tried doing "grub-install /dev/sda"

now grub actually loads properly, but when I choose ubuntu I get something along the lines of "invalid partition" and when I choose WinXP I get something along the lines of "NTLDR missing"

Using the Ubuntu LiveCD and choosing "boot from first hard disk" gives me the exact same grub menu, except every option works as intended.

Should I still go ahead with the procedure you posted?

---

### Post by meyou on 2007-07-26
bump

---

### Post by dannyboy79 on 2007-07-27
> **meyou said:**
> well, before reading this post, I tried doing "grub-install /dev/sda"

now grub actually loads properly, but when I choose ubuntu I get something along the lines of "invalid partition" and when I choose WinXP I get something along the lines of "NTLDR missing"

Using the Ubuntu LiveCD and choosing "boot from first hard disk" gives me the exact same grub menu, except every option works as intended.

Should I still go ahead with the procedure you posted?

ok, now the problem is that your menu.lst located within /boot/grub/ isn't pointing to the correct location to where your kernel is. That's also the case with your WinXP info within that same file. So, please boot to a livecd, mount your /dev/sda2 partition whereever you'd like, then cd to /boot/grub/menu.lst and please post the contents of that file so that I can help you edit it. Also please post the contents of the device.map file as well. ALso let me know what the output of sudo fdisk -l  is? Then I can help once I get ALL the info I have requested.

---

### Post by mordalo on 2007-07-29
Ubuntu noob here...

I'm having the same problem as the person who posted this originally, and followed your instructions to the letter, and they worked (thankyouverymuch), and Ubuntu boots normally.

XP isn't working, however.  I'm getting an error "NTLDR is missing, press CTRL-ALT-DEL to reboot".

XP is still there.  I can see read (and write, thanks to installing Automatix) to the NTFS partitions and I can see NTLDR, boot.ini and ntdetect.com

Since you asked for it, here's my device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

menu.lst:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

And here's the boot.ini for XP:

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Any help will be appreciated!

---

### Post by dannyboy79 on 2007-07-29
> **mordalo said:**
> Ubuntu noob here...

I'm having the same problem as the person who posted this originally, and followed your instructions to the letter, and they worked (thankyouverymuch), and Ubuntu boots normally.

XP isn't working, however.  I'm getting an error "NTLDR is missing, press CTRL-ALT-DEL to reboot".

XP is still there.  I can see read (and write, thanks to installing Automatix) to the NTFS partitions and I can see NTLDR, boot.ini and ntdetect.com

Since you asked for it, here's my device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

menu.lst:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

And here's the boot.ini for XP:

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Any help will be appreciated!

well just looking at something is wrong. according to your ubuntu boot options you're "root" ubuntu partition is on (hd1,1), which would be hard drive sdb and partition 2. So, I also need to see your sudo fdisk -l please. you could simply try to change your windows grub entry to hd0,0 IF windows is installed on sda, that should do it. then if that's the case, you don't need the map lines because those are only for when windows is not on the first hard disk. Windows is picky like that. 

so it would be:
#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

good luck. also, please let me know if you're dual booting where each os is on a different hard disk or dual booting with 1 hard disk.

---

### Post by mordalo on 2007-07-30
> **dannyboy79 said:**
> well just looking at something is wrong. according to your ubuntu boot options you're "root" ubuntu partition is on (hd1,1), which would be hard drive sdb and partition 2. So, I also need to see your sudo fdisk -l please. you could simply try to change your windows grub entry to hd0,0 IF windows is installed on sda, that should do it. then if that's the case, you don't need the map lines because those are only for when windows is not on the first hard disk. Windows is picky like that. 

so it would be:
#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

good luck. also, please let me know if you're dual booting where each os is on a different hard disk or dual booting with 1 hard disk.

Thanks for the advice, DannyBoy, but alas, it's still not booting into XP

Here's my fdisk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9533    35616105   83  Linux
/dev/sdb3            9534        9729     1574370    f  W95 Ext'd (LBA)
/dev/sdb5            9534        9729     1574338+  82  Linux swap / Solaris

sda1 is a SATA drive and is just for storage.  There's no OS on the SATA (sda1) drive.  

sdb is IDE, with Windows in the first partition. I checked the BIOS and it's set to boot to the IDE drive first

I noticed that the NTFS partition on sdb2 is the boot partition, but shouldn't it be the Linux partition, since that's where GRUB is located?  

I know Windows is picky...I've worked with it (alas) for the last 10+ years, but have only started to venture into *nix distros in the last year or so. 

Thanks for the help.  It's much appreciated!

---

### Post by merlinus on 2007-07-30
Did you try this in /boot/grub/menu.lst:

#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

-merlin

---

### Post by mordalo on 2007-07-30
I got it.

Went into an older version of the menu.lst file.  It didn't have the newer kernel listed, but when I copied it into the file, and tweaked it a bit, it worked.

Here's the correct file:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=09054512-dcc2-4cd0-8dfc-351496b8084a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

Once again, thanks for all the help, folks!

---

### Post by dannyboy79 on 2007-07-31
just so you're aware, you menu.lst clearly states that your kernel is located on /dev/sda2. Since your device.map states that (hd0) is /dev/sda. As I said earlier, something just isn't right. It's always possible that the device.map isn't correct any longer if you moved drives around. But I am just pointing this out so if you have problems in the near future, you can understand a little better.

I am glad that by taking the map command out for your winxp booting that worked, along with changing the (hd1,0) of course. Since I didn't know whether you were booting 2 seperate disks or what, I couldn't properly help you. Out of curiosity, what does the #groot line state within your menu.lst. It should be whereever grub's root location is which is normally the same location that your kernel is at. In the /boot partition.

I also notice you haven't gone to the newest kernel, that will then change your ide disk drive BACK TO HDB . It has to do with the libata ide driver I believe. ANyway, if you aren't using the UUID within your fstab, you won't be able to boot up again. Good luck

---

### Post by mordalo on 2007-08-12
I'm sorry it took me so long to respond.  I was AFK for about a week, and when I got back, it turns out the IDE hard drive was dying!

I tried to salvage it, but no good.  Tried to image it, but it didn't work.  Decided the best thing to do would be a new install on a new drive.

I did, and once again, I received the errors.  Thankfully, I had your tips and suggestions saved (printed out before  the drive died) and they worked with no problems.

Thanks again for the help, folks!

---

### Post by dannyboy79 on 2007-08-13
glad I could help.

---

### Post by Khell on 2007-08-14
alright, I am having the same problem.  I am trying to dualboot windows xp pro and ubuntu and at first windows tried to boot and gave me the blue screen of death.  Then I setup the grub and got the dual boot option, but when I try to enter ubuntu i get "Error 22:  No such partition"  and when I try to boot XP pro I get the message "NTLDR is missing  Press Ctrl+Alt+Del to restart.  I can get ubuntu to boot from the first hard drive using the cd but I can't get anything from XP pro.  I am going to post my menu.list

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=63c1a46a-782c-4226-83dc-18bc52eb2066 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=63c1a46a-782c-4226-83dc-18bc52eb2066 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=63c1a46a-782c-4226-83dc-18bc52eb2066 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=63c1a46a-782c-4226-83dc-18bc52eb2066 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


and my device.map


(hd0)	/dev/hdb
(hd1)	/dev/sda


and the output of sudo fdisk -l


Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       15547     2000092+  82  Linux swap / Solaris
/dev/sda3   *       15548       20527    40001850   83  Linux
/dev/sda4           20528       30401    79312905   83  Linux


I am also a noob to ubuntu so my final question is what is the MBR?
:confused:

---

### Post by dannyboy79 on 2007-08-14
what does your 
#groot 
line look like in your menu.list. This always very hard to troubleshoot but the MBR is the Master Boot Record. NOw since you have 2 different drives, you have 2 MBR's. Which ever hard drive is being booted first per the bios, that's the drive you want to install grub to. Check out the this Grub page, it's invaluable.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Khell on 2007-08-14
ok, here is me groot, or at least I think this is it.


## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

---

### Post by Khell on 2007-08-16
ok, I got the problem fixed and this is what I found and did.  I had just reinstalled windows xp pro and didn't have service pack 2.  I was installing it on a 250 gig drive but windows service pack 1 wouldn't except that large of a drive.  so when i installed ubuntu it was currupting the install for windows.  also my computer was setting the serial drive as hd1 and my parallel as hd0.  well when i installed ubuntu it was putting the grub in the MBR of my parallel hard drive and both my OS's are on my serial drive.  This was why I was getting the errors when I tried to boot from grub.

To fix this I simply unplugged my parallel drive then reinstalled windows, then updated to service pack 2.  Once I did this windows registered the full 250 gig.  after this was done I installed ubuntu and updated it.  After all of this was done then I plugged my parallel drive back in.  Windows picked the drive up immediately but I will have to mount it for ubuntu.

I hope telling what I have done will help anyone else having this trouble.

---

### Post by dannyboy79 on 2007-08-17
great job, way to work through it.

---

### Post by Khell on 2007-08-17
What I need to know now is how to permanently mount me second hard drive on my ubuntu desktop.  Any suggestions on this would be welcome.  I was told to use fstab but I am not sure how.  I am searching the forum for info now and hope to solve this problem as well.

Thanks for your help so far.

---

### Post by anandus on 2007-09-22
Hi, me too has this problem, so I think it's okay to post it here instead of making a new topic.

I installed XP first, then Ubuntu (guide resize). But booting from the Hard Disk gives me a 'error no operating system', instead of Grub.
Both are installed on the first SATA disk.

Here is my device.map:
```
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda
(hd3)	/dev/sdb
```

Here is my menu.lst (with the unneeded bits taken out):
```
[...]

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=135683da-7a33-4b77-a54d-2b6cfaea8dbf ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

[...]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

And here is my fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9777    78533721    7  HPFS/NTFS
/dev/sda2   *        9778       19057    74541600   83  Linux
/dev/sda3           19058       19457     3213000    5  Extended
/dev/sda5           19058       19457     3212968+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30401   244196001   83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  83  Linux
```

Call me silly, but shouldn't it just boot?
The settings in the Bios are okay, I've also tried choosing the disk (with F8 during startup) and booting the Live-cd and choosing 'boot first hard disk'.

All to no avail. What did I miss? :)

---

