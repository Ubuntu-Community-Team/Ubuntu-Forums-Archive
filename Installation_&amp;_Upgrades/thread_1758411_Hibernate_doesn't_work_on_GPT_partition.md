---
title: "Hibernate doesn't work on GPT partition"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by lifelike27 on 2011-05-14
Hey guys,

I was finally able to triple boot Ubuntu, Windows 7 and OS X on my laptop. In order to do that, I had to use a GUID partitioning table (GPT) to get OS X installed but Windows requires a MBR partitioning table. 

To get it all working, I formatted my hard drive to GPT, installed OS X followed by Windows then Ubuntu. Then booted to Ubuntu and installed a package called gptsync which, from what I understand, simulates an MBR partition for Windows to work. Which means it has to also simulate four partitions even if I have more. Creating more (and then running gptsync to get Windows to work) would be useless because none of the operating systems recognize it. I'm also unable to create logical partitions in GPT, only primary.

When installing Ubuntu, I wasn't able to setup a partition for my swap drive. I did this after all installations were complete. Added the drive to fstab and after a reboot (ran gptsync as well before that) the hibernate option appeared on the power button. If I click it, the screen goes blank and doesn't do anything after that. It's still running with a blank screen, but it's stuck like that.

Running fdisk I get this:

```
jon@jon-ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80f9a090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       35418   284281856    7  HPFS/NTFS
/dev/sda3           36512       48670    97655808   83  Linux
/dev/sda4           48670       60785    97319940   af  HFS / HFS+

```

Running gptsync again when already synced I get this:

```
jon@jon-ubuntu:~$ sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         411648    568975359  Basic Data
 3      586559488    781871103  Basic Data
 4      781871104    976510983  Mac OS X HFS+
 5      568975360    586559487  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       411648    568975359  07  NTFS/HPFS
 3      586559488    781871103  83  Linux
 4      781871104    976510983  af  Mac OS X HFS+

Status: Tables are synchronized, no need to sync.


```

When using GParted, you can see all the extra partitions you make as well.

I tried creating a separate partition for storing all my media files for all the operating systems to access but without running gptsync, Windows can't boot. When I do run gptsync, Windows boots, but like I said, none of the operating systems recognize the partition.




Any ideas?

---

