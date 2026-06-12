---
title: "Need to load 3ware 9650SE driver during install"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by kansberry on 2006-12-26
I am attempting to install Ubuntu Server on a system I build last week but can not figure out how to load drivers for the 3ware 9650SE RAID controller during install (would like to boot from the RAID). To this point, I have removed one of the SATA drives from the RAID and installed Ubuntu on it. I then downloaded the source of the 3ware drivers for kernel 2.6.17 (I believe this is the kernel version of server) and ran make. Once that had completed, I copied the files created to a floppy diskette, attached the driver back to the RAID and attempted to reinstall with this "driver" diskette. However, can not figure out how to load drivers. System continues to state that drivers could not be found on diskette.

What files extensions is the system looking for?
Do they need to be in a specific directory?
Are there command line arguments that I need to pass?

Any help would be appreciated. I am rather new to the whole Linux thing, but would like to learn more.

Thanks,
Kevin

---

### Post by SubWolf on 2007-01-17
I was just looking at a new server for our company, and the one I fancy has a 3Ware 9650SE controller. Their [driver page](http://www.3ware.com/support/OS-Support.asp) claims to support RH, SuSe, etc, but doesn't include the "2.6.x kernel supports" or "sources available" lines... worrysome.

Gonna call them at some point, but would love to know of any other experiences with this hardware and Ubuntu, as thats what I'd want to load on it.

---

### Post by supuntu on 2007-01-24
In my experience, 3ware provides excellent *nix support. Most recently, I installed Ubuntu Server 6.10 amd64 with a binary driver for a 9650 sent to me by 3ware support.

Simply send them a request for a compiled driver at [email]support1@amcc.com[/email] (found at this helpful knowledgebase article: [http://www.3ware.com/KB/article.aspx?id=14546](http://www.3ware.com/KB/article.aspx?id=14546)). 

Hope this helps.

---

### Post by pc-cito on 2008-01-28
Hi all

I'm with the same problem.

Hi have a RAID-5 (4x1 TB) and into BIOS all works fine, but when i try to install ubuntu server 7.10 it cannot see the drives.

3ware.com dont have support to ubuntu 7.10, only to 6.06 or 6.10.

Any idea??

---

### Post by dean123 on 2008-01-28
> **pc-cito said:**
> Hi all

I'm with the same problem.

Hi have a RAID-5 (4x1 TB) and into BIOS all works fine, but when i try to install ubuntu server 7.10 it cannot see the drives.

3ware.com dont have support to ubuntu 7.10, only to 6.06 or 6.10.

Any idea??


>>Hi have a RAID-5 (4x1 TB) 

You can't install linux/Ubuntu on 2TB+ array.  Use 3ware bios utility to create a small boot volume while creating the raid5 unit then install Ubuntu 7.10 on the boot volume. I had to do that with my big system.

---

### Post by pc-cito on 2008-01-29
You're right.

That's my current RAID config and linux filesystem:

sda -> boot
sdab+sdc -> raid 5

sda (5 GB) /boot (ext3, bootable flag)
sdb (2.72 TB) /home (ext3)
sdc1 (1.8 TB) / (ext3)
sdc2 (2 GB) swap

I know 5GB is too much to "boot partition"

I hope it works, it's only 5 hour to format diks :-\"

---

