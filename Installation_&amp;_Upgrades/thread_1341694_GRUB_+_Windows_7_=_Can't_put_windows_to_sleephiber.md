---
title: "GRUB + Windows 7 = Can't put windows to sleep/hibernate"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by Antithesis on 2009-11-30
Hi all,

I recently had this problem with my machine, which I just solved, but since other people might run into it, I thought I'd put the solution up here for future users. While not strictly an Ubuntu issue (the problem appears in Win7) it is related to the Ubuntu install. 

**Symptom**: With Windows 7 installed, installing Ubuntu with GRUB on the MBR can lead to Windows unable to enter sleep or hibernate mode (The screen will go dark for a second, but immediately come back on). Reverting the MBR using the windows 7 DVD fixes the issue (but prevents GRUB from working).

**Issue**: For sleep/hibernate to work, the first windows partition needs to be marked as boot, even with GRUB installed.

**Solution**: In Ubuntu, use gparted (If not install, add it). On your booting hard drive (usually /dev/sda), make sure that the first windows partition (normally /dev/sda1) is marked as 'boot'. Close gparted and restart. 

GRUB should work just as before (It is on the MBR, so it doesn't really care), and windows will be able to put to sleep and hibernate without issues.

Hope this helps.

---

### Post by justin956235 on 2009-12-18
hi i was hoping that you could help me out with this i have the same exact problem, just with a different setup. I have windows 7 installed on hd 2 in my system and ubuntu 9.10 installed on hd 1 with grub installed on it also. I did what you said in here and made it so boot was set to the first partition on the windows drive ( it was already) also i thought it might help to tell u that my linux partition with grub was set to boot also, i think grub set it to that. my system loads and grub works and everything is dandy, but in win 7 i get the same problem that you described with sleep. plz help thanks a bunch

---

### Post by rvjr on 2010-03-09
Hi Justin!

What did the trick for me is the following:

You don't need to set the boot flag on the Windows7 partition itself, but really on the FIRST partition on the drive where the Windows partition resides on (in my case this was this small 100MB recovery partition windows automatically creates).

Best
Rainer

---

### Post by lucidmyth on 2010-03-21
rvjr: Excellent! That solved it.

---

### Post by Jontebullen on 2010-06-02
i had to register and say thx alot! this worked for me as well, installed ubuntu+grub and hibernating on windows 7 stopped working, but now i got it going again! :popcorn:

---

### Post by dinub1 on 2010-06-10
> **rvjr said:**
> Hi Justin!

What did the trick for me is the following:

You don't need to set the boot flag on the Windows7 partition itself, but really on the FIRST partition on the drive where the Windows partition resides on (in my case this was this small 100MB recovery partition windows automatically creates).

Best
Rainer

It still does not work for me. I have Sidux installed with GRUB. I checked with gparted and the 1st partition on the disk is indeed marked as "boot". It still can't hibernate (I meant Windows 7).

---

### Post by UrbenLegend on 2010-06-25
Thanks for the tip! I used KDE's partition manager in Kubuntu, set the boot flag on my first partition, which happened to be Windows 7, and now Windows hibernates! I always thought it was my video drivers that were at fault.

---

### Post by Aeric on 2010-12-07
Hi, I also have Ubuntu and Windows 7 in the same harddisk. After reading the above posts, I try to use Windows to solve the problem. Go to Control Panel > Administrative Tools > Computer Management then click Disk Management under Storage. My harddisk is partitioned as Linux Ext4, Linux Swap, NTFS ( C: ) and NTFS ( D: ) where Windows 7 is installed in partition C: so I rightclick the partition and click "Mark Partition as Active" and click on "Yes" when a dialog box is prompted. Close the Computer Management tool and try to hibernate. Tada... Hibernate is working now!

Thanks to above expert who give me the idea and solve my problem. ;)

---

### Post by misterbiskits on 2010-12-23
setting the boot flag didn't work for me.   typing "powercfg -h off" into the windows 7 command prompt seems to have worked, Windows 7 now sleeps as it should.

---

### Post by chris3689 on 2010-12-23
I haven't had problems with sleep, but I did have the hibernation issue (which was very problematic when my computer decides to hibernate in my bag).

