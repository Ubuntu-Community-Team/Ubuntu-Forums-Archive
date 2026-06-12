---
title: "Dual boot with Win XP, couple questions"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by horseatingweeds on 2010-11-27
I'm about to install Ubuntu on an older computer along side XP, and have a few questions, and wouldn't mind some confirmation of the wisdom of my plan.

1. I've been reading about the Master Boot Record. Will this be altered by the Ubuntu installation to give the choice of which OS to boot on start-up? 

I'm working with a 160GB HD. It's got two partitions: sda1 fat32 4GB with 3GB used (Compaq recovery), and sda2 ntfs 145GB with 85GB used (Windows). I plan to shrink sda2 from 145GB to 100GB or so. 

2. Is Gparted the best tool for shrinking this partition, or is it better to use window's disc manager? 

In addition to non-partitioned space, this will leave around 50GB free. I then plan to allocate 37GB of that in the following logical partitions on installation with ubiquity:

/boot   100mb
/root    5gb
(swap) 2gb
/home 15gb
/tmp   1gb
/usr    3gb
/var    10gb

I'll be the only user. And this system will be primarily a php development environment - sort of as a backup to my newer system, a place to experiment with Linux, and a practice run before installing Ubuntu on my newer system.

3. Does this sound reasonable?

---

### Post by coffeecat on 2010-11-27
> **horseatingweeds said:**
> 1. I've been reading about the Master Boot Record. Will this be altered by the Ubuntu installation to give the choice of which OS to boot on start-up? 

Yes. grub stage 1 will be written to the MBR. Some more grub code will be written to the embedding area, which is the gap between the partition table and the first partition. But the rest of grub - including stage 2 and the grub.cfg file - will be on your root partition.

> **horseatingweeds said:**
>  I'm working with a 160GB HD. It's got two partitions: sda1 fat32 4GB with 3GB used, and sda2 ntfs 145GB with 85GB used. I plan to shrink sda2 from 145GB to 100GB or so. 

2. Is Gparted the best tool for shrinking this partition, or is it better to use window's disc manager? 

With Windows XP it is generally OK to shrink the C: partition with Gparted. There are reports of occasional problems with Vista and Windows 7, so with those two it's probably better to use Windows own disk manager. Does XP have a disk manager capable of shrinking the C: partition? I wasn't aware of this.

> **horseatingweeds said:**
>   In addition to non-partitioned space, this will leave around 50GB free. I then plan to allocate 37GB of that in the following logical partitions on installation with ubiquity:

/boot   100mb
/root    5gb
(swap) 2gb
/home 15gb
/tmp   1gb
/usr    3gb
/var    10gb

That is - in my view - unnecessarily complex. A separate swap is routine. A separate /home is a good idea. Some people like to have a separate boot - there are pros and cons, and the merits of a separate boot could be debated. But why do you think separate /tmp, /usr and /var partitions would be a good idea? For a home system that's a very inefficient of disk drive space. When you refer to '/root', do you mean the root partition (properly referred to as '/') or the root home directory? Either way, it's too large if your /usr is going to be separate. The /usr directory is always the largest so if you're going to put /usr, /var and /tmp in separate partitions, your / partition doesn't need to be that large at all.

Go for a separate /home and swap, and have a separate boot if you really think that's a good idea, but I suggest you put everything else in one / partition.

---

### Post by horseatingweeds on 2010-11-27
Thanks coffeecat

Is it wise or possible then, to backup the MBR, in case something goes awry? 

According to this article: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)  Windows disc manager can shrink the C: partition. The article also seems not to favor either Gparted or disc manager for this job. It does say Gparted can safely shrink C: without first fragmenting it, which is interesting. However, looking at disc manager on xp now, I don't see how to shrink anything...

Yes, by 'root' I mean /

My reasoning for a separate /usr partition is that /usr doesn't change often, and could use ext2, in addition to it being a good practice for purposes of exporting users and other things I won't be doing any time soon. 

/var changes frequently, so I understood it to be a good practice to keep it separate as well, to prevent fragmentation. 

The boot partition also changes infrequently, and I've read that many machines prefer the boot partition to be near the beginning of the disc - which reminds me of another question I had: Will this be a concern on a dual boot system, Ubuntu's boot files not being at the beginning, rather towards the end, even right after the windows stuff? 

I can't remember my reasoning for /tmp... I must have read something advocating it. Perhaps because it changes frequently too.

Regardless, I'm not vested in any idea and am open to advice. Would this then be a wiser configuration? 

/boot   100mb
/  15gb
(swap) 2gb
/home 15gb

