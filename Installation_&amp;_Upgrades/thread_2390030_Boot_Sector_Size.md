---
title: "Boot Sector Size"
date: 2018-04-24
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2018-04-24
I noticed a couple days ago I was receiving a notification that my system had an update available.  So I clicked to update and this is the message I got.  The thing ios it doesn't say how to increase the size.  It does say how to compress the sector, but nothing about how to do it or how to increase it.  I am on a 1 terabyte hard drive with about 720 gigabytes free!

---

### Post by oldfred on 2018-04-24
Have you backed up system?
Have you removed any proprietary drivers and ppas. If not update may not complete.
You need to houseclean before update. I prefer backup, total new install & restore data as then you have done a total houseclean.

 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels) 

# check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by TheFu on 2018-04-24
Ninja'd by oldfred!  ;)

We need more detailed data.  Please post the command and output from 3 commands below using "code tags" - that's under Adv Reply (#):
```
df -h
df -hi
sudo fdisk -l
```
That's what your post should look like with code tags. Things line up nicely from a terminal and we don't waste bandwidth with unnecessary images. BTW, providing the img in the OP **was** good, clear.

Thanks.

It might just be that you haven't run **sudo apt autoremove **recently.  I'd try that first.

---

### Post by shane_faulkinbury2 on 2018-04-24
I might go ahead and do what oldfred said since I'm sure it's 18.04  LTS!  Am I correct?


Anyway, here you go TheFu.

```
$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        787M  9.4M  778M   2% /run
/dev/mapper/ubuntu--vg-root  911G  157G  708G  19% /
tmpfs                        3.9G   53M  3.8G   2% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   102M  102M     0 100% /snap/skype/22
/dev/loop2                   102M  102M     0 100% /snap/skype/23
/dev/loop4                   163M  163M     0 100% /snap/spotify/13
/dev/loop3                   160M  160M     0 100% /snap/spotify/5
/dev/loop7                    87M   87M     0 100% /snap/core/4486
/dev/loop1                   102M  102M     0 100% /snap/skype/19
/dev/loop5                   163M  163M     0 100% /snap/spotify/6
/dev/loop6                    82M   82M     0 100% /snap/core/4206
/dev/loop8                    87M   87M     0 100% /snap/core/4407
/dev/sda2                    473M  421M   28M  94% /boot
/dev/sda1                    511M  3.5M  508M   1% /boot/efi
tmpfs                        787M  112K  787M   1% /run/user/1000

```

```
~$ df -hi
Filesystem                  Inodes IUsed IFree IUse% Mounted on
udev                          977K   553  976K    1% /dev
tmpfs                         984K   803  983K    1% /run
/dev/mapper/ubuntu--vg-root    58M  472K   58M    1% /
tmpfs                         984K    78  984K    1% /dev/shm
tmpfs                         984K     7  984K    1% /run/lock
tmpfs                         984K    17  984K    1% /sys/fs/cgroup
/dev/loop0                    1.5K  1.5K     0  100% /snap/skype/22
/dev/loop2                    1.5K  1.5K     0  100% /snap/skype/23
/dev/loop4                     24K   24K     0  100% /snap/spotify/13
/dev/loop3                     25K   25K     0  100% /snap/spotify/5
/dev/loop7                     13K   13K     0  100% /snap/core/4486
/dev/loop1                    1.5K  1.5K     0  100% /snap/skype/19
/dev/loop5                     25K   25K     0  100% /snap/spotify/6
/dev/loop6                     13K   13K     0  100% /snap/core/4206
/dev/loop8                     13K   13K     0  100% /snap/core/4407
/dev/sda2                     122K   328  122K    1% /boot
/dev/sda1                        0     0     0     - /boot/efi
tmpfs                         984K    46  984K    1% /run/user/1000

```

