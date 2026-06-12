---
title: "Please review my partition scheme"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by charliezen on 2012-04-17
Hi, I am a total noob with Linux.

Brand new computer with 1.5 TB HDD, 6GiB Memory, Windows 7 pre-installed.

I want to double boot with Ubuntu but I do not want to use WUBI. (Nice to discover CD Emulating software though).

 
This is how the disk is showing now (I have just installed basic programs like Skype, browsers, Foxit, 7Zip, security apps, etc).

sda1----NTFS----PQSERVICE----18G----11.8G-Used----(recovery)
sda2----NTFS----SYSTEM RESERVE----100M----33.59M-Used----boot
sda3----NTFS----MyComputer----1.35T----32G-Used
unallocated----unallocated----1M---

Initially I wanted to get rid of the Recovery and System Reserve partitions, but I have such a huge disk that I guess I can live with them.

QUESTION: does the unallocated space constitutes the fourth primary partition?

So I went and tried shrinking in Windows with no success, even deleting the event cue, defrag and all that but was no use.

Then I discovered the partition managers, a bunch of them out there and settled on GPartED-Live.  Burned the ISO and all ran perfect.

Now I want to partition sda4 like this (assuming that I still have sda4 available):

sda4----Extended
----sda5----/boot----256MB----Ext2
----sda6----/(root)----10GB----Ext4 (how much here if I am taking out /usr, /var, etc.)
----sda7----swap----6GB----Ext4
----sda8----/home----30GB----Ext4
----sda9----/usr----2GB----Ext4 (just 2 users, mainly me)
----sda10----/var----3GB----Ext4
----sda11----/tmp----3GB----Ext4
----sda12----/opt----5GB----Ext4
----sda13----/svr----???----Ext4
----sda14----/shared----Rest----NTFS

from /var down (except /shared of course) I have doubts of the space needed.  I hare read a bunch of stuff and the numbers go all over the place from really low in the MB to high in the GB, so...

Thanks in advance for your advice!

Carlos

---

### Post by darkod on 2012-04-17
No, the unallocated space does not belong to a partition. On the contrary, that is the space on the disk not belonging to any partition, primary or logical (extended).

So, you can create linux partitions as logical partition during your ubuntu installation.

Why so many ubuntu partitions?

In general, for a home system you would use /, swap and /home. Add to that the shared NTFS partition and that's it.

Many separate partitions are usually for servers with specific roles, and even then that was used years ago. These days it is used less and less. So, if you are reading some tutorials, make a note how old are they also.

---

### Post by oldfred on 2012-04-17
+1 on Darko's suggestion.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I think Herman does not even have swap as he now uses a swap file.

Partitioning is very personal, and even my own optimal partition scheme is not so good a year or two later as what I am doing has changed.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by charliezen on 2012-04-17
Thanks for the advice guys... yes, I guess I was reading old tutorials and threads in forums.

So lets see how it would go:

sda1----NTFS----PQSERVICE----18G----(recovery)
sda2----NTFS----SYSTEM RESERVE----100M----boot
sda3----NTFS----MyComputer----60GB (shrinked from 1.35TB)
sda4----Extended
----sda5----/boot----256MB----Ext2
----sda6----/(root)----25GB----Ext4 (size OK?)
----sda7----swap----2GB----Ext4 (desktop, not hybernating)
----sda8----/home----30GB----Ext4
----sda9----/shared----300GB----NTFS
----sda10----/data1----150GB----Ext4
----sda11----/data2----150GB----Ext4
unallocated----unallocated----614.65GB---

What you think of that?

Q0:  Does GPartED keeps all the Windows info safe when shrinking/resizing?  or do I need to take any extra precautions?

Q1:  Is the size of root OK? That is where the core and drivers go right?

Q2: Can I leave all that space unallocated and use it later? or is it better to distribute it all now?

Q3: I read I can keep /data1 and /data2 there and then mount them or symlink them in /home? Is that correct?

Q4: Do I need to do anything with /shared? or it just stays there and both OSs will see and use it?

THanks for the help.  It is a little overwhelming with all that Linux info out there and sometimes it points to different directions.

@darkod: what does Boot Info Script does? and why use it?

Thanks again,
Carlos

---

### Post by darkod on 2012-04-17
The size of root is fine, 25GB is plenty.

During the install you can skip creating /shared, /data1 and /data2. Leave all that space unallocated. Then you can create them later and make an entry in /etc/fstab to mount them at boot.

