---
title: "Inconsistent Data Read &amp; Memory Issue after Installation"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by SuperLoser on 2012-12-29
Hello Ubuntu Community,


I'm quite new to Linux (some very limited experience with openSUSE several years ago) but since I'm really tired of Windows, I feel the time to switch over to Linux has come.

I have installed 12.10 yesterday, and have some issues for which I'd like to ask advice.

Okay, first of all a short description of my box, and of what I've done so far:
BIOS: Intel MQ96510J.86A.1754.2008.1117.0002
Mainboard: Intel DQ963FX with Graphics Chipset Q965/Q963
CPU: Intel Pentium Dual CPU E2180 @ 2.00GHz
PCI Graphics Card: ZOTAC GeForce GT430
Sound: onboard (Windows uses NVIDIA High Definition Audio from graphics card install)
Wired Networking Adapter: Intel 82566DC Gigabit Network Connection
Wireless Networking: none
Optical Drive: LG DVD burner, model GH24NS90 (ATA Device)
HDD1 (sda): Samsung HD502HJ
HDD2 (sdb): Samsung HD320KJ

Windows 7 is installed on sda1-3.

I have installed Ubuntu on sdb as follows (I used Unetbootin with mini.iso, since 12.10-desktop.iso doesn't permit use of the LVM):
sdb1: Bootable - ext4 - /boot
sdb5: Volume Group, consisting of / + /home + /tmp + /usr + /var (all ext4) + 2x swap.
Since Windows always acts up if it isn't installed on the first HDD in row, and since Windows updates tend to overwrite the MBR, I have placed GRUB on sdb1 but use the Windows boot manager (edited with EasyBCD).

When booting the system and choosing Ubuntu, I am greeted by the following:
[COLOR=Blue]Initialize variable space ...
Starting cmain() ...
Fatal! Inconsistent data read from (0x90)0+32
Fatal! Inconsistent data read from (0x90)16+1
[/COLOR][INDENT][COLOR=Blue]This repeats 4 times, so that, all in all, I have 10 lines of the above.
[/COLOR][/INDENT][COLOR=Blue](hd1,0)
[Multiboot-kludge, loadaddr=0x100000, text-and-data=0x6739, bss=0x0, entry=0x100968]

[COLOR=Black]Then GRUB starts, with several options.
If I choose 'Memory test (memtest86+)' or 'Memory test (memtest86+, serial console 115200)' I get the following:
[COLOR=Blue]error: too small lower memory (0x99100 > 0x8f000).

[COLOR=Black]Choosing 'Ubuntu' or 'Ubuntu with advanced Options' boots the system, i.e. I get to the log-on screen and can use Ubuntu.

I recall that, during partitioning, fourth console (L-Alt+F4) once or twice issued a warning, but said something along the lines of 'proceeding with formatting as requested'.

/etc/fstab looks like this:
[COLOR=Blue]/dev/mapper/PALA-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=34dd0e98-3248-429d-92db-2eecad9f6a4b /boot           ext4    defaults     $
/dev/mapper/PALA-home /home           ext4    defaults        0       2
/dev/mapper/PALA-temp /tmp            ext4    defaults        0       2
/dev/mapper/PALA-users /usr            ext4    defaults        0       2
/dev/mapper/PALA-variable /var            ext4    defaults        0       2
/dev/mapper/PALA-swap_1 none            swap    sw              0       0
/dev/mapper/PALA-swap_2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/COLOR]

[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black]I suspect Ubuntu doesn't really appreciate use of the LVM on desktop systems.[/COLOR][/COLOR][/COLOR][/COLOR]


In addition, I had some problems with my graphics card (GPU lock after a few seconds of desktop operation) which I could solve by setting GRUB to 'nomodeset' and apt-getting the proper NVIDIA drivers.

