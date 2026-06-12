---
title: "Impossible to mount large windows raid?"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by batjew_beyond on 2012-04-25
In a new build of mine, I went a little overboard, and installed 3 3tb drives.  Going to just pay for backup services so I'm just going Raid 0 for ease of access, and read/write speeds, but it would be nice to actually have all my media available to me in both Ubuntu, or another flavor of linux, for all my everyday stuff, and Windows 7 for gaming, etc.  
I already know there's no way in Hell, Windows 7 is going to be able to read a raid setup in Linux, so I'm trying to set up the raid in Windows and mount it.  
I've tried fake raid, Windows striped raid, kpartx, dmraid, mdadm.  (sorry if any of those are nonsense, I've been at this for about 6 hours now), Nothing works.  No matter what I do, The three drives are just seen as sdb, sdc, sdd.  Nothing in the /dev/mapper.  
Been doing all this from live CDs and thumbdrives.  Tried Xubuntu, Mint, and plain old Ubuntu, although I doubt there'd be any differences from using xfce instead of Unity.  
Anyone ever had any luck with something like this?
Additional info:
Asus Sabertooth 990fx, AMD Fx8150, 3x3TB drives, attempted with both the AMD SB950 fakeraid, and with all drives in AHCI and striped by windows.  Reason they're starting from sdb is that the OS drive is a separate SSD.

---

### Post by darkod on 2012-04-25
> **batjew_beyond said:**
> 
Asus Sabertooth 990fx, AMD Fx8150, 3x3TB drives, attempted with both the AMD SB950 fakeraid, and with all drives in AHCI and striped by windows.  Reason they're starting from sdb is that the OS drive is a separate SSD.

If I am not mistaken this means no raid, and striped in windows might mean some sort of windows software raid. That is why linux wouldn't read it, the same as if it was the other way around.

For fakeraid you need the option in bios to say RAID, not AHCI. But make sure to read the board manual and to have the correct disks in the raid ports. Usually not all ports are raid, maybe only two or four depending on the board.

If you have the SSD in one of them for example, it will think you want to do raid with it.

Try setting up the raid like that, install win7, and then the ubuntu Alternate Install CD should have no problem installing on that fakeraid.
The liveCD can be used too but installing grub usually fails so you will have to be ready to add it afterwards. Don't be surprised if grub doesn't install if you insist on using the liveCD.

---

### Post by batjew_beyond on 2012-04-25
You are mistaken, but probably only because that was a 3AM ramble for me.  
I have tried both windows striping, which gives a dynamic disk, and is said to be mountable with mdadm in several posts here, as well as the motherboard raid controller.  Both times the raid disk has been completely recognized by Windows 7.  
I'll clear things up a little more.  The SSD is in "Raid Ready" mode, which I honestly have no clue as to what that is supposed to be, it was just needed to actually install windows on it.  Maybe.  That was another fiasco.  Anyway, the SSD is partitioned with 2 10 gig ext4 partitions for Linux installs, and the rest is NTFS for the windows OS partition.  
dmraid -ay or whatever the command is, does indeed mount the two Ext4 partitions, but, they're already visible and mounted.  

Have not tried the alternate install CD.  Might give that a shot, but I was trying to actually get these recognized by a live disc before I go any further.  The issue seems to be that dmraid, which is used for fakeraids, will not function on gpt partition tables.  That kind of makes it useless to me, because even the individual drives would need to be gpt to have the full size available.

This guy seems the most like my problem, and seems to be based on the Windows dynamic disk striping, but all attempts at getting the partition recognized as fakeraid, or as a Windows 7 striped disk fail.
[http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)

---

### Post by darkod on 2012-04-25
Ubuntu will not play nice with dynamic disks.

I would stick with making the fakeraid work. If the SSD is in raid mode it seems it's connected to the RAID port. That would explain dmraid -ay activating it.

Since you don't want the SSD into a raid if I understand it correctly, just connect it to another port. It should be able to work in AHCI mode. On top of that, if the board has only two raid ports and the SSD is in one of them, I can't figure out how you could try whether the fakeraid will work or not. You would need two of the 3TB disks connected to the two raid ports, and to configure an array in the raid bios.