```
$ sudo fdisk -l
[sudo] password for none: 
Disk /dev/loop0: 101.9 MiB, 106799104 bytes, 208592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 101.6 MiB, 106532864 bytes, 208072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 101.9 MiB, 106803200 bytes, 208600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 159.5 MiB, 167231488 bytes, 326624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 162.1 MiB, 169943040 bytes, 331920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 162.6 MiB, 170479616 bytes, 332968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 81.7 MiB, 85692416 bytes, 167368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B147CD07-192D-4A79-B6D2-D662FEB5DC2E

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2050047     999424   488M Linux filesystem
/dev/sda3  2050048 1953523711 1951473664 930.5G Linux filesystem




Disk /dev/mapper/sda3_crypt: 930.5 GiB, 999152418816 bytes, 1951469568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 924.7 GiB, 992825311232 bytes, 1939111936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 5.9 GiB, 6325010432 bytes, 12353536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 86.5 MiB, 90726400 bytes, 177200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by TheFu on 2018-04-24
```
/dev/sda2                    473M  421M   28M  94% /boot
```
is the problem.
So you installed using LVM. That creates a separate /boot partition for the required boot files.  Yours is full, probably with old kernels.
Did you run the **sudo apt autoremove** command suggested? That should clean up stuff.  I have less than 200MB on my /boot here, so that is most probably the issue.


I don't understand the 18.04 reference.  Nobody should be using that yet for anything they need. Testing is fine, but should be willing to wipe it.

---

### Post by shane_faulkinbury2 on 2018-04-24
I think that worked!  I'll have to check tomorrow morning when I do a reboot.  Thanks TheFu.

```
$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        787M  9.4M  778M   2% /run
/dev/mapper/ubuntu--vg-root  911G  156G  709G  19% /
tmpfs                        3.9G  114M  3.8G   3% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   102M  102M     0 100% /snap/skype/19
/dev/loop2                    87M   87M     0 100% /snap/core/4486
/dev/loop1                   102M  102M     0 100% /snap/skype/23
/dev/loop7                   102M  102M     0 100% /snap/skype/22
/dev/loop6                   163M  163M     0 100% /snap/spotify/13
/dev/loop4                   160M  160M     0 100% /snap/spotify/5
/dev/loop3                    87M   87M     0 100% /snap/core/4407
/dev/loop5                    82M   82M     0 100% /snap/core/4206
/dev/loop8                   163M  163M     0 100% /snap/spotify/6
/dev/sda2                    473M  151M  298M  34% /boot
/dev/sda1                    511M  3.5M  508M   1% /boot/efi
tmpfs                        787M   96K  787M   1% /run/user/1000
none@none-HP-Compaq-8200-Elite-SFF-PC:~$ df -hi
Filesystem                  Inodes IUsed IFree IUse% Mounted on
udev                          977K   541  976K    1% /dev
tmpfs                         984K   798  983K    1% /run
/dev/mapper/ubuntu--vg-root    58M  343K   58M    1% /
tmpfs                         984K   166  983K    1% /dev/shm
tmpfs                         984K     7  984K    1% /run/lock
tmpfs                         984K    17  984K    1% /sys/fs/cgroup
/dev/loop0                    1.5K  1.5K     0  100% /snap/skype/19
/dev/loop2                     13K   13K     0  100% /snap/core/4486
/dev/loop1                    1.5K  1.5K     0  100% /snap/skype/23
/dev/loop7                    1.5K  1.5K     0  100% /snap/skype/22
/dev/loop6                     24K   24K     0  100% /snap/spotify/13
/dev/loop4                     25K   25K     0  100% /snap/spotify/5
/dev/loop3                     13K   13K     0  100% /snap/core/4407
/dev/loop5                     13K   13K     0  100% /snap/core/4206
/dev/loop8                     25K   25K     0  100% /snap/spotify/6
/dev/sda2                     122K   302  122K    1% /boot
/dev/sda1                        0     0     0     - /boot/efi
tmpfs                         984K    44  984K    1% /run/user/1000
none@none-HP-Compaq-8200-Elite-SFF-PC:~$ sudo fdisk -l
Disk /dev/loop0: 101.6 MiB, 106532864 bytes, 208072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 101.9 MiB, 106803200 bytes, 208600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 86.5 MiB, 90726400 bytes, 177200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 159.5 MiB, 167231488 bytes, 326624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 81.7 MiB, 85692416 bytes, 167368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 162.1 MiB, 169943040 bytes, 331920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 101.9 MiB, 106799104 bytes, 208592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B147CD07-192D-4A79-B6D2-D662FEB5DC2E

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2050047     999424   488M Linux filesystem
/dev/sda3  2050048 1953523711 1951473664 930.5G Linux filesystem




