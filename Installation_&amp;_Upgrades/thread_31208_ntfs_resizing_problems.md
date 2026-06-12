---
title: "ntfs resizing problems"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by DLM on 2005-05-02
first off, let me say that I love ubuntu, I used the live cd for a while and decided I had to install it.
But, here's my situation.
I have windows xp (ntfs) taking up all of my 60 gig drive.  When I use the built in ntfs resizer in the ubuntu installer, and I change the size of the partition, the size just stays the same when I hit enter.  Any cure or another method for doing this?
thanks

---

### Post by nad on 2005-05-02
The linux ntfs driver is presently read only. You can not resize an ntfs partition with it. The cure would be to support or otherwise contribute to the devs working on this project or convince M$ to help as they are presently looking for ways it can "build bridges" to the open source community.

The method is to use a windoze program.

---

### Post by jodef on 2005-05-02
[QUOTE=nad]The linux ntfs driver is presently read only. You can not resize an ntfs partition with it. The cure would be to support or otherwise contribute to the devs working on this project or convince M$ to help as they are presently looking for ways it can "build bridges" to the open source community.

The method is to use a windoze program.[/QUOTE]

I think you may be mixing up the ntfs drivers that enable one to read or write to a linux partition these are independent of the resizing function. Linux distros have long had support for resizing NTFS partitions though there is the standard warning BACK UP YOUR DATA FIRST!

> I have windows xp (ntfs) taking up all of my 60 gig drive. When I use the built in ntfs resizer in the ubuntu installer, and I change the size of the partition, the size just stays the same when I hit enter. Any cure or another method for doing this?
thanks Unfortunately I have never used the Ubuntu partitioning tools do you have any other Linux live CDs e.g. Knoppix or PCLinuxOS they also carry partitioning tools. The latter in particular has the graphical tool diskdrake which is excellent for these type of tasks and easy to use.

---

### Post by theerga on 2005-05-02
What i did is i backed up my data i wanted backed up put in the windows xp cd went throught the install process and reformated my hd to lesser amount. and reinstalled windows alltogether after that i instaled linux and for the partition i selected use largest constant free space or some option sort of like that

---

### Post by nad on 2005-05-02
I stand corrected. Not only does ntfsresize safely resize ntfs filesystems, but I found this at the project homepage at sourceforge.net:

News

Feb 24, 2005 	Ubuntu 5.04, codenamed "Hoary Hedgehog", is the newest distribution that added support for non-destructive NTFS resizing during installation by the use Partman and ntfsresize. Here is how you can do it when the [Partitioning disks] screen appears:

   1. Choose the "Manually edit partition table" option.
   2. Choose the NTFS partition you want to resize.
   3. Choose the "Size:" line.
   4. Choose <Yes> if you are asked about "Write changes to disk and resize the partition?".
   5. Enter the new size.
   6. Please wait patiently until the resize process frees the needed space for Ubuntu installation.

---

### Post by az on 2005-05-03
The ubuntu installer safely resizes ntfs partitions.  You do not have to reinstall windows after you install ubuntu.

---

### Post by Jenda on 2005-05-03
Just about how safely is that? My friend has a 20 GiB NTFS drive, and he'd like to try a dual boot. He does not have a burner, so backing up everything would be difficult. My advice was backup only your personal work - everything else you can download again.  Was that correct?

---

### Post by az on 2005-05-03
[QUOTE=Jenda]Just about how safely is that? My friend has a 20 GiB NTFS drive, and he'd like to try a dual boot. He does not have a burner, so backing up everything would be difficult. My advice was backup only your personal work - everything else you can download again.  Was that correct?[/QUOTE]

It depends.

I would say that the ubuntu installer partitionner is very very safe.  That would not stop me from backing up my stuff....

---

### Post by Jenda on 2005-05-03
[QUOTE=azz]It depends.

I would say that the ubuntu installer partitionner is very very safe.  That would not stop me from backing up my stuff....[/QUOTE]
 Hmm. Well that does help. But how much would you back up? Just the personal stuff or even music, programs? I didn't have this problem, because I already had a split drive to start with.

---

### Post by jonny on 2005-05-03
It's very difficult to perform a full backup with windows, so be prepared to lose something - especially saved and unlocked levels on games - if it all goes pear shaped.  Almost everyone uses windows in administrator mode, so programs and users can and do store data anywhere on the hard drive.  This includes tricky places like the registry and hidden files.

You only want to back up data: programs are best reinstalled.  In XP, there's a documents and settings wizard that'll guide you through most of the steps; alternatively, start with everything in c:\Documents and settings and then scour the hard drive.  Many applications store data in a subdirectory of c:/program files/<app name>.  Make sure that you first set your file browser to show hidden files.

If it's any consolation, you only need to back up one place (/home/) with ubuntu.  Much simpler!

---

### Post by Jenda on 2005-05-03
[QUOTE=jonny]It's very difficult to perform a full backup with windows, so be prepared to lose something - especially saved and unlocked levels on games - if it all goes pear shaped.  Almost everyone uses windows in administrator mode, so programs and users can and do store data anywhere on the hard drive.  This includes tricky places like the registry and hidden files.

You only want to back up data: programs are best reinstalled.  In XP, there's a documents and settings wizard that'll guide you through most of the steps; alternatively, start with everything in c:\Documents and settings and then scour the hard drive.  Many applications store data in a subdirectory of c:/program files/<app name>.  Make sure that you first set your file browser to show hidden files.

If it's any consolation, you only need to back up one place (/home/) with ubuntu.  Much simpler![/QUOTE]
 Oh I have no doubts that Ubuntu is a gazi-trifilion times better, but thanks for the advice... The main problem still remains though... the guy does NOT have a burner. I do. We each have a flash drive, 384 MiB altogether, he has a decent i-net connection, I don't... Any ideas?

---

### Post by az on 2005-05-04
It is a personal thing.  If we are talking about the only copies of the first few hundred pictures of the baby, no way.  If we are just talking about openoffice, winMx and a few games, who cares?

---

### Post by jonny on 2005-05-04
[QUOTE=Jenda]The main problem still remains though... the guy does NOT have a burner. I do. We each have a flash drive, 384 MiB altogether, he has a decent i-net connection, I don't... Any ideas?[/QUOTE]Unscrew your case, unplug your burner and put it in his PC.  It's at most a 10 minute job.  Or buy a burner for £10 (UK street price).  Your data's worth more than that.

---

### Post by Jenda on 2005-05-18
Hmm, thanks for the help.

It seems my case is screwed up, and no unscrewing is possible (in this *case*, it's my uncles computer, which I can't touch...bummer). 
Anyway, the guy is so fed up with Windows (which deleted most of the stuff intended for backup anyway - user error...), that we are installing on Saturday, backing up only the 384 Mib that'll fit on the flash drives...

---