---

### Post by markhausman on 2011-01-11
This is to confirm one of the earlier solutions (Aeric's).
 
My (Dell Inspiron) laptop has 3 Windows partitions (in order, 100 MB marked "DELLUTILITY", 15 GB marked "Recovery", and the main 400+ GB partition marked "OS", with all the normal operating system files and program and user data), in addition to the Ubuntu/Linux area.
 
Using Ubuntu's Disk Management tool, I found that the 2nd Windows partition was flagged as bootable. I tried changing the 1st partition to bootable (as suggested by Antithesis). This did not work. Following Aeric's advice, I returned to Windows 7 and (using its Disk Management tool), set the 3rd, "OS" partition to "Active". This worked! I can now successfully hibernate in both Windows 7 and Ubuntu.
 
FWIW, when I restarted Ubuntu I now found that the 3rd partition was marked "bootable". I infer that the Windows phrase "Active" must mean the same thing as the Linux phrase "bootable". The significant factor was not to set the *first* partition bootable/active, but the *actual* partition used for my system files.

---

### Post by mitzone on 2011-03-25
> **rvjr said:**
> Hi Justin!

What did the trick for me is the following:

You don't need to set the boot flag on the Windows7 partition itself, but really on the FIRST partition on the drive where the Windows partition resides on (in my case this was this small 100MB recovery partition windows automatically creates).

Best
Rainer

Thanks dude..This did the trick for me too.
Have a nice one.

---

### Post by Quatrix on 2011-08-21
> **justin956235 said:**
> hi i was hoping that you could help me out with this i have the same exact problem, just with a different setup. I have windows 7 installed on hd 2 in my system and ubuntu 9.10 installed on hd 1 with grub installed on it also. I did what you said in here and made it so boot was set to the first partition on the windows drive ( it was already) also i thought it might help to tell u that my linux partition with grub was set to boot also, i think grub set it to that. my system loads and grub works and everything is dandy, but in win 7 i get the same problem that you described with sleep.

I know this is an old thread, but I have the same problem as Justin and haven't found a solution.  I have the GRUB/Ubuntu drive (with some non-OS storage partitions) as hd0/sda and Windows 7 all by itself on hd1/sdb.  The Windows 7 and GRUB/Ubuntu partitions are already marked as "boot" in fdisk (below) and GParted and "active" in Windows and Acronis.  However, hibernation only works if I bypass GRUB and boot directly from the Windows 7 drive.  The solution given here only seems to work if everything is on the same physical drive.

By the way, there's a quick and easy way to determine whether hibernation problems are due to partition issues or something else.  Just go to Control Panel > System > Advanced System Settings > Startup and Recovery > Settings and look at the "Default Operating System" drop-down at the top.  If there's a partition issue then the drop-down is empty.  EasyBCD will also give you an error message when it starts.

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc566bf2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4208    33799168   83  Linux
/dev/sda2            4209       21832   141564779+  17  Hidden HPFS/NTFS
/dev/sda3           21833      182401  1289770458    f  W95 Ext'd (LBA)
/dev/sda5           21833       29665    62918537    7  HPFS/NTFS
/dev/sda6           29666      140627   891302218+   7  HPFS/NTFS
/dev/sda7          140628      177179   293603899    7  HPFS/NTFS
/dev/sda8          177180      182401    41945683+   7  HPFS/NTFS

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
242 heads, 36 sectors/track, 28704 cylinders
Units = cylinders of 8712 * 512 = 4460544 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x724fc7a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       28704   125032448    7  HPFS/NTFS
```

---

### Post by Khronos1 on 2011-11-06
Just a heads up but setting the 100MB System Reserved partition to carry the boot flag fixed not only the issue of my computer not being able to go to Sleep, but it also fixed an error (0x80070002 The system cannot find the file specified) that I was having when I tried using Windows Backup.

---

### Post by parth.s on 2011-11-16
Nice one! I was looking for this for a long time...

Just one point in win7 the first partition is the recovery one, so its the partition on which win7 is installed that needs to be selected as boot, in my case its /dev/sda2

Thanks a Ton! Cheers!

---

### Post by Mark Phelps on 2011-11-16
> **parth.s said:**
> Nice one! I was looking for this for a long time...

Just one point in win7 the first partition is the recovery one, so its the partition on which win7 is installed that needs to be selected as boot ...

Actually -- NO.  It's not the order of the partition that matters, it's what it contains.

When you buy a PC preloaded with Win7, there will be a small 100MB "boot" partition.  That is the one containing the boot loader files.  The Win7 OS files will be on another partition.

In other cases, the Win7 boot loader directory and files -- and the Win7 OS files -- are in the same partition.

The CORRECT partition is the one containing the Win7 boot loader directory and files. Where this happens to be on the drive depends entirely on HOW Win7 was installed.

So, it's not necessarily true that the correct partition to have the boot flag is the first, or the second, or ...  Instead, it's the one containing the boot loader stuff.

---

### Post by ludwigbaum on 2011-12-08
Mark Phelps is right.
I recommend the following method - if possible:
The installation of Linux changes the ownership of the boot-procedure. The recovery-partition may not start anymore.

Therefore:
BEFORE installing Linux, make a copy of the recovery-partition or primary installation (USB-stick). 
Create a Windows-repair-CD (if the functionality is not included in the recovery-system)
Install a minimal WUBI or MINT4WIN (4 GB are sufficient). Make a copy of /boot/grub/grub.cfg .
In this copy, you will find the original values.

Now install as many Linux-distributions as you want. (By now, I am trying three).
If the hibernate-function of Win 7 does not work:

- Start the repair-CD/USB-stick
- Start the command-line
- bootrec /fixmbr
- bootrec /fixboot

Start the WUBI or MINT4WIN-System (reinstall it if necessary).
In the terminal:
sudo update-grub

Restart.
The trick is, that hibernation works and Wubi/mint4win gives easy and independent, Win7-compatible (hibernation-friendly) control over Grub. If you don’t need the original copy of grub.cfg, you can install Wubi/mint4win at any time.

---

### Post by bug-me-not on 2012-02-21
I was wondering why win7 was not hibernating. After reading this thread here's what fixed it for me:

Triple boot partitions: XP, Win7, Ubuntu (in that order). Grub 2.

cmd.exe (run as admin): ```
**powercfg.exe /hibernate on**
```hiberfile size was 75% of RAM size. 
So I changed the registry setting **HKLM\System\CurrentControlSet\Control\Power\HiberFileSizePercent to 100**. Rebooted. Now hiberfile size is 100% of RAM size.  
Changed "What power buttons do" to enable hibernate.

Booted using PartedMagic boot cd and **selected XP partition as boot** (previously win7 was boot).  Rebooted into win7 and now win7  hibernates!

Thanks folks.

---

### Post by CorruptDNA on 2012-03-24
thanks!

---

### Post by Quatrix on 2012-03-24
> **CorruptDNA said:**
> thanks!

Huh?

---

### Post by Mark Phelps on 2012-03-26
> **bug-me-not said:**
> Booted using PartedMagic boot cd and **selected XP partition as boot** (previously win7 was boot).  Rebooted into win7 and now win7  hibernates!

Remember back in my post where I said the CORRECT partition was the one containing the Windows Boot Loader files?

When you have XP on a PC and then install Win7, it will write its boot loader files to the XP partition.  So, in that case, the XP partition needs to have the boot flag turned on.

---

### Post by sk8erguy1978 on 2012-06-11
I am having the same issue with windows 7 not wanting to sleep or even shutdown properly when booted through grub2.  If I change the boot and force the drive which windows resides on to start and bypass grub2 windows works perfectly.  Again I have tried all the suggestions here to no avail, I change the boot in Ubuntu but when I update grub it still sees the wrong partition?  I have attahced two screenshots that might help someone see if I am doing something wrong...Thanks!

---

### Post by sk8erguy1978 on 2012-06-11
After a few days I finally got it.  Turns out I did not try misterbiskits suggestion of "powercfg -h off."  However before doing that I did remove the boot flag completely from Ubuntu for the Windows partition... So, not sure if the combo had anything to do with it, have not restarted Ubuntu yet.

Anyway, thanks for all the great ideas in this thread!  See you all around!):P

---

### Post by jaktar on 2012-06-16
> **misterbiskits said:**
> setting the boot flag didn't work for me.   typing "powercfg -h off" into the windows 7 command prompt seems to have worked, Windows 7 now sleeps as it should.

In my case, my boot flag was already set.  Using your suggestion of "powercfg -h off" worked perfectly.  This being a desktop, I don't intend to use hibernate, but I could see that this could be a problem for laptop users.

Thanks!

---

### Post by dna_gene on 2012-06-23
Oh boy this takes a while.  to speed you along: powercfg.exe -energy in a windows 7 cmd.exe with admin rights - fixs as many problems as you can.   if sleep works but hybrid sleep and hibernate don't and you boot with grub: set boot flag for the mini partition (recovery) that windows made when it installed itself - note do NOT do this with windows disk manager as it will BREAK your system (if you did do this use testdisk with puppy linux to recover (but believe me - you don't want to do that)!!!) Instead use parted or gparted or sysrescue disk or your linux partition and fdisk and set the boot flag on that partition.   Still not hibernating (like me?) then you need to use the grub menu option that boots windows from the small partition usually /dev/sda1 (you set the boot flag didn't you?) Ok that should be it. Good luck ( when you set up grub it probably gave you more that one windows partition start up option - USE the /dev/sda1 (or 1st small partition with recovery partition on it - it has the smarts to start up a hibernated windows system)....

---

### Post by Quatrix on 2012-06-23
> **dna_gene said:**
> Oset boot flag for the mini partition (recovery) that windows made when it installed itself

The recovery partition is optional, and many people (such as myself) don't have one.

---

### Post by Toci on 2012-08-03
> **Mark Phelps said:**
> Actually -- NO.  It's not the order of the partition that matters, it's what it contains.

When you buy a PC preloaded with Win7, there will be a small 100MB "boot" partition.  That is the one containing the boot loader files.  The Win7 OS files will be on another partition.

In other cases, the Win7 boot loader directory and files -- and the Win7 OS files -- are in the same partition.

The CORRECT partition is the one containing the Win7 boot loader directory and files. Where this happens to be on the drive depends entirely on HOW Win7 was installed.

So, it's not necessarily true that the correct partition to have the boot flag is the first, or the second, or ...  Instead, it's the one containing the boot loader stuff.

 This was my case. Except the partition is 750MB (the RECOVERY one).
 I used Gparted through the Ubuntu live-cd to change the flag.

 I struggled with this for a long time, but it works now. Thank you very much.

---

### Post by amilmand on 2012-09-22
If there's still anyone out there who can't hibernate his/her GRUB booted win7 and is still looking for an answer here you go another one;
just to be clear the setup is the following;
```
sda:
   Win7 bootloader
   sda1 ntfs System Reserved (100MB,Win7BootFiles)
   sda2 ntfs Windows7Files   (the rest on sda, Win7Install)
sdb:
   GRUB
   sdb1 ntfs Data  (the rest on sdb,Data)
   sdb2 swap       (8GB,SWAP)
   sdb3 ext4       (30GB,Linux)
```

GRUB above means GNU GRUB or GRUB2 that came packed with Ubuntu.
So after running update-grub the notable generated entries are like:
for Windows7:
```

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os
{
	savedefault
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root D2BA9E65BA9E45BF
	chainloader +1
}

```
and for linux:
```

menuentry 'Kubuntu, with Linux 3.2.0-30-generic' --class kubuntu --class gnu-linux --class gnu --class os 
{
	recordfail
	savedefault
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root 7a5eb1c2-19f1-4d1c-a18f-176b3be8ae62
	linux	/boot/vmlinuz-3.2.0-30-generic root=UUID=7a5eb1c2-19f1-4d1c-a18f-176b3be8ae62 ro   
	initrd	/boot/initrd.img-3.2.0-30-generic
}

```
We should know that windows-es (Win9X DOS Vista Win7) are assuming themselves being on the first hard-drive, which should not be a problem since our GRUB sets the root to (hd0,msdos1).
After a long time trying out various solutions and menu entries found on the web and constructed by myself, I found that the code above is very very misleading since the search statement overrides the root variable after the "set root" so the indexing of the hard drives isn't necessarily as suggested above the search. I mean of course GRUB believes it to be correct and although it can it doesn't swap the hard drives around helping the installed windows.
(after reading a lot (I mean a lot) about grub and getting familiar with its console function and its various commands (which in my opinion I shouldn't have been forced to do as an end user)) I tried to boot from the console (this is the grub console now) like this:

```

set root='(hd0,msdos1)'
ntldr /bootmgr

```
and I got a "file not found" error (what the hell).
The right one turned out to be:
```

set root='([COLOR="Red"]hd1[/COLOR],msdos1)'
ntldr /bootmgr

```
Of course I still couldn't hibernate because of the twisted hard drive indexing. 
So the correct menu entry for me is the following:
```

menuentry "Windows 7"
{
	drivemap -s (hd0) (hd1)
	set root='(hd1,msdos1)'
	ntldr /bootmgr
}

```	
the drivemap command virtually swaps the two hard drives given as parameters, but it's properly documented in [the GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").
As this is a known disability of the windows family it really should be integrated in the script generating the menu entries


So the real solution is then:
Finding out the correct hard drive index (the partition index should be correct)
In the GRUB press 'c'.
This will bring up the GRUB console you will get a
```
grub> 
```
It's just like any other console just the commands are a little different.
Now type ls.
This will list the available hard drives and the partitions, further more
in my case if I type ls (hd0,msdos1) it lists the known properties of the (hd0,msdos1) partition which turned out to be my ntfs Data partition.
If you know the proper indices you should turn off the os_probe script which generates the win7 entry from a regular console in ubuntu like this:
sudo chmod -x /etc/grub.d/30_os-prober
after that edit the '40_custom' file in the same place (/etc/grub.d/) and write the following (but of course with the proper hard disk index for this example the hard disk index of the one containing the 'System Reserved' partition will be 9999)
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" --class windows --class os {
	drivemap -s (hd0) (hd9999)
	set root='(hd9999,msdos1)'
	ntldr /bootmgr
}

```
then update-grub and done.

---

### Post by NHellFire on 2012-09-24
amilmand is correct. Windows expects to be the first HDD and refuses to sleep if it's not.
You can fix it in /etc/grub.d/30_osprober, just change:
```
      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
        ;;
        *)
          cat << EOF
        drivemap -s (hd0) \${root}
EOF
        ;;
      esac
```

To:
```
        cat << EOF
      drivemap -s (hd0) \${root}
EOF
```


I've submitted a bug: [https://bugs.launchpad.net/bugs/1055880](https://bugs.launchpad.net/bugs/1055880)

---

### Post by deyka on 2012-12-29
> **Antithesis said:**
> Hi all,

I recently had this problem with my machine, which I just solved, but since other people might run into it, I thought I'd put the solution up here for future users. While not strictly an Ubuntu issue (the problem appears in Win7) it is related to the Ubuntu install. 

**Symptom**: With Windows 7 installed, installing Ubuntu with GRUB on the MBR can lead to Windows unable to enter sleep or hibernate mode (The screen will go dark for a second, but immediately come back on). Reverting the MBR using the windows 7 DVD fixes the issue (but prevents GRUB from working).

**Issue**: For sleep/hibernate to work, the first windows partition needs to be marked as boot, even with GRUB installed.

**Solution**: In Ubuntu, use gparted (If not install, add it). On your booting hard drive (usually /dev/sda), make sure that the first windows partition (normally /dev/sda1) is marked as 'boot'. Close gparted and restart. 

GRUB should work just as before (It is on the MBR, so it doesn't really care), and windows will be able to put to sleep and hibernate without issues.

Hope this helps.
I had the same problem (Windows 7 64-bit and Ubuntu 12.04 64-bit) and your solution worked beautifully. So simple!
Thanks a lot.

---

### Post by Victor_Zhang on 2013-09-28
I tried setting the boot flag on different partitions, and it's still not working. 

My T430 came with a 320G HD (/dev/hda). It has an utility partition /dev/hda1, and Windows 7 is installed on /dev/hda2. 

I replaced the DVD tray with a SSD drive (/dev/hdb), and put Ubuntu on it. I then changed BIOS' boot order to make the new SSD as the first boot device, old 320G HD as second. 

When the system starts up, it goes to the SSD first and GRUB takes over, I then can choose between Win 7 and Ubuntu from the GRUB menu. So far, Ubuntu works as expected in all aspects - hibernation works perfectly. However, Win 7 is no longer be able to hibernate. I know it's not related to hardware drivers and hibernation file because hibernate worked fine before I installed Ubuntu. 

Win 7 is not seeing the "Default Operating System" drop-down from the "Startup and Recovery" settings regardless which partition (hda1 or hda2) is flagged as "boot". What else can I do? 


Here is my disk setup: 



Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x84e23367


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000    7  HPFS/NTFS/exFAT
/dev/sda2         1026048   625139711   312056832    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004ab0


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   218056703   109027328   83  Linux
/dev/sdb2       218056704   234440703     8192000    5  Extended
/dev/sdb5       218058752   234440703     8190976   82  Linux swap / Solaris

=======================

This is the follow up after a few hours of reading and study about the problem. I ACTUALLY SOLVED THE PROBLEM after trying different things including screwing up the MBR, rebuilding GRUB2 and etc. 

Here is what I did: 

- Read Amilmand's answer on page 3 carefully
- Read the Grub documentation and understand a bit more about Windows booting
- Apply Amilmand's method: turning off auto OS probers, add a custom entry to /etc/grub.d/ 
- Set Boot flag to /dev/hda1

Everything is working well now - both Win 7 and Ubuntu can hibernate.  :-)

---

### Post by Stephen_Damm on 2014-06-12
> **NHellFire said:**
> amilmand is correct. Windows expects to be the first HDD and refuses to sleep if it's not.
You can fix it in /etc/grub.d/30_osprober, just change:
```
      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
        ;;
        *)
          cat << EOF
        drivemap -s (hd0) \${root}
EOF
        ;;
      esac
```

To:
```
        cat << EOF
      drivemap -s (hd0) \${root}
EOF
```


I've submitted a bug: [https://bugs.launchpad.net/bugs/1055880](https://bugs.launchpad.net/bugs/1055880)


Sorry to bump this old thread but I had the exact problem described by OP.  It had nothing to do with which partition was marked as boot, the windows 7 partition does have to be marked as boot but it also has to be the first HDD.  GRUB was the culprit.  This patch worked for me on Ubuntu 14.04 install.   Patch the osprober file and run update-grub.  Windows 7 can hibernate or hybrid sleep just fine now.

---

### Post by affa2 on 2014-08-07
Great suggestion. It works for me. System: Windows 7 + Ubuntu 14.04

For my case, normal Windows OS runs under /dev/sda2, which I select to boot windows in the multi-boot menu.
Using gparted, it was found that /dev/sda1, which is occupied by Recovery Partition, was flagged somehow flagged as 'boot'.
I simply right click on /dev/sda2 and mark it as 'boot'. Reboot and Windows hibernate works again! ;)

---

### Post by wentwog on 2014-10-01
Can you, please, help me with the following issue.

My setting is:
/dev/sda1 - Windows7 200 mb partition, stores windows boot loader, I suppose.
/dev/sda2 - Windows7 main partition (OS and user files)
/dev/sda3,6,7,8 - Open SUSE Linux partitions. One of them stores grub, I suppose.
I've attached the picture to be clear.
[ATTACH=CONFIG]256886[/ATTACH]

My problem was that Win7 was able to go sleep but unable to go hibernate. Using Gparted I have seen that boot flag is on sda3, where Open SUSE Linux resides. Using the main method of this thread I've moved the boot flag from sda3 to sda1. Now Windows is able to hibernate. BUT, I can't load Linux since Windows is loading and grub dialog isn't shown.

How this can be fixed?

---

