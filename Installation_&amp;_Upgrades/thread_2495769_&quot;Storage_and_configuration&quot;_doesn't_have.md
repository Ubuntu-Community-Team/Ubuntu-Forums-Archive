---
title: "&quot;Storage and configuration&quot; doesn't have green &quot;Done&quot;"
date: 2024-02-29
forum: Installation &amp; Upgrades
---

### Post by rustytravis on 2024-02-29
Greetings, I'm trying to install 22.04 Server on a laptop with an nvme ssd with 2 partitions. I select the partition, mount it at "/", and everything seems right, but the "Done" selection at the bottom doesn't turn green so that I can select it. I have been trying for over 6 hours, and come to you for help, please?

I'd really like to install this operating system.

---

### Post by TheFu on 2024-02-29
When you do custom partitioning, you are expected to create ALL NECESSARY PARTITIONS, set the flags, and choose the correct file system types for each. If you don't know what those required partitions are, you'll never manually be able to accomplish it.

So, do a default install with default partitioning.  Note all the partitions that get created and all the flags and types assigned to them using **parted**.  Then you can manually create them in the next install, sized how you like.

About 4 yrs ago, maybe 7 yrs ago, I stopped using the partitioning screens in the Ubuntu installers. They are simply too cumbersome to create partitions. When the installer gets to the disk setup part, I toggle to a different tty and use scp to copy over my partitioning and LVM setup script.  On the to-be-installed system, I modify that script for the specifics of the allocations I want and create all the partitions, PVs, VGs, and LVs, sized as I like.  Generally, it isn't worth formatting them, since the Ubuntu Installers will demand to format some, regardless of the current state.

I've posted my server disk setups here a few times.  Look for 20.04 and lsblk output from my userid here.  Since I use LVM, I don't need to be too accurate with initial sizing. Best to start small since LVM makes expanding storage + ext4 file systems about 5 seconds of effort, while the system keeps running.

---

### Post by rustytravis on 2024-02-29
> **TheFu said:**
> When you do custom partitioning, you are expected to create ALL NECESSARY PARTITIONS, set the flags, and choose the correct file system types for each. ... 
The two available partitions are already formatted as ext4. The selected 2TB partition is mounted as "/".

> **TheFu said:**
> So, do a default install with default partitioning.  Won't that destroy data in partition 2?

---

### Post by TheFu on 2024-02-29
> **rustytravis said:**
> The two available partitions are already formatted as ext4. The selected 2TB partition is mounted as "/".

Won't that destroy data in partition 2?

Before installing any new OS, a backup is required.  If you don't want any data loss, having backups is mandatory, never optional.  If you install a "server" OS, this is expected, basic, knowledge.

---

### Post by rustytravis on 2024-03-06
So Ubuntu won't let one install onto the partition of choice?

---

### Post by TheFu on 2024-03-06
> **rustytravis said:**
> So Ubuntu won't let one install onto the partition of choice?

A typical install requires at least 2, if not more, partitions.  These partitions must be of the correct type and have the correct file system type(s).  The best way I know to get the information for what is required on your specific system is to allow the automatic installer to wipe a disk, create the required partitions, then you need to ensure your manual partitioning and formatting and selected mounts for those partitions match the minimal requirements.

There are different partition types depending on UEFI/Legacy BIOS and which type of partition table the system storage has.  There are other dependencies if you choose different file systems or volume management or encryption.  It gets complicated.

When you have things setup correctly and the specific partitions connected to the correct/allowed file system types and mounted to the allowed/required locations, then the installer will let you move forward.

I've posted my partitions and storage choices many times in the last few years. You can use those for reference, assuming you want to follow the way I do it. Otherwise, you can find someone else's or figure out what's required on your own.  

I haven't said anything new here. Maybe I put things clearer?  IDK.

---

