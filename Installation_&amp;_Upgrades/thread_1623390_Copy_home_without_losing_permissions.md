---
title: "Copy /home without losing permissions?"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by shadowofblood on 2010-11-16
I backed up my "/home" and "/usr" folders from a previous installation.

How can I copy them on to my new installation without losing my permissions?

I tried using nautilus, but everything had "Root-only" permissions after I pasted the files.

---

### Post by oldfred on 2010-11-16
Dld you backup to a NTFS external drive? If so you lost all permissions and ownership.

This has what the permissions should be for /home. Do not know about /usr.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

this is my /usr from karmic which is what I have still on my portable.
```
fred@fred-laptop:/usr$ ls -l
total 272
drwxr-xr-x   2 root root  69632 2010-11-11 09:17 bin
drwxr-xr-x   2 root root   4096 2010-05-07 19:21 games
drwxr-xr-x  92 root root  12288 2010-11-07 23:39 include
drwxr-xr-x 257 root root 114688 2010-11-12 08:26 lib
drwxr-xr-x  42 root root  32768 2010-11-07 23:38 lib32
lrwxrwxrwx   1 root root      3 2009-12-21 20:54 lib64 -> lib
drwxr-xr-x  11 root root   4096 2009-12-28 14:22 local
drwxr-xr-x   3 root root   4096 2009-12-31 20:08 man
drwxr-xr-x   2 root root  12288 2010-11-12 08:26 sbin
drwxr-xr-x 393 root root  12288 2010-05-14 11:40 share
drwxrwsr-x  17 root src    4096 2010-07-31 00:28 src

```

---

### Post by shadowofblood on 2010-11-16
Yes, I backed up to an NTFS partition.  I'm working on restoring permissions and ownership now using that link you provided.  Since I'm applying permissions to the contents of /home, the process is taking a while.  I'll post back and let you know how it goes.

---

### Post by shadowofblood on 2010-11-17
I tried the method in the link above, but it just froze and didn't change any permissions/ownership.

Can anyone tell me a method I can use to change the permissions and ownership of all the files in my /home directory?

I'm not particularly worried about /usr at the moment; I just want my files working.

---

### Post by oldfred on 2010-11-17
You cannot change the backup in the NTFS partition, you are changing your install in an ext3 or ext4 partition?

What does not work from the 4 commands in the summary at the bottom of the link?

---

### Post by shadowofblood on 2010-11-17
I used nautilus to copy the /home folder from the NTFS backup and I pasted the contents into my /home folder on my ext4 partition.  After pasting the files, all permissions/ownerships were set to Root-only.  I need to change them to my account.

The command that freezes is:
```
sudo chown -R username:username /home/username
```

After entering that command in the terminal (replacing "username" obviously), the terminal displays a blinking cursor while it's, so I assumed, changing permissions.  However, after leaving it open for about 12 hours, the blinking cursor was still there and not a single file had been fixed.

---

### Post by oldfred on 2010-11-18
Whenever I have run chown or other file commands they run very quick.

Not sure did you run this first?
sudo chown username:username /home/username/.dmrc

I would also try just changing one file or one folder and see what happens.

---

### Post by shadowofblood on 2010-11-18
I ran the command with the -R option one folder at a time.  I have all my /home folders/files set to the correct permissions now :p

Question:  Is there a way to transfer files while applying the correct permissions at the same time?

---

### Post by oldfred on 2010-11-18
Each of these commands can be used, but you need to include specific parameters with each. See man page  for each command. You cannot copy to NTFS and preserve permissions & ownership.
man rsync

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

