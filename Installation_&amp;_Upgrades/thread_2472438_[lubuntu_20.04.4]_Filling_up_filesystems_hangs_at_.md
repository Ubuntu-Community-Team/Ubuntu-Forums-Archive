---
title: "[lubuntu 20.04.4] Filling up filesystems hangs at 10%"
date: 2022-02-27
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-02-27
Today I'm trying to install Lubuntu 20.04.4 from a live system booted off a loop iso on a FAT32 USB flash. The installation seems to be stuck at 10% for 10 minutes at least. I'm not sure if anything is going to happen, but there is maybe an occasional blip on the HDD LED. I'm putting it on an old 2011 Acer Veriton X2610 (UEFI firmware) with 1G RAM and a 160Gb Sata II SSD.

I set it up to use LVM ahead of time and set mount points using the installer, installer GUI accepted my configuration. 

Is there a non-GUI installer, or a way to watch the detailed progress of "Filling up filesystems." The mouse cursor froze also, is that normal during install? I think I might hard power off, and use the USB Startup Disk creator to install and see how that goes.

EDIT. Startup disk creator created install media on a 32Gb Transcend Jetflash pen drive, booted OK, crashed at 10% with a pop up error window that reads:

"Installation Failed. Failed to unpack image "/cdrom/casper/filesystem.squashfs" rsync failed with error code 11."

EDIT. Same error with using the mkusb.

Is it possible to unpack the squashfs ahead of time and have the installer use that instead?

---

### Post by GhX6GZMB on 2022-02-27
"Filling up filesystem" can easily take 20 min.

---

### Post by guiverc on 2022-02-27
> **breakdaze said:**
> 
Is there a non-GUI installer, or a way to watch the detailed progress of "Filling up filesystems." The mouse cursor froze also, is that normal during install?

"Installation Failed. Failed to unpack image "/cdrom/casper/filesystem.squashfs" rsync failed with error code 11."

EDIT. Same error with using the mkusb.


Turns out(**) I've experienced this [before ]("https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1894364")and it exists [upstream]("https://github.com/Nitrux/calamares-qml/issues/1") but I have no memory of it sorry.  All I can think of is 
- ensure you've partition the system correctly, and
- if you have a failed install - ensure you reboot **before** trying to install using `calamares` again.

In comment #2 of my own bug report you'll note I turn on the *verbose* logging of `calamares` so as to get more detailed information, but as happens *somewhat *often, the error (*with logging on*) does not re-occur so I didn't get my detailed information to find out what was wrong.  Maybe you'll be lucky and find the same.. ie. start `calamares` using

```
sudo -E calamares -d 
```


***My choice of wording ("Turns out") is I'm convinced I've seen this question before & I locked on the squashfs error I think last response. If I'm wrong, or I've just confused you, just ignore the bits you don't understand.*

*As for monitoring the system; I just switch to a text terminal & explore IO etc. I'm occasionally installing terminal tools to do this, but what I use varies on where I want to look, or what I consider the issue is; common is just looking at file IO.*

---

### Post by breakdaze on 2022-02-27
@guiverc
Thanks, the man pages didn't seem to have a reference to that option. EDIT. Oh here it is: [http://manpages.ubuntu.com/manpages/bionic/man8/calamares.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/calamares.8.html)

I was just looking at the overall Lubuntu installer guide.

 I will try that and do some more testing and ensure my filesystems are also OK.

Is there a detailed procedure about how to manually install a system by hand and skip using the installer altogether?

thanks!

---

### Post by GhX6GZMB on 2022-02-27
There's no reason to do a manual install.
The Calamares installer is extremely good.
If you're doing manual partitioning you need to take care that your partitions make sense and are mounted correctly. As you're at "Filling up filesystems" you're past this point, but might want to review it.
I recommend 20...30 GB for /

---

### Post by breakdaze on 2022-02-27
I think they are good sizes, and they were not mounted before install, but I set mount points in the installer. I should mount them from the Live System, and test them a bit though. I also did the swapoff command since I read that was important.

---

### Post by breakdaze on 2022-02-28
I tried again with Startup Disk Creator, and the debug option of calamares. First I did a test:

