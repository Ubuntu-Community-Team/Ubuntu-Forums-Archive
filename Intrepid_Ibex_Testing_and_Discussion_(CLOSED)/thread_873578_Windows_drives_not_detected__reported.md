---
title: "Windows drives not detected / reported"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-07-29
My Windows XP (NTFS) drives are no longer reported / accessible with 8.10.

I'm running a clean install of a3.

Any suggestions please?

---

### Post by forger on 2008-07-29
1) how did you install intrepid? what partitioning method in the installer did you choose?
2) post the output of the following command:
```
sudo fdisk -l
```

3) someone else should take it from here :)

There's a slight chance that you have erased your windows partitions, hopefully that's not the case

---

### Post by DavidONE on 2008-07-29
1. manual install from alpha 3 LiveCD.  I had 8.04 installed before with partitions for 'Swap' (1GB), '/' (8GB) and the remainder of the 750GB for '/home'.  I formatted '/' and deleted all settings from '/home' before installing.

2. ```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16d316d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10454    83971723+   7  HPFS/NTFS
/dev/sda2           10455       91200   648592245    f  W95 Ext'd (LBA)
/dev/sda5           10455       91200   648592213+   7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17301730

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2   *         123        1095     7815622+  83  Linux
/dev/sdb3            1096       91201   723776445   83  Linux

```

3. no worries - thanks for your help. :)  As you can see, the fdisk shows that the XP partitions are there, but they're not being shown on my desktop or in Nautilus (that I can find).

The Windows partitions are fine - I've booted in to XP since installing 8.10.

---

### Post by ronacc on 2008-07-29
I wonder if this is part of bug# 251991  , cd/dvd's and usb sticks are mounted and opened twice when inserted  and other linux partitions are shown in places>computer and nautilus sidebar but cannot be mounted as user . Try this switch user to root and see if your windows partitions show up . I don't have any windows partitions to try it , and you can mount your linux partitions as root and they will show and be accessabile when you switch back to user .

---

### Post by DavidONE on 2008-07-29
I logged in as root using [http://www.linuxquestions.org/questions/showthread.php?p=2709694#post2709694](http://www.linuxquestions.org/questions/showthread.php?p=2709694#post2709694) which subsequently stopped my wireless from connecting, which I solved by deleting all network config files I could find in /home (not elegant, but it worked).

I still couldn't see my XP partitions from root account.  I'll keep an eye on [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991) unless there are any other suggestions here.

Thanks again. :)

---

### Post by ronacc on 2008-07-29
oh well it was a guess , I havent run windows for many years so I couldn't try it myself that way . A better way to change to root once you have set your root password (not the password you use for sudo) is to use the green running man at the top right corner, that brings up a box wher you can choose switch user ,cancel, or logout . switch user will let you login as root without killing your "user" session which logout would , then you can switch back and take up where you left off . also be careful of sudo and gksudo right now , performing some operations with them nukes your system . invoking fileroller as root and sometimes using a root nautilus (gksudo nautilus) to copy files are 2 things that have bitten me that way.

---

### Post by DavidONE on 2008-07-29
Hmmm.  I did try setting root pswd, logging out of MYUSER and then in to root but I was still refused at the login screen.  Must've FUBARed something... not unusual - I'm more dangerous than competent in Linux. ;)

This is just a test install for me - I keep trying to migrate off Windows, but there's always a little something that keeps me hooked.  One day....

Thanks once again. :)

---

### Post by ronacc on 2008-07-29
jumping into the middle of a developement release is not the easiest way to switch off of windows but you will learn to swim :) or atleast tread water real good :lolflag:

---

### Post by SunnyRabbiera on 2008-07-29
ibex is an alpha, not good for newcommers or non crazy people

---

### Post by Gina on 2008-07-29
I'm afraid I'm not quite crazy enough to install Intrepid on the only machine I have that has Windows on it (there are still very occasional times when I require Windows - eg. support for friends).  I'm pretty sure this is all tied in with the Nautilus mount bug though so I suggest using mount from the command line (with sudo).  I can't get Nautilus to mount HD partitions other than the /.

---

### Post by ronacc on 2008-07-29
@ gina  as I said above you can "switch user " to root mount the drives either from place>computer or nautilus , they will show up twice of course:confused: then when you switch back to user they will stll show on the desktop and be availble , having now nuked my system twice with sudo and gksudo I avoid using it until that bug is squashed .

---

### Post by Gina on 2008-07-29
Yes, I should have added "as normal user" when talking about Nautilus.

Showing twice or not at all... fun eh???? :lolflag:

---

### Post by cecilpierce on 2008-07-30
It works for me after I "sudo mount /media/sda1" and it has to be in /etc/fstab >
/dev/sda1 /media/sda1 ntfs defaults,umask=007,gid=46 0       1

---

### Post by jfernyhough on 2008-07-30
Something odd happened to my install during updates which messed up group memberships. My user account had been removed from pulse, samba, and in this case most importantly, fuse.

ntfs-3g uses fuse to mount your NTFS Windows drives, and your user must be allowed to use fuse.

Go to System,Administration,Users and Groups.
Click Unlock, type your password.
Click Manage Groups.
Find and select fuse, click properties.
Check the select box beside your username, click OK.
(at this point it's worth checking users,pulse,pulse-access,sambashare and making sure your user is part of each of those groups too)
Click Close, Close.

You'll have to log out and back in to check the effects, but this should mean your Windows drives reappear. As is by magic. :)

---

### Post by DavidONE on 2008-07-30
Thanks for the suggestion.  I was already a member of the fuse groups, although not 'users'.  I added myself to that group and logged out / in, but no difference.

---

### Post by DavidONE on 2008-08-09
Bug [251991]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991") has been fixed and I still can't access my Windows drive.

I tried cecilpierce's suggestion of "sudo mount /media/sda1" but it reported 'can't find'.  I checked and there is no 'etc/fstab' or 'etc/mtab'.  Is that significant?

Any other suggestions please?  Otherwise I guess it's a bug report....

---

### Post by cariboo on 2008-08-09
> I tried cecilpierce's suggestion of "sudo mount /media/sda1" but it reported 'can't find'. I checked and there is no 'etc/fstab' or 'etc/mtab'. Is that significant?

You are missing a / it should be /etc/fstab and /etc/mtab. To manually mount a partiton the command is:

```
sudo mount /dev/sda1 /media/sda1 
```

Jim

---

### Post by DavidONE on 2008-08-09
Thanks, Jim.  Yeah, I knew it was '/etc/fstab' - just forgot to type out the leading '/'.

I tried your code and got:

```
fuse: failed to access mountpoint /media/sda1: No such file or directory
```

...and, sure enough, there's no /media/sda1 - all that's contained in /media is 'link to folder cdrom' and 'cdrom0'.  Do I need to manually create 'sda1', etc.?

---

### Post by Gina on 2008-08-09
Yes - you need to make a directory as mountpoint eg. **sudo mkdir /media/sda1** or **sudo mkdir /media/mydata** etc.  Then you can use **mount** to associate the drive or partition with the mountpoint.

---

### Post by DavidONE on 2008-08-10
Thanks, Gina - that worked, I can now access my XP drives.

Bug raised: [https://bugs.launchpad.net/ubuntu/+bug/256587](https://bugs.launchpad.net/ubuntu/+bug/256587)

---

### Post by duncan_nz on 2008-08-18
I was having the same problem as DavidONE, after reading this thread and the solutions, I can confirm the bug.

Also mounting the drives manually seems to be the way to go.

---

