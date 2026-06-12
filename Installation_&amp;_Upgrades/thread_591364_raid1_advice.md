---
title: "raid1 advice"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by appye on 2007-10-25
I am setting up a computer for my buddy who does not know anything about computers and does not wish to.  He is going to use it for standard things like email, web searching, downloading stuff, etc.  Basically it is a standard end user desktop machine.

I wanted to put some redundancy in there so he does not have to worry about backing things up himself (please no lectures on why raid1 is not a good substitute for proper backup)...  What I have come up with is using the alternate installation disk and creating a RAID1 array for his /home directory.  Currently, here is the layout I currently have:

sda
 7gb ROOT - /
 33gb RAID

sdc
 7gb SWAP
 33gb RAID

Multidisk device
 33gb HOME - /home

I realize my nomenclature is probably incorrect, but I digress.  I wanted to get some advice on what would be considered a good setup.  I have considered setting up both hard drives entirely in RAID1 and then having a 1gb swap, 6gb / and 33gb /home all running in raid1 ... but it did not seem like a good idea to me to run swap in RAID.  I have also thought about having a swap partition on each drive NOT running in raid1, but then having / and /home running in raid1.

I am not sure what would be the best way to go about doing this.  I only have two hard drives to work with.  I do NOT want to set it up with separate partitions for things like /var /opt /usr and etc...  I am also aware that people will probably raise an eyebrow about the small / partition, but this person will never use 6gb on his root partition.

---

### Post by kidders on 2007-10-26
Hi there,

I know you'll *hate* this, but (at least for the benefit of future readers) I should mention one or two things you _don't_ want to hear...

Assuming there are limits to the amount of disk space your friend has available, forgetting about RAID1 (which is wasteful to the tune of 200% of the disk space a filesystem would otherwise consume) really is worth considering, particularly since we're talking about a /home filesystem. If you had mentioned any other directory, I might feel differently, but RAID will offer your friend absolutely no protection against the single most common data loss scenario suffered by peoples' personal files ... incidents like "Oh crap, I didn't mean to delete that" or "Damn... did I hit 'Save' or 'Save as'?".

Feel free to tell me to shut my big mouth & read the second paragraph of your o/p again ... I won't be offended hehe ... but I thought it best to be sure you really *do* want RAID 1 in your friend's /home, even if it comes at the cost of a convenient location for regularly scheduled, behind-the-scenes backups.

Anyhow, on to what you *do* want to know about...

Using RAID 1 for a major location like /home will double the load on your friend's I/O bus, so there are a few performance issues worth taking into account:

**- I -**
Adding a third or subsequent disks in the future will likely cause a much more significant performance penalty than expected, so it would be nice to avoid having to do that, and find a place for swap, etc. on the two disks that will store /home, like you suggested.

**- II -**
In that case, you'll probably want to focus on keeping the non-RAID load on each disk as equal as possible. For many I/O operations, a delay accessing one physical disk will make the fact that the other may well be idling irrelevant, so I would recommend opting for your suggested approach to swap ... putting one swap partition on each physical disk, both with equal priority.

**- III -**
Beyond that, how best to split the load the rest of your system places on the disks depends on the typical usage patterns you expect. Incidentally, you'll also need a /boot partition, but you can discount that completely, in terms of any performance or space consumption considerations.


I hope that helps.

---

### Post by appye on 2007-10-27
Point taken on the user error part of things.  I actually have regular scheduled backups set up very well on windows machines I have built.  I am an excellent windows batch filer, but I have not yet ventured into the world of bash, nor do I know how to schedule tasks or where equivalent startup/shutdown/logon/logoff scripts.  I know some basics.

In Windows, I have a batch file scheduled once a day (and at every shutdown) that runs different backup operations based on the existence of what I call a &#8220;tagfile,&#8221; MONTHLY.TXT.  If MONTHLY.TXT does not exist, it recursively copies (with verification) all the users data that does not have the archive bit set to a BACKUP folder on another hard drive.  If MONTHLY.TXT does exist, it deletes any folders called LASTMONTH renames BACKUP to LASTMONTH and recreates the backup directory by copying everything the user has, regardless of whether or not the archive bit is set.  

Another scheduled task that runs once a month creates the MONTHLY.TXT file.  Pretty much everything is done with the IF EXIST, RENAME and XCOPY commands.

This way, the user gets an incremental backup that runs quite often, generally gets to keep files that may have been overwritten, and the backup folder does not get too cluttered with files that actually should be deleted.

I could probably figure out how to do this in bash.  I have played around with a scripting language called Mortscript that seems similar to bash.  Use of the 'if' command is quite different from windows, and I do not know about any equivalents to the archive bit in NTFS.  Also, what about file copy verification?  Using the /v switch in xcopy does this.  Is there an equivalent or maybe already built into the command?

Regular backups that occur while the user may be using the machine need to be mostly incremental for me to be satisfied with this approach.

---

### Post by kidders on 2007-10-27
Hmmm....

You'll find Linux shells far more flexible than Microsoft's one, so I suppose the first thing to mention is that you needn't limit yourself to such simplistic approaches to deciding what to back up. Having said that, of course, simple things tend to work the best.

Another observation I would make is that many users tend to use rsync (or similar) for backup purposes. It's a nice tool, although I don't make much use of it myself.

Other things...[LIST]
[*]There are various ways of verifying the condition of copied data, although "cp" itself doesn't provide one. Personally, I've never found it to be necessary. The "cp" command may have other features you might find convenient for backing stuff up though.
[*]I would discourage the use of file attributes as a means of deciding what to back up and what to ignore, because most of them don't translate well between filesystems.
[*]The best reference for basic utilities like "if" is its man page. In the case of "if", "man test" is also useful. Incidentally, in many cases, the use of "if" is unnecessary. For example, ```
[ -w /etc/resolv.conf ] || echo "resolv.conf is not writable."
```
[/LIST]

---

