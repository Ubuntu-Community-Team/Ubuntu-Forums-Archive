---
title: "Feasibility of Ubuntu on USB stick (Not the live CD)"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by ItsJweed on 2008-10-30
Hey,

I would really like to actually **install** linux on a flash drive rather than just have the live cd bootable from a flash drive. I know that flash drives have a limited number of writes so I wasn't planning on having a swap partition on the drive. (Most computers I would boot it from would already have a swap partition anyway.) I also understand that with file system journaling I could use up the 10,000 writes fairly quickly. 

I have four questions.

[LIST=1]
[*]If I use fat32 on the drive so there is no journaling, wouldn't I avoid burning out my drive in a short period of time?
[*]What size drive minimum would I need? I've heard ubuntu needs 2.3 gigs so I'm guessing a 4 gig drive would cut it?
[*]I know that some types of memory have to be re-written every time they are read. Are flash drives like this?
[*]Is there any other reason I haven't thought of that would make this a bad idea or otherwise unreasonable/infeasible?
[/LIST]

Thanks,

J

---

### Post by snowpine on 2008-10-30
A full install to USB stick works very well. The only slightly tricky part is when you get to the final step of the installer, you need to click Advanced and make sure Grub is written to the flash drive and not your computer's internal hard drive! I would not be too concerned about wearing out the flash media, what with the extremely low price of a 4gb stick (the minimum I would recommend) these days.

---

### Post by C.S.Cameron on 2008-10-30
I agree with snowpine.
I have been using a full install to one flash drive for over a year.
I find it much better than a persistent install, It is just like booting from hard disk, and not much slower if you format "/" and "/home" partitions as reiserfs.

---

### Post by the.weavster on 2008-10-31
Can I put a live Ubuntu CD in the CD drive of my laptop, a USB stick in the USB port and do an install from one to the other?

And once I've done that I'll be able to boot my laptop from the USB stick?

---

### Post by snowpine on 2008-10-31
> **the.weavster said:**
> Can I put a live Ubuntu CD in the CD drive of my laptop, a USB stick in the USB port and do an install from one to the other?

And once I've done that I'll be able to boot my laptop from the USB stick?

Yes, exactly. But as I mentioned in my previous post, make sure to install Grub to the USB stick, not your hard drive.

I also recommend not putting a swap partition on the USB stick, if your computer has enough RAM that you can do without (or an existing swap partition on your hard drive).

Good luck!

---

### Post by the.weavster on 2008-10-31
That's cool!

Thanks alot, I'm off to get a new USB stick.:)

---

### Post by meganox on 2008-10-31
Don't use FAT!  Use ext2, it's a proper Linux filesystem but without journaling.

---

### Post by ItsJweed on 2008-11-02
> **meganox said:**
> Don't use FAT!  Use ext2, it's a proper Linux filesystem but without journaling.

I was thinking about that but I wasn't sure if my computer would be able to boot from the device if it couldn't read the file system. Thinking about it now though, the computer would boot into the grub bootloader on the flash-drive and it is grub that would support reading from the ext2 file system, no?

---

### Post by C.S.Cameron on 2008-11-02
I have been doing manual partitioning, formating "/" and "/home" partitions using the reiserfs file system.
This seems to help the speed running from a flash drive.

---

### Post by blazercist on 2008-11-02
What about the limited write/read cycles on flash media? Don't you need to be worried the drive will fail with regular use?

---

### Post by ItsJweed on 2008-11-21
> **blazercist said:**
> What about the limited write/read cycles on flash media? Don't you need to be worried the drive will fail with regular use?

Without swap on the device, and with a non-journaling file system it shouldn't be much of an issue. Even if it does ultimately cause the drive to fail, they are extremely cheap nowadays.

---

