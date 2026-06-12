---
title: "recommended partition strategy?"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SeanBlader on 2009-10-20
So on the advice of a friend I've previously setup a separate /, /home, and swap partitions, which has been very effective. Previously though with difficulties hibernating because of conflicting drivers I've stopped bothering, and with Jaunty's boot speed I just gave up on using swap since I also never end up using enough ram (4 gb total) to bother. So I figured safer to skip a swap partition on the SSD. But with challenges with a previous laptop having problems with finding /boot this time I set it as it's own partition. So on the system I am expecting to upgrade to the Release Candidate this week I have currently:
```

dir      total     available
/boot    53.1 mb    5.3 mb
/         9.2 gb    4.9 gb
/home   108.1 gb   63.6 gb

```
With Grub2 would it be better to go back to combining / and /boot? Or with Grub2 do I need to allocate it more than 50 mb?

---

### Post by darco on 2009-10-20
I am currently running KK on a partition w/NO swap and I have not seen any performance loss. I have 8gigs of memory. I also noticed when running VMWare WS, it no longer goes into suspend mode which I always wanted it from doing but never figured out how....
I am on a pc so hibernate/suspend wouldnt work anyways

darco

---

### Post by slakkie on 2009-10-20
I don't have a separate /boot partition I do have:

/ (20GB)
/var/log (300MB)
/opt (2GB)
/home (50+GB)
swap (500MB)

I could shrink my root to about 10GB I guess and give /home some more, and perhaps increase swap to 1GB.

---

### Post by dabl on 2009-10-20
> **SeanBlader said:**
> 

I just gave up on using swap since I also never end up using enough ram (4 gb total) to bother. So I figured safer to skip a swap partition on the SSD.



I'd say that's the wrong reason to omit a swap partition.  If you ever wish to hibernate, aka Suspend-To-Disk, then that requires a swap partition of at least ~1.5GB (i.e. the size of everything running plus a bit of overhead, at the moment you wish to hibernate it).

As far as a /boot partition, it's only needed to boot XFS, Reiser4, and other "exotic" filesystems.  No need for it for ext3/ext4, JFS, or reiserfs.

---

### Post by kansasnoob on 2009-10-20
Having no swap space at all screws up initramfs and you will have boot problems, whether it's just slow boot, or inability to boot after a kernel upgrade.

Don't believe me? Try it and see.

---

### Post by darco on 2009-10-20
> **kansasnoob said:**
> Having no swap space at all screws up initramfs and you will have boot problems, whether it's just slow boot, or inability to boot after a kernel upgrade.

Don't believe me? Try it and see.

Strange, I have had no initramfs or any of those problems you mentioned....Like I said above, I see no performance loss w/o a swap partition.

free -m
             total       used       free     shared    buffers     cached
Mem:          7934       1056       6877          0         36        575
-/+ buffers/cache:        444       7489
Swap:            0          0          0

---

### Post by SeanBlader on 2009-10-20
> Don't believe me? Try it and see.
I don't believe you. Check out my [bootchart]("http://home.pacbell.net/spintec1/misc/ilum-jaunty-20091019-1.png").

I haven't had a swap partition since I installed Jaunty, and it rarely takes longer than 15 seconds to from Grub to GDM on my relatively slow 1.4ghz system. Never had any problem booting after a kernel update either. Something in your initramfs strategy seems to have gone horribly right on this system I suppose. Ironic that a default install wouldn't setup a swap partition when it sets up a single partition for the whole drive. Any idea where the missing swap strategy fits in there?

And let me put it this way, I never want to hibernate, or suspend to disk. That would just shorten the lifetime of my SSD, as would writing temp data to it. And last I heard the recommendation if you want to hibernate is at least as much space as your system contains in RAM. Well I don't want to waste 4 gigs of SSD space for a partition that system monitor reports is NEVER used. I don't understand why you'd want to hibernate when the system starts up in less than 20 seconds. I'd say that I'd occasionally like to suspend to ram, but with 3+ hours of battery life, I usually just close the lid leave it running and go where I need to use it. I've left it running for the half hour commute home a number of times, isn't that why we invented batteries?

But come Karmic I'll merge / and /boot again into a single partition. Thanks Slakkie and Darco. Slakkie you could definitely decrease the size of your / partition, I only gave it 9gb and could probably drop it to 7 easily enough. Your mileage may vary though based on the number of installed applications and packages you have.

---

### Post by kansasnoob on 2009-10-20
Do as you wish but I can guarantee you that this statement is nonsense:

> Ironic that a default install wouldn't setup a swap partition when it sets up a single partition for the whole drive.

A "default" install always creates a swap partition!

---

### Post by SeanBlader on 2009-10-20
Fair enough, I've never let a default install happen on my systems.

So thank you for coming to the forums with an open mind and being helpful. Oh wait.

---

### Post by donniezazen on 2009-10-20
What partition is read and write by both Ubuntu and Windows? I know fat is one of them but i have heard it is slow and not reliable.

SK

---

### Post by kansasnoob on 2009-10-20
> **soham_1207 said:**
> What partition is read and write by both Ubuntu and Windows? I know fat is one of them but i have heard it is slow and not reliable.

SK

Win XP onward and all modern Linux can handle ntfs. In Ubuntu just add either ntfsprogs or ntfs-config.

---

