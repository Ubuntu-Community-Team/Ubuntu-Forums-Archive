---
title: "Partioning and Raid advice"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by TheGreatSage on 2007-07-15
Hi There

I have posted this in the newbie section, but as there is a lot of activity in that forum, it quickly sunk into the abyss.


I have recently built a new pc. As I have a pair of NAS drives, I wasn’t interested in internal storage and just bought a 160g drive to run multiple opp systems.

A week later and after looking into raid 0 and raid 1 options, I have decided to at least buy another 160 g drive or a pair of drives around 300 GB and configuring RAID. I'm not yet sure how I want to go about partitioning my setup.

My current drive I split into 2 x 20 gig NTFS partitions for windows, 1 x 5 gig dos partition (c) and a 15 gig etx3 part for Ubuntu + 1 gig Linux swap. I’m not sure whether to go down the same road again with my new drives, or whether it would be best to keep windows and Linux on separate drives.

I am leaning towards keeping both opp systems on 1 drive and using the other drive for mirroring.

Anyone have any advice?

Thanks

---

### Post by kidders on 2007-07-16
Hi there,

Purely from a performance perspective, I would suggest two things...

**1: Keep mirroring to a minimum.**
Especially if you're planning on using more than two or three hard disks, your hardware might not like it if every single I/O operation takes up twice as much bandwidth as it's "supposed" to. Many modern motherboards tempt users to plug in lots and lots of storage devices, and set up things like elaborate RAID arrays, despite the fact that they're not very well equipped to handle all the I/O at the "up to [x] Mbps" rates they advertise.

[B]2: Avoid idle devices
[/B]This suggestion may seem almost contradictory to #1, but it's important to design a *certain* amount of parallel accessing into your partitioning scheme. For instance, a /usr, /lib and a swap filesystem will very often be accessed simultaneously by an OS, making it somewhat inadvisable to put them all on the same physical device, when you don't have to. Additionally, ensuring that many (ie maybe not *all*) your hard disks are doing at least *some* work, no matter which one of your OSs you're booted into, should help extend their lifespans.



So, for instance...[LIST]
[*]If you want to use RAID 1, consider mirroring /home only, rather than your entire system.
[*]If you're into memory-intensive stuff (multimedia editing, etc.), you might want to throw a couple of swap partitions onto devices not being used for anything else, so they can seek quickly.[/LIST]One other random suggestion: In my experience, many users seem intent on allocating *absolutely all* of their available hard disk space to some purpose, even if they don't intend to actually make use of it. It's amazing how handy a nice chunk of unallocated space can be when something bad happens, or you suddenly need to do something weird.

---

