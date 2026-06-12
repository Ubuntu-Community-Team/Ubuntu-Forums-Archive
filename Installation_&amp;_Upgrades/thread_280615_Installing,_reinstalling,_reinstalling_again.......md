---
title: "Installing, reinstalling, reinstalling again......"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by Praxidike on 2006-10-19
Is there a way to copy the entire contents of the hard drive once I have installed everything as I want it, then if it messes up (or I mess it up, more likely), just delete the hard drive and replace it with the backup from a different hard drive?

(As you can probably see, I'm a Windows convert so used to reinstalling everything ;) )

I'm just getting used to Linux, slowly.

Thanks

---

### Post by h4rdwire on 2006-10-19
Raid...Lol...

On a windows system ? Ghost it.

---

### Post by gn2 on 2006-10-19
> **Praxidike said:**
> Is there a way to copy the entire contents of the hard drive once I have installed everything as I want it, then if it messes up (or I mess it up, more likely), just delete the hard drive and replace it with the backup from a different hard drive?

(As you can probably see, I'm a Windows convert so used to reinstalling everything ;) )

I'm just getting used to Linux, slowly.

Thanks

This command is for copying an entire Linux hard drive hda to new hard drive hdb: 

**dd if=/dev/hda of=/dev/hdb**

If there are NTFS partitions on the drive you would be best to clone it with Acronis True Image.

---

### Post by Praxidike on 2006-10-19
> **gn2 said:**
> This command is for copying an entire hard drive hda to new hard drive hdb: 

**dd if=/dev/hda of=/dev/hdb**
So if I do that, then to restore, do I just do the same thing again, but swap a and b around?

(There's no NTFS partition, at least I don't think so - Linux is the only OS on this PC at the moment (going to run XP in VMware though, hopefully that won't interfere...)

---

### Post by gn2 on 2006-10-19
> **Praxidike said:**
> So if I do that, then to restore, do I just do the same thing again, but swap a and b around?


Not entirely sure if the drive to be copied to has to be empty first....

I've been using Ubuntu on my laptop every day for the last six months and haven't needed to do any re-installs or had stability issues of any kind whatsoever.

It's definitely not Windows....

---

### Post by lloyd_b on 2006-10-19
> This command is for copying an entire Linux hard drive hda to new hard drive hdb:

dd if=/dev/hda of=/dev/hdb

This is extremely dangerous.  "dd" commands to /dev/hd... entries have the potential to do a lot of damage.

Another point is that doing this while the partition/drive you're copying is mounted can easily lead to a corrupt copy (for instance, what if it's copying a directory while another program is creating files in that directory!).

Personally, I'd consider the idea of a "backup drive" to be a waste of disk space (unless the install process was particularly difficult on that machine).  But then, they're your disks...

If you insist on having such a backup drive, I'd suggest installing a copy of Ubuntu on BOTH drives, then set "grub" so that you can easily boot to either one.  From that point, it's a matter of a simple "tar" command to make a backup of one drive onto the other.

Lloyd B.

---

### Post by Praxidike on 2006-10-20
Ah, I'll just have to hope it doesn't mess up then!  By the sounds of it, it shouldn't go wrong as often as Windows anyway, it's just a bit of a pain reinstalling (already done it a couple of times while playing around with it, takes forever having to redownload things!)

Thanks anyway. :)

---

