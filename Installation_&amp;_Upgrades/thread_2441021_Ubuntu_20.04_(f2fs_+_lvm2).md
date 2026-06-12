---
title: "Ubuntu 20.04 (f2fs + lvm2)"
date: 2020-04-17
forum: Installation &amp; Upgrades
---

### Post by inferexcav on 2020-04-17
Hi! I'm new to linux and lvm, this is my first try to manage partitions, usually I went with one partition.

So I have installed ubuntu 20.04 release candidate on temp ext4 partitions then rsync boot to dev/sda1 (f2fs) and rsync root to dev/mapper/system-root (f2fs on lvm)
Mount binded folders and work further under chroot. Since I have GPT drives and Legacy Bios I made a grub install on dev/sda and I've added to [COLOR=#000000][FONT=Verdana]/etc/default/grub  [/FONT][/COLOR][COLOR=#006600][FONT=Courier]GRUB_CMDLINE_LINUX="rootfstype=f2fs quite splash"[/FONT][/COLOR] and commented out [COLOR=#006400][FONT=verdana]if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi [/FONT][/COLOR]because it gave an error "[COLOR=#006400]sparce file not allowed[/COLOR] ". 
Now when I dealt with it, I have errors on boot:
[COLOR=#800000][    0.293886] pci 0000:03:02.0: BAR 1: error updating (0xd8020000 != 0x98020000)
ln: /tmp/mountroot-fail-hooks.d//scripts/init-premount/lvm2: No such file or directory
fsck.f2fs: error whule loading shared libraries: libf2fs.so.5: cannot open shared object file: No such file or directory
fsck exited with status code 127
The root filesystem on /dev/mapper/system-root requires a manual fsck

[/COLOR]Possible problems:
1) apt-get install didn't work properly under chroot for some reason so I manually copied /sbin/fsck.f2fs from livecd dir to f2fs root dir, maybe it has dependencies on other files. At least I compiled initramfs after this copy-paste...
2) do I need to add lvm2 to initramfs-tools/modules as well?

I have no idea what to do next, these errors already manually troubled me so much... I really appreciate any help. Thanks!

P. S.
my etc/initramfs-tools/modules:
[COLOR=#000000][FONT=monospace]f2fs
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]crc32_pclmul
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]crc32_generic[/FONT][/COLOR]

---