I wouldn't recommend leaving 600+GB unallocated, if you decide to create /shared, /data1 and /data2 before the install. You will have to expand them later to use that unallocated space (or simply create new partitions), and resizing partitions always carries some risk to the data on them.

Try to figure out your requirements and create bigger data partitions from the start. That way you have no resizing later.

---

### Post by charliezen on 2012-04-17
> **darkod said:**
> 
Try to figure out your requirements and create bigger data partitions from the start. That way you have no resizing later.

But how do I know what are my requirements? 
How big to create each partition?

---

### Post by strask on 2012-04-17
> **charliezen said:**
> 
sda3----NTFS----MyComputer----60GB (shrinked from 1.35TB)
sda4----Extended
----sda5----/boot----256MB----Ext2
----sda6----/(root)----25GB----Ext4 (size OK?)
----sda7----swap----2GB----Ext4 (desktop, not hybernating)
----sda8----/home----30GB----Ext4
----sda9----/shared----300GB----NTFS
----sda10----/data1----150GB----Ext4
----sda11----/data2----150GB----Ext4
unallocated----unallocated----614.65GB---

What you think of that?
Personally, I think it's far too many partitions. You just need a root (/) partition and optionally a swap partition (you can do swap with a file in the filesystem, so you don't strictly need a separate partition for it) and that's it. Everything else can be part of the root partition.

Years ago there were good reasons for having lots of separate partitions; but those reasons no longer exist. Simpler is better.

> Q0:  Does GPartED keeps all the Windows info safe when shrinking/resizing?  or do I need to take any extra precautions?
ALWAYS back up your data right before doing something drastic like shrinking a partition.

---

### Post by darkod on 2012-04-18
> **charliezen said:**
> But how do I know what are my requirements? 
How big to create each partition?

According to the data you plan to store.

If you can not make the decision now, you can use LVM. For LVM you WILL NEED to have a separate /boot partition outside the LVM, otherwise it's not required. also, you will have to leave out the shared NTFS partition outside the LVM because windows can't read the LVM. It will be only for your ubuntu partitions.

In that case, during the install, you would create:
- shared NTFS partition
- /boot ext4 partition
- all the rest of the disk as one LVM type partition

After that you simply create Logical Volumes in the LVM which you can resize dynamically without losing the data on it. So you can start with smaller partitions, and grow them as you need.

You can google around for more details how LVM works, to see if it matches your requirements.
Also, for installing with LVM you will have to use the Alternate Install CD, not the standard cd.

---

### Post by MonkeyPaw on 2012-04-18
> **darkod said:**
> No, the unallocated space does not belong to a partition. On the contrary, that is the space on the disk not belonging to any partition, primary or logical (extended).

So, you can create linux partitions as logical partition during your ubuntu installation.

Why so many ubuntu partitions?

In general, for a home system you would use /, swap and /home. Add to that the shared NTFS partition and that's it.

Many separate partitions are usually for servers with specific roles, and even then that was used years ago. These days it is used less and less. So, if you are reading some tutorials, make a note how old are they also.

Yes to this. On my 100GB HDD, I have a 10GB root, 89GB home, and 1GB swap. With 8GB of RAM, I've yet to hit the swap file. :p

I'm probably going to wish my root partition was bigger, but I'm thinking of going to a 500GB HDD before too long. I recently switched from Windows and I've left that HDD untouched for the time being. So far so good. :)

---

### Post by al111 on 2012-04-18
> **charliezen said:**
> 

sda1----NTFS----PQSERVICE----18G----11.8G-Used----(recovery)
sda2----NTFS----SYSTEM RESERVE----100M----33.59M-Used----boot
sda3----NTFS----MyComputer----1.35T----32G-Used
unallocated----unallocated----1M---

Initially I wanted to get rid of the Recovery and System Reserve partitions...Carlos

If you delete the 100M SYSTEM RESERVE partition, Windows 7 won't boot-

For some reason, it's created when Windows 7 is installed to an unallocated space-

What I do to avoid creating the 100M Windows 7 boot partition, is to create an NTFS partition first, then boot with the Windows 7 Install Disk and install to the new NTFS partition I just made-

For some reason, that 100M boot partition won't be there....

---

### Post by MonkeyPaw on 2012-04-18
> **al111 said:**
> If you delete the 100M SYSTEM RESERVE partition, Windows 7 won't boot-

For some reason, it's created when Windows 7 is installed to an unallocated space-

