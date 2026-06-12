---
title: "Ubuntu FULL install - Partition Optimizing"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Grams79 on 2008-11-13
[COLOR="SeaGreen"][SIZE="1"]I'm up late again clicking away at the system.
When I felt like reinstalling Ubnuntu once again.

After testing the "use entire disk" first install partition option a few times.
I began to notice a mess of sorts, piling up around my workstation.
The system seems to become a mess after a while and starts to drag it's feet.
I'm on state of the art hardware as of late 2008, it is never the problem.

I'm posting this while doing the install.
I'll take a screenshot of my optimized and tested custom partition method for a full install of Ubuntu.[/SIZE][/COLOR]

*[SIZE="3"]Grams79's first install partition guide 2008[/SIZE]*

During a fresh install of Ubuntu.
Choose _manual partition_.
Click _New partition table_ (total free space).

_EXT3_ and _Primary_ option for all.
*In order starting from first.*
**/boot**
**/ (root)**
Create the **SWAP** at the "end".
*Going into extended next.*
**/var**
**/usr**
**/tmp**
**/home** *Use all free space.*

Pass this around if needed, but please leave my humour in the post.
hehe

---

### Post by Grams79 on 2008-11-13
Updated to full and here is the results screenshot.
All vanilla, no extra applications installed.

You welcome everyone, always happy to contribute.
:guitar:

---

### Post by wizard10000 on 2008-11-13
If I was building a server I might consider partitioning as you suggest except that I usually only use separate partitions for root, /var, /home and swap.

It's true that a runaway process can fill up /var with logfiles so it's a good idea for a server to have /var on a separate partition just in case something like that happens, but I think such a complicated partition setup is overkill for a home computer.

Knocking on wood, I haven't needed a separate /boot partition on a Linux machine in years.  I've been able to repair kernel problems by simply maintaining more than one kernel version on the hard drive - I normally keep the current and two previous versions.

I do agree that /home should always be on a separate partition simply because it makes it easier to reinstall or upgrade an OS without disturbing your data - which should be backed up anyway, yes?  ;)

If there's more than one physical hard drive in the system I normally put the swap partition on the outside edge of a disk other than where the OS resides - my current setup looks like this:

/dev/sda = 36gb SCSI drive:

/ = the entire drive is used for the root partition - there is no separate boot partition on this machine.

/dev/sdb = 250gb SATA drive:

swap = I use a 2gb swap partition on the outside edge of the platter - disk access is a bit faster on the outside edge of the disk.

/home = the balance of the drive is a home partition.

Now if this machine was a server I'd put /var on /dev/sdb just so a runaway process wouldn't break the OS.

Sometimes less really is more - IME eight partitions on a single spindle will limit you more than they'll help you.

Just my opinion -

---

### Post by Grams79 on 2008-11-13
> **wizard10000 said:**
> I do agree that /home should always be on a separate partition simply because it makes it easier to reinstall or upgrade an OS without disturbing your data - which should be backed up anyway, yes?
I agree 100%, thanks.

---

