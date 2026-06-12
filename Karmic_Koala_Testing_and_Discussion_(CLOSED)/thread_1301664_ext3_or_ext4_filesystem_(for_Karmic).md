---
title: "ext3 or ext4 filesystem (for Karmic)?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by viking_maniac on 2009-10-26
What's the difference between the two and what is actually recommended? Are there any pros and cons with any over the other?

---

### Post by The Cog on 2009-10-26
ext4 is newer of course. It can handle larger directories and files, although ext3s limits are way beyond what you are likely to encounter in normal usage so this difference is largely academic. ext4 is supposed to be faster.

There was talk a while ago about ext4 being able to lose contents under certain circumstances, and maybe 6 months ago (upgrading to Jaunty) I did suffer disk corruption and data loss on an ext4 partition, along with an OS crash. Which was cause and which was effect, I can't be sure. But I did have to reinstall after the second crash because of the mess the disk was in. I gather ext4 has been improved since then, and I have used it for several hours now without mishap. Since it is now the default filesystem, I guess the Ubuntu admins feel it is now trustworthy. I think I will change to ext4 when I upgrade all my PCs to Karmic.

---

### Post by anaconda on 2009-10-26
if you need to be able to access the drive from windows, then ext3 is better.

also in a rare case if you need to recover data from your drive ext3 is older, and so the data recovery programs are better for it.

---

### Post by The Cog on 2009-10-28
> **anaconda said:**
> if you need to be able to access the drive from windows, then ext3 is better.

I'm pretty sure I read somewhere that the windows ext3 drivers don't support recent ext3 changes - the number of inodes, the block size or something like that. I don't remember exactly what the problem was, but I do remember thinking it meant that the windows drivers no longer of any use.

---

### Post by flipper9 on 2009-10-28
You can listen to the fear mongering about ext4, change the default from ext4 to ext3 during setup, and live with the slower performance of ext3.  It's your choice.

---

### Post by Onesimus on 2009-10-28
I am surprised a new thread was started on this.  This has been endlessly discussed in the forums.  Ext4 is the default in Karmic because it is now stable.

---

### Post by flipper9 on 2009-10-28
And if you are so worried that ext4 is so unstable, then why are you running Karmic at either the RC or recently released stage?  I think you'd be worried about the whole system being unstable.  If you really cared about perfect stability, you'd be running an older version of Ubuntu.

---

### Post by humphreybc on 2009-10-28
ext4 is fine, it's completely stable. There is no point using ext3 now.

---

### Post by flipper9 on 2009-10-28
Ext4 Pros: faster, supports more directories, etc.
Ext Cons: if you listen to fear mongering on the internets, you might worry yourself into a tizzy.  Not supported by Windows 3rd party drivers and possibly older disk tools (why would someone use an outdated OSS disk tool???)

Ext3 Pros: supported by Windows 3rd party drivers for read/write access. More stable for the tinfoil hat crowd or those that believe old postings on the internets
Ext3 Cons: slower than the new Ext4 format, limits in several areas.

---

### Post by grandtoubab on 2009-10-28
> **flipper9 said:**
> Ext4 Pros: faster, supports more directories, etc.
Ext Cons: if you listen to fear mongering on the internets, you might worry yourself into a tizzy.  Not supported by Windows 3rd party drivers and possibly older disk tools (why would someone use an outdated OSS disk tool???)

Ext3 Pros: supported by Windows 3rd party drivers for read/write access. More stable for the tinfoil hat crowd or those that believe old postings on the internets
Ext3 Cons: slower than the new Ext4 format, limits in several areas.


And Ext4 needs GRUB2 but if you upgrade from 09.04 you keep Ext3 and Grub-Legacy. Thats is my configuration and Karmic is OK like that. My files. some movies and mp3 really don't need Ext4:lolflag:

---

### Post by viking_maniac on 2009-10-28
Okay, thanks for the feedback!

