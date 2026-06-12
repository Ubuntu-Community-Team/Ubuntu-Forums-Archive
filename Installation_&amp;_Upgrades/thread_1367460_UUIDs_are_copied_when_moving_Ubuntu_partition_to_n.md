---
title: "UUIDs are copied?? when moving Ubuntu partition to new hard drive"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by davace on 2009-12-29
This may be common knowledge but it took me many googles to figure out and at the very least, writing it will make me feel better inside.


PROBLEM:  Copying partitions also copies the UUID which may subsequently cause problems with GRUB if it is using UUIDs to recognise your root partition.

DETAIL:
I wanted to move my existing Ubuntu install to a new hard drive.

I used a GParted boot CD/DVD (or was it just Parted?) to copy my original root partition from my old hard-drive, to a new one.  I then resized it to take up the majority of the new drive.  (The shortcut version - this copies the UUID too!)

The problems started when I was trying to get GRUB to boot my new hard drive.  After much troubles I found that the two partitions have been given THE SAME UUID during the copy - which may make sense in some circumstances, but not in mine, where I wish to continue using the old root partition.

I learned by plugging and unplugging hard drives from my motherboard that if I only connected my new hard drive (with the copied partition) then everything would work - Ubuntu/linux would boot from the new partition.  But when both 'new and old' hard drives were connected (even though the 'old' drive was connected to the second SATA slot (or hd1 when verified through GRUB) the kernel would still use hd1 (and not hd0) as the root drive!  Interestingly "mount" would still show that /dev/sda1 was mounted on / - even though it was infact /dev/sdb5 (as verified by mounting /dev/sdb5 to /mnt)

Once I (eventually) figured out that both partitions were given the same UUID it was very easy to change one of them (use tune2fs and uuidgen - I would recommend changing the UUID of your old partition) and then everything works fine - presuming that (as I had already) you have ensured grub works on your new hard drive too.  (When first confronted with something called a UUID - I just presumed it was a manufacturer number (it sounds so official :)

Anyhow - really pesky thing to figure out, so I wanted to make some noise about it so that hopefully others with the same problem might hear it.  As for "who should fix this" I won't even pretend to know :).
 
Mostly I am hoping that either... this is really easy for others with the same problem to find in a web search, and save time... or, this is fixed sometime soon - even a system halt/pause & warning during boot-up would be better (hard drive repartitioning/rearranging just doesn't happen that often).

Cheers,

David 

PS

The (stranger) symptoms:
* mount command would say that /dev/sda1 was mounted on / but I could mount /dev/sdb5 and access the same drive that was visible on /.  However, if I then opened GParted, it would show /dev/sda1 as the drive that I expected it to be, that is, the drive which GRUB recognised as hd0.

* using vol_id showed TWO DIFFERENT id values for the drive IDs - I have NO idea where the second number came from - although admittedly one looked "formatted with hyphens and everything" and the other did not.

---

### Post by phillw on 2009-12-29
Whenever you use linux to 'photo-copy' (cloning system) a hard disk or partition, it does exactly what it says on the tin. You were using a system to make a backup / transfer, whereby you do not need to do ANYTHING if you are either doing disaster recovery, or migrating to a new drive.

They should **not** have been both plugged in at the same time, after the data transfer.

To all intents and purposes you had two identical areas. The fact one of them had underscores **_** is how linux copes with such an occurance - this would only happen normally during something like disaster recovery. The system had NO way of knowing if you were trying to rescue data or doing something a bit 'unusual' that being plugging in two identically UUID'd drives - as you can see by the UUID, the chances of this happening by chance is, to say the least, remote.

You should use the likes of tar to "suck" data off a hard drive and deposit it to another system. When you have two hard drives on the same computer, rsync is a nice way of doing it. In neither of those instances would you compromise the UUID.

Just a bit of back-ground for you.

Regards,

Phill.

---

### Post by davace on 2009-12-29
Re: Phillw

I Totally and Completely agree with you.  I am not trying to say that the software did the wrong thing in any way,

BUT... 

I am equally sure I won't be the last person not to realise this, and my comment was definitely motivated more to help others, than to try and point blame at any one.  

Valid or not, I found many sites that told me that the best way to migrate my installation was to simply copy the partition, and for some unexplainable reason, this definitely seemed 'simpler' than to use some 'foreign' tar command and worry whether it would copy the /dev section etc.

And so any others that don't realise the repercussions of doing this instead of the tar method, will probably fall into the same trap as me.  So I hope my post tells them of the repercussions.  

OTOH,
thanks for your response.

David

---

### Post by polyrhythmic on 2010-04-30
This is absolutely unexpected behavior, as a UUID by definition should be absolutely unique.  There is no warning from the partition editor, nor is the OS or the partition manager equipped to handle partitions with duplicate UUIDs -- mount, unmount, parted are all confused about which partition they are addressing.

Googling for this issue shows it as rather common, and [those]("http://gparted-forum.surf4.info/viewtopic.php?id=13285") who [know better]("http://ubuntuforums.org/showthread.php?t=924103#3") seem to [all]("http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html") have learned of this bug [the hard way]("http://paulgoscicki.com/archives/2007/05/ubuntus-uuid-schizophrenia/"), as I did.  I say **bug** for two main reasons:

1. One of the most common uses of partition editors is to create backups, because it should be the most straightforward way to get an exact copy of a partition, that can be **safely** left on the HDD and only accessed when needed.  It's unrealistic to think that partitions are always copied to a separate, to-be-disconnected drive.  Users coming from other OSs will expect to be able to copy a partition in this manner without worry.

2. **[It has been listed as a bug since 2007]("https://bugs.launchpad.net/ubuntu/+source/parted/+bug/148743")**.  If it was by design, that would be noted and the bug would be closed.  Also, if it was by design, I would think that the OS or partition editor would be better equipped to handle it -- if the Ubuntu installer can remind you to remove the install CD before rebooting, GParted can remind you to remove the HDD (or change the UUID) so you don't hose your backup on the next boot.

I would consider myself an advanced user and I never would have predicted duplicate UUIDs.  Users who use Ubuntu who are less concerned with the internals may be corrupting their backups right now without a clue.  The only way to discover the bug is with careful observation -- and it's hard to notice until you've already mounted (one of) the two duplicate partitions, defeating the purpose of a safe backup.  Considering Ubuntu is designed in many ways to be the most approachable Linux distro, this is very important.


Otherwise, using the term "UUID" is a misnomer and should be changed.


Thanks,

**Charles**

[I]
P.S. For anyone else who ends up here with this same issue, the simplest fix to change the UUID is:[/I]
```
tune2fs -U random /dev/sda1
```

---

### Post by ottosykora on 2010-04-30
yes, but this would mean, that you would need some kind of selection before copying, asking you what you want do with the copy later.
When I clone a disk, I intend to use it as such later as it is, so I intend the boot manager to boot all the partitions as if it was on the original, no chnages, no updates of grub menu etc. In such case one is happy to have sectorwise copy function producing as much as possible exact copy of the original.

If someone is just doing other partition with similar content on the same computer, he will need to arrange for all that boot list matter anyway after that, so normal partition back up and partition restore is possible, this will format the partition anyway and thus producing other number. 
Sectorwise copy has an aim to produce exact copy and not to change a bit on the target.

---

### Post by laudaka on 2011-01-02
Many thanks Davace to start this thread and for you elaborate explanation of the weird symptoms. And thanks to the others for more about the solution.

I knew making a backup of a complete partition in GParted couldn't be as easy as clicling Copy and Paste. I had a premonition weird where going to happen.

I really needed a copy of the whole partition (thus the complete file system / ), because I was installing Ubuntu Linux on a crappy computer. I install step by step a few packages at a time. And if the PC gets stuck at startup I wish to boot into the other partition to fix things. Instead of having to use the Ubuntu Minimal CD for the umpteenth time.

Ah many thanks.

The result of copy and paste in GParted was in my case that my pc booted at random one of the two Ubuntu Linux partitions! And I had also like described above that weird thing that the partition shown to be mounted by **mount** wasn't really the mounted partition.

I'll try that solution now. I expect it to work.
```
tune2fs -U random /dev/sda1
```

---

### Post by laudaka on 2011-01-02
Yes! It worked. I'm grateful. I still had to reinstall GRUB2 (v1.9) to  both partitions by using the Rescue mode of some Ubuntu CD. The Ubuntu  Minimal CD is the only one working on that crappy system so I used  that.

I first reinstalled grub with the partion /dev/sda7 mounted. That's the partition that I don't want to be booted by default. And then I reinstalled grub with the partition /dev/sda8 mounted, the one that I do want to boot by default. That's the one that should be at the top of the list in the grub menu at startup.

Maybe I could have skipped the step of reinstalling in the partition /dev/sda7, because the grub in the MBR is never using the grub in /dev/sda7. But I just wanted to be sure the problem of UUID's was solved.

---