I have no sound on Skype, but 'Audacious' Music Player works (minor issue which I'll figure out); I just mentioned it to make a complete report..

I'd be most grateful for help regarding the 'fatal error' and 'memory error' issues, which must be eliminated.

Thanks for your time.


Cheers,
SL
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by ronparent on 2012-12-29
> /etc/fstab looks like this:
/dev/mapper/PALA-root / ext4 errors=remount-ro 0 1 <-----!!!
# /boot was on /dev/sdb1 during installation
UUID=34dd0e98-3248-429d-92db-2eecad9f6a4b /boot ext4 defaults $
/dev/mapper/PALA-home /home ext4 defaults 0 2
/dev/mapper/PALA-temp /tmp ext4 defaults 0 2
/dev/mapper/PALA-users /usr ext4 defaults 0 2
/dev/mapper/PALA-variable /var ext4 defaults 0 2
/dev/mapper/PALA-swap_1 none swap sw 0 0
/dev/mapper/PALA-swap_2 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

I suspect that you are trying to install to a drive currently marked in the metadata area as part of a fakeRAID set. If it is actually a RAID set writing to one of the two drives will break the set. If you are not using the two drives as RAID then you need to erase the meta data from both drives to restore them as independent drives. Once we know the particulars of your situation we can advise you on how to proceed.

---

### Post by SuperLoser on 2012-12-29
Hi ronparent,


thanks for the response.

To the best of my knowledge, there is no RAID (fake or actual) set up on my box.
I have never used a RAID setup on any comp yet.

I have backed up and reinstalled Windows a few days ago, to dedicate separate drives to the two OSs.
In the course of this, both HDDs have been totally wiped clean and reformatted (quick format using Windows Explorer) repeatedly.

I have also used W7's Disk Manager to ensure that the HDD dedicated for Ubuntu consisted of 320.1GB unallocated space by creating a single, primary NTFS partition on it and then deleting that partition again.
Shouldn't all metadata have been wiped by this?

I've just spent an hour and a half STFW for a way to read metadata off a hard disk ... the only thing I've found (and that is of questionable value, too, IMHO) is this: [http://blog.fpmurphy.com/2010/05/hard-disk-metadata.html](http://blog.fpmurphy.com/2010/05/hard-disk-metadata.html)

Which particulars do you require?


Cheers,
SL

---

### Post by ronparent on 2012-12-29
The RAID metadata is written to special sector on each separate disk used in a RAID set and will remain persistent until erased. To do this is simple. Boot to a live cd/dvd and in a terminal install dmraid:

> sudo apt-get install dmraid

 I'm rusty but as I recall you then use dmraid to erase the metadata on each drive:

> sudo dmraid dmraid -rE /dev/sda

Repeat for sdb. Let us know if this workeed.

---

### Post by SuperLoser on 2012-12-29
Okay, I've seen a reference to *dmraid* during my earlier search.
Will try as you've advised ... but only tomorrow morning.  :)
It's nearly 2am here, and I've had a long day, hehe.

I'll read up on it again before actually applying *dmraid*; I have to be absolutely sure that nothing else on the Windows disk is being affected.
I have backups, but I earn my living online, so a data loss or some other mess-up on the Windows disk would suck really hard.

Thanks for the advice; I'll report tomorrow how it went.


Cheers,
SL

---

### Post by oldfred on 2012-12-30
Is there some reason you want the extra system partitions? That is often used by servers, but not really needed for Desktops.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

    
And why LVM? Because you have the extra partitions, and may need to resize them?
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)


And if dual booting with Windows I suggest a separate NTFS data partition, so you do not write into the Windows system partition. You can then set Windows system as read only to avoid accidents as the Linux NTFS driver exposes all the hidden files & folders in Windows that it like to hide.

---

### Post by SuperLoser on 2012-12-30
Hi oldfred,


thanks for the links ... some interesting thoughts on those threads.

I have two reasons for wanting to use LVM:
1.) Sooner or later I'll switch over to a server setup, so that I won't have to use third party webhosting services anymore. So setting up my PC 'server-style' is practising and getting used to the setup.
2.) VG setups are so much more flexible; LVs can be resized with a few clicks / commands.

