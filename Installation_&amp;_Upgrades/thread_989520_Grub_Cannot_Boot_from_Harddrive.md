---
title: "Grub Cannot Boot from Harddrive"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by NoSkill on 2008-11-21
Hi,

      I've installed Ubuntu 8.10 and everything is working out great. Presently I am dual booting with Windows XP( Windows installed first on a different harddrive than ubuntu) but cannot boot from the windows hard-drive. Grub is telling me that the device does not exist.

The first bootable hard-drive is the one that boots ubuntu. 

Fdisk yields:

> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35cc9dc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38297   307620621   83  Linux
/dev/sda2           38298       38913     4948020    5  Extended
/dev/sda5           38298       38913     4947988+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16713       37810   169469685    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e6cf85e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       30515   245103705    f  W95 Ext'd (LBA)
/dev/sdc5               2       30515   245103673+   7  HPFS/NTFS



menu.lst shows 

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Any ideas on how to successfully boot windows?
Thanks

---

### Post by caljohnsmith on 2008-11-21
How about trying:
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 
```
Let me know if that works, of if it doesn't, what exactly happens after you select it in the Grub menu. :)

---

### Post by NoSkill on 2008-11-21
I tried, with no luck

the Error is,

Error:22 No Such Partition

after I select the winXP from Grub menu

> **caljohnsmith said:**
> How about trying:
```
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 
```
Let me know if that works, of if it doesn't, what exactly happens after you select it in the Grub menu. :)

---

### Post by caljohnsmith on 2008-11-21
OK, I see the problem now; even though your Windows is the only partition on the drive, it is labeled as "sdb2" or the second partition. How about:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd1,1)[/COLOR]
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Give that a shot and let me know how it goes.

---

### Post by NoSkill on 2008-11-21
> **caljohnsmith said:**
> OK, I see the problem now; even though your Windows is the only partition on the drive, it is labeled as "sdb2" or the second partition. How about:
```
title Microsoft Windows XP Professional
root [COLOR="Blue"](hd1,1)[/COLOR]
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Give that a shot and let me know how it goes.

Tried that too:

Error 21: Selected Disk does not exist.
Press any key to continue.

Thanks alot for your time by the way

---

### Post by caljohnsmith on 2008-11-21
I think we will nail it this time since this is the only possibility left, and it makes sense that Windows is on (hd2) because of your previous "Error:22 No Such Partition" error:
```
title Microsoft Windows XP Professional
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```
OK, I'm betting $10 that's going to work this time. :)

---

### Post by NoSkill on 2008-11-21
Ok NOW we're getting something. After I changed the settings the computer tried to boot. But I was met with yet another error.

> Windows could not start because of a computer disk hardware configuration problem. Could not read from the selected boot disk. Check boot path and disk hardware. Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information

Any suggestions??

---

### Post by caljohnsmith on 2008-11-21
Great, well maybe I didn't lose the full $10 then, because obviously we're booting the right partition finally. :) One thing I notice though is that your sdb2 partition starts at about 138 GB, so you have about 138 GB of unallocated space. Did you by chance delete sdb1 at some point? It sounds like Vista may have put its boot files in sdb1, so with sdb1 gone Vista is maybe pouting about losing its boot files. But sdb2 does have the boot flag set, so that may contradict that theory. Also, since Vista says it can't "read from the selected boot disk", that might mean Vista originally put its boot files on your sda drive (or another drive) which it can't access now. 

Do you have your Vista Install CD? How about booting that and do a "Vista Repair"; that is usually enough to get Vista booting again if Vista has lost its boot files. If you don't have a Vista Install CD, you can instead download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and use that. It might be that the Vista CD won't let you do a Vista Repair with an error about your hardware not meeting its boot requirements (or something like that); if that happens, let me know, and we can work around it. Anyway, let me know how it goes. :)

---

### Post by NoSkill on 2008-11-21
Hrm, this is windows xp that is installed. I have the CD and will be attempting a repair. 

Question, if I repair will the MBR be overwritten and as such will i be loosing GRUB and access to my ubuntu partition?

Thanks a million for all your time spent helping me

---

### Post by caljohnsmith on 2008-11-21
> **NoSkill said:**
> Hrm, this is windows xp that is installed. I have the CD and will be attempting a repair. 

Question, if I repair will the MBR be overwritten and as such will i be loosing GRUB and access to my ubuntu partition?

Thanks a million for all your time spent helping me
You're certainly welcome, and I apologize for being so brain-dead that I forgot that you have XP rather than Vista. #-o But before you try and repair XP from the CD, how about first posting:
```
sudo mount /dev/sdb2 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note the "-l" is a lowercase L, not a one. Also, you didn't mention, but what happened to sdb1?

---

### Post by Arseny92 on 2008-11-21
> Question, if I repair will the MBR be overwritten and as such will i be loosing GRUB and access to my ubuntu partition?
Yes, when you do the repair from the Windows disc, grub will be overwritten with bootmgr (Vista), or ntldr (XP).

---

### Post by caljohnsmith on 2008-11-21
> **Arseny92 said:**
> Yes, when you do the repair from the Windows disc, grub will be overwritten with bootmgr (Vista), or ntldr (XP).
At least for my Windows XP Home Edition, that fortunately was not the case; I did a Windows repair and Grub was untouched. I've heard some people say that doing a "Windows Repair" using Windows XP Professional CD will replace Grub in the MBR with a Windows MBR, so I think it depends on what version you are using. :)

---

### Post by NoSkill on 2008-11-21
> **caljohnsmith said:**
> You're certainly welcome, and I apologize for being so brain-dead that I forgot that you have XP rather than Vista. #-o But before you try and repair XP from the CD, how about first posting:
```
sudo mount /dev/sdb2 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Note the "-l" is a lowercase L, not a one. Also, you didn't mention, but what happened to sdb1?

