---
title: "Parition Question..."
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by modestmelody on 2008-03-12
I'm about to do a reinstall for the first time in a while.  I've setup a /home directory (without any configs yet, but with all of my media) on a second drive.  When in the partition tool installing Ubuntu I know that I can just select that drive to be the mount point /home.  Now here's the question-- if I make sure to select to NOT reformat that partition, despite the change in name/mount point, will Ubuntu (and it should, IIRC) still install the necessary components in this folder to operate as a /home (hidden files) and not destroy my folder already named "Documents", "Music", etc?

Thanks.  Pretty simple question, but never really thought about how Ubuntu handles this kind of conflict on install.

---

### Post by taurus on 2008-03-12
What filesystem is that partition that you plan to mount it to /home?  You should not mount a ntfs or vfat filesytem to /home because things will break and they will break as soon as you try to log in the first time.

---

### Post by modestmelody on 2008-03-12
> **taurus said:**
> What filesystem is that partition that you plan to mount it to /home?  You should not mount a ntfs or vfat filesytem to /home because things will break and they will break as soon as you try to log in the first time.

Crud.  The intention would be to use a vfat system (which must be why my attempts to move it broke) since I share files between Windows (used very sparingly) and Linux.

Next computer was going to be a Hackintosh to share files...

So I guess /home for me will not be able to hold my media files until I'm 100% Linux.  That's news that makes me sad.

---

### Post by taurus on 2008-03-12
If you want to share files between Ubuntu and windows, create a partition and mount it to somewhere like /media/share with either ntfs or vfat filesystem.  That way, you can write to it either in Ubuntu or windows.  Then, things won't be so sad anymore.

---

### Post by modestmelody on 2008-03-12
> **taurus said:**
> If you want to share files between Ubuntu and windows, create a partition and mount it to somewhere like /media/share with either ntfs or vfat filesystem.  That way, you can write to it either in Ubuntu or windows.  Then, things won't be so sad anymore.

I already do that... but I was hoping to make use of those empty folders in my /home folder at the same time.  I guess it's a peeve I have that desires to have the most consolidation as possible.

---

### Post by egalvan on 2008-03-13
> **modestmelody said:**
> I already do that... but I was hoping to make use of those empty folders in my /home folder at the same time.  I guess it's a peeve I have that desires to have the most consolidation as possible.

I do just what you want, my LINUX HOME also has all my "media" and Windows data. Windows-specific stuff is in a folder labeled "win".  Music, movies, downloads, etc are in there respective /home places....
also, I use FireFox in Linux and Windows, pointing to the same /profiles/ directory on my LINUX partition.

How?

"Ext2 Installable File System for Windows"

which you will find at:

[http://www.fs-driver.org/](http://www.fs-driver.org/)


Read carefully, follow instructions, enjoy.

I don't understand why so few people use this. It's worked for me.  

As I get further and further away from Windows, my machine is becoming more and more Linux only.... soon my mapping/GPS programs (DeLorme and MS Streets & Trips) will be the only things left (well, maybe my DVD savers)
:popcorn:

---

### Post by Shazaam on 2008-03-13
Most linux media related apps can read from a Windows partition. I have ALL of my music/pics etc. on my XP partition and point Ubuntu to it. Gutsy has write access to Window so if you download something in Ubuntu it's easy to move it to Windows. Or use the program that egalvan mentioned to go in the reverse direction.
Be careful, after you enable write access from Windows to Ubuntu you MAY find a "Recycle Bin" on your Ubuntu desktop. :)

---

### Post by egalvan on 2008-03-13
> **Shazaam said:**
> Most linux media related apps can read from a Windows partition. I have ALL of my music/pics etc. on my XP partition and point Ubuntu to it. Gutsy has write access to Window so if you download something in Ubuntu it's easy to move it to Windows. Or use the program that egalvan mentioned to go in the reverse direction.

That is the easier way, I'll admit... and when I started dual-booting, it's what I did.
But I wanted to reduce both my dependency on Windows, and the size of the Windows partitions. Learning curve, you know...



> **Shazaam said:**
> 
Be careful, after you enable write access from Windows to Ubuntu you MAY find a "Recycle Bin" on your Ubuntu desktop. :)

Wow, i hadn't thought of that! I've got to check it out.  :lolflag:

:popcorn:

---