The only thing that worries me with ext4, because I'll use a lot of very important data in Karmic, is that ext4 is more likely to corrupt or loose files/data during system crash, power loss or accidental hard booting; compared to ext3.

> **Delayed allocation and potential data loss**

Delayed allocation poses some additional risk of data loss in cases where the system crashes before all of the data has been written to the disk.

The typical scenario in which this might occur is a program replacing the contents of a file without forcing a write to the disk with fsync. Problems can arise if the system crashes before the actual write occurs. In this situation, users of ext3 have come to expect that the disk will hold either the old version or the new version of the file following the crash. However, the ext4 code in the Linux kernel version 2.6.28 will often clear the contents of the file before the crash, but never write the new version, thus losing the contents of the file entirely.

Altering this behavior by using fsync more often could lead to severe performance penalties on ext3 filesystems mounted with the data=ordered flag (the default on most Linux distributions). Given that both file-systems will be in use for some time, this complicates matters enormously for end-user application developers. In response, Theodore Ts'o has written some patches for ext4 that cause it to limit its delayed allocation in these common cases. For a small cost in performance, this will significantly increase the chance that either version of the file will survive the crash.

The new patches are expected to become part of the mainline kernel 2.6.30. Various distributions may choose to backport them to 2.6.28 or 2.6.29, for instance Ubuntu made them part of the 2.6.28 kernel in version 9.04—Jaunty Jackalope.[9]