---

### Post by dino99 on 2010-11-27
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by coffeecat on 2010-11-27
> **horseatingweeds said:**
> Is it wise or possible then, to backup the MBR, in case something goes awry? 

You could with dd, but it's easy enough to restore the Windows bootloader with a Win XP install disc, with lilo from the live CD, with supergrubdisk and several other utilities.

> **horseatingweeds said:**
> According to this article: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)  Windows disc manager can shrink the C: partition.

I cannot see where it says that the XP disc manager can shrink the C: partition. I believe this was introduced with Vista.

> **horseatingweeds said:**
> My reasoning for a separate /usr partition is that /usr doesn't change often, and could use ext2... 

Oh yes it does. Every time you apply system or app updates or install something. Ext2 would be bad idea.

> **horseatingweeds said:**
> .... , in addition to it being a good practice for purposes of exporting users and other things I won't be doing any time soon. 

The /usr directory is nothing to do with user accounts. It's where installed apps, libraries, utilities, etc are stored.

> **horseatingweeds said:**
>  /var changes frequently, so I understood it to be a good practice to keep it separate as well, to prevent fragmentation. 

Fragmentation is not an issue on Linux filesystems, unless more than 90% full.

> **horseatingweeds said:**
>  The boot partition also changes infrequently, and I've read that many machines prefer the boot partition to be near the beginning of the disc

A theoretical rather than a practical concern.

---

### Post by Quackers on 2010-11-27
When I had XP installed I used GParted Live CD to resize the C: drive. I don't believe it can be done from within XP iirc.

---

### Post by gordintoronto on 2010-11-27
If you're doing mostly web development, I would be tempted to put /var on a logical partition. Unless the site includes videos, 10 GB is a HUGE web site! A friend runs a site with hundreds of pages, dozens of small videos and a relatively small number of images (maybe a couple of hundred), and the whole site is around 5 GB.

---

### Post by oldfred on 2010-11-27
Herman does not like anything separate and I have reverted to keeping /home in /, but have all my data in /data or a shared NTFS partition.

With desktops there is no reason to have separate system partitions:

Herman on advantages/disadvantges of separate system partitions post #3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by efflandt on 2010-11-27
2 things you probably want to do before shrinking XP (which works fine with gparted from live/install CD or USB).  Defragment to move files down, and disable virtual memory (which cannot be moved) I think from Control Panel > System > Advanced.  Make a note of virtual memory settings before disabling it.  You have to reboot after disabling virtual memory to have it take effect.

Once you resize Windows, you could create the other partitions you want for Linux with gparted.

After resizing an ntfs partition, gparted will mark it as dirty so Windows will chkdsk it when it boots.  So after resizing it, you may want to reboot and let that happen just to make sure that is still functioning.  You could re-enable virtual memory at that point.

Then install Ubuntu manually selecting the partitions you created for it.  But don't make so many partitions without knowing what you need, or you will just end up short of space on one while having loads of unused space on another.

PS: Back in 2004 when I did not do anything before trying to shrink WinXP I could only shrink it 24 GB on a 200 GB drive.  But more recently when I discovered Ubuntu just before 9.10 was released, by defragging and disabling virtual memory, I could have freed up more than 150 GB if I thought I needed that much.

---

### Post by horseatingweeds on 2010-11-27
Thanks everyone - new information, confirmation, and information that contradicts my earlier information - which is more often a good thing, unless you're in a hurry, and I'm not. ;)

> **efflandt]2 things you probably want to do before shrinking XP (which works fine  with gparted from live/install CD or USB).  Defragment to move files  down, and disable virtual memory (which cannot be moved) I think from  Control Panel > System > Advanced.  Make a note of virtual memory  settings before disabling it.  You have to reboot after disabling  virtual memory to have it take effect.

Once you resize Windows, you could create the other partitions you want for Linux with gparted.

After resizing an ntfs partition, gparted will mark it as dirty so  Windows will chkdsk it when it boots.  So after resizing it, you may  want to reboot and let that happen just to make sure that is still  functioning.  You could re-enable virtual memory at that point.

Then install Ubuntu manually selecting the partitions you created for  it.  But don't make so many partitions without knowing what you need, or  you will just end up short of space on one while having loads of unused  space on another.

PS: Back in 2004 when I did not do anything before trying to shrink  WinXP I could only shrink it 24 GB on a 200 GB drive.  But more recently  when I discovered Ubuntu just before 9.10 was released, by defragging  and disabling virtual memory, I could have freed up more than 150 GB if I  thought I needed that much.     [/QUOTE]

