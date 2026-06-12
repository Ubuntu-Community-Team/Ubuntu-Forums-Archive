---
title: "Win XP &amp; Ubuntu"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by dannyb37 on 2006-08-09
Hi,

Another question, that I can't seem to find the answer to...

Is there a way that I can have winXP & Ubuntu linux running on a partitioned hard drive and be able to accsess each partition in XP an ubuntu?

Out of preference I would rather not use windows atall but I am somewhat forced to for things like my iAudio U2's firmware! :mad: 
And 1 or 2 games! :p that I'm not too bothered about!

Just last time I had a duel booted system I couldent accses the other hard drive partition, windows cant read the linux hard drive format and linux cant read the ntfs. Is there some other way?

How much can I get away with having on my winXP partition, I want it useing minimal space! ;) 

Thanks,

~ Danny

---

### Post by Lord Illidan on 2006-08-09
I have my XP partition on FAT 32. That is fully readable and writeable by Linux. Linux can also read and write to NTFS now.

Regarding Ext3 partitions, XP can read them with this tool [http://www.fs-driver.org/](http://www.fs-driver.org/)

There's another tool for ReiserFS but not as good as of ext3:
[http://yareg.akucom.de/](http://yareg.akucom.de/)

If you want to install the whole thing from scratch, make sure you give XP at least 10-20 gigs of space depending how you are going to use it.
I have XP on 20 gigs of Fat 32, as I store my music on my Linux partitions.

---

### Post by hopstah on 2006-08-09
you can set linux up to read from your ntfs partition, but writing to it is still buggy, from what i understand.

getting your winxp to be able to read from your ext2 or ext3 drive will require a program called explore2fs.  windows has poor support for non-microsoft file systems, so you will need this third party program.

---

### Post by anilc on 2006-08-09
First, for getting linux partition in winXP, you can use the tool
explore2fs.
To see win partition in linux, enter the following command in root shell.
mount /de/hda1 /mnt
this will mount the partition hda1(most probably c:\ drive in win)
in /mnt directory. Similarly you can mount other drives by changing hda1 to hda2,hda3....

---

### Post by dannyb37 on 2006-08-09
Thanks for the link! ;)
How do I get linux to read a ntfs partition? or is it default?

And is "linxDrive:\" the "home\" part of a drive on linux? same folders and such?
E.g. L:\usr\danny\ would be my home directory?

& If I ran out of space on my windows partition would I be able to install to the linux partition? or re-size the partition table?

Thanks,

(1.5 gigabyte (GB) of available hard disk space.* is required for XP so light use - about 1 or 2 games, SonicStage, firmware updater for my iAudio U2 and anti-virus, firewall and such.. 
I would say 10-15GB, lol - but as I plan to get a 120GB hard drive so I guess I'll give linux a nice rounded 100GB! lol)

Your help is very much appreciated! :D

Edit: Saw the post above me! lol, I was already typeing this! :P
So do I have to mount it each time I want to accsess it or can I get it automaticaly there? ](*,)

---

### Post by randell6564 on 2006-08-09
> **dannyb37 said:**
> Hi,

Another question, that I can't seem to find the answer to...

Is there a way that I can have winXP & Ubuntu linux running on a partitioned hard drive and be able to accsess each partition in XP an ubuntu?

Out of preference I would rather not use windows atall but I am somewhat forced to for things like my iAudio U2's firmware! :mad: 
And 1 or 2 games! :p that I'm not too bothered about!

Just last time I had a duel booted system I couldent accses the other hard drive partition, windows cant read the linux hard drive format and linux cant read the ntfs. Is there some other way?

How much can I get away with having on my winXP partition, I want it useing minimal space! ;) 

Thanks,

~ Danny

I dont think that you will be able to access ext3 from windows, but I know that you can access your windows from ubuntu.  You would just have to add your windows partitions to your /etc/fstab

Linux CAN read ntfs ANd fat32.  You cannot write to ntfs from Linux but you can to fat32.  There is supposedly applications out there that enable you to write to ntfs, but it is dangerous and I do not recommend it!

---

### Post by dannyb37 on 2006-08-09
> **randell6564 said:**
> You would just have to add your windows partitions to your /etc/fstab

Whats this mean to a newbi? :) lol thanks

---

### Post by randell6564 on 2006-08-09
> **dannyb37 said:**
> Whats this mean to a newbi? :) lol thanks

OOPS! Sorry!  Let me give you a link that will show you just how this is done.  [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

That one is for NTFS.

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

That one is for Fat32.

Have Fun!

---

### Post by nightfire117 on 2006-08-09
I'm probably not one to voice his opinion, seeing as I am a Linux noob, but I hope you're aware that writing to NTFS is still... unstable under Linux. Of course, I've tried it, but... meh.

Randell6564, you're awesome, thanks alot for those links I think I bookmarked those pages but lost them hehe. 

Personally, I have a small drive for Ubuntu, hooked up as my primary master, and my primary slave is my Windows XP drive. That way, I can use Grub and select which OS I want, which... is usually Windows anyway :( because I've been having X issues with Ubuntu, otherwise I'll probably be on my way to making Linux my primary OS. Because of WINE and other such projects!!! :) Alsoooo I'm gonna tackle triple-boot - or maybe quad-boot (if you throw Vista in there) - of WinXP, Mac OSX, Ubuntu, and quad if you have 

I have Ubuntu on 10 GB, which is all I'd sacrifice for it, seeing as it's not my primary OS (yet!!!). 20 GB would be okay, if you'd like, but I'd not go over 15. I belive that Debian itself fits on... about... 1 Gb or so...? So... maybe Ubuntu is about 1.3 GB, I'd go with that. 

~Nightfire

---

### Post by randell6564 on 2006-08-09
> **nightfire117 said:**
> 
I have Ubuntu on 10 GB, which is all I'd sacrifice for it, seeing as it's not my primary OS (yet!!!). 20 GB would be okay, if you'd like, but I'd not go over 15. I belive that Debian itself fits on... about... 1 Gb or so...? So... maybe Ubuntu is about 1.3 GB, I'd go with that. 

~Nightfire

Trust me , My Friend, stick with ubuntu/Linux and you will soon be dumping your Windoze!

Just takes time to get the feel of things. I threw my XP cd in the trash just last week! Thanks to all the folks here at ubuntu forums, I have been able to assist you!  Glad to help! Now, gimme' some beans! 'Burp'

---

### Post by dannyb37 on 2006-08-10
lol

With the mounting of the ntfs drive, do I have to do it each time I want to accsess it or just the once?

---

### Post by randell6564 on 2006-08-10
> **dannyb37 said:**
> lol

With the mounting of the ntfs drive, do I have to do it each time I want to accsess it or just the once?


Once it is in your /etc/fstab, you should be good to go!

---

### Post by Lean 946 on 2007-10-21
Try This:

[Windows Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot")

Hope this help you :) .
Lean.

---

### Post by randell6564 on 2007-10-21
[COLOR="Red"][SIZE="3"]Correction to previous posts:
[COLOR="Blue"]I DID throw my WinXP CD into the trash, but have since reinstalled for dual-boot setup since there are still things that I need from Windoze.[/COLOR][/SIZE][/COLOR]
[COLOR="SeaGreen"][SIZE="3"]That doesn't mean I like it though..HMMF! lol![/SIZE][/COLOR]

---

