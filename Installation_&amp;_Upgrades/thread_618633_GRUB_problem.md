---
title: "GRUB problem"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by PfromD on 2007-11-20
I'll try to detail all my steps in case what seems minor actually can be the cause of the problem at hand.
First I installed 7.04 on the second SATA drive on the raid controller of the MB. The raid is not being used as a raid, and this disk held a knoppix install prior to the ubuntu install.
All worked well, and grub correctly let me select either windows (disk 1) or ubuntu (disk 2).
Ubuntu it self didn't work  100% though: the 'X-server' didn't start up due to some missing driver. I went to ubuntu.com (via windows) to ask for help on this issue and saw that 7.04 wasn't the most recent ubuntu. So I fetched the Gutsy Gibbon 7.10 and used partition magic to clean the drive completely before this 7.10 install. 
The install seemingly worked ok, but when completed and the pc needed to be restarted (w/o the cd ofcourse) GRUB says "ERROR 17" and then halts. Can't even boot windows :(
How do I go about this obstacle?

---

### Post by Pumalite on 2007-11-20
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
See if changing the boot order of your hard drives fixes the problem. If not; read on.

---

### Post by PfromD on 2007-11-20
I've tried every boot setup possible without it making any difference.
I then 'read on' and dl'ed the grub superdisk and ran a fix, and it helped to the extend that the grub menu now is loading, but when I select either one of the Ubuntu options it reports back, that the disc can't be mounted. Which can't be entirely true as I've had a couple of different Linux distros installed on that disk, and they mounted/booted just fine.
Furthermore when attempting to start windows via the fixed grub I'm being told that hal.dll is missing/corrupt ... but I remember having run into that error message some years ago when adding a new disk, and that this error was fixed w/o too much hazzle. 
But it doesn't change the fact that I can't seem to boot Ubuntu properly :(
And this in fact is the first time I've encountered problems of this sort during a Linux install, but I'm not in any way a Linux guru so please dumb down any help so I'm able to keep pace ;-)

---

### Post by meierfra on 2007-11-21
At the grub menu at boot up  press "c".  This will get you a "grub>" prompt. Type

```
find /boot/grub/menu.lst  
```
 (l is a lower case L, not the number one) 

The output will by something of the form (hdx,y)   (probably (hd0,0) or (hd1,0)) You  will need to remember  the exact values for x and y.

Press Esc to get back to the grub menu. Select Ubuntu, but do not  press enter. Press "e" instead.  At  the new screen press "e" again. 

You will get a screen with just one line : " root (hd?,?)"
Change the line so that it reads

root (hdx,y)

So  for example if the output of "find ...." was  (hd1,2)  change the line to "root (hd1,2)"

Press Enter and  then "b"

This should boot you into  Ubuntu.

This method works for a one time boot. To really fix you problem you need to edit the file "/boot/grub/menu.lst"

Open a terminal (Applications->Accessories->Terminal) and type


```
cd /boot/grub (this changes the current directory)

sudo cp menu.lst menu.lst.backup (creates a back up of menu.lst)

gksudo gedit menu.lst  (opens "menu.lst" in a new window)
```

Look for the line

#groot (hd?,?)

and change it to

#groot (hdx,y)


Save and close  the file. Back in the terminal type

```
sudo update-grub
```

This should allow you to boot  into ubuntu from now on. 

To be able to boot into windows you will have to edit "menu.lst" one more time.  Please post  the output of 

```
sudo fdisk -l
```
(again lower case L) and  the actual values  for (hdx,y), and I will be able to help you with that.

---

### Post by PfromD on 2007-11-23
yay. So far so good :) Ubuntu loads as intended.
The output of fdisk -l reads :
```

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43d6d784

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12268    98542678+   7  HPFS/NTFS
/dev/hda2           12269       14946    21511035    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d66d660

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        4865    39070080    f  W95 Ext'd (LBA)
/dev/hdb5               2        4865    39070048+  82  Linux swap / Solaris

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4233ded4

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               2       36483   293041665    f  W95 Ext'd (LBA)
/dev/hdc5               2       36483   293041633+   7  HPFS/NTFS

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d163d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4500    36146218+   7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedf7e9d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4310    34620043+  83  Linux
/dev/sdb2            4311        4500     1526175    5  Extended
/dev/sdb5            4311        4500     1526143+  82  Linux swap / Solaris

```
I figured the correct entry for windoze would be hd2,0 but apparently that wasn't the case
Right now the last entry in menu.lst reads
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		1
root		(hd2,0)
savedefault
makeactive
chainloader	+1

