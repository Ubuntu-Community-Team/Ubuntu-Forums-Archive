---
title: "Can't seem to get GRUB back after reinstalling Windows..."
date: 2005-04-03
forum: Installation &amp; Upgrades
---

### Post by LoneIgadzra on 2005-04-03
I've been following [these instructions](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) in an attempt to get the GRUB menu back after reinstalling Windows. I get as far as step 4 without incident, where the command "grub> root (hd0,0)" only produces the following error:

Filesystem type unknown, partition type 0x7

Now when I mounted my linux drive in the process of booting off the CD and gaining root access, I picked the one labeled "Linux" rather than "Extended" which produced an error when I tried it. So I'm pretty sure I did that part right. The only thing I can think which might be screwing this up is an assumption that the Linux partition is the first one on hda, when on my computer it is actually /dev/discs/disc0/disc/part5 or something, but since the guide doesn't explain what it is that it's having me type, I have no way of troubleshooting further.

---

### Post by prio on 2005-04-04
What is the output of 
sudo fdsik -l /dev/hda ?
If you are sure you are using the correct linux partition boot in to a rescue disk and run fsck on it to make sure it isn't damaged.

---

### Post by LoneIgadzra on 2005-04-04
I'm assuming you mean this stuff (literally typing 'fdisk -l /dev/hda" does nothing):

~ # fdisk -l /dev/discs/disc0/disc
omitting empty partition (5)

[overall information about size of hard disc]

/dev/discs/disc0/disc/part1  [size information] 7   HPFS/NTFS
/dev/discs/disc0/disc/part2  [size information] 5   Extended
/dev/discs/disc0/disc/part3  [size information] 82 Linux Swap
/dev/discs/disc0/disc/part5  [size information] 83 Linux

(Incidentally, how big should a swap partition be?)

---

### Post by prio on 2005-04-06
Have you tried *root (hd0,5)* ? And *root (hd0,4)*? Are you using scsi or raid? I have no experience with them. General rule of thumb is that swap should be twice physical ram. But I think with 1gb ram or bigger equal amount should be ok.

---

### Post by LoneIgadzra on 2005-04-07
No to the question about SCSI and RAID; just plain old IDE/ATA. And thanks for the info. Got a little farther, using *root (hd0,5)*. Unfortunately the setup command does not go forward error free:

> 
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded. succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2/boot/grub/menu.lst"... failed

Error 22: No such partition

Gah. I imagine I probably screwed it up trying to install GRUB automatically from the Ubuntu installer (by choosing "go back" and then picking "install GRUB" from the menu that comes up).

---

### Post by prio on 2005-04-07
Boot to the grub cli and tyep root (hd0<tab>
And post the output. (Where <tab> is pressing the tab key.)
Also post your /boot/grub/menu.lst file. It seems like its misconfigured.

---

### Post by mike3131 on 2005-04-09
Hi, I am having the same trouble.  i.e., the standard error msg when trying to boot winxp:

 "Booting 'Windows NT/2000/XP'
root (hd0,0)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

It seems like there are a lot of posts regarding this issue on the Ubuntu Forums.  FYI, my WinXP partition is on /dev/hda1.  My output from doing the above command is:

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82

grub>

Also, there is some kind of "fix" for SuSE v9.1 - would it apply to Ubuntu? ( [http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html) )

I have enabled LBA on both my drives in the BIOS.  I have run fixmbr and fixboot using the WinXP installation CD, but that produces an "Operation System Not Found" error at boot.  I have tried rootnoverify.

btw, if there's a sure-fire method of installing Windows/Ubuntu, then I'm willing to wipe my entire drive and start over.  Maybe I should make a /boot partition?

---

### Post by LoneIgadzra on 2005-04-09
[QUOTE=prio]Boot to the grub cli and tyep root (hd0<tab>
And post the output. (Where <tab> is pressing the tab key.)
Also post your /boot/grub/menu.lst file. It seems like its misconfigured.[/QUOTE]

I'm afraid the only access I have to grub is via booting from the Ubuntu 4.10 disc, where those instructions don't do anything. Everything I've done hasn't fixed the basic problem that grub doesn't come up when I boot. I guess I'll just reformat and reinstall Ubuntu when the next version comes out (if it's not out already). As I recall, when I first installed 4.10 it took about 3 hours to download updates in the command line, effectively rendering my computer unusable - an experience I'm not anxious to repeat. It's not like I ever use it anyway; in the rare event that I can find an actual installer for a program (rather than just the source code) I can rarely ever seem to make it work. It was a lot worse when I was using Mandrake though... god, nothing I installed worked.

---

### Post by mike3131 on 2005-04-09
Download the Live CD and issue those instructions.  Make sure to su to root before issuing the grub command (i.e., for Live CD, type "sudo su").

Also, the newest version (Hoary v5.04) is out.

Just FYI, my next plan is to install WinXP on a different harddisk from the Ubuntu install.  Might want to try that if things don't go well.

---

### Post by mike3131 on 2005-04-10
My problem is fixed.  I will tell my story - maybe someone will benefit.

Now, I was always having trouble getting Grub to boot winxp.  I would select the Windows option at boot, and then nothing would happen (i.e., a "hang").  I had already enabled LBA in BIOS and reinstalled several times.   

I have two hard drives, hda=Linux, hdb=Windows.  Here's my fdisk output:

>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30033    15136600+  83  Linux
/dev/hda2           39143      238202   100325925   83  Linux
/dev/hda3           30034       34102     2050776   83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1912    15358108+   7  HPFS/NTFS
/dev/hdb2   *        1913        4316    19310130    7  HPFS/NTFS

These partitions contain:

/dev/hda1 = (hd0,0) = Ubuntu 
/dev/hdb1 = (hd1,0) = Windows XP 

Here is my Grub file from /boot/grub/menu.lst that finally did the trick:

> title WindowsXP on /dev/hdb1
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1

It turns out that the map command is essential!  I never understood what it actually did, so I stayed away from it until I found a website that explained its usage.  

> 
The "map" lines under the Windows section are essential for getting your installation to work. These are the magical lines that trick Windows into believing that it's installed on the first partition of the first disk. If you don't map the Windows partition to (hd0,0), Windows will destroy your partition table and you won't be able to boot anything.
[http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html](http://www.tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html)

I spent a lot of time installing/reinstalling both operating systems, which was just unnecessary.  Good luck!

---

