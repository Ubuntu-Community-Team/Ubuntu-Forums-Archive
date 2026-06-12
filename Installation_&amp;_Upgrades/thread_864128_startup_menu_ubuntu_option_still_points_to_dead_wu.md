---
title: "startup menu ubuntu option still points to dead wubi install after 8.04 install"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by dave50seven on 2008-07-19
Hi

I had xp and vista installed, slow as hell so wanted to try ubuntu and was recommended wubi. I couldn't get it working, so uninstalled it but the 'ubuntu' option in windows boot manager remained. 

Meanwhile both versions of windows died (for unrelated reasons) so I got an 8.04 iso which runs fine as livecd and seemed to partition my drive and install fine but on reboot I arrived at windows boot manager, chose ubuntu option and got:

"windows failed to start" etc.

"File: \ubuntu\winboot\wubildr.mbr   Status: 0xc000000f    Info: The selected entry could not be loaded because the app is missing or corrupt"

I'm guessing I need to point the boot manager to the real ubuntu 8.04 install, I don't want to remove boot manager altogether because I still want access to vista in safe mode for the time being.

I can still boot ubuntu off the CD and can now see the ubuntu installed drive with everything apparently installed ok on it.

Any help very much appreciated!

---

### Post by ajgreeny on 2008-07-19
It sound as if grub was not installed, or not installed properly for some obscure reason.  The simplest way to proceed is:-

1   Make sure Ubuntu is really installed on hard disk using the ubuntu liveCD by booting to that, and then in Applications>>Accessories>>Terminal running ```
sudo fdisk -l
```and copying the output here if you can not understand it.

2   If you can see that ubuntu is definitely there as expected, use the info below to install grub.
Having booted into the ubuntu live CD, open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck, I hope this gets you up and running.

---

### Post by dave50seven on 2008-07-24
Hi ajgreeny, 

thanks so much for getting back to me, sorry I haven't replied sooner, 

I tried what you suggested but sadly still not booting from HD. Here's the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19f919f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3015    24217956   83  Linux
/dev/sda2            3016       19457   132070365    f  W95 Ext'd (LBA)
/dev/sda5            6200       11299    40965718+   7  HPFS/NTFS
/dev/sda6           11300       19457    65529103+   7  HPFS/NTFS
/dev/sda7            3016        6061    24466932   83  Linux
/dev/sda8            6062        6199     1108453+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47cb778a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           12752       24792    96719332+   f  W95 Ext'd (LBA)
/dev/sdb2               1       12751   102422376    7  HPFS/NTFS
/dev/sdb5           12752       19126    51207156    7  HPFS/NTFS
/dev/sdb6           19127       24792    45512113+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b13e4c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         261     2096451    b  W95 FAT32
/dev/sdc2             262        9874    77216391    7  HPFS/NTFS
/dev/sdc3            9875       14946    40740840    f  W95 Ext'd (LBA)
/dev/sdc5            9875       14946    40740808+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,6)
grub> root (hd0,6) 
root (hd0,6)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

I tried the same again but with 'setup (hd1)', which reported successful, but pc still goes to Windows boot manger.

I'm not bothered about saving vista any more.

Thanks again for your help!

---

### Post by dstew on 2008-07-24
Which disk is your BIOS set to boot? Maybe it is booting from one of the other disks instead of /dev/sda.

---

### Post by dave50seven on 2008-07-24
I'm in!!!! :-D

I can't choose which HDD to boot from in the BIOS, it only has options 'cd-rom' 'hard disk' 'usb' etc. 

But - according to fdisk the only other bootable partition besides ubuntu was a 2 Gb Fat32 partition on my old ATA drive. I have 2 SATA drives (one had XP and vista installed on different partitions - I always assumed it booted from one of these) and 1 ATA. I just physically disconnected the ATA and the pc booted into ubuntu straight away. 

Maybe the BIOS automatically gives boot priority to ATA drives?

Now I need to figure out how to override that so I can reconnect it (I guess change or delete the MBR from the ATA drive, but at least meanwhile I can explore a cool new OS)

Thanks for all your help guys!

---

