---
title: "duplicate sources.list entry messages unclear"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2013-05-13
When I run sudo apt-get update I get some messages that are unclear:
> W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring/restricted amd64 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring/restricted i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates/restricted amd64 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_raring-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates/restricted i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_raring-updates_restricted_binary-i386_Packages)

So, what is duplicated with what? 
Is the problem within sources.list, or between sources.list and /var/lib/apt/lists, or in the repositories? 
Without line numbers, it's difficult to know which part of /etc/apt/sources.list (or /var/lib/apts/lists?) is causing the problem. 

Any ideas what if anything I need to do here?

---

### Post by Bashing-om on 2013-05-13
Hi !          jcoles; 

The sources list files are in:
/etc/apt/sources.list  and;
in the directory /etc/apt/sources.list.d
to look for the duplication
```
cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
cat /etc/apt/sources.list.d/<some file> ##//from the ls command//

```

When found, use gedit with elevated privileges to edit out the duplications .....make a backup of the file prior to editing.[INDENT=2]
good 'nuff ?

[/INDENT]

---

### Post by jcoles on 2013-05-13
The first command just lists sources.list. 

The second command shows
> ~$ ls -la /etc/apt/sources.list.d
total 16
drwxr-xr-x 2 root root 4096 May 13 20:22 .
drwxr-xr-x 6 root root 4096 May 13 20:45 ..
-rw-r--r-- 1 root root   49 May 13 20:22 dropbox.list
-rw-r--r-- 1 root root   49 May 13 20:22 dropbox.list.save


Using the third command, I list those two dropbox files, which both contain:> deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main which is not included in sources.list. Do I delete one of the dropbox files? But the dropbox entries were not the ones listed in the error messages.

---

### Post by jcoles on 2013-05-13
The more I look at it, the less sense it makes.

There is no such string as "raring/restricted" or "raring-updates/restricted" in the sources.list file. So what are these error messages about?

---

### Post by fantab on 2013-05-13
You have both architectural repos enabled, ie you have 64bit and 32bit. If you are using 64bit then you don't need 32bit/i386. Do this:

```
gksudo gedit /etc/apt/sources.list
OR
sudo gedit /etc/apt/sources.list
```

Delete the unwanted line or comment out with "#" in front of the un-needed line. Save the file and run:

```
sudo apt-get update
```

---