Disk /dev/mapper/sda3_crypt: 930.5 GiB, 999152418816 bytes, 1951469568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-root: 924.7 GiB, 992825311232 bytes, 1939111936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 5.9 GiB, 6325010432 bytes, 12353536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 162.6 MiB, 170479616 bytes, 332968 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by TheFu on 2018-04-25
a) please mark this thread as solved to help the community out, if you think it is solved.
b) df -i .... shows inode counts.  You don't have any issue with that. No need to worry about them 99.99999% of the time.  When those run out, there aren't many solutions.
c) / is huge!

/dev/mapper/ubuntu--vg-root  911G  156G  709G  19% /
I would never have / be larger than 25G, then I'd put non-OS stuff, like /home somewhere else.  Because you are using LVM, you can shrink it, create another LV for other places as you need, then make a file system and mount it where you like.  Much easier to do when it isn't full.

Why?  Storage architecture is all about backups.  Backing up the OS when it is 25G is much easier than backing up 900G. I bet if you looked, all the OS stuff is only 15G or less.  It is hard to use even 25G for OS files and applications.  It is usually media files and WINE-stuff that eat up storage and all that goes into your HOME. If you create a spare LV (also 25G) you can mirror the OS to the other one fairly easily.  With a tiny bit of effort, you'll never be left with a computer that won't boot.  And if you only allocate enough storage for /home (the LV that home uses), then you won't be surprised with all the crap that ends up there just because you forget to clean things up.

Make sense?

LVM is amazing and choosing to install with it really does add some fantastic flexibility to you.

---

### Post by shane_faulkinbury2 on 2018-04-26
I'm going to leave it open for now because ever since I cleaned everything up  I'm not getting the update information!  As you can see i have System Settings set for the LTS upgrade.  Should I do it manually?

---

### Post by TheFu on 2018-04-26
New is the enemy of stable.  

Do not upgrade without a full, system-level, backup first.

Also makes sense to review the "release notes" for 18.04.  There are a few gotchas in the long list of issues that impact me AND you.  LVM is one of them.

They will fix many of the known issues, but getting it early has some risks.  I'll probably wait until June to move my test desktop. I won't be moving any other systems until 2019 at the earliest.

---

### Post by shane_faulkinbury2 on 2018-04-27
I figured out the problem and got it to work running a 

```
[COLOR=#444444][FONT=&quot]update-manager -cd[/FONT][/COLOR]
```

But I got an error after it ran awhile, so it must be the LVM.  Can I load without the LVM and then set it up manually after the upgrade or should I stick with 16.04 for now and hopefully wait for them to fix the issue?

---

### Post by TheFu on 2018-04-27
Stick with 16.04.
Moving to LVM for the OS is non-trivial.
Using LVM for new storage, outside the OS, is an intermediate skill.

IMHO.

But it is your system.  If you can deal with the issues, report bugs and supply fixes, then go for it!

---

### Post by shane_faulkinbury2 on 2018-04-29
oldfred,

At this point I think I'm just going to take your advice since it is the LTS.

I've been waiting sveral days now and nothing!

Thanks for your help guys

---

