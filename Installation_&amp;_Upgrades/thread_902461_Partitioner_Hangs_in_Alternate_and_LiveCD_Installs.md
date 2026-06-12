---
title: "Partitioner Hangs in Alternate and LiveCD Installs, please help!"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by AbeBorker on 2008-08-27
Hi folks,

I'm a newcomer to linux, old hat with computers.  I've been trying to solve this problem now for two days so I've caved and hoping that someone here will help me.

I have a Toshiba a15 sattelite that my dad thought was bricked, but I breathed new life into it and want to install ubuntu. I tried the live cd and loved it.  I tried the Install from the liveCD and it went well until trying to partition my ext3 partition.  Where it would hang up for hours.

I read online that the alternate CD might avoid the buggy partitioner, so I gave it a go.  I'm now working with the alternative CD and now have the "Partitions Formatting" screen stuck at 33%, reading "Creating ext3 file system / for in partition #1 of SCSI1 (0,0,0) *sda)..."

If I hit Alt + RtArrow a few times, I get to the log, and it's throwing out lines every few seconds.  that look like this,

DATE : TIME : kernel: [ crazy long #'s ] ata1.100: status {DRDY ERR }
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: status {ABRT }
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: configured for PIO0
DATE : TIME : kernel: [ crazy long #'s ] ata1.: EH complete
DATE : TIME : kernel: [ crazy long #'s ] ata1.100: Exception at Emask


and lots and lots of other things too!  Honestly, it all moves so fast, it's hard to type in everything, I wish I had a way just to post it all without having to look over my shoulder and retype it!  These are just five lines among many that show up.  And after 30min or so, the status bar and screen are still the same....

I tried Standard and Advanced IDE in the BIOS, and I checked the CD, and I tried the LiveCD too, so I think it's not my CD.  The HD is old, but I just was able to install WinXP on it two days ago.

Arg, I'm going insane.  Someone please tell me what I can do.  I can get to the console!  And I can provide anymore information that might be needed.

---

### Post by sandysandy on 2008-08-27
try gparted CD.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

burn it as iso image to make bootable CD.

then pop in CD drive and reboot computer.

see tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by AbeBorker on 2008-08-27
Thanks Sandy,

I found the Gparted liveCD iso, I'll burn it and go from there...  I assume this will let me format my partitions and then just run the ubuntu alternate again?

Am I correct that I want my partitions to be
1: a very large ext3 partition for ubuntu
2: a small swap partition (2-3 times the size of my RAM)
?

EDIT:  I guess I jumped the gun, thanks for the links!  When I first loaded the page all I got was the first line of your post.

---

### Post by sandysandy on 2008-08-27
ur main partition [COLOR="Blue"]/[/COLOR] will be large.

SWAP is generally 1.5 times to 2 times ur RAM. But if ur RAM is large, SWAP may not be needed unless u intend to hibernate. but with enough disk space u can just make it.

r u planning ubuntu as the only distro or u intend to dual boot with windows or any other OS

regards[SIZE="4"][/SIZE][SIZE="6"][SIZE="7"][/SIZE][/SIZE]

---

### Post by sandysandy on 2008-08-27
some links on installing ubuntu

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/8.04/installation-guide/i386/index.html](https://help.ubuntu.com/8.04/installation-guide/i386/index.html)

also, links on dual booting XP & Ubuntu (if required)

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


regards

---

### Post by AbeBorker on 2008-08-27
Alright, how long should formatting a 30GB drive be....  I think there's problems...  and I have it as,

28gb ext 3 partition
2gb swap

Both primary partitions.  It just seems like the ext3 partition is taking a VERY long time.

---

### Post by sandysandy on 2008-08-27
can u post snapshot from gparted 

regards

---

### Post by AbeBorker on 2008-08-27
It's been now almost an hour... no sign of formatting....

I can't post a screenshot.  The process in bold under details appears to be:
mkfs.ext3 -L "" /dev/

As to the partitions I'll try to duplicate the Gparted window before I press Apply:

Partition           Filesystem    Label   Size
New Partition #1    ext3                  25.99 GB
New Partition #2    linux-swap    swap    1.95 GB

Furthermore, upon canceling the formatting process, Gparted just stays "Scanning all devices" and I'm forced to do a hard reset...

---

### Post by AbeBorker on 2008-08-27
I had a thought, are there any ways I could check out the integrity of the hard drive?  Like through the Ubuntu live CD.

Would bad sectors affect the partitioning process, or would it just work around them?

EDIT:  I'm gonna try and make a 2gig ext 3 partition just as a test...

---

### Post by AbeBorker on 2008-08-27
No dice on the small ext3 partition... however....

I was able to make a 20gb fat32 partition!  Which gets me nowhere of course....

---

### Post by sandysandy on 2008-08-27
try to format it again as ext3 and give it all the time in the world for formatting:)

regards

---

### Post by AbeBorker on 2008-08-27
Well I'm gonna go leave the house for like 5 hours....  We shall see!

---

### Post by gatenby_jp on 2008-08-27
If just leaving it does not do the job 

Try partitioning as follows ... during the live cd install select manual partitioning

make a partition of say 4 gigs and select / as the mount point
make a second partition of say 8gig and select mount point as /usr
make a third partition of most of the remainder and select mount point /home
the remainder should be swap space

and try that way ... in any event it makes for a better install of linux than a single partition ... on any re-install you would not reformat the /home partition simply remount it

---

### Post by AbeBorker on 2008-08-27
Woohoo!  Five hours later, I have a 22.47gb ext3 partition.  Now I just seem to be hanging up on the swap partition.

After a few minutes it has an error.  Under libparted messages it says "Input/output error during write on /dev/sda"

Just when I thought I was over the hurdle...

---

