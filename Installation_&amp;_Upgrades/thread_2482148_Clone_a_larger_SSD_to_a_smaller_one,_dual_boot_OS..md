---
title: "Clone a larger SSD to a smaller one, dual boot OS...."
date: 2022-12-21
forum: Installation &amp; Upgrades
---

### Post by jakemaverick911 on 2022-12-21
Is there any easy way to do this? Spent most of the day trying but Clonezilla won't do it neither will any of my other disks....

It's been quite a while since I did any of this, but I have Acronis True Image....I'm sure in the past it was able to do this job and keep them bootable? I have two machines here....I've only tried so far on the Windows 10 only machine (not dual booted it yet). Acronis fails...does clone and also restores image but not bootable. I know I have no hope with the dual boot machine....

As I say it's been quite a few years....I'm hoping some new freeware about that will make it muppet proof? I didn't use to be a muppet, and porbably not a complete muppet now...but have suffered some brain damage in the intervening years... :-(

---

### Post by howefield on 2022-12-21
Resize the source disk to size of destination disk (or smaller) then Clonezilla should do it.

I'm sure that you have backed up all important data first.

---

### Post by jakemaverick911 on 2022-12-21
I did read on that and that was the last thing i tried before posting here! I have backed up, but no way to restore/ bootable right now. Re-sizing may have been what has now bricked the windows machine...trying repair options now, it just won't boot.

There is an advanced option in clonezilla to skip the bit where it checks the size of the disks as well...tried that from clone and image as well, neither actually worked for me so taring my hair out now.....

---

### Post by jakemaverick911 on 2022-12-21
ah, i think i just realised....when i resized the disk, i didn't think about the recovery partitions and other little bits....that must've been what did it, but now windows 10 still won't boot, recovery options aren't working....and i'm in the wrong forum for it now :-(

---

### Post by ubfan1 on 2022-12-21
Years ago, I did use Macrium Reflect (free version) to copy a Windows install to a smaller SSD. That worked fine, but wasn't dual boot.

---

### Post by VMC on 2022-12-21
You didn't mentioned what file system your trying to reduce. If its ext4 then [fsarchiver]("https://www.fsarchiver.org/") will work.

---

### Post by jakemaverick911 on 2022-12-22
still on just the windows 10 machine, so ntfs....think i will try  macrium reflect next! thanks. Gparted should let me resize the  partitions in lunux though, when i get to that one?

---

### Post by TheFu on 2022-12-22
> **VMC said:**
> You didn't mentioned what file system your trying to reduce. If its ext4 then [fsarchiver]("https://www.fsarchiver.org/") will work.

+1 for fsarchiver.  However, the target partitions will need to be pre-created and the compressed images will need to be at the partition, not for the whole disk.
This isn't 100% bonehead, since you'll need to validate the /etc/fstab correctly points at any file systems via UUID or volume name for the system to boot.
I haven't used fsarchiver in some years.  I'm fairly certain it supports installing to small partitions for file systems it "understands" and ext3/4 and NTFS should be in that list.

These days, I use imaging for very specific needs, but not for things where backup/restore processing works better, which is almost everything. If you can't restore user data and the OS + configs in less than 45 minutes, I'd say you need a better backup/restore solution.  Obviously, if there are 40TB of data, restoring all of that will take longer, but the core OS and documents for 10 users with all user and system settings should restore in less than 45 minutes, easily.  30 minutes for systems with well-managed storage.

BTW, in Linux, as long as the files are mounted where they are expected to be located, there's nothing magical happen.  The /etc/fstab controls mounts at boot, so it is possible to setup partitions, file systems, rsync files between 2 storage areas, then update the /etc/fstab for new UUIDs on the new storage, and then just reboot.  If that doesn't boot, then something is missing related to grub or EFI, which are easily installed and updated ... in about 3 minutes.  The trick is to get the files moved/copied as they are with the correct owner, group, ACLs, permissions and xattrs from file system A --> file system B.  If you have multiple file systems, just be consistent in the move/copy.

If it harder to explain in words than the actual effort to make it happen, assuming you can use mount, edit an fstab, and use rsync with the correct options that retains hardlinks and symbolic links and files.   However, any proper backup tool should handle these things, which is another reason to just use the normal, expected, system backup and restore process - assuming it isn't "clone".

---

### Post by jakemaverick911 on 2022-12-22
thnx ThrFu, not fully read that yet but will come back to that shortly, i hope....

been a nightmare day, must've copied the contents across 20x today, cdn't get it to boot....tried with macrium reflect free in the end, did it quick from within windows...but on reading the help there it finally tells me windows 10 will not boot from an external enclosure! so it had probably worked previously...i never knew that, only been using windows 10 for a few weeks now...so just gave myself a good slap and hope some of you a lil laff.... ;-)

I know this probably ain't the best place to be asking....but here is the weird thing...it wouldn't copy everything across! There were four partitions...couple piddly 100 meg Healthy EFI partitions that seems to have combined into one on the new drive, the large bit that went across fine...and the one it couldn't do was a 513mb ntfs partition saying it would not fit, but i have a lot of unallocated space + an F drive now that I don't have permission to access. I think they're all to do with system restore files?

Had to do a few things to make it bootable, but everything seems fine/ booted on that drive now. Although i have to select from 3 versions of windows 10 to boot...but i'm sure i can clean up the boot manager at some point, might be best to see if linux will sort that out when i get to dual boot that...

it was just the smaller partitions that was causing me a lot of problems it seems...

---

### Post by TheFu on 2022-12-22
I've never seen Win10 and have never used Macrum anything.   Not how I roll.  I got tired of dealing with licenses and stupid limitations set for the benefit of a company, not the users.

Windows does need to be installed first, before any other OS.

Having empty space doesn't seem like a sufficient setup. I'd think the actual target partition(s) need to exist before copying data over.

Other people will need to answer the other questions.

---

### Post by VMC on 2022-12-22
One caveat, if its NTFS and Windows don't use fsarchiver. Read the info on fsarchiver home page..

---

### Post by TheFu on 2022-12-22
> **VMC said:**
> One caveat, if its NTFS and Windows don't use fsarchiver. Read the info on fsarchiver home page..

[https://www.fsarchiver.org/cloning-ntfs/](https://www.fsarchiver.org/cloning-ntfs/)
Seems that since MS-Vista, the NTFS support is less.  They've placed significant warnings about using it for NTFS.  Seems their stance is to try it, perhaps it will work.  And since nothing will be lost anyway, why not?  They also say to not use it on production systems.  Makes me wonder if some data wouldn't be transferred and no warning/error would be shown if that happens.

---

### Post by jakemaverick911 on 2022-12-23
thanks for all the help folks! pretty much sorted now. Macrium and Arconis mostly sorted it in the end...buti am kicking myself for not knowing that windows 10 can not be booted from an external enclosure! that just strikes me as bizarre...and several TB written to the drive that didn't need to be + so much work....

but please close the thread now.

---