/  (root) is 20GiB ext4, I was manually able to mount it, mount the iso, mount the squashfs, and then copy the contents to it as a test.

But it appears calamares is trying to copy stuff to /tmp and I think the live system / is mounted on /cow, which is in RAM, correct? Or...?

It runs out of space: [https://pastebin.ubuntu.com/p/Sbz8ZgXBkS/](https://pastebin.ubuntu.com/p/Sbz8ZgXBkS/)

It warns about no EFI System Partition, but I know that. I plan to use a USB stick for that. That's not my problem. Perhaps my 1 GB RAM is not enough for what it is trying to do.

Some outputs from the live system:
```
lubuntu@lubuntu:/$ sudo findmnt -D /tmp
SOURCE FSTYPE   SIZE  USED AVAIL USE% TARGET
tmpfs  tmpfs  927.7M  927M  640K 100% /tmp

lubuntu@lubuntu:/$ sudo findmnt -T /
TARGET SOURCE FSTYPE  OPTIONS
/      /cow   overlay rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work,xino=off

```

Looks like /tmp is full!

```
lubuntu@lubuntu:/$ df
Filesystem                  1K-blocks    Used Available Use% Mounted on
udev                           893816       0    893816   0% /dev
tmpfs                          189984    6020    183964   4% /run
/dev/sdb1                     1887552 1887552         0 100% /cdrom
/dev/loop0                    1756032 1756032         0 100% /rofs
/cow                           949908  103840    846068  11% /
/dev/disk/by-label/writable  27404236   45460  25943660   1% /var/log
tmpfs                          949908       0    949908   0% /dev/shm
tmpfs                            5120       4      5116   1% /run/lock
tmpfs                          949908       0    949908   0% /sys/fs/cgroup
tmpfs                          949908  949268       640 100% /tmp
tmpfs                          189980       8    189972   1% /run/user/999
tmpfs                          949908       0    949908   0% /tmp/calamares-root-2zg0hdrl/run
lubuntu@lubuntu:/$ lsblk /dev/sdb
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sdb      8:16   1 28.5G  0 disk 
&#9500;&#9472;sdb1   8:17   1  1.8G  0 part /cdrom
&#9500;&#9472;sdb2   8:18   1  3.9M  0 part 
&#9492;&#9472;sdb3   8:19   1 26.7G  0 part /var/crash

```
```
lubuntu@lubuntu:/$ sudo blkid
/dev/sdb1: UUID="2022-02-23-09-08-19-00" LABEL="Lubuntu 20.04.4 LTS amd64" TYPE="iso9660" PTUUID="78728c63" PTTYPE="dos" PARTUUID="78728c63-01"
/dev/sda: UUID="dqCChJ-I02s-r3hR-IXBh-o4ye-LrVb-cfw7S7" TYPE="LVM2_member"
/dev/loop0: TYPE="squashfs"
/dev/sdb2: SEC_TYPE="msdos" UUID="54C5-9C6C" TYPE="vfat" PARTUUID="78728c63-02"
/dev/sdb3: LABEL="writable" UUID="f637b55c-81b1-4920-bf07-5d449c199219" TYPE="ext4" PARTUUID="78728c63-03"
/dev/zram0: UUID="0541c109-1e27-4f95-8299-0b5635e99bba" TYPE="swap"
/dev/zram1: UUID="710190c5-4992-47ea-a16e-626914458702" TYPE="swap"

```

Or it doesn't like LVM? I was able to mount all the volumes I created manually and move files around, etc.

Next step, remount /tmp somewhere on a block device first.

---

### Post by ActionParsnip on 2022-02-28
Did you check the ISO you used to make the USB stick?

---

### Post by GhX6GZMB on 2022-02-28
Is this a multiboot install?
The lsblk and blkid outputs look totally weird.

---

### Post by breakdaze on 2022-03-01
@ActionParsnip  I had not checked the ISO before, but since that's a good idea, I have now done so. The SHA256 sum was correct. Thanks.

@ml9104 Not multiboot. One SSD drive, no other OS, no bootloader (that is going to come from a separate USB stick with GNU GRUB 2.04 and EFI files on it).

I'm using LVM on a physical device, so the word partition doesn't apply here. There is no partition table, but there is a LV group on the PV. I made the LV for root (/) 20.0 GiB. Also, the reason the outputs look weird is the calamares installer does something to make it that way. A chroot, I suppose. It looked normal before I ran the installer. That's one reason a reboot is needed to try the process again. I will show you the output of my LVM2 stuff below. I had already created the PV and the VG, as well as the 4 LV I wanted to use, gave them a label, and created ext4 filesystems on them (except the swap). Below I will show the output of the lvm program where I display what I have, then create one more LV with a size of 20 GiB named temp. This is a digression from the failed install, as I already mentioned I was using lvm, but for those who are not familiar, I will post the code.

By the way, since the calamares installer does chroot or whatever, it continues to make it's own /tmp then fill it up and fail with rsync error 11 since it uses my RAM for this. 1Gb, as I said. Did you see the pastebin?

Here is output from gdisk, showing no partition table:
```
lubuntu@lubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.5

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): q
lubuntu@lubuntu:~$ 

```

LVM stuff:
```
lvm> pvdisplay /dev/sda
  --- Physical volume ---
  PV Name               /dev/sda
  VG Name               ace0
  PV Size               149.05 GiB / not usable <3.84 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              38156
  Free PE               19149
  Allocated PE          19007
  PV UUID               dqCChJ-I02s-r3hR-IXBh-o4ye-LrVb-cfw7S7
   
lvm> vgdisplay ace0
  --- Volume group ---
  VG Name               ace0
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               <149.05 GiB
  PE Size               4.00 MiB
  Total PE              38156
  Alloc PE / Size       19007 / <74.25 GiB
  Free  PE / Size       19149 / 74.80 GiB
  VG UUID               sy4v6Q-sQUa-StkI-fsNr-F4cd-oVWO-s6r1UZ
   
lvm> vgs
  VG   #PV #LV #SN Attr   VSize    VFree 
  ace0   1   4   0 wz--n- <149.05g 74.80g
lvm> lvs
  LV   VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  boot ace0 -wi-a----- 252.00m                                                    
  home ace0 -wi-a-----  50.00g                                                    
  root ace0 -wi-a-----  20.00g                                                    
  swap ace0 -wi-a-----   4.00g                                                    
lvm> lvcreate -L 20G ace0 -n temp
  Logical volume "temp" created.
lvm> quit
  Exiting.
lubuntu@lubuntu:~$ sudo mkfs -t ext4 /dev/ace0/temp
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 5242880 4k blocks and 1310720 inodes
Filesystem UUID: 47c054f1-66c1-4ed7-9ced-bde3dd734ccc
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done   

lubuntu@lubuntu:~$ sudo lvdisplay ace0
  --- Logical volume ---
  LV Path                /dev/ace0/swap
  LV Name                swap
  VG Name                ace0
  LV UUID                Hl4RLk-W6Gk-2utW-nKPF-R5Up-DjRE-yNQ73G
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2022-02-26 21:18:19 -0800
  LV Status              available
  # open                 0
  LV Size                4.00 GiB
  Current LE             1024
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/ace0/boot
  LV Name                boot
  VG Name                ace0
  LV UUID                AWybLt-cye8-n65U-sVW8-08ZZ-BDys-IgcybN
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2022-02-26 21:18:56 -0800
  LV Status              available
  # open                 0
  LV Size                252.00 MiB
  Current LE             63
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
  --- Logical volume ---
  LV Path                /dev/ace0/root
  LV Name                root
  VG Name                ace0
  LV UUID                feYnMv-dOlc-sXhY-Zwc6-G8YN-04IN-x2O66K
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2022-02-26 21:19:32 -0800
  LV Status              available
  # open                 0
  LV Size                20.00 GiB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:2
   
  --- Logical volume ---
  LV Path                /dev/ace0/home
  LV Name                home
  VG Name                ace0
  LV UUID                u6e88Y-h2eC-HQ1l-A04t-CD9f-BcVZ-DPv30k
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2022-02-26 21:22:51 -0800
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3
   
  --- Logical volume ---
  LV Path                /dev/ace0/temp
  LV Name                temp
  VG Name                ace0
  LV UUID                3g5EDk-JNdu-vNNe-Fwem-Fxhl-Icl9-orwubq
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2022-02-28 20:08:32 -0800
  LV Status              available
  # open                 0
  LV Size                20.00 GiB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:4
   
lubuntu@lubuntu:~$ sudo fsck -C -M /dev/ace0/temp
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/ace0-temp: clean, 11/1310720 files, 126322/5242880 blocks
lubuntu@lubuntu:~$ sudo fsck -C -M /dev/ace0/home
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/ace0-home: clean, 11/3276800 files, 284558/13107200 blocks
lubuntu@lubuntu:~$ sudo fsck -C -M /dev/ace0/root
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/ace0-root: clean, 11/1310720 files, 126322/5242880 blocks
lubuntu@lubuntu:~$ sudo fsck -C -M /dev/ace0/boot
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/ace0-boot: clean, 11/64512 files, 6188/64512 blocks

ubuntu@lubuntu:/media/lubuntu/T7/iso GNU_Linux$ sudo blkid |grep ace0
/dev/mapper/ace0-boot: UUID="b19b2345-03f7-4602-bff7-165f8567eade" TYPE="ext4"
/dev/mapper/ace0-root: UUID="6d9a1c9b-3407-4276-914d-fcca0422f9ab" TYPE="ext4"
/dev/mapper/ace0-home: UUID="8ba0252a-ba70-4f75-9fdf-a31378ea6fba" TYPE="ext4"
/dev/mapper/ace0-swap: UUID="b4712066-08e3-4441-a8af-24dee54c3f66" TYPE="swap"
/dev/mapper/ace0-temp: UUID="47c054f1-66c1-4ed7-9ced-bde3dd734ccc" TYPE="ext4"

lubuntu@lubuntu:~/Desktop$ sudo lsblk |grep lvm
&#9500;&#9472;ace0-swap 253:0    0     4G  0 lvm  
&#9500;&#9472;ace0-boot 253:1    0   252M  0 lvm  
&#9500;&#9472;ace0-root 253:2    0    20G  0 lvm  
&#9500;&#9472;ace0-home 253:3    0    50G  0 lvm  
&#9492;&#9472;ace0-temp 253:4    0    20G  0 lvm  /tmp

```

I omitted some changing of directories and other stuff not relevant.

As you can see, the filesystems on the volumes pass the fsck cleanly.

Maybe there is a text based installer, or some other way. I don't think calamares is going to work out in my situation. I guess I will file a bug report.

Also, here I will attach links to the screenshots of the failed install attempt through the calamares GUI.

[https://ibb.co/nwq5RR7](https://ibb.co/nwq5RR7)
[https://ibb.co/TPxC5LQ](https://ibb.co/TPxC5LQ)
[https://ibb.co/zfx6WSp](https://ibb.co/zfx6WSp)
[https://ibb.co/6YMzgYB](https://ibb.co/6YMzgYB)

cheers

---

### Post by breakdaze on 2022-03-01
@guiverc
Looks like the bug I'm getting is related to my small amount of RAM, the same as the upstream issue you linked to. On that he said the only fix was adding more physical RAM to the computer.

Should I try to go through the bug report process specifically for Lubuntu? I had a look at the Wiki. Looks like I need to install a certain program to help.

---

### Post by guiverc on 2022-03-01
1GB of RAM is very small.

I used devices with 1GB of RAM for QA-testing releases of *i386* Lubuntu, which was into the *disco* or Lubuntu 19.04 cycle, but have always used 2GB or more with *amd64* which is all Lubuntu/Xubuntu have released since dropping *i386* pre-19.04's official release.  Most of my QA-testing is done on boxes with 4GB of ram like the *sony vaio* I experienced the issue on (*my launchpad bug report; that box is used very regularly for QA-test installs & I didn't recall that bug so encountering it is very rare in my experience*) but I do use 2GB devices on occasion.

[Lubuntu no longer provides minimum specifications]("https://lubuntu.me/taking-a-new-direction/"), with most of our users using devices that have 16GB of RAM anyway; though a good 1/5-1/4 of users are using old devices that cannot expand that high (*myself included on this 2009 dell!*).

In filing bugs, the best answer you'll get will be from upstream, but I'd still file with Lubuntu first anyway.  What I would recommend is

- File on launchpad with Lubuntu/Ubuntu; see [https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/) but no additional program [*to be installed] *is required for that; `ubuntu-bug calamares` is all that is needed at a terminal after a failed install, which is all I would have done on my filed [URL="https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/1894364"]example 
[/URL]
- I would re-test using the *latest* version of `calamares` to see if it occurs there, that is only available with [Lubuntu *jammy* currently]("http://iso.qa.ubuntu.com/qatracker/milestones/429/builds").  I'd file it there too if the bug occurs; and provide links (*in comment at least*) so the bug reports can be found & linked (I'd likely mark the *focal* or 20.04 report a duplicate of the *jammy* report as the latest version will be the most useful).

Once its confirmed on the *latest* version of `calamares` you can access you can take it upstream. That would be filed on [github]("https://github.com/calamares/calamares/issues"), and if you're lucky a fix sometimes occurs rather quickly (*my [last]("https://github.com/calamares/calamares/issues/1884") took less than a day* *though I wouldn't expect that fast*;* as they need to confirm it*)

**Notes:**

For Lubuntu & bugs filed on launchpad.net (*or in fact anywhere*)   they'll need to be confirmed; I've performed multiple installs of Lubuntu in the last 24 hours, and 50+ in the last 14 days and not experienced the issue. I've also **not** seen our other [Lubuntu] QA-testers report any (*and they've performed more installs in those time-frames than I have!*). Of our testers, I also use the oldest (or *resource challenged*) equipment too (*mostly using c2d & c2q or pre-i3/i5 era hardware*) so am more likely to experience it (*my most common install box is a 2006 HP*)

Upstream are only interested in the *latest* version; which is why a *focal* report (3.2.20-0ubuntu1) may not attract attention for them (*except to request you to re-test using a later version*), but *jammy* (3.2.41.1-0ubuntu3) may. I usually also *confirm* issues using a non-Ubuntu system before taking upstream; but that caused me to delay for a long time that last issue I took upstream (*the example I used they fixed in less than a day*) so confirming in non-Ubuntu can just delay the process.

Anyway; **no additional packages are required to file bugs on a Lubuntu system** using standard Ubuntu [apport]("https://launchpad.net/apport") tools as they exist on all official releases.

---

### Post by breakdaze on 2022-03-01
@guiverc

OK, I was mistaken, this system actually has 2GB of RAM - I just re-checked the BIOS. I think the /tmp created by the installer was 1 GB of RAM, so somehow that got stuck in my head.

The system is from the year 2011, and it's an Acer Veriton X2610 with a Pentium G630 2.70 GHz. The firmware is UEFI.

Anyway, I downloaded Jammy Jellyfish, and I will try to install it. Why do we need to preserve the environment: "sudo -E calamares -d" ?

It's interesting, the 20.04.4 hybrid ISO of Lubuntu had the partition named "writable" (which I understand is the new name for the persistence partition for live USB sticks), but this hybrid ISO doesn't have that, only the ISO9660 and a small EFI System Partiton FAT12. I was thinking if calamares had used that writable partition for the /tmp then the problem possibly could have been avoided.

Anyway, I will try this new version with the hilarious name. :)