```
where "title 1" obviously should be changed to "title Windows XP"

---

### Post by meierfra on 2007-11-23
Since you didn't tell me the what (hdx,y) really was and since you  have various different HTTP/NTFS partition it is a little difficult to guess the correct parameters. But you should be able to figure them out by pressing "c" at the grub-menu at boot up. Type

root (hds,t)
map (hd0) (hds)
map (hds) (hd0)
makeactive
chainloader +1
boot


If you know that Windows is on the  first partition of its drive, then  use t=0, if its the second partition , use  t=1.
Since you have five different hard drives, s could be anything from 0 to 4.
Actually if windows is first in the boot sequence in the bios, then s=0. If its second then s=1 and so on.
If s=0 skip the two lines starting with map.

If this did not work, try different values for s and t.
Once you successfully booted into windows change menu.lst accordingly:


title  Windows XP
root (hds,t)
map (hd0) (hds)
map (hds) (hd0)
makeactive
chainloader +1

Of course choose the values for s and t which worked at the boot up. Skip the map lines if s=0. You can choose any title you like, it won't effect to booting process.

---

### Post by PfromD on 2007-11-23
heh, sry .. the correct entry for booting linux is hd3,0

---

### Post by meierfra on 2007-11-23
```
the correct entry for booting linux is hd3,0
```

Actually with your five different hard drives and various HTTP/NTFS partition, I'm still not able to guess the correct parameters. Just  try to follow  the directions from my previous post. If you need more help let me know what the boot sequence is  (check the bios if you don't know) and also let know where Windows is installed (which hard drive  and which partition)

---

### Post by PfromD on 2007-11-23
Well, the thing is, that the two drives in question (the linux- and the windows-drive) aren't part of the BIOS as such. I can only access the BIOS for those two drives after the BIOS has has done its thing. But that's why I assumed that the windows drive where (hd2,0) as the drive that now serves linux is the second drive on the built-in raid controller.  
The boot sequence in the BIOS is cd-rom, HD0, but the raid controller overrides this in some sense, as HD0 (IDE0) is one of the storage-disks ... not quite sure which one though.
I'm not totally sure if the windows-partition is the first, but as far as I recall it is, and a small one for documents, on the same drive.
But perhaps the easiest thing is just to try out a bunch of the different options for (hds,t)

---

### Post by PfromD on 2007-11-23
(hd0,0) returns "missing/corrupt hal.dll
(hd0,1) missing ntldr
then "drive/partition doesn't exist" until (hd3,0) which is the linux one, and (hd4,0) (missing hal.dll) which might be the right one as it's the second drive on the raid controller that is set to boot and the drive preceding it *probably*  gets numbered after the drive that's set as boot.
I'm not too sure why either missing hal.dll or ntldr occurs though .. but I'll try to find a guide on this issue and try to resolve it

---

### Post by meierfra on 2007-11-23
Good luck. It's probably a raid problem, and I know  nothing about raid.

---

### Post by PfromD on 2007-11-23
Might be, but I can't see why it should pose a problem now when it hasn't previously .. I've had functional dual-boots with other distro's on the drive that now holds Ubuntu.
I'm a bit tired to be fooling around with this now however ... it's usually when a bit too tired that the stupid mistakes are done ;)

---

### Post by Pumalite on 2007-11-23
Just in case; read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by meierfra on 2007-11-24
Couple of suggestions:

1)  Don't forget to use the  two map lines  with  root (hd1,0), root (hd2,0) ...

2) You might be able to figure how grub  orders the hard-drives by using

```
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (hd4)

