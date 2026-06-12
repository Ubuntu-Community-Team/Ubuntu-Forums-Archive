---
title: "Guide: How To Backup Operating Systems"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2008-05-27
I have posted a new Wikibooks guide "How To Backup Operating Systems"...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

This guide extends on the information in the older guide here...
[http://ubuntuforums.org/showthread.php?p=2148017](http://ubuntuforums.org/showthread.php?p=2148017)

Comments and suggestions are welcome.

---

### Post by lisati on 2008-05-27
> **IgnorantGuru said:**
> I have posted a new Wikibooks guide "How To Backup Operating Systems"...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

This guide extends on the information in the older guide here...
[http://ubuntuforums.org/showthread.php?p=2148017](http://ubuntuforums.org/showthread.php?p=2148017)

Comments and suggestions are welcome.

I went for a look and got the following message:
```

There is currently no text in this page, you can search for this page title in other pages or edit this page.

    * If you recently created this page, try purging the server cache or searching the deletion log.


```

---

### Post by MyNameisTheStig on 2008-05-27
I didn't find any error message on the page

I dunno what's up with yours lisati

---

### Post by IgnorantGuru on 2008-05-27
> **lisati said:**
> I went for a look and got the following message:

Sorry about that - you grabbed the link right after I posted it.  I copied it with dots ... in the middle of the link which is why it didn't work.  That has been corrected.  The correct link is 
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

---

### Post by IgnorantGuru on 2009-07-26
A fairly major edit to this book was posted today which includes an expanded section on the MBR & boot process, how to backup and restore the partition table (including extended partitions), and other additions.

[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

---

### Post by IgnorantGuru on 2010-01-12
A fairly major rewrite and update of [How To Backup Operating Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems) is available. This includes a method which supports ext4 using the new FSArchiver, and it is now both GRUB v1 and v2 friendly.
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

And a PDF version for printing...
[http://en.wikibooks.org/w/index.php?title=Special:Book&bookcmd=render_article&arttitle=How+To+Backup+Operating+Systems&writer=rl](http://en.wikibooks.org/w/index.php?title=Special:Book&bookcmd=render_article&arttitle=How+To+Backup+Operating+Systems&writer=rl)

---

### Post by walt11 on 2010-06-04
[SIZE=2]Thanks for the guide. I have your updated version, and it's clarified a number of things for me. But I've run into a file system permission problem in creating the archive.

I'm using a recent System Rescue CD (1.5.5), and using fsarchiver. I've tried 2 different target file systems on different drives, but get the same error message for both:

[/SIZE]```
[errno=30, Read-only file system]:
archwriter1 C#116, archwriter_create():
cannot create archive /mnt/target/backup-sdb5.fsa
```[SIZE=2]

I'm attempting to backup sdb5. The first target I tried was /dev/sda1, an internal drive and boot volume. The second was /dev/sdb1, an external USB connected drive (and the same drive with the Ubuntu partition I want to back up.)

I've tried manually to change permissions using chmod, but the system changes them back to read only! I've tried to use sudo, but I'm told that command isn't available, and to use _sudo. (When I try that, I get some output which is unintelligible, to me at least.)

Any help would be most appreciated. Thanks.[/SIZE]

---

### Post by IgnorantGuru on 2010-06-04
> **walt11 said:**
> I've tried 2 different target file systems on different drives, but get the same error message for both:

I haven't encountered this before.  If you type mount, does it show the volume mounted as readonly (ro)?

When using SystemRescueCD, you are always root, so there is no need for sudo.  You might try explicitly mounting the volume as read-write.  eg
```
mkdir /mnt/target
mount -o rw /dev/sda1 /mnt/target
mount
```

The last mount should return something like:
**/dev/sda1 on /mnt/target type ext3 (rw)**

Also, you could test if the drive is writable:
```
touch /mnt/target/testfile
ls /mnt/target/testfile
```

If that creates a file with no error, then you might want to ask about this problem on the fsarchiver forum... the author is generally quite responsive
[http://www.fsarchiver.org/forums/](http://www.fsarchiver.org/forums/)

I will be interested in the solution you find - I may add a note to the guide.

---

### Post by walt11 on 2010-06-04
[SIZE=2]Thank you for the very quick response!! I tried the things you suggested, with these results:

After the 
[/SIZE]```
mount /dev/sda1 /mnt/target
```[SIZE=2] the
[/SIZE]```
mount
```[SIZE=2]
showed **/dev/sda1 on /mnt/target type ntfs (rw)**
(The fact that it's ntfs shouldn't matter, should it?)
But when I did the
[/SIZE]```
touch /mnt/target/testfile
```[SIZE=2] I got **touch:cannot touch '/mnt/target/testfile': Read-only file system**.
BUT, I did another
[/SIZE]```
mount
```[SIZE=2] immediately after this, and it showed the same thing as above, **/dev/sda1 on /mnt/target type ntfs (rw)** !!

I repeated the whole using -o rw in the original mount command, and the results were identical.
[/SIZE]

---

### Post by IgnorantGuru on 2010-06-04
> **walt11 said:**
> (The fact that it's ntfs shouldn't matter, should it?)

That may be causing the problem.  Use "-t type" to indicate the correct type, eg:
```
mount -t ext3 -o rw /dev/sda1 /mnt/target
```

Replace "ext3" above with the correct type for that partition (check /etc/fstab if you're not sure).  (You probably don't need the "-o rw" but it won't hurt.)

The fact that touch reported an error tells you it really is a read-only system, not a problem with fsarchiver.  So you just need mount to mount it correctly and you should be okay.

---

### Post by IgnorantGuru on 2010-06-04
One other thing... you might want to verify that /dev/sda is the drive you think it is - it's possible that SystemRescueCD is numbering your drives differently, especially if a USB drive is involved.

```
fdisk -l | more
```

to see the drives.

---

### Post by walt11 on 2010-06-04
[SIZE=2]The -t ntfs didn't help, and I tried a ls to show more:
[/SIZE]```

mkdir /mnt/target
ls -l /mnt
```[SIZE=2]
And at that point, the permissions on /target are [B]drwxr-xr-x
[/B]Then I did:
[/SIZE]```
mount -t ntfs -o rw /dev/sda1 /mnt/target
ls -l /mnt
```[SIZE=2]And the permissions on /target have been changed to [/SIZE][SIZE=2]**dr-x------** even though ```
mode
``` shows (rw) still, at that point[/SIZE].
[SIZE=2]
I rebooted before seeing your following post, but I had earlier done a [/SIZE]```
ls -l /mnt/target
```[SIZE=2] and all the files I expected to be there are.

Thanks again for responding so quickly. I probably won't be able to get back to you again until late tomorrow (Sat.)
[/SIZE]

---

### Post by IgnorantGuru on 2010-06-04
> **walt11 said:**
> The -t ntfs didn't help

If the partition is in fact ntfs, then I think you need to use ntfs-3g, as the ntfs supported on SystemRescueCD is read-only.

[http://sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support](http://sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support)

```
ntfs-3g /dev/sda1 /mnt/target
```

---

### Post by walt11 on 2010-06-04
[SIZE=2]Thanks!! That looks like the solution! Won't be able to try it until tomorrow evening, and will let you know.[/SIZE]

---

### Post by walt11 on 2010-06-05
> If the partition is in fact ntfs, then I think you need to use ntfs-3g,  as the ntfs supported on SystemRescueCD is read-only.

[http://sysresccd.org/Sysresccd-manua...-Write_support]("http://sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support")

     Code:
     ntfs-3g /dev/sda1 /mnt/target 
[SIZE=2]
[SIZE=2]That was exactly what I needed.[/SIZE] Thank you so much, again. I'm now the proud owner of a 6.1 GB file system archive.[/SIZE]

---

### Post by IgnorantGuru on 2010-06-05
> **walt11 said:**
> ]That was exactly what I needed.[/SIZE] Thank you so much, again. I'm now the proud owner of a 6.1 GB file system archive.[/SIZE]

Good - I think I will make a note of that in the guide.

---