So far I haven't seen anything against fakeraid + gpt but I haven't worked with huge disks either. You might have a point. I would still pay more attention making that work.

On a side note, if the SSD has raid meta data on it now after being activated with dmraid earlier, you will need to remove that meta data so that ubuntu will see it as a single device. You can do that with:
sudo dmraid -E -r /dev/sda

---

### Post by batjew_beyond on 2012-04-25
Think you may be looking at the wrong specs on the board.  
It has 6 SATA 6.0GBPS connections on the AMD SB950 raid controller.  
SATA1 is the SSD, SATA2-4 are the RAID drives.  
To get windows to install had to set the SSD as a "RAID READY" logical disk, and then the other 3 drives are in as LD-2, a 3 disk 64k striped drive.

I might see if I can still get windows to boot if I change the SSD from RAID READY to something else, and then perhaps it will be ignored by dmraid.

Believe I already removed the metadata, but I'll double check next I have a chance to fiddle with this.

---

### Post by darkod on 2012-04-25
I can't search for that board manual right now, but it has to have an option or sata ports that are outside the raid. It's impossible that all 6 ports have the same setting, either raid or ahci.
You either set it port by port, in which case you need to try with SATA1 in ahci.
Or it says in the manual which ports are excluded from the raid when you use the raid sata mode. You need the SSD in one of these none-raid ports.

It might not be a good comparison, but my 4yrs old board has 6 SATA2 ports, and if you set it to raid that includes only ports 5 and 6. The first 4 remain in the general sata mode which can be ahci or ide.

There must be something like that.

The reason why windows doesn't install on the SSD if it's not in RAID READY mode might be if it's connected to a raid port, it doesn't accept anything but RAID options.

I am only speaking in general terms, and I might be wrong, but for me, it's clear. RAID options (or ports) only for disks that you want to use in the array (which excludes the SSD). Plain and simple.

---

### Post by batjew_beyond on 2012-04-25
From my own recollection, the drives are set to AHCI or IDE independantly, but once raid mode is selected, all drives are in raid mode.  
Manual agrees with me, but I'll check for sure when I get a chance.
From manual: "Due to chipset limitation, when set any of SATA ports to RAID mode, all SATA ports run at RAID mode together."

Since an ASRock manual I found while googling had a bit more info, I'll say that Raid Ready allows the individual disks to be set to AHCI.  Their definition:
RAID Ready
RAID Ready arranges individual physical drives the same as if they were attached to the PC&#8217;s motherboard controller.
The advantage is that the AMD SB700 Controller can accommodate up to four physical drives, more than most PC
motherboards. As a single physical drive, RAID Ready does not offer the performance or security advantages of other
RAID logical drives. However, you can create a backup drive by: Inserting an unformatted physical drive or
designating an installed physical drive. In RAIDXpert, you create, manage, and delete a RAID Ready the same as a
logical drive. A RAID Ready logical drive has only one physical drive. You can designate from one to four of your
physical drives as RAID Ready.

---

### Post by darkod on 2012-04-25
In that case, it sounds good.

With the 3 disks set in fakeraid raid0 and activated, ubuntu live mode should see a /dev/mapper/.... device. And the alternate installer should work. Or the standard installer with possibly adding grub2 later separately.

It might be a driver issue not recognizing the array.

The 12.04 LTS is few days away from being released, but you can try the Alpha burned on a cd if it sees the array in live mode. I wouldn't install it though, not until it is released which should be tomorrow.

---

### Post by batjew_beyond on 2012-04-27
NOPE.
So, as I have it now, SSD is just a disk, the big 3 are Raid 0, showing in AMD Raid Expert, formatted NTFS with GPT rather than MBR.
Pop in Xubuntu 12.04 alternate amd64, goes through, get to partitioning.  Nothin' there.  Well, the disks are there, but it lists SDB as having no partition scheme, SDC and SDD as free space.
the SSD is read fine, it says it installs, I reboot hoping to try and just configure it.  No OS found.  Burning the AMD x64 desktop to a thumb drive now to see what I can do there, but so far, looks like I might be stuck with just windows for a few months.

---

