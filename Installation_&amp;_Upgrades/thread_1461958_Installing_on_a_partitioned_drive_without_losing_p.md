---
title: "Installing on a partitioned drive without losing previous data"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by huntrrr on 2010-04-24
I have a computer that was running Windows XP on a partitioned drive. The system crashed, And I cannot find the XP disk from a few years back...so I want try Ubuntu.

**How can I install ubuntu on my c: drive without losing my data from the other two partitions?**

(i.e. when i started the install from the Ubuntu cdrom, it gave me three choices, and I'm not sure which will save  my existing data on the E: and F: partitions...) 

If I could back-up my existing data I would, but I need a working OS to do that. HELP!

---

### Post by mikewhatever on 2010-04-24
If installed on one of the existing partitions, only that partition gets formatted, and data on other partitions is untouched, thus needs no saving. Don't leave any useful data on the partition you are planning to install to, and be careful to only format the target partition.

---

### Post by C.S.Cameron on 2010-04-25
When you get to partitioning in he install process make sure the format box is checked only on the partition you want to install to.

---

### Post by Herman on 2010-04-25
> I have a computer that was running Windows XP on a partitioned drive. The system crashed, And I cannot find the XP disk from a few years back...so I want try Ubuntu.That's an excellent idea to try Ubuntu, I highly recommend replacing any proprietary operating system with Ubuntu. :)

I'm not sure why your old system crashed, but I would be asking friends and relatives for a lend of an XP Installation CD for running a file system check in the C:/ drive, that might fix it. 
Unfortunately since it is a proprietary system, people tend to covet the 'Installation' disks for it, if they have one. 
You absolutely need an XP 'Installation; disk, (and not a 'Recovery' disk), to repair or maintain your proprietary operating system. 
It's absolutely scandalous that  not every one who pays with the hard-earned money from the sweat of their backs doesn't always get a proper 'Installation', (and repair) CD.
With a Windows 'Installation' CD you could run CHKDSK /R from a recovery console and most likely fix the file system enough to rescue any files in it and even likely get the operating system working again.
All the more reason never to trust any proprietary operating system.
> If I could back-up my existing data I would, but I need a working OS to do that. HELP!Your Ubuntu Live CD is ideal for accessing and rescuing your old data.
If I were you I would use the Ubuntu Live CD for copying and pasting the existing data from all three of your old partitions in the internal hard disk to some other hard disk first, such as an external USB drive or something like that.

There are also some distros like Puppy Linux or Parted Magic that will boot in your DVD drive and load into your computer's memory and run from there, and eject from the CD/DVD drive, thus leaving the CD/DVD drive available for making backups to DVDs or CDs.

You really should make a backup of your existing data before doing anything with any operating system's installer, no matter what operating system you're trying to fix or install.
Although the Ubuntu installer is made as safe as possible and is certainly equal to or better than any other, it is still possible for things to go wrong. Human error is one reason. Hardware glitches are another reason, such as a speck of dust on an optical drive lense or an intermittent random voltage fluctuation from a PC's power supply, a failing CPU fan or anything like that. Any of those can endanger your data if any of they happen to eventuate at a critical time during an operating system installation process.

Since you're not re-partitioning your disk, but only reformatting one partition you should be fairly safe, but you should always be making regular backups of your data anyway, even for normal everyday computing, it's just good practice.

---

