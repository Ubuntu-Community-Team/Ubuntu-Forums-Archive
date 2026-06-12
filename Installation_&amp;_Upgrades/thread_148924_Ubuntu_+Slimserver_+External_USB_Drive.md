---
title: "Ubuntu +Slimserver +External USB Drive"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by DarthOverlord on 2006-03-22
I just rebuilt my mp3 server/file server using Ubuntu Breezy and I have a question.  Previously I was running a FAT32 drive inside my SUSE server and I was able to syslink to my home directory where Slimserver detected my library.

Now I want to try and run the MP3 library off an external hard drive.  I tried mounting the drive in the home directory, but when I set slimserver to scan this library it brings up zero songs.

I am stumped, any suggestions???

---

### Post by DarthOverlord on 2006-03-23
Well, it seems to be a permissions issue.  

drwx------ 4 Darth Darth 32768 1969-12-31 19:00 Music

How would I go about changing the permissions?

Tried to mount using:

sudo mount /dev/sda5 /home/Darth/Music/ -t vfat -o iocharset=utf8,umask=000

The permissions are still drwx -------

Any advice?

---

### Post by simonn on 2006-03-24
Use the  gid and uid parameters of the mount command. See man mount.

---

### Post by simonn on 2006-03-26
I will elaborate on my previous post as I now have time.

Firstly...

DOS file systems (vfat etc) do not have the capability to store permission and ownership details, so for this to be implemented in *nix they can be specified as options when mounting i.e. using the uid, gid and umask. See man mount.

Secondly...

slimserver requires read access, but for the sake of security I would not give it write access.

Finally...

Just a security tip...

On my home PC I have a user and group called public and a directory in the filesystem called public. The user public cannot log in.

Anything in public (basically media and documents that anyone with access to the PC can access) is owned by public:public and has 640 permissions (750 for directories of course).

This is so that:

1) I can control access to public folders just by adding or removing a user to the public group 

2) Nothing in the public folders can be deleted (except by me if I have su prevelidges at the time, but I guess I have to be careful) accidentally or otherwise - even if the user is a member of the public group

I have to add the user slimserver runs under to the public group.

---