What I do to avoid creating the 100M Windows 7 boot partition, is to create an NTFS partition first, then boot with the Windows 7 Install Disk and install to the new NTFS partition I just made-

For some reason, that 100M boot partition won't be there....

The system reserve partition is sort of like an MS recovery partition. I believe it lets you load a set of repair tools in case you can't boot into 7. I think it is similar to the bootable recovery CD that you can make after install.

---

### Post by darkod on 2012-04-19
> **MonkeyPaw said:**
> The system reserve partition is sort of like an MS recovery partition. I believe it lets you load a set of repair tools in case you can't boot into 7. I think it is similar to the bootable recovery CD that you can make after install.

I don't think so. Win7 has 3 boot files, the same as earlier versions. But what MS started to do with win7, is creating the small 100MB or 200MB partition with two of the boot files, and only the third file is on the C: partition. This happens only if you create the C: partition with the installer.
If you have an existing partition to use, it does not create the small one and you save one primary partition.

I have never needed to use it as recovery, but I think it's worthless for that. It's simply a separate partition with /bootmgr and /Boot/BCD on it.

---

### Post by oldfred on 2012-04-19
I think part was just to have repair separate, but the main reason was so you can encrypt main partition and learn that you have to have separate partition as efi will. But I notice with efi, they still create a /boot partition.

I really do think they all are excuses and they just wanted to use all 4 primary partitions. Microsoft does not want users modifying system, nor does the computer vendor as they are not set up to help except by a script on their own system, and do not want odd issues or questions.

If they did not want to use all 4 primary partitions they would put some into logical.

---

### Post by rewyllys on 2012-04-19
> **charliezen said:**
> . . . . Q0:  Does GPartED keeps all the Windows info safe when shrinking/resizing?  or do I need to take any extra precautions?. . . 
A few installations ago I learned the hard way that it is better to use a Windows partition manager to shrink the partition that contains the Windows system files themselves.  That is to say, I experienced having GParted fail to shrink the main Windows partition safely.  

OTOH, I've known GParted to handle correctly partitions with just Windows-file-system (i.e., NTFS) data files.

---

### Post by al111 on 2012-04-19
The windows partition manager does do a good job...

---

### Post by jerome1232 on 2012-04-19
> **darkod said:**
> If you can not make the decision now, you can use LVM. For LVM you WILL NEED to have a separate /boot partition outside the LVM, otherwise it's not required.

Actually these days grub can boot a lvm volume, no sweat.

As others have suggested, leave it simple, at most a / and /home, even that is debatable, I go with a 40 GB / (plenty of room for installing lots of applications) and link my relevant folders under ~/ to their counterparts on my Windows partition which is mounted at /windows, that way personal data is seamlessly shared between the OS's.

---

### Post by charliezen on 2012-04-21
Thanks guys!  lots to think about and digest!

LVM sounds interesting, I will read about it...

@jerome1232:  how do you "link my relevant folders under ~/ to their counterparts on my Windows partition " ?

Thanks again!

---

### Post by jerome1232 on 2012-04-21
I use symnlinks, basically I delete my ~/Documents, ~/Videos, ~/Music, and ~/Downloads. Then you can middle click drag the folder you want those files to actually go into into your home, clicking make link when you let go. Then rename the links to "Documents", "Videos", etc... 

I mount my Windows partition at /windows, an option that was there using the installer *don't opt to format the partition*, so I just used it. As an example my ~/Documents is a actually a link to /windows/Users/Jeremy/Documents etc...

---

### Post by charliezen on 2012-04-21
Thanks, I will read about this too...
is ~/ the root?

I assume "middle click" is clicking with the middle button of a mouse!
How do you middle click with a 2 switch mouse?

---

### Post by jerome1232 on 2012-04-21
~/ means your users home (in my case ~/ = /home/jeremy)

I believe clicking left and right buttons simultaneously emulates a middle click.


> **charliezen said:**
> 

LVM sounds interesting, I will read about it...



I love LVM, it does add complication to things but I wanted to give you a little view of why it's nice, especially if you change your partitions up a lot. On my little home server I have quite a few volumes, it uses lvm and I ran out of space on /var. Using LVM I can just make it bigger without ever shutting down the machine. I actually just happened to be doing this atm and thought about this thread.

