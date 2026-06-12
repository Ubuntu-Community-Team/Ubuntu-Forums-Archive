---
title: "How do I manually mount Ext3 partition with 777?"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2007-10-10
Good day, everyone!
Well, I do not know where to put my post really. Here's my problem: I have made a server for our  customer and they wanted an encrypted FS on a separate drive that is Ext3. I made it. Their workers log onto it using different accounts with XDMCP and they share this drive that has some company info. The problem is, as you probably guessed, that when someone creates or modifies a file others are not able to write into it. I cannot mount the drive with fstab 'cause they want it to be mounted manually every time server starts. so the only choice is mount.

The question is how do I mount an Ext3 partition with 'mount' giving rwx access to all users. Thank you!

---

### Post by maybeway36 on 2007-10-10
That is so annoying!
I suppose wou could just chmod -R 777 /mountpoint every once in a while, but that's sort of messy.

---

### Post by naazgull on 2007-10-10
Hi,

You can run mount with *-o rw*, but that means that users can access the filesystem, not **all** the files in it. The permissions of files and directories are stored in the file system backbone and a simple mount command can change them all. 

Cheers,

---

### Post by PryGuy on 2007-10-10
> **maybeway36 said:**
> That is so annoying!
I suppose wou could just chmod -R 777 /mountpoint every once in a while, but that's sort of messy.Well, people, I'm really lost here...

---

### Post by PryGuy on 2007-10-10
> **naazgull said:**
> Hi,

You can run mount with *-o rw*, but that means that users can access the filesystem, not **all** the files in it. The permissions of files and directories are stored in the file system backbone and a simple mount command can change them all. 

Cheers,How it can be changed?

---

### Post by PryGuy on 2007-10-11
Okay, my general ideas are:
1. Reformat drive with some other non native FS, Like NTFS or FAT32. I know it's rubbish but it will work, unstable though.
2. Mount the Ext3 partition with smbfs from the same computer with 777 so it would appear as a drive for  terminal users. That is insecure.

What do you guys think?

---

### Post by vanadium on 2007-10-11
to automatically set all permissions open, you would need to set the umask to 000, but as already mentioned before, this is just like opening all doors and highly insecure. The proper way to solve this issue is to create a group, for example "shared", and give that group read and write permissions on the drive.

Modifying files will go seamlessly, however when creating a file, the user explicitly needs to change the group of the file to "shared". there is also another way: the user can "log in" on the group shared

newgrp shared

and from that point on, any file that that user creates will automatically belong to the "shared" group.

I believe you can overcome that "inconvenience" above by setting the grpid option during mounting. Then, new files are automatically set to the group of the directory where it is created.

---