I have initially set up a rather small Logical Partition (60GB) for the VG, which left me with about 260GB unallocated, which I can incorporate into the setup at any time, according to disk space needed.

This HOWTO is quite interesting: [http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

I know Ubuntu doesn't really provide for usage of the LVM on desktop systems ... the *ubuntu-12.10-desktop.iso* doesn't even offer its use at all ... which is why I've used the *mini.iso* for a netinstall.

In regard of having an extra NTFS partition: there is no real need for that; the first thing I do on every Windows system I set up is *showing hidden files* and* file extensions of known file types* ... so I'm used to being careful about accidentally messing with system and config files.

Do you think the 'fatal error' and 'memory error' may have been caused by using LVM?


Cheers,
SL

---

### Post by SuperLoser on 2012-12-30
Okay, I've booted live with ubuntu-12.10-desktop-i386.iso and ran dmraid:

> ubuntu@ubuntu: ~$ sudo dmraid -r
no raid disks
ubuntu@ubuntu: ~$ sudo dmraid -rE  /dev/sdb
no raid disks and with names: "/dev/sdb"
ubuntu@ubuntu: ~$ sudo dmraid -rE  /dev/sda
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu: ~$So there really were no RAID settings of any sort on either disk.

By the way, I'd tried to install Debian 6.0.6 prior to Ubuntu; the installer either kept freezing while formatting partitions or gave the following error message, after formatting:
[COLOR=Blue]The attempt to mount a file system with type ext4 in SCSI4 (0,0,0), partition #1 (sdb) at /boot failed.[/COLOR]
(I tried with ext4/3/2, with the same result, sometimes varying to [COLOR=Blue]... partition #5 (sdb) at / [COLOR=Black].)

The /etc/fstab I posted in the OP reports a problem mounting '/ ' as well.
I'll now have a look at sdb, checking surface et cetera, so determine whether there is a mechanical problem with the drive.
Will report findings here.

SL

Edit / P.S.: Surface Test with *Partition Wizard 4.2.2* resulted in no errors (at least on the 298.09GB visible to Windows). The disk appears to have no mechanical issues.
[/COLOR][/COLOR]

---

### Post by ronparent on 2012-12-30
Have you tried turning off the raid option in bios?

---

### Post by SuperLoser on 2012-12-30
My BIOS doesn't offer any RAID settings.

S.M.A.R.T. is enabled, but that surely should have no impact on anything.

---

### Post by ronparent on 2012-12-30
RAID is apparently not an issue. 

What do you get in response to a terminal command of blkid?

---

### Post by SuperLoser on 2012-12-30
Hey ronparent,

thanks a lot for spending so much time with this; I appreciate it.  :)


> user@Host:~$ **sudo blkid**
/dev/sda1: LABEL="Windows 7 Ultimate" UUID="3AD024A5D0246979" TYPE="ntfs" 
/dev/sda2: LABEL="Win Applications" UUID="509C27CC9C27AC02" TYPE="ntfs" 
/dev/sda3: LABEL="Win Data" UUID="1EFC2B11FC2AE2AF" TYPE="ntfs" 
/dev/sdb1: LABEL="boot" UUID="34dd0e98-3248-429d-92db-2eecad9f6a4b" TYPE="ext4" 
/dev/sdb5: UUID="fCuEDI-iqJv-QwgA-7Adp-EA7u-vsYZ-zmdGww" TYPE="LVM2_member" 
/dev/mapper/PALA-home: LABEL="home" UUID="3530ff17-ba5a-400d-9765-9ee869eee1f1" TYPE="ext4" 
/dev/mapper/PALA-root: LABEL="root" UUID="c94bcbfe-4e5c-4a9d-844e-68dbe5e8ee63" TYPE="ext4" 
/dev/mapper/PALA-swap_1: UUID="ccb98421-8c71-4d02-850f-e8f594380cb7" TYPE="swap" 
/dev/mapper/PALA-swap_2: UUID="73f9ff82-c386-4ccf-85f0-067da375fc68" TYPE="swap" 
/dev/mapper/PALA-temp: LABEL="temp" UUID="94149ac7-ffc3-4ec5-9158-34fe0bfe3319" TYPE="ext4" 
/dev/mapper/PALA-users: LABEL="users" UUID="f5b31fcc-64ab-4a34-9298-fcfb11270ea7" TYPE="ext4" 
/dev/mapper/PALA-variable: LABEL="variable" UUID="debd229a-63e5-4f8a-8b53-a5545cbd76a9" TYPE="ext4" 
user@Host:~$-------------------------------------------------

> user@Host:~$** less /proc/partitions**

major minor  #blocks  name

8        0  488386584 sda
   8        1   62915584 sda1
   8        2   41944064 sda2
   8        3  383523840 sda3
   8       16  312571224 sdb
   8       17     985088 sdb1
   8       18          1 sdb2
   8       21   58660864 sdb5
  11        0    1048575 sr0
   2        0          4 fd0
 252        0   19537920 dm-0
 252        1    9773056 dm-1
 252        2    2449408 dm-2
 252        3    2449408 dm-3
 252        4    1961984 dm-4
 252        5   19537920 dm-5
 252        6    2949120 dm-6
/proc/partitions (END)

Cheers,
SL

---

### Post by ronparent on 2012-12-31
No I must apologize - because after re-examining your original post it appears that grub may not like its situation. Since you can successfully boot Ubuntu though, it is non-fatal, but a nuisance.

You have done the right thing in installing grub to a non LVM partition. But for some reason it glitches on boot. Your problem is over my head because I am not familiar with the intimate details of setting up and running a LVM install. We need to get the attention of someone expert on LVM. If anyone else has had simular problems it would probably warrant a launchpad bug report. I think forum protocol would provoke response if you write 'bump' in your message. Sorry I couldn't be of more help.

---

### Post by SuperLoser on 2012-12-31
Hey ronparent,


after some more research I agree with you about the problem probably being GRUB-related.

When editing Window's boot menu with EasyBCD, the application writes and saves a file called 'ang0' into Window's C:\ directory, as well as a file called 'AutoNeoGrub0.mbr' in folder C:\NST (this one is the boot path when booting Ubuntu).
The files are human-readable in part only, but still provides some hints about missing stuff (for want of a more precise term) and file connections.

Since Ubuntu is running and working properly, once it has started, the error is apparently not as 'fatal' as it initially appeared to be.
I guess (or hope, rather) the memory issue is only referring to GRUB, too.

I have not done much with Ubuntu, because I wanted to solve this problem before starting to work with it, of course.

So, removing and reinstalling it is no problem.

I'll now reinstall it with standard Desktop settings, i.e. one or two partitions only, no LVM, and then see whether the issue persists.
I'll also try using GRUB to boot into both Ubuntu and Windows, instead of editing the Windows boot manager with EasyBCD.

For the sake of having a complete thread, I'll post my findings here, before changing the thread's status to [SOLVED].

If necessary, I'll open a new thread with the appropriate title and tags.

Once again I'd like to thank you for the time you've invested in helping me.

Happy New Year to you (and to everybody else, of course).


Cheers,
SL

---

### Post by ronparent on 2012-12-31
Dear SL

Sounds like a plan. I would further suggest that you install the grub bootloader on your second drive and change your boot order to correspond. This leaves your Window bootloader unaltered and in place and allows you to easily restore your access to Windows if everything else goes south. I'm sure you will get a better handle on LVM once you get better used to working with Ubuntu.

Likewise, best of wishes to you for the New Year.

---