```

jeremy@voiceserv:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/voiceserv-root
                      9.2G  762M  8.0G   9% /
udev                   52M  4.0K   52M   1% /dev
tmpfs                  24M  740K   23M   4% /run
none                  5.0M     0  5.0M   0% /run/lock
none                   59M     0   59M   0% /run/shm
/dev/mapper/voiceserv-boot
                      267M  109M  144M  43% /boot
/dev/mapper/voiceserv-usr
                      4.6G  837M  3.6G  19% /usr
/dev/mapper/voiceserv-home
                      2.8G  802M  1.9G  30% /home
/dev/mapper/voiceserv-share
                       34G  176M   33G   1% /share
/dev/mapper/voiceserv-var
                      1.9G  1.4G  393M  78% /var
jeremy@voiceserv:~$ sudo -i
[sudo] password for jeremy:
root@voiceserv:~# man lvextend
root@voiceserv:~# lvextend voiceserv/var -L +5G
  Extending logical volume var to 6.86 GiB
  Logical volume var successfully resized
root@voiceserv:~# resize2fs /dev/voiceserv/var
resize2fs 1.41.14 (22-Dec-2010)
Filesystem at /dev/voiceserv/var is mounted on /var; on-line resizing required
old desc_blocks = 1, new_desc_blocks = 1
Performing an on-line resize of /dev/voiceserv/var to 1798144 (4k) blocks.
The filesystem on /dev/voiceserv/var is now 1798144 blocks long.
root@voiceserv:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/voiceserv-root
                      9.2G  762M  8.0G   9% /
udev                   52M  4.0K   52M   1% /dev
tmpfs                  24M  748K   23M   4% /run
none                  5.0M     0  5.0M   0% /run/lock
none                   59M     0   59M   0% /run/shm
/dev/mapper/voiceserv-boot
                      267M  109M  144M  43% /boot
/dev/mapper/voiceserv-usr
                      4.6G  854M  3.6G  20% /usr
/dev/mapper/voiceserv-home
                      2.8G  802M  1.9G  30% /home
/dev/mapper/voiceserv-share
                       34G  176M   33G   1% /share
/dev/mapper/voiceserv-var
                      6.8G  1.4G  5.1G  22% /var

```

---

### Post by charliezen on 2012-04-21
Wow, thanks jerome...
Does it grab the extra space from the unallocated space you have available?

Now I am really going to use it... and without signing off!

---

### Post by jerome1232 on 2012-04-21
> **charliezen said:**
> Wow, thanks jerome...
Does it grab the extra space from the unallocated space you have available?

Now I am really going to use it... and without signing off!

Yes, I left a lot of unallocated space for that reason, I can pretty much grow partitions at will if I need to do so, shrinking would require unmounting the volume, which is why I started small and increase as needed.

I still want to emphasize though, lvm does complicate things, for instance gparted won't see lvm volumes, you have to use specific tools for lvm, and what I have seen of the gui's avaible, they aren't full featured so you may end up on the command line when you want to manipulate lvm volumes.

---

### Post by charliezen on 2012-04-21
Jerome, thanks, I really appreciate your help!

Time to go read a bunch!

---

### Post by charliezen on 2012-04-21
Why do I need the alternate CD to install with LVM?

So with LVM will look something like this:

sda1----NTFS----PQSERVICE----18G----(recovery)
sda2----NTFS----SYSTEM RESERVE----100M----boot
sda3----NTFS----MyComputer----60GB (shrinked from 1.35TB)
sda4----Extended
----sda5----/shared----400GB----NTFS
----sda6----/boot----256MB----Ext2
----LVM----LVM----
--------lv-root----/(root)----60GB----Ext4 (size OK?)
--------lv-swap----swap----6GB----Ext4 (desktop, not hybernating)
--------lv-home----/home----60GB----Ext4
----unallocated----unallocated----750GB---

I have read that /boot has to be in a primary partition, but I do not have any available.
So, can I put it inside Extended? or am I going to have a lot of problems like this?

TIA

---

### Post by darkod on 2012-04-22
I think there should be no problem if it's a logical partition. Windows does have limitations and needs to work from primary partitions but I think ubuntu should be fine from logical. Try it.

---

### Post by jerome1232 on 2012-04-22
Yeesh, you are reading old guides! You don't even need a separate /boot, it can reside in a logical, it can even reside in a lvm volume (note on that server I showed earlier I had a separate /boot, but it resided on a LVM volume)

If you have that small-system-boot partition Win7 likes to make, you can even put the main windows partition on a logical.

---

### Post by charliezen on 2012-04-22
Thanks guys, I will give it a try!  jerome:   Could you direct me to modern linux guides?  Everything I search in google seems rather old, even the ubuntu info seems to be outdated even though it is released as the latest!

---

