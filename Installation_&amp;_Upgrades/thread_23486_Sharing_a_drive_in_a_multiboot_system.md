---
title: "Sharing a drive in a multiboot system"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by akshoslaa on 2005-04-02
Title pretty much says it all :P

I'm planning on multibooting my last remaining windows box (unfortunately can't do without one yet...) and have been looking at my options.

My current plan is:
My current 8gig hdd for windows (enough for xp and essential apps, with enough left to dump stuff to the desktop while I'm working on something... tends to be a good size)

Partitioning my 80gig storage drive for the linux installation, with the last ~60gigs being for instaling larger windows apps (mainly games)

And finally getting the biggest hdd I can find (on my budget that is :P) and using it for my new storage drive...

Herein lies the problem... I don't need/want to access the windows, or it's apps partition from Linux... Nor do I want to access the linux partitions from Windows...

But I want them _both_ to share the storage drive... (at least 200gig)

They both need read/write access, so NTFS is out (unless the NTFS drivers work now, but nobody told me :P)

It's over 32gigs, so from what I've been told I can't use FAT32... Although I've heard conflicting reports that something like partition magic, or the many linux based partition tools _can_ make FAT32 partitions over 32gigs, and Windows will recognise them... it just can't create them itself.

Surely someone else out there somewhere wants to be able to access their documents from both sides of a multiboot installation, and would care to impart their wisdom on the situation...

Short recap: I need to create a Large (>=200GB) Partition, with Read/Write Access under Both Windows and Linux... Any Suggestions?

---

### Post by alastair on 2005-04-02
Just make it FAT32 - the 32GB "limit" looked wrong to me because there have been many times I have seen bigger FAT partitions than that happily live with Linux. I think FAT32 supports 2TB partitions. See :

[http://linux.org.mt/article/filesystems#N10058](http://linux.org.mt/article/filesystems#N10058)

I'd be tempted to format the partition for use in XP. Then read the relevant "man" page on mount options in Linux.

---

### Post by MetalMusicAddict on 2005-04-02
Yep, FAT is the way to go. I have a seperate "Downloads" drive that is FAT. Just an old 15 gig. ;) PartitionMagic will format a larger than 32gig FAT drive but I dont think XP's built in tools will. GParted might also do it. "GParted" is a PartitionMagic like app.

---

### Post by Whiffle on 2005-04-02
Yep FAT32 works fine, I have an 80 gig drive and a 60 gig drive that I share between windows and linux, works like a charm.

Tip:  Make a directory with a . as the first character in the name, ie ,".windowscrap", and set windows to use that as its "My Documents" directory.  That way whenever windows creates its stupid "My pictures" and "my music" etc, you won't even have to look at it in linux :)

---

### Post by akshoslaa on 2005-04-02
[QUOTE=Whiffle]Yep FAT32 works fine, I have an 80 gig drive and a 60 gig drive that I share between windows and linux, works like a charm.

Tip:  Make a directory with a . as the first character in the name, ie ,".windowscrap", and set windows to use that as its "My Documents" directory.  That way whenever windows creates its stupid "My pictures" and "my music" etc, you won't even have to look at it in linux :)[/QUOTE]
 *chuckles* that was the plan :P

---

### Post by akshoslaa on 2005-04-02
Alrighty... Seems good to me... FAT32 here I come...
I had _hoped_ it would turn out to just be yet another failing with windows :P

-Thanks

---

### Post by cmikepee on 2005-04-09
my windows install uses the ntfs filesystem.  what are the issues regarding ntfs?  Ideally i would like to be able to access files that are on my windows partition and vice versa. do i need to convert it to fat32? or should i keep it ntfs and just create a small fat32 partition to "share" between the two and put files there when i need to go between Operating Systems?  And does the location of the partition on the hard drive matter?

---

### Post by akshoslaa on 2005-04-09
[QUOTE=cmikepee]my windows install uses the ntfs filesystem.  what are the issues regarding ntfs?  Ideally i would like to be able to access files that are on my windows partition and vice versa. do i need to convert it to fat32? or should i keep it ntfs and just create a small fat32 partition to "share" between the two and put files there when i need to go between Operating Systems?  And does the location of the partition on the hard drive matter?[/QUOTE]

Alrighty, simply put Linux only has read access to NTFS partitions (write access can be achieved, but is apparently risky, never tried it personally)
And (obviously windows cant read linux partitions (without the aid of third party software)

The only file system (that I know of) that's shared natievely between the two is FAT
Converting an NTFS drive to FAT(32) can be achieved with partition magic... Although this isn't a free tool. (I'd like to know of any free equivilents of partition magic, I've had a brief look at qparted, but it really seems to be lacking for the time being)

The best option is like you suggested, to have a 'shared' drive between the two os's formatted as FAT.

Windows doesn't need that much space for installation (I personally run an 8Gig drive for windows+essential apps, though enything down to 4gigs is usually enough. (Install any larger programs to the FAT drive)

Linux is pretty much the same as windows as far as space requirements go. 4-8gigs seems to be good.

So you need:
a windows partition (can be NTFS or FAT, you won't be storing your personal files there so you won't need it under linux)

A Linux Partition (+swap)

A Storage Partition, shared between the two, formatted as FAT. It doesn't really matter where on the drive the partition is, although sticking it on the end seems appropriate to me. (Although I think Windows has a hissy fit if it's not on the forst partition, could be wrong though)

Under windows point your my documents folder to an my documents folder you create on the storage drive (right click the 'my documents' entry under the folder tree, or on the desktop (not the actual folder under 'Local settings') and select 'move'

Then install Linux, and during setup, tell it to mount the storage partition somewhere (eg /storage) (I then created a symbolic link to the mount point under my home folder, seemed more useful)
 
I has to do some messing around with /etc/fstab to get it to give me write access (it was mounted as root, so everyone else only got read access.

under the partitions <options> section (4th column) I changed 'default' to 'rw,user,umask=0' (Not sure if 'user' was necessary, but doesn't sem to hurt)

---

### Post by akshoslaa on 2005-04-09
[QUOTE=cmikepee]my windows install uses the ntfs filesystem.  what are the issues regarding ntfs?  Ideally i would like to be able to access files that are on my windows partition and vice versa. do i need to convert it to fat32? or should i keep it ntfs and just create a small fat32 partition to "share" between the two and put files there when i need to go between Operating Systems?  And does the location of the partition on the hard drive matter?[/QUOTE]
 Just stumbled across gparted... basically partition magic, but for gnome... Haven't tested it (installed fine..) but it looks good...

I wonder if they're including it on the livecd... that'd be handy...
*shrugs*

anyway, you might want to check out:
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
(general info on messing with ntfs partitions)

---

