---
title: "fixMBR on a Liunx HDD"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by bPawn on 2006-10-07
Well, I accidentally run fixMBR on a linux HDD and of course everything is messed up. I tried the solution found in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but with no luck. The problem appears to be that my sda is no longer recognized as ext3 filesystem but as fat16, at least the partion manager of the installer says so. Any ideas on how to restore grub and my filesystem? Any help is more than appreciated since I have not backed up my data for a while.

---

### Post by bPawn on 2006-10-07
If I follow the first part of the guid I get 


```
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub>
```

Using the second method I get 

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/s /mnt/root
sda      sdb1     sg1      snd/     stderr   stdout
sdb      sg0      shm/     sndstat  stdin
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sd /mnt/root
sda   sdb   sdb1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda /mnt/root
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$
```


If I start the installer and manually edit partition table:

```
Number Partiton Type Status Size Used space Start End Label
01 /dev/sda1 fat16 Hidden 149.05GB N/A 0.00MB 149.05GB
```

which was not the case before fixMBR

(n00b question) I there any way to change the filesystem with mkfs without erasing the data?

---

### Post by Herman on 2006-10-07
Hello bPawn,
As you may already know, the MBR contains an area of 446 bytes for the bootloader's IPL code, plus the partition table area of 64 bytes, (four primary partition entry spaces of 16 bytes seach, and finally, the two byte 55aah bootable device signature. [Click Here for an illustration]("http://users.bigpond.net.au/hermanzone/p6.htm#What_does_an_IPL_really_look_like").
Normally, when we edit one part of the MBR, it does not affect the other parts very much. Partition editing software works on the partition table, and bootloaders write their codes in their section of the MBR. Although, bootloaders and partitioners can both change the 'active' flags, or 'hide' a partition It isn't common to have a filessytem changed by a bootloader. Probably you just need to fix your partition table enrty, and you actual partition and all its data will still be okay.

I have read a good report about someone using TestDisk to success fully recover an MBR for a disk with NTFS partitions on it, over in [GParted LiveCD]("http://gparted.sourceforge.net/") forums. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is one of the great  utilities included in the most up to date versions of GParted LiveCD.  (I also tried out partimage from a GParted LiveCD last night).
Be sure to read the TestDisk documentation first if you decide to give that a try.
If you decide to try it, you download GParted LiveCD version 0.3-1-1, for example, and burn the .iso to  a CD-RW or a CD.  (Unless you get the USB version).
Then you boot GParted LiveCD, and when it is booted, you open a terminal, and type 'testdisk' to get started. ```
testdisk

```I don't know what you need to do after that, I haven't needed to use it, but read the docs in the already provided link here,[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), I think it will be quite straightforward.

Good luck, and let us know how you get along. Other people in the future might benefit from your feedback. :D

Regards, Herman

---

### Post by Herman on 2006-10-07
After you get the partition table part of your MBR fixed, then catlett's excellent  how to, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), that you already mentioned should restore the IPL part of the MBR with Grub's code for you. Normally that how to should have worked and done all that would be required.

---

### Post by bPawn on 2006-10-07
Thank you guys! It's 2:40 in the morning and I feel like a zombie. I will try everything you suggested, when I wake up and keep you posted...

---

### Post by bPawn on 2006-10-08
Tata!!, I managed to restore my partitions and save my data.
Here is what I did:

-I had an HDD with a clean installation of win XP :-# . I downloaded TestDisk (win version).

-I wrote a new MBR. (however I 'm not sure if this helped at all)

-I realized that **I had to install SP1 in order TestDisk to detect the correct size of my linux HDD with correct 48 bit LBA blah blah.**

-I scanned for partitions (the *intel* option I think).

-I wrote partition info to the linux disk.

-I rebooted ](*,) 

-I used the **explore2fs** ([http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)) in order to copy the data to my win HDD.

----
I have not tried to install GRUB using this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) since I plan to install edgy. My guess is that GRUB installation should work just fine.

Also, I could not restore the swap partition (maybe I did smth wrong) but since I plan for a new installation it doesnt matter.

One more thing, If someone do not have a win installation I suggest using a live cd (i.e. knoppix ) as mentioned before.

I strongly recommend TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) if anyone messed up a linux HDD

---
hope this helps the next generations :-D

---

### Post by Herman on 2006-10-09
Thanks, I'm glad it worked, and thanks for the feedback too, I'll recommend testdisk again someday. :D
Regards, Herman

---