[http://en.wikipedia.org/wiki/Ext4#Disadvantages](http://en.wikipedia.org/wiki/Ext4#Disadvantages)


Or am I mistaking?

---

### Post by dabl on 2009-10-28
> The new patches are expected to become part of the mainline kernel 2.6.30.


I think you're worried about old news -- which kernel do you think comes with Karmic?  ;)

---

### Post by cor2y on 2009-10-28
Keep Ext3 if you need to access your linux home partition in windows, while it is possible to access an Ext4 partition in read mode  using one of the Ext3 third party windows apps this will result in disc corruption/errors that will have to be repaired (it does it automatically) the next time you boot to ubuntu.

---

### Post by whoop on 2009-10-28
> **grandtoubab said:**
> And Ext4 needs GRUB2 but if you upgrade from 09.04 you keep Ext3 and Grub-Legacy. Thats is my configuration and Karmic is OK like that. My files. some movies and mp3 really don't need Ext4:lolflag:

Ext4 needs grub2? I don't think so... btrfs /, yes. But ext4...

---

### Post by rajeev1204 on 2009-10-28
Just remember one thing,if you dont have a karmic live cd in case of a crash, you can forget about recovering your ext4 partition as the older live cd's do not recognise it and wont mount it.

I learned this truth the hard way.

---

### Post by philinux on 2009-10-28
> **rajeev1204 said:**
> Just remember one thing,if you dont have a karmic live cd in case of a crash, you can forget about recovering your ext4 partition as the older live cd's do not recognise it and wont mount it.

I learned this truth the hard way.

+1 many times.

---

### Post by flipper9 on 2009-10-28
> **rajeev1204 said:**
> Just remember one thing,if you dont have a karmic live cd in case of a crash, you can forget about recovering your ext4 partition as the older live cd's do not recognise it and wont mount it.

I learned this truth the hard way.

So maybe make one to do the install and keep it handy?  Prevention is the best prescription for this problem.  Or just find another computer and make one...it's pretty easy with CDROM/DVD/USB options.

---

### Post by flipper9 on 2009-10-28
> **grandtoubab said:**
> And Ext4 needs GRUB2 but if you upgrade from 09.04 you keep Ext3 and Grub-Legacy. Thats is my configuration and Karmic is OK like that. My files. some movies and mp3 really don't need Ext4:lolflag:
You could have used EXT4 in Jaunty, and I don't believe you didn't need Grub2 for that.

---

### Post by jeffus_il on 2009-10-28
ext4 has many improvements on ext3, see:
[http://kernelnewbies.org/Ext4]("http://kernelnewbies.org/Ext4")

I have been using it for a few months without a problem.

I would never be without a current livecd or usb stick

---

### Post by psyke83 on 2009-10-28
> **viking_maniac said:**
> 
The only thing that worries me with ext4, because I'll use a lot of very important data in Karmic, is that ext4 is more likely to corrupt or loose files/data during system crash, power loss or accidental hard booting; compared to ext3.

Or am I mistaking?

Yes, you are [mistaken] - the information you're quoting is outdated. Look at the kernel versions mentioned; Karmic is based on kernel 2.6.31, and the specific data loss issues in EXT4 have been resolved.

---

### Post by iamnotthemessiah on 2009-10-28
used ext4 with no probs in jaunty so see no reason to go back to ext3

---

### Post by sdowney717 on 2009-10-28
i noticed a speed boost
and been using it since alpha 6 karmic with no trouble.

---

### Post by Zoot7 on 2009-10-28
I've been using ext4 for both my home partition and the system partition with Jaunty for about 3 months now, no problems whatsoever. :)

The main difference I notice with ext4 is that fsck is a LOT faster than it was with ext3.

---

### Post by Piscium on 2009-10-28
Same with me. I have Jaunty and have been using ext4 for home and root for about 3 months without problem. 

I have also been using grub 2. By and large I am happy. There is one of my partitions where it can find two out of four kernel versions, not sure why (it does not see the two most recent versions). But as I can get to that partition via BIOS (with F12) it does not really affect me.

---

### Post by ezsit on 2009-10-28
> Ext3 Pros: supported by Windows 3rd party drivers for read/write access. More stable for the tinfoil hat crowd or those that believe old postings on the internets
Ext3 Cons: slower than the new Ext4 format, limits in several areas.

Have you actually checked the list of advantages in ext4? If you do, all of the advantages are purely academic for the majority of home users. If you are running a server or storage farm, then ext4 has some major advantages, but for most intents and purposes, ext3 is more than capable for home use.

If you are building a system with an eye toward the future, ext3 or ext4 are fine, especially since many people are waiting for btrfs anyhow and will switch to that as soon as its available. Ext4 is merely a stopgap measure until btrfs becomes stable.

---

### Post by dabl on 2009-10-28
> **ezsit said:**
> 

 ext3 is more than capable for home use.



Right.  For example, its extremely slow periodic fsck on boot gives you _way_ more time to sit and stare at the little line of blinky dots on the black screen, wondering when it will ever end, whereas ext4 just flies through fsck so fast that you won't even have time to go get a cup of coffee ...


:D

---

### Post by ezsit on 2009-10-28
> its extremely slow periodic fsck on boot 

Wow, I never noticed. I reboot my desktop about once a week, so I get that slow (about 20 seconds for my drive) fsck once every 30 weeks or so. I can't say that 20 seconds every 30 weeks has made much of a difference in my life. I think I've wasted more time peeing. ;-)

---

### Post by jeffus_il on 2009-10-29
> **ezsit said:**
> Have you actually checked the list of advantages in ext4? If you do, all of the advantages are purely academic for the majority of home users. If you are running a server or storage farm, then ext4 has some major advantages, but for most intents and purposes, ext3 is more than capable for home use.

If you are building a system with an eye toward the future, ext3 or ext4 are fine, especially since many people are waiting for btrfs anyhow and will switch to that as soon as its available. Ext4 is merely a stopgap measure until btrfs becomes stable.

Here are the advantages, they are impressive.
[http://kernelnewbies.org/Ext4]("http://kernelnewbies.org/Ext4")

"Multiblock allocation" and "Fast fsck" are not academic.

---

### Post by jeffus_il on 2009-10-29
> **ezsit said:**
> Wow, I never noticed. I reboot my desktop about once a week, so I get that slow (about 20 seconds for my drive) fsck once every 30 weeks or so. I can't say that 20 seconds every 30 weeks has made much of a difference in my life. I think I've wasted more time peeing. ;-)

Peeing is not a waste of time,
You need to make room for beer.

---

