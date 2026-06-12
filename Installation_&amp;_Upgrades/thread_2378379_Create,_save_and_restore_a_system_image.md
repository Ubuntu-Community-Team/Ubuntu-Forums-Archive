---
title: "Create, save and restore a system image"
date: 2017-11-22
forum: Installation &amp; Upgrades
---

### Post by dam034 on 2017-11-22
Dear users,

I have a LAN server hosted by a minipc.

Now it has ubuntu, and I want to create a system image preventing to reinstall the OS if I do mistakes.

I want to save the system image in another computer, and to restore that image if necessary.

Obviously I have all the computers in LAN, then I can use network feature.


How can I do?

Thanks

---

### Post by mastablasta on 2017-11-23
you mean while the system is running?

otherwise it is simple and there are a few options.
1. backup only what is needed (settings, user files...) and on restore, reinstall fresh system and apply the backups.
2. system image

for backup there are so many push (where data is pushed from clients to some backup server or drive) as well as a few pull options (where central server monitors and pulls the backups to a certain place). both have CLI as well as GUI options. depends what you want and need. have a look at this table: [https://en.wikipedia.org/wiki/List_of_backup_software](https://en.wikipedia.org/wiki/List_of_backup_software)

recomended clients - Areca, Duplicati, LuckyBackup, rdiff-backup
recomended server - backuppc

for system image clonezilla is a descent one and is updated regularly. it's interface is kind of lame and i think it needs work on the GUI and user experience. 
another i use is redobackup. while it has a very nice GUI interface, it is still using 12.04 as base. and i am not sure it will ever be updated. then again for older PC's that don't need latest drivers it will do just fine.

cloning software:
[https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software](https://en.wikipedia.org/wiki/Comparison_of_disk_cloning_software)

---

### Post by dam034 on 2017-11-23
> **mastablasta said:**
> you mean while the system is running?
No, also with system power off.

I want to create an image of all the ubuntu partitions mounting, and save onto a FTP server.

I can run a USB flask disk or CD on the pc to backup it, so I don't touch the OS I want to backup.

What you advice me?

Thanks

---

### Post by mastablasta on 2017-11-23
for the OS itself it is easiest to just back configs and settings and list any added programs, since Linux takes about 20-30 mins to reinstall & restore. this can be done with any clients side push backup service i mentioned. all you need to do is backup the right folders.

but if you have time you can also image the drive using clonezilla (for example after all is setup as you want it to be)

---

### Post by greyfaux01 on 2017-11-25
I can vouch for redobackup. Ive used it for years to backup/image my entire OS/filesystem in 1 swipe, but for the longest time ive never needed to actually do a restore. So i was always a little skeptical. Then recently, i was running out of HDD space, found an old HDD of a friends that was bigger, and i followed the very simple on screen instructions, and low and behold, the restore worked, in fact thats the computer im using right now.

I did have to reinstall grub though, but a simple run of disk-repair (or boot-repair-disk i think actually) from cd did all that for me, automatically. Redobackup does not have the fined grained options of say clonezilla, but for backing up entire partitions/hard drives, i personally love it. I put my backup on a terabyte external because it was like 150gb, but the os and all programs/data was around 300gb (i think).. so generally speaking it should compress it to around half the size of the entire system after backup.

That said i know you can do the same thing with clonezilla, but i find it interface/questions somewhat confusing, although thats my own lack of knowledge/experience. Redobackup is easy to use and stable. And yes it will probably never be updated, so that makes me sad.

---

### Post by kyknos12 on 2017-11-26
you can take a look at it my project System-Restore-Linux [https://bbs.archlinux.org/viewtopic.php?id=230438](https://bbs.archlinux.org/viewtopic.php?id=230438) 
I have been working for quite some time in backup-remaster some difference distributions, but I was looking for ways to work properly in the same way in any distribution, I did a lot of training but I did it, the restoring system will work and evolve to the choice piece for installation grub-efi or legacy possibility of choice and installation lvm, lvm encrypt from user, newer releases with new features will run with time

---