---

### Post by breakdaze on 2022-03-02
@guiverc

OK, I'm having some issues getting very far with Jammy.

In calamares installer, there is no longer an option to set the mount point for /boot on the list, and it won't allow me to type a name in manually. There is /boot/efi but that's not what I want.

I tried hitting Print Screen to take a screen shot to share, but that doesn't work (worked on 20.04.4 live session).

```
lubuntu@lubuntu:~$ w
 22:01:42 up 34 min,  2 users,  load average: 0.35, 0.25, 0.36
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
lubuntu  tty1     :0               21:27   34:34  45.22s  3.44s lxqt-session
lubuntu  pts/1    -                21:46   15:10   5.78s  0.00s sudo -E ./lubuntu-calamares.desktop -d6

```

---

### Post by guiverc on 2022-03-02
Ubuntu *jammy* uses a later version of `calamares` so options maybe different to *focal*.  *The [20.04.4 release ]("https://fridge.ubuntu.com/2022/02/25/ubuntu-20-04-4-lts-released/")is still rather recent for me; so I've seen it heaps of times in recent weeks & far more than I've installed the jammy release (43 times on the QA tracker & that's not counting daily ISOs pre-RC).*

You asked why use `sudo -E calamares -d`; sorry I can't give a good answer as I've forgotten it (ie. actual reason why).  The ISO is assumed to run in the *live* user's ID, and that's what we test it with, so at the very least it's what we've tested, but I know there is a better reason than that (*I just can't recall it sorry**; if you'd asked why in 2018 I'd have been able to tell you*)

FYI:  log is found in ~/.cache/calamares/session.log

I note `sudo -E ./lubuntu-calamares.deskto...` in your prior answer; I'd not provide paths.

On the Lubuntu ISO there are three possible paths; 2 will work & 1 will not. The one that doesn't work is added by the *calamares* code itself & it would require more work to constantly remove it than is worth it so we ignore it. I'd suggest not providing path (*even though I suspect yours is good*) just as that is QA-tested *almost daily *& I know works.

Assuming you have a launchpad ID, you can cause your QA-test install of *jammy* to be tracked via adding it to the QA tracker - [http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/)

Today's ISO didn't build; so you'll find yesterday's available for current download.

FYI:  I'd expect PRINTSCREEN to work; it should open `screengrab` (*jammy*) showing you the picture it created & allows you to specify where to save including filename.

---

### Post by breakdaze on 2022-03-02
Ok, so calamares is in the environment path is what you're saying, and just do: sudo -E calamares -d6

No, the print screen button no longer makes the screen grab pop up.

Well, I guess I can install the /boot directory to / and not have a separate volume and mount point. But it's unfortunate that it's not completely configurable and requires one to pick from a menu list.

Thanks for the info about where to fi.d the session log.

---

### Post by guiverc on 2022-03-02
I booted the daily (*no new daily had been built due issues, so it was one I'd already done some testing on*) & on hitting PrintScreen it worked for me using a sony-vaio *thingy*.  I did have to press the key twice; but I just took that was the crappy keyboard (*I like mechanical keyboards I use on desktops*)

If you can't get it again; you might consider filing a bug on that (for *jammy*); I'd suggest using `ubuntu-bug lxqt-globalkeys` and I'll specifically test for it on numerous devices (*to ensure we don't have an issue; I may also ensure other testers to give it a try too given they'll use different hardware*) but given we use the key *irregularly* ourselves in filing, commenting on, writing documentation etc, we are testing/using PrintScreen rather regularlyand on different hardware.

---

### Post by breakdaze on 2022-03-03
@guiverc
I tried to get a crash report for calamares, but that would not work either. Print Screen button worked this time.
[https://postimg.cc/YG6gvQyD](https://postimg.cc/YG6gvQyD)

---

### Post by guiverc on 2022-03-03
In that case I'd report the bug report using a browser first (eg. on this page [https://bugs.launchpad.net/ubuntu/+source/calamares](https://bugs.launchpad.net/ubuntu/+source/calamares) you'll note a ***REPORT A BUG* **link top right which will allow filing the report online)...

Then **after** the report is filed; you'll have a launchpad bug ID (say 9999999) for that report, where you can run

```
apport-collect 9999999
```

so details can be added to the *prepared report* from the *live* session where the error occurred.  Note: 9999999 will be whatever the launchpad bug ID was. **This should be done on the box where the problem occurred **(same session ideally).

For me; I'm usually using the box I'm using now to start the bug report (ie. *my primary box*) then switching to the box where I'm running the QA-test install that failed and run the `apport-collect` there so correct details are obtained.  You maybe able to do it all on the one box (*I've done it that way myself*) but it's up to you.  Key is the `apport-collect` must be run on the box where the issue occurred; and it should be the exact same session for a decent report which we can explore.

If you're unable to run the `apport-collect` in that session (*I believe unlikely, but we won't know until tried* *and there are rare cases where it's impossible too*) you can ask me again for more clues; **but** if required you can re-start the session (ie. reboot) and run it at least on the same box; **BUT please mention it's a subsequent session **(ie. you were forced to reboot due to problem you outline) so we know why report is ~empty without error(s)/clue(s).

---

