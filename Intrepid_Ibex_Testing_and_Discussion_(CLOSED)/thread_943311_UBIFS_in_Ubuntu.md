---
title: "UBIFS in Ubuntu?"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ub1476 on 2008-10-10
Kernel 2.6.27 has now been released, and I see it has support for a filesystem called UBIFS, which is for pure, flash-based storage. I have a Samsung 64GB SSD and I wonder if I should install UBIFS on it as a filesystem? Is it available from the partition screen when you install Ubuntu?

---

### Post by lithorus on 2008-10-10
> **Ub1476 said:**
> Kernel 2.6.27 has now been released, and I see it has support for a filesystem called UBIFS, which is for pure, flash-based storage. I have a Samsung 64GB SSD and I wonder if I should install UBIFS on it as a filesystem? Is it available from the partition screen when you install Ubuntu?

It will do you no good anyway. From [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)
> UBIFS is a new filesystem designed to work with flash devices, developed by Nokia with help of the University of Szeged. It's important to understand that UBIFS is very different to any traditional filesystem: UBIFS does not work with block based devices, but pure flash based devices, handled by the MTD subsystem in Linux. Hence, **UBIFS does not work with what many people considers flash devices like flash-based hard drives, SD cards, USB sticks, etc**; because those devices use a block device emulation layer called FTL (Flash Translation Layer) that make they look like traditional block-based storage devices to the outside world. UBIFS instead is designed to work with flash devices that do not have a block device emulation layer and that are handled by the MTD subsystem and present themselves to userspace as MTD devices.

---

### Post by ShirishAg75 on 2008-10-10
any examples for what these devices would be for which UBIFS has been invented?

---

### Post by Ub1476 on 2008-10-10
Oh, well thanks for the info. :)

Does anyone know if Intrepid support a filesystem which might be preffered for SSD? I currently use EXT2 since it's a non-journaling system, but it's very outdated..

---

### Post by solitaire on 2008-10-10
Their is always 'JFFS2' file system.

UBIFS looks very interesting, pity their are not many compatible SSD's 'in the wild' at the moment, so it might be a while before anyone here uses it as a file system. :(

---

### Post by jdong on 2008-10-10
> **ShirishAg75 said:**
> any examples for what these devices would be for which UBIFS has been invented?

MTD block devices such as the built-in flash partitions on many embedded devices (routers, PDAs, etc)

They are not for SSD devices that you buy that bridge directly into USB mass storage or some other subsystem -- those onboard already have a lot of the wear-leveling features and such you'd expect from a flash-based filesystem.

The same applies for JFFS2 -- UBIFS  is more of a new/improved drop-in for JFFS2

---

### Post by Ub1476 on 2008-10-13
So in simple words SSD made for laptops does not work with UBIFS. I wonder when a good filesystem for SSDs will come out..

---

### Post by jdong on 2008-10-13
> **Ub1476 said:**
> So in simple words SSD made for laptops does not work with UBIFS. I wonder when a good filesystem for SSDs will come out..
SSDs exposed over traditional storage busses have built in firmware that makes them designed to be used like any other storage device. they do not need a specialized filesystem.

---

### Post by Ub1476 on 2008-10-13
Oh, I didn't know that. Thank you :)

Does this mean that using Ext3 or maybe even Ext4 (and disable journaling) would be a good move?

---

### Post by zekopeko on 2008-10-13
is see no problem with putting ext3 on a SSD disk. they already have firmware that takes into account the level of wear&tear so your data get distributed across the whole hard drive. not to mention that modern SSD disks have a lifetime of (single digit here) million writes/reads and it would take you YEARS to demolish it's capability to store data. worst case scenario would be that the SSD firmware would mark sectors that are no longer good and you would lose some space.

---

### Post by jdong on 2008-10-13
> **Ub1476 said:**
> Oh, I didn't know that. Thank you :)

Does this mean that using Ext3 or maybe even Ext4 (and disable journaling) would be a good move?

You shouldn't disable journaling -- SSDs don't offer any extra data integrity protection compared to traditional storage media. Also, you should avoid external journaling devices as I've yet to see one setup that doesn't result in a higher risk of out-of-order hazards.

Just use it normally like any other device.

---

### Post by bigbear2350 on 2008-10-15
Yeah they do
On a crash a hard disk head can scribble garbage all over the Inode tables (rare)

SSDs will proably just corrupt the Inode being written too on a crash.

---

### Post by jdong on 2008-10-15
> **bigbear2350 said:**
> Yeah they do
On a crash a hard disk head can scribble garbage all over the Inode tables (rare)

SSDs will proably just corrupt the Inode being written too on a crash.

Both claims are completely unsubstantiated. If mechanical hard disks are vulnerable to brownout garbage then SSDs are as well. I don't know if either is, to be honest, but I surely hope they both take protective measures against this common failure scenario.

EDIT: Furthermore, what does scribbling garbage and single point corruption / incomplete write have to do with journaling at all? Journaling does not offer protection against the "scribbled garbage" scenario you gave. It offers fast metadata consistency restoration on the "single inode operation wasn't completed" case. In short you are screwed if the disk gets scribbled on blackout.

---

### Post by bigbear2350 on 2008-10-15
oh i misread the page this page. [http://zork.net/~nick/mail/why-reiserfs-is-teh-sukc](http://zork.net/~nick/mail/why-reiserfs-is-teh-sukc)

> You see, when you yank the power cord out of the wall, not all parts
of the computer stop functioning at the same time.  As the voltage
starts dropping on the +5 and +12 volt rails, certain parts of the
system may last longer than other parts.  For example, the DMA
controller, hard drive controller, and hard drive unit may continue
functioning for several hundred of milliseconds long after the DIMM's,
which are very voltage sensitive, have gone crazy and are returning
total random garbage.  If this happens while the filesystem is writing
critical sections of the filesystem metadata, well, you get the visit
the fun web pages at [http://You.Lose.Hard](http://You.Lose.Hard).

I was actually told about this by an XFS engineer, who discovered this
the hardware.  Their solution was to add a power fail interrupt and
bigger capacitors in the power supplies in SGI hardware, and in Irix,
when the power fail interrupt triggers, the first thing the OS does is
to run around frantically aborting IO transfers to the disk.
Unfortunately, PC-class hardware doesn't have power fail interrupts.
Remember, PC-class hardware is cr*p.

Why doesn't ext3 get hit by this?  Well, because ext3 does physical
block journalling.  This means that we write the entire physical block
to the journal and, only have the updates to the journal are commited,
do we write the data to the final location on disk.  So if you yank
out the power cord, and inode tables get trashed, they will get
restored when the journal gets replayed.


---

### Post by jdong on 2008-10-15
Ok, that is a different matter -- implementation of journaling strategies. ext3 is a bit more redundant in its journaling on-disk format compared to XFS, reiserfs, and other integrated-journal filesystems but this has nothing to do with journaling itself.

Furthermore, the purpose of journaling is NOT just for this corner-case of brownout-disk-writes. It also is able to protect against abrupt-poweroff inconsistencies that fsck cannot piece together after the fact on a non journaled filesystem -- this is even true on solid state media (see Soft Updates for asynchronous non-journaled filesystem implementations that also provide this integrity guarantee)

---

### Post by jdong on 2008-10-15
I should also add that since then the default journaling method has been switched to ordered metadata-only, so your actual data blocks are not protected by this guarantee, nor does ext3 perform journal-checksumming so that if you turn on journaling of full-data "garbage blocks" don't get blindly copied back.


Which goes back to point 1: If you expect your disk to be spewing garbage on brownouts, you're screwed.

---

