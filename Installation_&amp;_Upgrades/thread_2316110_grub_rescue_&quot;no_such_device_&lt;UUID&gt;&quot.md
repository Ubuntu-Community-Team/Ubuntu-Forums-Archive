---
title: "grub rescue &quot;no such device &lt;UUID&gt;&quot; when selecting grub Windows 10 entry"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by LloydM999 on 2016-03-05
When I try to boot Windows 10 from grub, I get a grub rescue prompt and:

[FONT=lucida console]error: no such device <UUID> 
setting partition type to 0x7
press any key to continue[/FONT]

Then a new screen with:
[FONT=lucida console]An operating system can't be found. Please remove any disk that doesn't contain an operating system.[/FONT]

I am running a dual-boot system (Legacy BIOS, no Secure Boot) with new installs of Win 10 on an SSD (sda) and Ubuntu + NTFS data partitions on an HDD (sdb). I have a /boot partition on the HDD. I can boot Windows fine with BIOS set to boot the SSD. With BIOS set to boot the HDD I get the grub menu with Ubuntu entries (which work fine) and 2 Windows loader entries /sda1 and /sda2 (which both result in the error).

This is *after* I ran boot-repair in Ubuntu with the "recommended" option and installed grub to sdb. Before that grub didn't show the /sda2 loader. I don't want to try any more "fixes" at this point without some advice, since I'm not sure what the failed boot-repair did.

My current bootinfo output is at [http://paste.ubuntu.com/15290020](http://paste.ubuntu.com/15290020). The UUIDs I get in the grub rescue error messages match the blkid output for the selected loader entry.
[FONT=courier new]
Device           UUID                                   TYPE       LABEL
/dev/sda1        94109C4D109C3866                       ntfs       System Reserved
/dev/sda2        CE4E9DD04E9DB227                       ntfs

[FONT=verdana]The sda boot flag is on sda1, the Windows "System Reserved" partition.[/FONT]
/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   976,771,071   975,745,024   7 NTFS / exFAT / HPFS

[FONT=arial][FONT=verdana][FONT=courier new][FONT=arial][FONT=verdana]The sdb boot flag is on my / partition (sdb6) not my /boot partition (sdb7).
[/FONT][/FONT][/FONT][/FONT][/FONT]/dev/sdb6    *  2,929,704,960 2,968,764,415    39,059,456  83 Linux
/dev/sdb7       2,968,766,464 2,969,741,311       974,848  83 Linux[/FONT]

Thanks for any help...
 -LloydM999

---

### Post by yancek on 2016-03-05
> [FONT=courier new][FONT=arial][FONT=verdana]Also, the boot flag is on my / partition (sdb6) not my /boot partition (sdb7).[/FONT][/FONT][/FONT]

That is not necessary for any Linux system I am aware of but is necessary for windows as is having boot files on a primary partition (windows).  You could try changing the boot flag to sda2 where your windows boot files are.

---

### Post by oldfred on 2016-03-05
Boot flag on sda, should be on sda1, but it looks like Boot-Repair copied boot files into sda2 so that should also work. Many users did not know system reserved is essential for booting Windows and delete it and could not boot nor repair system. So Boot-Repair copies boot files into main Windows drive. But system reserve mayu also let you boot into repair console with f8.

From BIOS or one time boot key like f10 or f12 can you directly boot Windows?
Grub only boots working Windows. And Windows cannot need chkdsk nor be hibernated. And Windows 10 fast start up setting is really always on hibernation. Windows also will turn that back on with some updates.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by LloydM999 on 2016-03-05
oldfred -

 A "select boot device during POST" feature isn't mentioned in my BIOS [manual]("http://global.shuttle.com/main/productsDownload?productId=1707"), and button-mashing F-keys during POST doesn't do anything. As I mentioned though it boots fine into Windows if I change the bot device to SSD in the main BIOS menu.

I do not have Fast boot enabled. The SSD is set to never use hibernation.
BIOS has Fast boot disabled and SATA mode is AHCI. The SSD is set to never use hibernation.
PC is a Shuttle SH87R6 (AMI BIOS 2.15.1236 SH87R00 2.03).

 -LloydM999

---

### Post by oldfred on 2016-03-05
Is drive set to AHCI mode, not IDE nor RAID?

The old IDE mode may restrict BIOS from looking for boot files beyond 137GB on drive.

---

### Post by yancek on 2016-03-05
If you post the manufacturer name someone might know what the key to enter setup is.

---

### Post by LloydM999 on 2016-03-05
Shuttle support told me that for this AMI BIOS, F7 is the key for the one-time boot-select menu. This is not documented in the BIOS guide or the BIOS display. There's a very short time that the BIOS will detect it, so you have to keep mashing it and hope for the menu before POST completes.

So my current workaround is to set the BIOS to default boot into SSD but also have the HDD in the HD option list. Then the BIOS normally boots into SSD for Windows; or I can hit F7, select HDD, then select the Ubuntu grub menu entry.

I still haven't solved the original problem. I paid my donation to boot-repair and I'll post the solution if they fix it...

 -LloydM999

---

### Post by oldfred on 2016-03-05
Found an old Shuttle post where it was the f key?

---

### Post by LloydM999 on 2016-03-05
Sorry, can we keep this thread on topic (getting Windows to boot from grub)? I don't really care about the boot select in POST right now.

---

### Post by oldfred on 2016-03-05
Windows is on sda which from BIOS in grub is hd0. 
Windows also expects to boot from BIOS drive seen as hd0.

And when booting from sdb, that is hd1.
But this in grub entry normally changes the bits on the drive that say which is hd1 & which is hd0 and Windows is normally happy to boot.
drivemap -s (hd0) ${root}

And if you can directly boot Windows from first drive, then your BIOS may not be writing data in standard fashion.
Often the only fix is then to install grub to sda. Or boot from one time key which you do not seem to have.

---