```

after you pressed "c" at the grub-menu. geometry (hd0) will list the partitions on hard drive (hd0).

---

### Post by PfromD on 2007-11-30
Better late than never, but I've tried out a couple of the suggestions now.
What I don't quite understand, is why all of the geometry (hdx) commands return the apparent number of partitions, but all except the ext3 partition on hd3 are "unknown filesystem". Furthermore I'm beginning to suspect that the worst has happened; windows-partition overwritten.
This I fear because when trying to do a correctional install using the windows cd, none of the harddisk are reported to contain a windows install :(
I seem to recall that this problem also occurred the last time a "missing hal.dll"-error arose when inserting a new harddisk that got indexed before the windows-hd, and that this had something to do with the drive having been formatted as a "dynamic drive" if I remember correctly. What I don't remember is how I went about fixing it.
I would think that the risk of the windows-drive being formatted is fairly low as I've been pretty attentive on selecting the drive I *knew* was the linux-drive when installing Ubuntu, but ofcourse the risk is always there.
But just from booting from the windows-cd and attempting a fix, I have to correct the GRUB loader using Super GRUB Disk ... amazing; just inserting/booting the windows disk starts messing up the booting procedure on the existing hd's/BIOS.
But my uneducated guess is, that if the entire windows-drive/partition actually where formatted, the "missing hal.dll"-error wouldn't occur, as nothing at all would then happen, or at best some kind of "missing OS" error would be returned .. so I'm hoping that windows is still there and I just don't know how to access it to fix it.

---

### Post by Herman on 2007-11-30
I normally keep away from any threads that contain teh word RAID, I have read a little about RAID, but there are so many different knids, if seems like a mamoth job to begin to understand them all and how they might affect booting and so on.
What I can offer you is this link, [hal.dll is missing or corrupt]("http://users.bigpond.net.au/hermanzone/p15.htm#hal.dll_is_missing_or_corrupt") which should be good advise for normal installations when RAID isn't used and some of that information might be useful to you anyway. It's worth a look.
Probably the part of it that may be most useful to you would be the link to Miles Comer's website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"), where you can download a Windows type of Super Bootloader CD, or USB, etc. Those have their own copy of NTLDR, NTdetect.com, and boot.ini in them, so you should be able to boot Windows with one of those almost no matter what! :)

If it's there at all.

Regards, Herman :)

---

### Post by PfromD on 2007-11-30
Well, The windows partition doesn't appear when viewing the hard drives through "places/computer", but a partition labelled "te" does, and it didn't show on the initial install of 7.04 either ... which worked a-ok as far as the dual-boot goes.
What's weird about "te" is that this partition didn't appear in windows, when I was able to boot it, and it contains some .. er, well porn :redface: that I don't even remember having dl'ed. 
When thinking about it I remember that this partition also appeared when using some of the distro's and live-cd's I've tried earlier.
That the windows partition didn't show via the previous distro's either I think might be due to the "dynamic drive" state of the windows-partition. I think it's "dynamic drive" it's called at least.
I think my best shot at getting it up and running again will be trying the 
bootcfg/rebuild
fixboot
through recovery console or the latter method you suggested. 
I haven't got any floppy disks at this time though, so that can't be done quite yet .. that second method.

---

### Post by PfromD on 2007-12-01
Ok, the bootcfg /rebuild command returns an error of not being able to find any windows installations ... so I guess that means I'm f*cked regarding the original windows install :(
Is there then a method of scanning the disk for documents to recover? I now of various windows-apps to do so, but what about doing it from Ubuntu? And then what about the documents I held in a 'safe' folder using windows' encryption feature? Foolish me didn't backup those prior to installing Ubuntu .... you know "real men don't do backup .. they cry"

---

### Post by Herman on 2007-12-01
Well there is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")  for scanning your hard disk for sectors that look like the start blocks of a partition that has been deleted and restoring the information about the deleted partition to the partition table. That will get all of your files and your operating ssytem and everything back all at once if you haven't overwritten vital sectors yet on your hard disk.

If you did overwrite vital areas of your hard disk already, you would probably still be able to recover a lot of your files with [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

I have used TestDisk and recorded illustrarted examples of what it's like in this web page, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html") in case it helps anyone.
I haven't tried Photorec myself yet.

You can install TestDisk and Photorec in Ubuntu with Synaptic package manager or apt-get and maybe other ways too.

Here's a good  thread,[ Disc Recovery]("http://ubuntuforums.org/showthread.php?t=447849")

Here's a Linux.com article:[How to recover lost files after you accidentally wipe your hard drive]("http://www.linux.com/articles/56588?tid=119&tid=13")

Here's a post, [Re: Recovering NTFS files from ext3 partition...]("http://ubuntuforums.org/showpost.php?p=1988280&postcount=3")

And here's another interesting post I thought was worth saving, [Re: Data recovery software]("http://ubuntuforums.org/showpost.php?p=3536560&postcount=7")

I hope something there will help you out.

Regards, Herman  :)

---

### Post by PfromD on 2007-12-01
ok, it ought to be installed now, but er... how the frink do I run the app? It isn't available through the applications-menu.

---

### Post by Herman on 2007-12-01
>  I have used TestDisk and recorded illustrarted examples of what it's like in this web page, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html") in case it helps anyone.

Regards, Herman :)

---

