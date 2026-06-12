---
title: "[SOLVED] upgrading from CD, but with a /var/lib partition"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by nmsmith on 2008-10-26
I have a mythtv box that is now running its fifth release of ubuntu. Every upgrade so far has been done using the automatic method. However, there are several issues with my current installation, including no desktop sound for existing users (new users created since hardy have got sound), cron not having worked properly for the last year, display resolution errors in gdm, ... the list goes on. I think that some of these have been caused by fiddling and editing config files over the past two years, which the dist-upgrade has not resolved correctly.

I have three partitions:
sda1 /         10G
sda2 /var/lib  270G for my mythtv recordings
sda3 swap      1.5G

To cure all my little bugs, I want to reinstall from the CD, reformatting sda1 for the / partition. I told the partitioner to mount /dev/sda3 at /var/lib, without reformatting, and without deleting the data.

I get this message:

> The file system on /dev/sda3 assigned to /var/lib has not been marked for formatting. Directories containing system files (/etc, /lib, /usr, /var, ...) that already exist under any defined mountpoint will be deleted during the install.

Please ensure that you have backed up any critical data before installing.

I need help deciphering this warning.

What will be deleted?
Are there any system files in /var/lib?
Are there any adverse implications to keeping my current contents of /var/lib?

I will be happy to continue so long as my /var/lib/mythtv, /var/lib/pictures and /var/lib/music directories are left intact. Unfortunately I don't have backup disks big enough to backup all the recordings in /var/lib/mythtv, so backup is not an option.

Help appreciated.

---

### Post by ddrichardson on 2008-10-27
/var/lib is variable state information and a fresh installation will not like it being from a previous release. I don't know much about MythTV but why is it keeping recordings in there? According to the [filesystem hierarchy]("http://www.pathname.com/fhs/2.2/fhs-5.8.html") a user should never need to modify it to get packages to work.

---

### Post by nmsmith on 2008-11-01
Thanks for that ddrichardson - where is Wattisham, I wonder?

I have followed the advice of [online guides]("http://ubuntuforums.org/showthread.php?t=340382") which suggest using XFS (as it's better at deleting large files) on a seperate partition, mounted at /var/lib. Mythtv creates /var/lib/mythtv, in which it stores all its recordings.

As this is where the bulk of my available space is (only 10Gb is left for the OS on /), I also have /var/lib/music for all my mp3 files, and use that location for backups and storing any other large amount of data.

I could do a manual copy of the data to a backup disk (I now have one), but would prefer just to leave the data as-is. I propose a solution:

[LIST=1]
[*] Copy everything in /var/lib that I want to keep to a subfolder called /var/lib/upgradetemp (from the livecd I guess, so that I don't break anything).
[*] Install from scratch, mounting the partition at /var/lib. Recall the text:
> Directories containing system files (/etc, /lib, /usr, /var, ...) that already exist under any defined mountpoint will be deleted during the install.
I'm guessing that this means it will leave the 'upgradetemp' directory untouched.
[*] In the new OS, reinstate the directories I'd like, such as the music, videos and mythtv directories.[/LIST]

Does this sound safe?

---

### Post by ddrichardson on 2008-11-01
Wattisham? Its not finding it, its getting out of it.

I'd say you could do what you propose but would be better off to rename /var to /oldvar then after installation move all the new /var that doesn't overwrite the recordings and so on into /oldvar (you'll have to do this from a LiveCD).

If you unmount /var, rename /oldvar to /var and amend the /etc/fstab to mount the original partition as /var.

Does that make sense?

---

### Post by nmsmith on 2008-11-01
Yes, I understand (you just have to read it slowly!)

I like that your method circumvents worrying about what the installer will or will not delete. However, it seems that your solution can be summed up as "*copy the freshly installed version of /var/lib onto my current copy*". Given that one of the main reasons for this reinstall is to remove 'cruft' (to use an intrepid term), I would prefer to be able to "*copy the data I want to keep onto a fresh /var/lib*". This may also be safer as I'll be up-down-grading from 64-bit Hardy to 32-bit Intrepid for an easier life.

I think I'll do this:

[LIST=1][*]Install afresh to my current root partition.
[*]Erase from my current XFS partition anything but my media files and other to-keep data.
[*]Copy the contents of /var/lib to my XFS partition.
[*]From a Live CD, rename /var/lib to /var/oldlib or similar.
[*]Mount the new partition at /var/lib
[/LIST]

Can you see any holes in that plan? I'm a bit stuck at how to do step 4. Should I edit fstab from the Live CD session?

---

### Post by ddrichardson on 2008-11-01
Might work, I mean var is fairly transient by nature so I can see why it bothers you but that said it shouldn't be accumulating cruft (nice word btw). Its mainly lock files and tmp files - why MythTV is using it I really don't know.

If you have backed up the files you want then copy them across afterwards I guess, if not then go with your plan. If MythTV wasn't using /var/lib we'd be fine.

---

### Post by nmsmith on 2008-12-13
I finally bit the bullet and did the upgrade today. There were lots of issues unrelated to the above, and I in fact ended up 'upgrading' to 32-bit Hardy instead. Nonetheless I now have a fresh install. The following may be useful to other mythtv users wishing to reinstall, keeping their recordings in /var/lib on a separate partition:

Everything discussed above in this thread went largely without hiccups. I did things in this order:

[LIST=1]
[*]Backup mythtv database ```
mysqldump -u root -pPASSWORD mythconverg > mythconverg.dump
```
[*]Backup other files (obviously!)
[*]Install Ubuntu
[*]Install mythtv
[*]Import the database ```
mysql -u root -pPASSWORD mythconverg < mythconverg.dump
```
[*]Reboot into live CD session
[*](On the system hard drive, not the live session filesystem...) Move /var/lib to /var/oldlib (To make this easy I did 'sudo nautilus' and simply renamed the folder)
[*]Erase unwanted files in XFS partition (everything but mythtv folder, in most cases I expect)
[*]Copy contents of /var/oldlib to xfs partition. **This didn't work at first**, as I did it from the live CD and gave everything root:root ownership. **In order to preserve permissions, I used**: ```
cp -r --preserve /var/oldlib/ /var/lib/
```
[*]Edit fstab to mount XFS partiton at /var/lib. **Remember to create the directory /var/lib in your system hard drive - I forgot at first**
[*]Reboot into Ubuntu
[/LIST]
I'm now back where I wanted to be: with all my recordings intact, my database intact, and yet a fresh installation of Ubuntu. Bliss!

Health warning: I trust anyone reading this to take lots of precautions, and think through the implications of each step. Every existing system will be slightly different, and I have omitted lots of the extra things which I knew were particular to my own files. I have also (for the sake of clarity) omitted lots of the fiddling about needed to make the above steps work. This is NOT a 'HOWTO' - it's for people who know what they're doing! </condescending>

And finally, ddrichardson, my thanks again.

---

### Post by ddrichardson on 2008-12-14
Glad you got a solution, hope that MythTV start complying with standards!

---