### Post by dino99 on 2020-04-18
Looks like your project is quite border line
[https://askubuntu.com/questions/452914/installing-ubuntu-14-04-on-a-f2fs-partition](https://askubuntu.com/questions/452914/installing-ubuntu-14-04-on-a-f2fs-partition)

---

### Post by TheFu on 2020-04-18
Someone new to Linux and LVM probably shouldn't attempt what you are attempting.  Booting from non-default storage isn't a trivial thing and it will bring pain that you don't know today.  I did this back in the 1990s and was stuck with all sorts of problems for years because of my choice.

Now, if you want to use f2fs for data, that's great, wonderful, easy, fine.  Using it for boot and for the OS - that will be painful.

But if you are a Unix wizard, please, continue. Linux is mostly like Unix, so you should be fine and already have read the errors and solved them. Interesting project. Please take careful notes and wipe the system when you are done, then retrace those steps again to be 100% certain it is repeatable.

I really hope you appreciate my candor.  You can attempt anything you want, of course.

---

### Post by inferexcav on 2020-04-19
So, basically since I was using chroot for the first time, I should have properly set up [COLOR=#242729][FONT=Consolas]resolv.conf[/FONT][/COLOR] and apt [COLOR=#242729][FONT=Consolas]sources list[/FONT][/COLOR] ...
After this fix apt-get started working again and it was possible for me to install f2fs-tools, xfsprogs, bcache, etc. Then I added to initramfs script that mounts all lvm volumes on start just in case because its linux and initramfs finally let me load in the system. UBUNTU PLS ADD AT LEAST STOCK F2FS SUPPORT, I don't even talk about lvm on luks... 
What do you think about my partitions filesystems and sizes? Now I have:
/dev/sda 120GB:
/dev/sda1 1GiB f2fs /boot
/dev/sda2 110GiB lvm:
 - dev/system/cache 12GiB bcache caching point 
 - dev/system/db 10GiB f2fs
 - dev/system/home 5GiB f2fs
 - dev/system/root 8GiB f2fs
 - dev/system/swap 12GiB linuxswap with swappiness=10 (Total RAM = 8GB)
 - dev/system/tmp 1GiB f2fs
 - dev/system/usr 8GiB f2fs
 - dev/system/var 5GiB f2fs
 - dev/system/ unallocated 50GB for lvm snapshots
/dev/sda3 48MiB fat32 grub
/dev/sdb 1.77TiB:
 - dev/data/srv 1.37TiB bcache backing point
 - dev/data/ unallocated 0.4TiB for cron backuping lvm snapshots from different volume group
/dev/bcache0 1.37TiB xfs

I know it's very complicated project for someone who barely knew how to use mount command on its start, but I managed to do it. After so many tried to load now I can use the mount and mount bind with closed eyes without checking fdisk for partitions names. Initially I was doing everything on top of LUKS, but god damn I decided I need more speed than security, especially, if I'm using bcache. I hope this info can help!

Disk speeds:
SSD f2fs:
237.6 MB/s avg rr | 165.3 MB/s avg wr | 0.27 msec avg access 
HDD:
128.9 MB/s avg rr | 60.3 MB/s avg wr | 14.38 msec avg access
HDD with bcache (writeback mode) as xfs:
127.3 MB/s avg rr | 70.8 MB/s avg wr | 14.36 msec avg access

Lots of pain for 10% increase in disk write speeds and luxury privilege of snapshots and changing partition sizes without any harm. Can't properly check benefits of bcache for read speeds since files, as I understand, should be in the system for a while and accessed several times.
I'm already crying deep inside thinking that one day apt-get update/upgrade will spoil all the honey I have rn. Gotta learn how to use lvm snapshots and backup them with cron on the separate drive because of the logical volumes snapshot limitations, they have to be on the same drive as partitions, but I'm already so done.

---

### Post by inferexcav on 2020-04-19
> **dino99 said:**
> Looks like your project is quite border line
[https://askubuntu.com/questions/452914/installing-ubuntu-14-04-on-a-f2fs-partition](https://askubuntu.com/questions/452914/installing-ubuntu-14-04-on-a-f2fs-partition)

I've been there, read that. Outdated info! But thanks for the reply...

---

### Post by inferexcav on 2020-04-19
> **TheFu said:**
> Someone new to Linux and LVM probably shouldn't attempt what you are attempting.  Booting from non-default storage isn't a trivial thing and it will bring pain that you don't know today.  I did this back in the 1990s and was stuck with all sorts of problems for years because of my choice.

Now, if you want to use f2fs for data, that's great, wonderful, easy, fine.  Using it for boot and for the OS - that will be painful.

But if you are a Unix wizard, please, continue. Linux is mostly like Unix, so you should be fine and already have read the errors and solved them. Interesting project. Please take careful notes and wipe the system when you are done, then retrace those steps again to be 100% certain it is repeatable.

I really hope you appreciate my candor.  You can attempt anything you want, of course.

I decided to go this hard way only because I read a bit about lvm snapshots since backing up partitions was always for me a mystery as well as to help extend my SSD drive life and improve OS/apps boot times. Tho on the other side I'm using bcache which is reducing SSD life, so it's kinda hypocritical paradox.

When I started, I knew that sooner or later my house of cards will be mercilessly destroyed by apt-get update/upgrade. I decided it will be easier for me to learn one time how to use LVM snapshots and roll back than destroying my USB port with LiveCD every time new problem appears .__.

---

### Post by TheFu on 2020-04-20
Snapshots are a temporary thing.  Not something we keep around too long, certainly not more than a week.  Backups have always required being placed on other storage. The purpose of LVM snapshots for backup processing is only to have a static, 100% quiescent area, for the backups to pull data.  By setting up all those LVs, you've drastically complicated things to the point of .... well ...  absurdity.  You've made so many things hard for ZERO return. Whatever.  You will learn, grasshopper.

No same-release patching should harm your layouts or file systems, assuming they work.  Every new kernel may leave you with a non-booting OS. I hope that doesn't happen, but you need to be prepared for that about 2-3 times a month.  It is only when moving to the next release in 22.04 that you'll feel the pain.  If you move sooner, what a waste.

Desktop storage layout just doesn't need as much storage as you've thrown at this for the OS stuff. 25G is usually 10G over what anyone uses.  

Server storage layout needs much, much, less storage for the OS. I have entire servers running in less than 2G of storage, total, for the OS.  So, give a server 10G for all the OS stuff and add more to /var/ if you need that area to be larger for logs, VMs, Containers.

There are lots of threads here about storage layouts. Clearly, you've seen some, somewhere.  Why have separate LVs for /usr and /bin and /root?  Why? What's the point of so much swap?  Today, the only point of swap is to provide feedback to the user that they need to reduce memory demands.  Swap needs to be on slow storage, so that feedback is clear, felt.  I suppose, if you have customers who you dislike and want to leave, you could use 50G of swap and load up all sorts of programs (over commit) so pretty much every process gets swapped.  That's what Godaddy does with their cheap VPS tiers.  They either want the customers to upgrade to more RAM, more disk, or go somewhere else.  

/home can be whatever size you want.  Lots of people don't bother with a separate /home, since the data directories are going to be symlinked to other storage.  
Any system with over 4G of swap has problems, IMHO.

I'll be quiet now. It is your system.

We brought the horse to the pond .... doubt he will drink.

---

### Post by inferexcav on 2020-04-20
> **TheFu said:**
> Snapshots are a temporary thing.  Not something we keep around too long, certainly not more than a week.  Backups have always required being placed on other storage. The purpose of LVM snapshots for backup processing is only to have a static, 100% quiescent area, for the backups to pull data.  By setting up all those LVs, you've drastically complicated things to the point of .... well ...  absurdity.  You've made so many things hard for ZERO return. Whatever.  You will learn, grasshopper.

As I mentioned before, this is what I initially planned:
[COLOR=#000000][SSD] [/COLOR][COLOR=#000000]- dev/system/ unallocated 50GB for lvm snapshots
[/COLOR][COLOR=#000000][HDD] [/COLOR][COLOR=#000000]- dev/data/ unallocated 0.4TiB for cron backuping lvm snapshots from different volume group
[/COLOR]snapshots goes to SSD and then cron backups those shanpshots once a day to HDD during the night, it's good that a snapshot will take the same amount of space as changes it been made to the partition, the only thing I doubt right now is it a good idea at all make snapshots of the database partition? Maybe there are better tools than snapshot for database backup purposes, IDK yet.[COLOR=#000000]
[/COLOR]
Yes, it may look absurd, but there are several reasons behind:
1) LVM allows you to resize volumes any time. Yes with f2fs (IMO should extend life to SSD) it's a bit more hassle, since it doesn't shrink partitions "out of the box" and you need to transfer files on ext4 first, and then create smaller f2fs.
2) This is basically future web server for back-end file processing queue, all the partitions will be mounted as system dirs. I've done this for several reasons:
[LIST]
[*]If apache uploads or db, or logs, or tmp files, or home, or var somehow fill up all the available space, I don't want to disturb services' work with such a stupid problem.
[*]I had windows as a main system but I didn't have enough space for snapshots on the same drive. I wiped windows 60GiB partition and gave myself a luxury opportunity to make furute ubuntu disk partitions x1.5 bigger than it was initially planned. Now I don't need to check everyday worried something went wrong because there was not enough of space.
[*]It's my first serious project, so yes, I'm still learning, please consider this as well.
[*]Even if the partition fills up, it's very easy to increase the volume size of any partition, or decrease it, even swap, if I don't need it.
[*]Data protection and separation. If user or group somehow have access to the whole partition IMO it's very bad, it can be accidentally wiped out or more confidential data can be stolen/more harm can be done than it was initially planned. And it's harder to separate data you want to definitely store.  I don't want to have tmp, home, apache and db on one partition, since it's just a bomb with delayed explosion.
[/LIST]

> **TheFu said:**
> No same-release patching should harm your layouts or file systems, assuming they work.  Every new kernel may leave you with a non-booting OS. I hope that doesn't happen, but you need to be prepared for that about 2-3 times a month.  It is only when moving to the next release in 22.04 that you'll feel the pain.  If you move sooner, what a waste.

Desktop storage layout just doesn't need as much storage as you've thrown at this for the OS stuff. 25G is usually 10G over what anyone uses. 

This is why I choose LTS, even if it's a release candidate, I really hope there shouldn't be any serious changes in the kernel in a few days on the release. 22.04 will come out in two years, I definitely have time to not only figure out how to properly upgrade server kernel without restart and any data loss but also how to make own modified kernel, but honestly I don't have right now any reason for the latter.

When I used the whole partition for the OS, I used 20-25GiB as well. Since partitions doesn't share the space between each other anymore, each of the partitions requires its own extra space, which for obvious reasons all extra spaces and data itself will go above 25GiB in total. Even with all that I have 50GiBs unallocated just in case if one logical volume will go breaking bad and fill up unexpectedly fast. After the installation with gnome (don't throw stones at me please, I will remove gnome as soon as I finish with everything, tho I don't think it will give me that much space on deletion) I don't regret choosing 8GB for the root partition since root already has left with 818.1MB space available, can resize with two clicks (or command lines after gnome is gone) any time I need.

> **TheFu said:**
> Server storage layout needs much, much, less storage for the OS. I have entire servers running in less than 2G of storage, total, for the OS.  So, give a server 10G for all the OS stuff and add more to /var/ if you need that area to be larger for logs, VMs, Containers.

There are lots of threads here about storage layouts. Clearly, you've seen some, somewhere.  Why have separate LVs for /usr and /bin and /root?  Why? What's the point of so much swap?  Today, the only point of swap is to provide feedback to the user that they need to reduce memory demands.  Swap needs to be on slow storage, so that feedback is clear, felt.  I suppose, if you have customers who you dislike and want to leave, you could use 50G of swap and load up all sorts of programs (over commit) so pretty much every process gets swapped.  That's what Godaddy does with their cheap VPS tiers.  They either want the customers to upgrade to more RAM, more disk, or go somewhere else.

I checked 10+ different threads about layouts, filesystems, and the thing I learned, it's almost the same as with distro - there is a way that is generally followed but everyone has their own needs, so everything varies a lot, even between two servers difference can be huge in partition sizes and filesystems used. There are a lot of variables: how much space do you have, do you use cache or not, do you use swap or not, do you use single or multiple partitions, any lvs, any dbs, any raid, any other web services, etc. I try to consider all these factors.

I do agree that swap need to be on slow storage, however, since I changed the swappiness from 60 to 10, swap will be used in very low priority, only when RAM is about 7+ out of 8GB of ram. So only when it's really needed and SSD have much better random read/write/access times, doesn't make it more sense to have swap on SSD if you want to have relatively workable speed compare to HDD swap, which sometimes just slow down the server to the point u wish you just run out of memory. So I can be wrong, but yes for HDD I would use x0.5 of RAM I have with default swappines 60, for SSD I decided to go with x1.5RAM and 10 swappiness ( swappiness also should extend SSD life while giving good speeds when you really need swap; I use big swap maybe to protect system during exceptional large file processing, maybe for future system updates, sometimes they can be also RAM hungry) Well, maybe not that hungry with 8GB of total RAM, but it's better to be overprepared than otherwise. Since SSD 10x+ times slower than RAM and is used as caching device for HDD in writeback mode, as well as parallel writing to snapshots, I bet when swap will be used I will still feel it tho not that painful if it were on HDD. Anyway, I hope I will find even more advantages in the future to justify SWAP size. I hope you understand that space is the least out of my problems, really. I'm more considered about the server uptime and server components life duration, write/read/access speeds as well as data backups.

> **TheFu said:**
>  /home can be whatever size you want.  Lots of people don't bother with a separate /home, since the data directories are going to be symlinked to other storage.  
Any system with over 4G of swap has problems, IMHO.

I'll be quiet now. It is your system.

We brought the horse to the pond .... doubt he will drink.

I read, if you want to use hibernantion (I don't need one, but just for the sake of the example) you need to use a bigger swap than you have RAM, around x1.25-1.5 times larger, so how does desktop manage swap over 4G but server can't when it's basically the same OS? Isn't it a problem to only x32 bit system with fat32 filesystem where the max possible size of the file is exactly 4GB?

Also can you please explain how technically separate storage and separate partitions differ from each other in terms of the file workflow in the OS? Basically, isn't mount binding the separate partition is kinda the same thing as being symlinked to other storage? The sentence looks for me like: people don't bother with separate /home, since they bother linking it to other storage. I thought, this is exactly what I do, but with logical storage instead of physical one ._.

Does it really matter what swap size is? If it fills only when ram is filled, to prevent *outofmemory*.
Does it really matter what swap size is? If I still keep (snapshots considered) ~25GiB(!) unallocated and 12GiB swap, or ~33GiB(!) unallocated and 4GIB swap while have 7+GiB of ram available
Main priority for me it's a server uptime with more than average usability experience. Is there a better solution for my problem? Thank you for your replies, guys.

Well, If it were up to me, I would choose you be better speaking than quiet. I still have questions and I really appreciate your responses and learn from them. Thanks!

P.S. Sorry in advance for all the grammar, spelling and punctuation mistakes, eng is my 3rd lang.

---

### Post by jazxhibit on 2020-05-22
i have the same issues previously. 
Idk why or how event recovery mode got the same problems.

My solutions :

fsck manually to the path the system complained about.

Exp: fsck /dev/sda1/

It will force check again, at the end it will ask u to request the missing files at lost+found.

Yes all the way. BOOTED &#9786;&#65039;

---