### Post by srs5694 on 2011-05-14
First, please read two pages from my online GPT fdisk (gdisk) documentation: The ["What's a GPT?"](http://www.rodsbooks.com/gdisk/whatsgpt.html) page and the ["Hybrid MBRs: The Good, the Bad, and the So Ugly You'll Tear Your Eyes Out"](http://www.rodsbooks.com/gdisk/hybrid.html) page. Combined, they should fill in a lot of the gaps in your knowledge and help you figure out at least some of what's going on.

In brief, your hybrid MBR is used by Windows, but not by OS X or Linux. The gptsync program is pretty inflexible in terms of what GPT partitions it includes in the hybrid MBR. You can do better with gdisk, or with some modified versions of gptsync I've seen.

This still leaves a couple of big issues, though. First, it's unclear what you mean when you say, in reference to your NTFS shared-data partition, that "none of the operating systems recognize" it. There are many different OS parts that might be said to "recognize" a partition, so unless you say what precise programs you're using and symptoms you're seeing, it's impossible to offer more than wild speculation. I recommend you start by showing us your GPT data, as revealed by GNU parted or gdisk. Type either of the following commands (the latter will require you to install the gdisk package):

```

sudo parted /dev/sda print
sudo gdisk -l /dev/sda

```Repeat this for all your disks, if you've got more than one. If there's any ambiguity, please identify what each partition is -- is it a Linux boot partition, a Windows C: partition, your shared NTFS partition, etc.?

The other big question, of course, is why your hibernation is not working. Your swap partition seems to be 8.3 GiB in size, according to the gptsync output, so it should be big enough for a computer with up to 8 GiB of memory. If you've got more memory than that, though, the swap partition's size is most likely the culprit. Beyond that, I'm not very well-versed in hibernation issues, since I seldom use this feature myself. I do know that I've successfully hibernated my laptop on a GPT disk (with a hybrid MBR, as well), but that's been in OpenSUSE, not in Ubuntu. There's probably a configuration option that didn't get set during installation because there was no swap space at that time, but I don't happen to know how to correct it. I'd say the odds of it being GPT-related are low, though, given my experience.

---

### Post by lifelike27 on 2011-05-14
Sorry I wasn't clear earlier. Basically, when I said I can't access it, I meant that (in Ubuntu) it doesn't appear in the sidebar for me to access. Nor does it appear in Windows or OS X.

My maximum RAM is 4GB and it was recommended that I make a swap drive twice the size of my total RAM.

The links you posted aren't working for me right now. I'll try again later.

GParted:
```
jon@jon-ubuntu:~$ sudo parted /dev/sda print
[sudo] password for jon: 
Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      20.5kB  210MB  210MB   fat32           EFI System Partition  boot
 2      211MB   291GB  291GB   ntfs            WINDOWS
 5      291GB   300GB  9003MB  linux-swap(v1)
 3      300GB   400GB  100GB   ext4            UBUNTU
 4      400GB   500GB  99.7GB  hfs+            Snow Leopard


```
gdisk:
```
jon@jon-ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D6E0F5CA-2E06-4AA1-A039-E9E1B7E7FDE9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 264165 sectors (129.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          411648       568975359   271.1 GiB   0700  WINDOWS
   3       586559488       781871103   93.1 GiB    0700  UBUNTU
   4       781871104       976510983   92.8 GiB    AF00  Snow Leopard
   5       568975360       586559487   8.4 GiB     8200  
```


Here's a screenshot of GParted as well to make it easier on the eyes: [http://dl.dropbox.com/u/8515110/temp/Screenshot.png](http://dl.dropbox.com/u/8515110/temp/Screenshot.png)

I merged the 'storage' partition I was talking about earlier with the Windows partition.

---

### Post by srs5694 on 2011-05-14
Sorry about the links; I accidentally posted the links that are good on my home network, not on the Internet. I've fixed that; they should work now.

As to the rest, the partitioning data looks good, and you should be able to access your Windows partition (/dev/sda2) from Linux or OS X. To further diagnose this, try (in Linux):


[list=1]
[*]Type "df". If you see an entry for /dev/sda2, then it means that the partition is already mounted at the location specified by that entry.
[*]Type "sudo blkid /dev/sda2". You should see output that identifies the partition as being NTFS. If you see no output, then it could be that the filesystem is badly corrupted; however, since the GNU Parted output you posted identified the partition as NTFS, I think this is unlikely.
[*]If the partition was not mounted in step #1, type "sudo mount /dev/sda2 /mnt". This should mount the partition at /mnt. If you get an error message, post it here.
[*]Check your /etc/fstab file for any entry that references /dev/sda2 or the UUID value reported by blkid for /dev/sda2. It's conceivable this is auto-mounting the partition or causing it not to mount at all. Report back any entry you find if you want advice on how to modify it.
[*]If you can boot Windows (even a Windows recovery disc), run CHKDSK on the partition from Windows. Linux (and perhaps OS X) often refuses to mount an NTFS volume if it's been improperly unmounted, and neither Linux nor OS X has a proper NTFS check tool, so fixing this problem requires booting Windows.
[/list]


Also, I *strongly* recommend you re-create your separate NTFS data-exchange partition. Directly accessing, and especially writing to, any OS's system partition from another OS is generally unwise. There are two reasons for this. The first is that drivers for non-native filesystems are generally imperfect. If the NTFS-3g driver used by Ubuntu has a bug, it could trash the whole partition qucker than you can say "d'oh!" The second reason is that different OSes frequently don't honor each others' security measures. (This is certainly true of Linux and Windows.) This makes it too easy to accidentally delete or modify files that the OS whose partition you're accessing would never permit you to delete or modify.

---

### Post by lifelike27 on 2011-05-14
When I type df, I can't find /dev/sda2. Instead:
```
jon@jon-ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             96121612   7143936  84094888   8% /
none                   1984672       724   1983948   1% /dev
none                   1995000      1432   1993568   1% /dev/shm
none                   1995000        96   1994904   1% /var/run
none                   1995000         0   1995000   0% /var/lock

```

I created the data-exchange partition again like you suggested and ran gdisk after that. This is what the partition table looks like now:
```
jon@jon-ubuntu:~$ sudo gdisk -l /dev/sda
[sudo] password for jon: 
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D6E0F5CA-2E06-4AA1-A039-E9E1B7E7FDE9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 264165 sectors (129.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          411648       205211647   97.7 GiB    0700  WINDOWS
   3       586559488       781871103   93.1 GiB    0700  UBUNTU
   4       781871104       976510983   92.8 GiB    AF00  Snow Leopard
   5       568975360       586559487   8.4 GiB     8200  
   6       205211648       568975359   173.5 GiB   0700  

```

GParted screenshot: [http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_003.png](http://dl.dropbox.com/u/8515110/temp/-dev-sda%20-%20GParted_003.png)

I'll try to boot into Windows either way and see what happens.

---

### Post by lifelike27 on 2011-05-14
So I tried booting into Windows (used update-grub just in case), and it didn't quite work. On the screen it showed:

```
find --set-root --ignore-floppies --ignore-cd /win7ldr

Error 15: File not found

Press any key to continue...
```

When I continued, I came to a screen that looked like the grub menu but with various ways to boot Windows. I tried all but none worked.

Screenshot: [http://dl.dropbox.com/u/8515110/temp/IMG_20110514_212007.jpg](http://dl.dropbox.com/u/8515110/temp/IMG_20110514_212007.jpg)

On the plus side, hibernate is now working as well as the storage partition!

---

### Post by srs5694 on 2011-05-14
In adjusting your partitions you seem to have wiped out the hybrid MBR, assuming your latest gdisk output is accurate. (It shows "MBR: hybrid" in the partition table scan when a hybrid MBR is present; but your latest output shows "MBR: protective", which means it's a conventional protective MBR.) This means that Windows won't boot from this disk -- at least, not unless you've got UEFI firmware. Thus, I recommend you re-create your hybrid MBR. Follow the instructions on my [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) Web page. Given your OS mix, I recommend putting partitions 2 and 6 (your two NTFS partitions) in the hybrid MBR and none others, unless perhaps you want to protect another partition by creating an entry for it.

Your boot loader screen shot suggests you're using GRUB4DOS, a GRUB offshoot intended for installation in DOS or Windows. Unless I've missed it, you haven't mentioned this before, so it's unclear how or where this got installed. Is it installed as your primary boot loader, or do you only see its menu after you select Windows from another boot loader menu? If the latter, it's possible that GRUB4DOS is improperly installed in a way that will make Windows difficult or impossible to boot, but I'm not positive of that. In any event, you should correct the hybrid MBR issue first, since you'll never get Windows to boot without that. You can then try booting Windows and, if it doesn't work, post back with more information about what boot loader(s) you have installed. It may be necessary to use your Windows installation or recovery disk to re-write the boot sector of the Windows partition.

---

### Post by lifelike27 on 2011-05-15
Brilliant! It worked! I saw your post in the early parts of the night and told myself I'd try it out the next day but I couldn't help myself, so I sat and did this at 3am!

I've successfully booted into Ubuntu and Windows, accessed the shared storage partition from both and successfully used hibernation on Ubuntu! Which is great since neither of us were sure how to fix it. I guess it was a GPT related issue after all.

Those links were very informative and they made me more confident about making changing with partitions.

For the record, I'm posting my commands that I used to get the hybrid MBR to work. For others who read this to have a second example (aside from yours on your website). I do urge others who see this post to please follow the links posted above by srs5694!

```
jon@jon-ubuntu:~$ sudo gdisk /dev/sda
[sudo] password for jon: 
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): r

Recovery/transformation command (? for help): h

WARNING! Hybrid MBRs are flaky and dangerous! If you decide not to use one,
just hit the Enter key at the below prompt and your MBR partition table will
be untouched.

Type from one to three GPT partition numbers, separated by spaces, to be
added to the hybrid MBR, in sequence: 2 6
Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N): y

Creating entry for GPT partition #2 (MBR partition #2)
Enter an MBR hex code (default 07): 07
Set the bootable flag? (Y/N): y

Creating entry for GPT partition #6 (MBR partition #3)
Enter an MBR hex code (default 07): 0u
Enter an MBR hex code (default 07): 09
Set the bootable flag? (Y/N): n

Unused partition space(s) found. Use one to protect more partitions? (Y/N): y
Enter an MBR hex code (EE is EFI GPT, but may confuse MacOS): 04

Recovery/transformation command (? for help): o
MBR disk identifier: 0x80F9A090
MBR partitions:
Number	 Boot	 Start (sector)	 Length (sectors)	Type
   1	    	            1	         411647 	0xEE
   2	   *	       411648	      204800000 	0x07
   3	    	    205211648	      363763712 	0x09
   4	    	    568975360	      407797808 	0x04

Disk size is 976773168 sectors (465.8 GiB)
```

If you want to clarify anything, regarding what caused hibernation to work after setting up the hybrid MBR please pm me, I'll be happy to use my computer as a test subject. :)

I really appreciate the help! Thanks a lot!

---

### Post by srs5694 on 2011-05-15
I'm glad it's working now! I'm afraid I don't have any ideas about why hibernation failed initially but now works.

One comment, though: When you created your hybrid MBR, you set the type code for GPT partition 6 (MBR partition 3) to 09. This is an MBR type code reserved for AIX. Linux ignores type codes, and of course Linux also ignores the MBR entries, but if this works in Windows it's a little surprising, since AFAIK Windows uses the type codes as a filter and only tries to mount partitions with type codes for FAT or NTFS partitions. You might therefore want to change this type code to 07. Your second pseudo-protective partition (MBR partition 4) is of type 04, which denotes a FAT partition. Windows might then try to access that space as FAT, which could wipe out some of your data. I recommend using something that will cause Windows to ignore this partition, like 09. You can change these using fdisk in Linux (do *not* try to use parted or GParted for this), or you can re-run the hybrid MBR tool in gdisk.

---

### Post by lifelike27 on 2011-05-16
So I did as you recommended once again, but I think I might have done something wrong. I can boot into Windows but the storage drive doesn't appear in My Computer. In the windows disk management, it says that the drive is unallocated.

This is what I did in the terminal when I ran gdisk again:
```
jon@jon-ubuntu:~$ gdisk /dev/sda
GPT fdisk (gdisk) version 0.6.14

Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!
jon@jon-ubuntu:~$ sudo gdisk /dev/sda
[sudo] password for jon: 
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): r

Recovery/transformation command (? for help): p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D6E0F5CA-2E06-4AA1-A039-E9E1B7E7FDE9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 264165 sectors (129.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          411648       205211647   97.7 GiB    0700  WINDOWS
   3       586559488       781871103   93.1 GiB    0700  UBUNTU
   4       781871104       976510983   92.8 GiB    AF00  Snow Leopard
   5       568975360       586559487   8.4 GiB     8200  
   6       205211648       568975359   173.5 GiB   0700  

Recovery/transformation command (? for help): h

WARNING! Hybrid MBRs are flaky and dangerous! If you decide not to use one,
just hit the Enter key at the below prompt and your MBR partition table will
be untouched.

Type from one to three GPT partition numbers, separated by spaces, to be
added to the hybrid MBR, in sequence: 2 6
Place EFI GPT (0xEE) partition first in MBR (good for GRUB)? (Y/N): y

Creating entry for GPT partition #2 (MBR partition #2)
Enter an MBR hex code (default 07): 07
Set the bootable flag? (Y/N): y

Creating entry for GPT partition #6 (MBR partition #3)
Enter an MBR hex code (default 07): 07
Set the bootable flag? (Y/N): n

Unused partition space(s) found. Use one to protect more partitions? (Y/N): y
Enter an MBR hex code (EE is EFI GPT, but may confuse MacOS): 09

Recovery/transformation command (? for help): w
```

---

### Post by lifelike27 on 2011-05-16
I should also mention that when I hit hibernate, from I see on my screen, it successfully hibernates. When I switch my laptop back on, it starts Ubuntu as a normal boot.

When I left chrome running before 'hibernating' it, when switched on, it says chrome crashed.

I guess I should mark this thread as unsolved again. :P

---

### Post by srs5694 on 2011-05-16
It looks to me like you used Ctrl+C to exit from gdisk without saving your revised hybrid MBR. You can check the status of the hybrid MBR by typing "sudo fdisk -lu /dev/sda" and seeing what partitions appear. (Compare their starting sector numbers to what gdisk reports to figure out which is which.) You *must* complete the operation and then use "w" to save your changes in gdisk or they'll vanish as soon as you exit from the program.

---

### Post by lifelike27 on 2011-05-17
Yikes! I think I hit Ctrl+C when I tried to copy the text from the terminal. It works again!

Thanks!

---

