---
title: "Ubuntu 10.10 &amp; 11.04(Alternate) failed install with RAID 0."
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by dchurch24 on 2012-01-14
Hi all,

I've been given a Dell PowerEdge 2800 and am trying to get Ubuntu installed on it. The Desktop edition failed as it couldn't see the RAID drives, so I tried 10.10 server edition. All goes well until it tries to partition the drives, then after about 10 minutes of sitting at 33% (which it jumps straight to) it tells me that the installation failed.
I read a few forum posts here, and elsewhere, and the consensus seemed to be that 10.10 Server edition was broken with regards to RAID.
I downloaded 11.04 Server (Alternate - as recommended by googling) and it's a similar story. The install goes fine until the partitioning of the drives, then the screen just goes blank.

The config of the RAID is as such:


SCSI3 (2,0,0) (sda) - 219.8 GB MegaRAID LD 0 RAID0 209G
SCSI3 (2,1,0) (sdb) - 293.1 GB MegaRAID LD 1 RAID0 279G

I'm trying to install on the first one.

Any ideas? Or should I try 11.10? Is it that I have configured the RAID incorrectly?


EDIT: After leaving it for some (considerable) time, the screen comes back on with the error:
```

Error opening /dev/sda: No such device of address

ERROR!!!

Retry or Cancel

```

---

### Post by darkod on 2012-01-14
Few points:

1. What are you trying to achieve actually? You want desktop or server installed? Just because desktop couldn't see the disks is not a reason to install server because we are talking about a completely different OS.

2. There is no such thing as 11.04 Server (alternate). There are three main images of ubuntu, the desktop, alternate and server. The server is used for server OS install and it has support for RAID and LVM.
The desktop and alternate both install the desktop OS with the difference that the alternate cd has support for RAID and LVM. The desktop cd doesn't but on the other hand it can boot into live mode.

The desktop cd might have not seen the disks because of the raid setup on them. The alternate cd should, as long as it can recognize the raid card. That is if you plan to install desktop OS.

Another option is not using the raid card, but instead to use the ubuntu software raid (if not dual booting). In that case you don't configure a raid array in bios or the raid card bios, but instead ubuntu on OS level configures a raid for you. You can do this for both the desktop and server OS.

And you are aware that RAID0 has no fault redundancy right? If you plan on running a server it's not exactly safe for your data. If one disk goes, everything goes.

---

### Post by dchurch24 on 2012-01-14
Hi, thanks for the reply.

I'm intending to use it as a Myth TV server. I intended to use RAID 0 for the OS partition(s). I'm not all that bothered about redundancy, if it dies, it dies and I'll rebuild.

I'm just getting frustrated that I can see the drives, yet no matter which version I try to install it fails at the partitioning stage of install.

Ideally, I'm trying to get a drive with the OS on and a drive for the data...although at this stage, I'd settle for simply managing to get an OS on it at all.
I've tried setting up the partitions manually, and now I get:

```

The ext4 file system creation in partition #1 of SCSI3 (2,0,0) (sda) failed.

```

Baffled. There's a lot of conflicting information on-line with regards to setting up RAID in Ubuntu. One site suggested that I configure the RAID card, then also configure Software RAID. That doesn't sound like it makes a lot of sense to me.

It just seems like such a waste of a machine at the moment.

---

### Post by dchurch24 on 2012-01-14
Reading some more around the forum, it seems that this is a commmon problem.

Is it even possible to get Ubuntu running with a RAID card? It sees the card and the drives, yet fails every single time when trying to create a file system, be it either guided, manual or use entire disk.

I've tried with 10.10 Desktop, 10.10 Server, 10.10 Alternate, 11.04 Server and 11.04 Alternate - all with the same error.

Can anyone confirm that they have got this working and that I'm not just wasting my time trying to get it up and running?