Indeed? I defraged, and was wondering about that blue chunk up there... Can disabling virtual memory cause any problems though? I worry because when I run windows on this machine the page file take one *horrible* beating on a fairly constant basis. There's a gig of RAM. You'd think that would be plenty.

[QUOTE=oldfred]Herman on advantages/disadvantges of separate system partitions post #3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)[/QUOTE]
This is a handy article!

[QUOTE=gordintoronto]If you're doing mostly web development, I would be tempted to put /var  on a logical partition. Unless the site includes videos, 10 GB is a HUGE  web site! A friend runs a site with hundreds of pages, dozens of small  videos and a relatively small number of images (maybe a couple of  hundred), and the whole site is around 5 GB. [/QUOTE]

My thought was to point Apache at a folder in /home, keeping all my data in one place. I'm also working with multiple site, and hopefully more. The main site I'm developing now is 120MB, but on my current Win dev environment (if you can call it that) I have several functioning copies to mess with. I also keep the database and file backups in the same area for purposes of organization. 

Still, you are right. Even 100 websites won't take up a lot of space, relatively. Small is fast and fast is good. 

[QUOTE=coffeecat said:**
> 

I cannot see where it says that the XP disc manager can shrink the C: partition. I believe this was introduced with Vista.


I've found the source of confusion. It's worded like this, but looking back now, *this* is under a **Vista** caption. "This may also be located in Windows Vista and Windows 7" When I read this part I must have thought xp was implied to what came before it.

[QUOTE=HowtoResizeWindowsPartitions]
The Windows Disk Management tool is also very good at  shrinking Windows, it's very fast and easy, if you don't count the time  it takes to defrag first. If you want to use the Windows partition  editor to resize Windows, here's how you can do that, 
Administrative Tools --> Disk Management tool -> Shrink Volume 
This may also be located in Windows Vista and Windows 7: 
Settings  -> Control Panel -> Administrative Tools -> Computer  Management -> Storage -> Disk Management -> Shrink Volume[/QUOTE]

Now I'm thinking I might just use guided partitioning... What about what dino99 is advocating? He advises having a separate partition only for /home and swap - swap with 2-4Gb, root with 12Gb, and /home with as much as you need?

---

### Post by gordintoronto on 2010-11-27
> **horseatingweeds said:**
> My thought was to point Apache at a folder in /home, keeping all my data in one place...

Now I'm thinking I might just use guided partitioning... What about what dino99 is advocating? He advises having a separate partition only for /home and swap - swap with 2-4Gb, root with 12Gb, and /home with as much as you need?

Good ideas!  A good maximum for swap is twice the size of memory, although just slightly larger than memory is usually enough. Even with Apache and Mysql running, Ubuntu consumes a remarkably small amount of memory.

---

### Post by horseatingweeds on 2010-11-29
Should the computer name for Ubuntu be the same as the computer name for the Windows xp installation? I was assuming no, until I started thinking about how other computers will regard the same MAC address having a different computer name.

---

### Post by lisati on 2010-11-29
> **horseatingweeds said:**
> Should the computer name for Ubuntu be the same as the computer name for the Windows xp installation? I was assuming no, until I started thinking about how other computers will regard the same MAC address having a different computer name.
It shouldn't matter if you're aware of it, but it can lead to confusion in some circumstances. I dual-boot Vista and Ubuntu 10.04 with different computer names for each. When I use Vista then boot back to Ubuntu, the name I use for Vista sometimes shows up in Places->Network, and usually goes when my router gets round to refreshing its list of connected devices.

---

### Post by horseatingweeds on 2010-11-29
Thanks Lisati, it looks like the computer name is easy enough to change anyway.

There must be something wrong with my XP installation, it struggles just to run. I know Linux is more efficient than Win, but this is unreasonable. Ubuntu runs like a new machine. Good glory...

---

### Post by oldfred on 2010-11-29
Not really wanting to make windows better:), but one of the biggest things that causes slow down is not enough space.

NTFS partitions (and Linux) need extra working room. NTFS needs about 30% free space or it starts really fragmenting files and slows way down. If you get to about 5% free it just about stops working.

Ext3 or ext4 reserves about 5% extra space (hidden) and does not need quite as much as NTFS but still will not work well when drive is full.

---

### Post by horseatingweeds on 2010-11-29
Windows can't blame space for this one... It's got 105Gb with 80Gb used, and that's after shrinking it. Before adding Ubuntu it had 145Gb with about 85Gb used. Maybe I'll experiment later and see if I can get old xp running better. It is terrible though, the HD spins away no matter what you're doing.

---

