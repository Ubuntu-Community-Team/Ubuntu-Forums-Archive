---
title: "Home directory &quot;moved&quot; after reinstall--need help to correct"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by jukingeo on 2010-03-04
Hello all,

I have been out of the Linux loop for a while.  Prior to the holidays I did something 'stupid' within Wine and ended up taking out my Ubuntu partition to the point where it wouldn't boot. Being that I have a triple boot system and I had plans for the holidays, I didn't want to risk a reinstall in the event that if something went wrong with Grub, it would render my whole system useless.  So I waited until now to reinstall Ubuntu.

I performed the reinstall this past weekend and for the most part I thought everything went fine, but I noticed something was different with the file system and when I attempted to load a 3.5gig program into Ubuntu yesterday, I got an error message saying that I don't have enough disk space.  I said to my self, "That is impossible as I have a 106gig partition for programs".

I have a separated system in which Ubuntu /root has an 8gig partition and the Home partition supposed to be the 106gig drive. I did this in the event I had to reinstall, I wouldn't loose my information.  Well apparently something went wrong with the install and it appears that I have two Home folders...one is on the 106gig drive and the other is in the root directory.   Making note of that explained why my program wouldn't load because the root partition is only 8gig.

So, my question is this:

Can I set Ubuntu back to the old Home directory, or do I have to reinstall once again?

As what under my avatar says, I am on Ubuntu Studio 8.04 (Hardy Heron).  I stuck with this older version because it has long term support.

I have a triple boot system with Windows XP, Puppy Linux, and Ubuntu Studio.  I have two SATA 500gig drives with the first drive being home to all the operating systems and programs.  The second drive is just for data.

Here is my fdisk -l I put the partitions usage in parenthesis:

geo@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf364

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13376   107442688+   7  HPFS/NTFS (Windows XP)
/dev/sda2           13377       21154    62476785   83  Linux (Puppy Linux)
/dev/sda3           21155       22026     7004340   83  Linux (Ubuntu Root)
/dev/sda4           22027       60801   311460187+   5  Extended (Windows Storage)
/dev/sda5           22027       34977   104028876   83  Linux (this should be Home)
/dev/sda6           34978       48044   104960646   83  Linux (Linux File Storage)
/dev/sda7           48045       60265    98165151    b  W95 FAT32 (Windows/Linux storage)
/dev/sda8           60266       60801     4305388+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f3c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14835   119162106    7  HPFS/NTFS
/dev/sdb2           14836       29636   118889032+   7  HPFS/NTFS
/dev/sdb3           29637       44471   119162137+   7  HPFS/NTFS
/dev/sdb4           44472       60801   131170725    b  W95 FAT32


Thank You,

Geo

---

### Post by oldfred on 2010-03-05
This is standard advice on how to move /home. Since you already have your home you can skip some steps. You will have to edit fstab with the correct data for your existing home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

If you have multiple installs, I prefer /data so I can have the same data in every install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by jukingeo on 2010-03-08
> **oldfred said:**
> This is standard advice on how to move /home. Since you already have your home you can skip some steps. You will have to edit fstab with the correct data for your existing home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

If you have multiple installs, I prefer /data so I can have the same data in every install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Hello,

Thank you for the information above.  I have much reading to do, but I did 'browse through' the first link and the latter half mentions 'reassigning' your home directory and that is what I am after. I am hoping it does work because as it is right now, my Home directory is too small and I can't really add any large programs (how I discovered the problem in the first place).

Geo

---

### Post by oldfred on 2010-03-08
Programs are not installed in home just your settings. Your root looks smallish. I like root to be 10-20GB and I have used about 5GB in my root with many installed programs.

---

### Post by jukingeo on 2010-03-09
> **oldfred said:**
> Programs are not installed in home just your settings. Your root looks smallish. I like root to be 10-20GB and I have used about 5GB in my root with many installed programs.

Back in the day (cue 2008 when I first started with Ubuntu), the "documented" procedure was to allot 4 to 5 gig for the root.  The recommended was to go to 7 or 8.  I went 7.  Perhaps 10 might be better for a new version, BUT for me I am still on Hardy 8.04.

I was told the programs go in the HOME file and not the root.  At any rate I did have separate root & home files when I initially installed Ubuntu.  It was just that I had a problem and the root was 'blown out' I had to reinstall Ubuntu.  Upon reinstallation I had noticed that a few things were wrong...or off.  Investigating the problem I saw that the Home directory was moved and wasn't residing on the correct partition.  So that is what I am trying to correct.

My home partition is 106gig BTW.

Geo

---

### Post by jukingeo on 2010-03-14
> **oldfred said:**
> This is standard advice on how to move /home. Since you already have your home you can skip some steps. You will have to edit fstab with the correct data for your existing home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

If you have multiple installs, I prefer /data so I can have the same data in every install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)


Hello, 

Ok, I was pretty much following the procedure on the first link, but I couldn't make any progress, so what I decided to do was just do a reinstall once again, but this time I made sure I set the reinstall to "manual", this way it wouldn't bypass the partition selection (which is what it did the first time on the reinstall).

I made note of where the original root and home directories were and assigned them accordingly.

The installation went well and now the $Home directory is on the drive/partition it should be.  Some of my programs were lost in the process though...mainly my games folder is gone and so is Open Office, but many of my other installs and my data is intact.

But before I declare this problem solved, a new issue presented itself.  After signing in on boot up, I get this error message:

"$Home/.dmrc file is being ignored.  ...File should be owned by user and have 644 permissions."

Anyone have any idea of what I should do to fix this?  Supposedly the file supposed to control the language and other personal settings, but up to now what changes I have been making ARE being saved.   At any rate, I know having an error message coming up like that upon boot up is not a good thing and I would rather correct the problem.

The thing is I can't even find this .dmrc file.   So some assistance would be appreciated.

But the good news is I am almost there.

Thanx,

Geo

---

### Post by oldfred on 2010-03-14
The error seems pretty common with editing of home and that is why I included a link in post #2 on dmrc errors.

---

### Post by jukingeo on 2010-03-15
> **oldfred said:**
> The error seems pretty common with editing of home and that is why I included a link in post #2 on dmrc errors.

Ooops!  Kinda missed that one up there.  Ok, I will check that out.

Thanx,

Geo

Edit:

Ok, that worked!  Now before I labeled this as solved, I am missing most of the programs that I had under my "Games" listing.   While pretty much most of my data is all intact, many of my programs such as Open Office and Evolution are gone too.  Is there a way I can restore those all at once or do I have to re-install those manually?

Thanx,

Geo

---