If not (and I'm starting to suspect that this is the case after 3 solid days of this), then is there a distro that WILL work with hardware RAID cards that I can use to run Mythbackend?

I'm surprised that the OS just doesn't see the RAID drives as one/two drives and install normally to be honest; it was my expectation that this would/should be the case.

Alternatively, instead of using the hardware RAID, how do I disable it and use software raid instead?

---

### Post by darkod on 2012-01-14
Not using a raid card depends on the card, but in general it should be like:
Go into the raid card setup bios (on boot), delete all raid arrays existing.
After that it should consider the disks as separate disks, at least in my logic. Shouldn't matter that the disks are connected to a raid card as long as you don't configure an array.

Also give 10.04.3 LTS a try, I see you didn't mention it in the list of versions you tried with. It's LTS release and should be more stable and compatible.

After you delete the raid arrays as above, I'm not sure if you would delete the raid meta data on the disks too, or the array deletion will do that for you. It doesn't hurt doing it yourself, but you will need to have a live cd for that, and boot into live mode (Try Ubuntu). Then in terminal simply run:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

That should get rid of the meta data and help the disks to be considered as separate disks. Don't forget deleting the arrays first in the card bios.

---

### Post by dchurch24 on 2012-01-14
Hi, thanks.

I'll give that a go - just trying something else at the moment, when that fails I'll try your method.

Thanks.

---

### Post by dchurch24 on 2012-01-14
Sadly, if I do that, Ubuntu - 10.10 (desktop/server/alternate) and 11.04 (d/s/a) AND 11.10 (d/s/a) all see no drives at all. They have been completely cleared and deleted.

The later versions 'kind of' see the drives, but just won't install on them.

It's looking like, despite recognising the PERC 4e that it just isn't compatible with it. I get a multitude of errors ranging from simply "can't install" to "drive is read-only".

I'm fairly certain that Ubuntu isn't compatible with this RAID card (despite lots of posts saying that it is).

It's looking like I have the largest, server shaped coffee cup coaster the world has ever seen.

---

### Post by darkod on 2012-01-14
One post from an older thread here, found on google, says that actually the perc 4e is fakeraid, not true hardware raid. If that is really true, using software raid is a better option.

Did you had a chance to try 10.04 with or without the raid card?

---

### Post by dchurch24 on 2012-01-14
I didn't try 10.04, simply because even if that works, it'll have to come off again. 

I have 5 Myth TV frontend clients that all talk to the server, if I downgrade to 10.04, I'll have to do all of the clients too (as the versioning between the FE and BE are very strict). I was hoping to not have to do that.

I think it's time to throw in the towel to be honest. I can't even get it to boot to a live cd any more. Christ only knows what's wrong with it.  Reading around, lot's of people seem to have not been able to get this up and running with Ubuntu. There's a few posts claiming that it will "be no trouble" and "will work out of the box", but I doubt that's been the case for anyone with one of these servers.

The odd thing is, 3 days ago it was running Windows 2003 perfectly, so it's doubtful that it's hardware.

Thanks for the help, but I think I'm going to lug this (very heavy) heap out for the dustmen.

---

### Post by darkod on 2012-01-14
Too bad.

But isn't Myth TV a separate program? I was under the impression you can install any version you want regardless what server version you are running. Maybe you will have to install the software directly, not from the repository, but it sounds doable.

I installed my Twonky from the downloads on their website on my 10.04.3 LTS. The latest version.

---

### Post by dchurch24 on 2012-01-14
It is seperate software, but I've found in the past that even compiling from source on a given distro won't allow it to talk to a server on a different distro, even though the versions are the same. They also have to have the same version of MySql running, and a few other things. 

I expect it is possible, but after spending a few days on it before, I gave up and upgraded the whole lot. It's not a bad thing to do once in a while ;-)

I may hold on and have a word with a sys admin I know (if I can get hold of him!), I may have been a bit hasty with throwing it in the bin ;-)

---

### Post by lucas1024 on 2012-01-22
I had the same experience with a RAID 0 array and 10.04. It completely dropped the drives from the aray, thereby wiping the disk. After restoring from backup, I got an SSD and I have RAID1 array as the data drive. Ubuntu install still causes the RAID array to drop.
I am trying to figure out how to get it to work.

---