Ok the  commands above yielded the following 
> andrei@Polaris:~$ sudo mount /dev/sdb2 /mnt
[sudo] password for andrei: 
andrei@Polaris:~$ ls -l /mnt
total 2095757
drwxrwxrwx 1 root root      12288 2008-11-09 20:55 2A Software Downloads
drwxrwxrwx 1 root root      12288 2008-09-17 20:49 4fcd4a4a49b7711b4a3340f7df1b4598
drwxrwxrwx 1 root root          0 2007-09-23 01:53 altera
-rwxrwxrwx 1 root root        210 2007-09-22 19:41 boot.ini
drwxrwxrwx 1 root root          0 2008-06-04 19:12 Brother
drwxrwxrwx 1 root root     151552 2008-11-11 08:44 Config.Msi
drwxrwxrwx 1 root root       4096 2008-02-07 07:06 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-07-23 06:29 DVDVideoSoft
drwxrwxrwx 1 root root       4096 2008-08-23 14:09 Games
drwxrwxrwx 1 root root          0 2008-08-31 21:23 Media
drwxrwxrwx 1 root root          0 2008-02-19 23:05 MSOCache
-rwxrwxrwx 1 root root      47564 2004-08-04 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-04 08:00 ntldr
-rwxrwxrwx 1 root root 2145386496 2008-11-02 13:05 pagefile.sys
drwxrwxrwx 1 root root      32768 2008-11-11 08:27 Program Files
drwxrwxrwx 1 root root          0 2007-10-03 01:14 RECYCLER
drwxrwxrwx 1 root root          0 2008-05-10 00:07 Software Projects
drwxrwxrwx 1 root root       4096 2007-09-22 23:56 System Volume Information
drwxrwxrwx 1 root root       8192 2007-10-02 23:50 VCPP
drwxrwxrwx 1 root root      28672 2008-03-25 00:26 VEGA-SAVED DOCS
drwxrwxrwx 1 root root       4096 2008-04-14 18:23 watcom-1.3
drwxrwxrwx 1 root root      94208 2008-11-11 08:26 WINDOWS
drwxrwxrwx 1 root root       4096 2008-04-30 10:12 Zips
andrei@Polaris:~$ cat /mnt/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)part

Now comes the big question, after i fix the MBR and boot windows, how do i get my ubuntu back without running into the same problems?

---

### Post by caljohnsmith on 2008-11-21
Fortunately, you have the three necessary XP boot files, and your boot.ini file is configured correctly too (at least the part you printed), so it looks like you're probably stuck with having to do a "Windows Repair" at this point. If Windows replaces Grub in your sda MBR, just follow these steps from your Live CD to reinstall Grub:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Anyway, let me know how it goes. :)

---

### Post by meierfra. on 2008-11-21
Don't do the Windows repair yet. boot.ini is NOT correct. It needs to be 

partition(1)

---

### Post by caljohnsmith on 2008-11-21
> **meierfra. said:**
> Don't do the Windows repair yet. boot.ini is NOT correct. It needs to be 

partition(1)
So even though XP is on sdb2, it doesn't use partition(2)? I didn't think it mattered whether sdb1 existed or not, only that XP was on sdb2. Did I get that wrong?

---

### Post by meierfra. on 2008-11-21
> I didn't think it mattered whether sdb1 existed

It does matter. Windows only counts partitions which really exist.

---

### Post by Arseny92 on 2008-11-21
> 
Don't do the Windows repair yet. boot.ini is NOT correct. It needs to be 

partition(1)
as the info provided at the first post states
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16713       37810   169469685    7  HPFS/NTFS
it is the second partition of second scsi drive

so based on that, the partition number in boot.ini is correct = 2 (Windows also number partitions from 1).
there is no /dev/sdb1 if this is correct
[quote=caljohnsmith]
One thing I notice though is that your sdb2 partition starts at about 138 GB, so you have about 138 GB of unallocated space. Did you by chance delete sdb1 at some point?
[/quote]

-------------------------

> Windows only counts partition which really exist.oh, correct, i've forgotten that (i use vista on my laptop, and it is not using boot.ini...).

------------------------
> 
andrei@Polaris:~$ cat /mnt/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW  S
[operating systems]
multi(0)disk(0)rdisk(0)part
you didn't provided the end of the file - multi(0)disk(0)rdisk(0)part**ition([COLOR=Green]?[/COLOR])="Windows XP..."**

---

### Post by meierfra. on 2008-11-22
Your boot.ini should look like:

```
[Boot Loader]
timeout=1
Default=multi(0)disk(0)rdisk(0)partition(1)\Windows
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect
```

To edit boot.ini from Ubuntu open boot.ini via:

```
sudo mount /dev/sdb2 /mnt
sudo nano /mnt/boot.ini
```

(Instead of nano you can use any editor which preserves the "dos" line breaks.  Don't use "gedit")

---

