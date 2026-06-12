---
title: "Ubuntu dual-boot on a HP Laptop"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by thehipporiff on 2007-03-07
I'm thinking of running a dual-boot with Ubuntu and XP on a HP laptop I bought here in Korea. 

My question is about GRUB mainly, but also about the partitioning tools that Ubuntu uses.

On the GRUB side, I always had problems with the GRUB that, for example, Fedora Core 2 and 3 packaged. I think it's a reasonably common problem, to do with designating mount points, or something, but I always ended up not being able to resolve it, despite lots of trying things from forums, and even enlisting a Linux-savy friend. It might even have been something more serious than mislabelled mounts, masquerading as an innocuous issue, I cant remember.
It wouldn't be a big deal, but I don't have all of the recovery software for my laptop. It's difficult to mime "Is there a recovery disc included? I might want to install Linux" to the Korean staff, and my Korean isn't up to computer-speak.
So, if GRUB cant load to Windows I lose access without being able to just scratch it and reinstall. Linux is great, but there are some things Windows has more support for. So, the dual-boot is the desirable option.
So, the question would be, has anything changed with this GRUB issue since whenever it was fedora 2 and 3 and their ilk were kicking around, and if not, is there something really obvious I missed trying to resolve the problem the last time around? The prospect of trying to resolve the issue again isn't appealing.

The other question is about gpart. Is it a non-destructive partitioning tool? I'd need to create the linux partitions from my existing NTFS data drive. So, I'd want to keep the information on there intact, and maybe convert it to FAT32 at the same time. Would that be possible, or would I need some other 3rd party partitioning tool to do that? I've checked the gpart site, and there wasn't anything I could find that explicitly mentioned it being non-destructive.

Thanks in advance.

---

### Post by Kateikyoushi on 2007-03-07
If you check the disc before resizing and defragment it few times it should be fine, but some people lost data probably missed those steps or had a bad drive to begin with. You can restore mbr from freedos cd for example to remove grub. As for me it picked up vista on the disk and added dualboot option to the menu automagically.

---

### Post by watson540 on 2007-03-08
dude, fc2 and fc3 were friggin aeons ago in linux years.

ya got nothing to worry about. grub always detects windows these days. they're quite drafty

---

