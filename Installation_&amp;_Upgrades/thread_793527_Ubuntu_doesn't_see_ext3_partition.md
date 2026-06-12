---
title: "Ubuntu doesn't see ext3 partition?"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by speedgator on 2008-05-13
After much heartache I decided to give in and just install Ubuntu using Wubi within my XP NTFS partition. I tried various times to boot from the CD and install onto it's own partition but it just didn't work or perhaps I was impatient.
Laptop has 74GB or so of usable hdd. Ubuntu is 10GB, total XP NTFS partition (including Ubuntu within) is 44GB. I read that with 2.6 kernel I wouldn't need a separate swap partition, swapfile would do just fine. The rest of my hdd I made ext3, coming to around 30GB or so. I did this thinking Ubuntu would read it natively and I could get XP to read it with the wonderful tool ext2fsd. This way I could access all my files from either OS.
Lo and behold, XP reads it just fine, Ubuntu doesn't. I made the partition using PartedMagic which uses GParted from what I can tell, nifty toolset booting from a usb thumbdrive. I also used this to resize my original XP partition with no ill effects.

System specs: Dell D620 3GB RAM, 75GB hdd

I'd appreciate help getting this partition read in Ubuntu. I tried some suggestions from this article [http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")(yes I google, yes I search, yes I read, yes I'm a Linux n00b, my apologies in advance folks).
I'd also appreciate if someone could tell me how to store my /home on that partition since I read doing so would preserve all my settings even when future upgrades come to Ubuntu.
While I'm at it I'd appreciate help with the wireless too lol I tried entering my SSID and WEP key to no avail.

Sorry again for the n00b questions and long post, thanks in advance to anyone with help and/or suggestions.

---

### Post by Partyboi2 on 2008-05-14
If you have already installed ubuntu you can move your /home folder to its own partition by following this guide. [COLOR=Blue][I][B][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[/B][/I][COLOR=Black]or you can create a /home partition when you install ubuntu by choosing to manual partition.
With your partition ext3 problem, maybe try another partitioning program and see what happens. You could boot a ubuntu live cd and use 'partiton editor' (System>Admin>Partition editor) to create the ext3 partition.
[/COLOR][/COLOR]

---

### Post by speedgator on 2008-05-14
speed@speed-laptop:~$ sudo fdisk -l
[sudo] password for speed: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd331d331

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738        9729    32065740   83  Linux

Disk /dev/sdb: 521 MB, 521142272 bytes
2 heads, 63 sectors/track, 8078 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0007bcd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8079      508912    6  FAT16
speed@speed-laptop:~$ 


********************
If I run disk usage analyzer:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I can access windows partition then and even write to it, but I don't see it mounted anywhere.

I see the ext3 drive listed but error:
Unable to mount the volume.
Details:
mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error In some cases useful info is found in syslog -try dmesg | tail or so

In computer file browser I don't see my windows partition, but I do see the ext3 drive, shows up as 32.8 GB Media, obviously can't access it though.

---

### Post by speedgator on 2008-05-14
Wiped out the ext3 partition in Ubuntu with GParted and recreated it, it mounts now but I can't write to it? Arg, frustration setting in...

speed@speed-laptop:~$ sudo fdisk -l
[sudo] password for speed: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd331d331

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738        9729    32065740   83  Linux

Disk /dev/sdb: 521 MB, 521142272 bytes
2 heads, 63 sectors/track, 8078 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0007bcd5

---

### Post by speedgator on 2008-05-15
Well, sadly, I just went with a NTFS partition to solve my issue. Disappointing that I couldn't use ext3 in Ubuntu :-/ 
Amazing that XP read it so well. Felt like even more of a slap in the face to me.

Next I'll try tackling moving my /home to that partition...

---

### Post by Partyboi2 on 2008-05-15
I don't think you will able to move your  /home to ntfs it will need to be on a ext file system.
Why not go back to a ext3 partition then if you are not able to write to the partition try changing the permissions to the partition
```
sudo chmod 777 -R /media/abc
``` changing abc to correct partition

---

### Post by speedgator on 2008-05-15
I'll try moving my /home to the ntfs shared partition, if it fails then I'll once again keep trying to make it ext3. 
Thank you for all your help!

---

### Post by speedgator on 2008-05-15
I just had a thought, why wouldn't /home be able to exist on ntfs? It currently resides on ntfs, my install is ubuntu within XP...

---

### Post by speedgator on 2008-05-15
Error logging in:

User's $HOME/.dmrc file is being ignored. This prevents the default
session and language from being saved. File should be owned by user
and have 644 permissions. User's $HOME directory must be owned by user
and not writable by other users.

Let me guess ;) this is due to it being a ntfs partition? No way of just changing the permissions?

---

### Post by speedgator on 2008-05-16
Somehow the ext3 partition was recognized. Great, I thought. I moved my /home to it just fine, no issues. Reboot and no /home. System is pooched. Rebuild. sigh
I'm giving up for now. Doing the wubi ubuntu within xp and then the "shared" partition with ntfs since ubuntu reads it better than ext3 (huh!?) and leaving my /home where it is :(
Makes me kinda sick that xp read everything right all the time and ubuntu didn't. Stings when wife asks why go through all that time and trouble for something that doesn't seem to be working any better. arg

---

