---
title: "Partioning the drive"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by kwandtke on 2008-01-28
I'm getting ready to build a decent Ubuntu box.  I've been playing around on an old PC and like what I find enuf that I plan on taking my fairly new Dell and making it better by dumping (sorta) XP and moving to Linux.

Now i'm pretty experienced in the Windows world .. and I've always followed the practice of partitioning a drive into an OS and a data section .. that way I could upgrade or do whatever to the OS without  worrying about my data.  

I have a nice 300g drive I've picked up for this adventure so I plan on setting up a Windows partition (wife needs a security blanket) of say  12g ...then an NTFS partition for data ... then ... The rest of the drive Linux can have.  So the question is  does it make sense to split that install up the same way to allow for a future install of the OS while leaving  the data area intake? If so ... how much space should I set aside for the Linux OS area?

---

### Post by imtheguru on 2008-01-28
> I've always followed the practice of partitioning a drive into an OS and a data sectionLinux likes this practice. [[http://tldp.org/HOWTO/Partition/requirements.html#AEN493]](http://tldp.org/HOWTO/Partition/requirements.html#AEN493])

For non-server systems:
/boot  : 32 MiB to 100 MiB
/     : 6 to 8gigs. Install two of everything and you still wont pass 5gigs.
swap  : 512MiB to 2GiB
/home  : (the rest)

Servers which host data might want to assign a partition for /var. Development servers which contain a lot of program code might want to further allocate a partition for /usr and /opt

Cheers.

---

### Post by Shootfast on 2008-01-28
Partitioning the drive like that should be fine. all my Ubuntu installs sit quite happily on 30gb. If you did want to separate the install for data integrity, the best way to do it would probably be:


[WINDOWS NTFS]  [DATA NTFS]  [UBUNTU HOME EXT3] [EXTENDED [MAIN UBUNTU EXT3] [SWAP]]

That way, you keep your settings and personal files on a separate partition if you want to reinstall, or change distro's.

---

