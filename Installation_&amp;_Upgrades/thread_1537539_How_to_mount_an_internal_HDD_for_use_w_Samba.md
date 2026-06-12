---
title: "How to mount an internal HDD for use w/ Samba"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by z61P on 2010-07-23
Apologies if this isn't the correct forum, but I didn't see a better one...
 
Anyway, I'm having some issues changing ownership on a Samba share, and I suspect it has something to do with how I mount the drive. Here's my setup:
 
The system has two physical hard drives in it, sda1 and sdb1. sda1 is the "primary" drive (the drive I installed the OS on). sdb1 is to be dedicated as a share for the Samba server. 
 
Here's my fstab entry for sdb1: 
 
/dev/sdb1 /samba/drive1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 2 
 
Is this correct, or at least reasonable? I'm suspicious of the "vfat" option for some reason. 
 
And here's my smb.conf share declaration: 
 
[public]
path = /samba/drive1/public
valid users = @staff
writeable = Yes
read only = no
public = yes
available = yes
browsable = yes
 
My problem is that I can't actually see the contents of this share (e.g. the readme.txt file I created from the console) from a Windoze PC. I'm pretty sure that's because I don't have *nix* permissions set correctly. Here's what I mean: 
 
tpmoore@ubuntu1:/samba/drive1/public$ ls -la
total 48
drwx------ 2 tpmoore root 16384 2010-07-23 10:22 .
drwx------ 3 tpmoore root 16384 2010-07-23 09:33 ..
-rwx------ 1 tpmoore root 111 2010-07-23 10:22 readme.txt
 
Attempts to 'chown' of the share, or any files in it result in a polite refusal from the system, for example: 
 
tpmoore@ubuntu1:/samba/drive1/public$ sudo chown :staff readme.txt
[sudo] password for tpmoore:
chown: changing group of `readme.txt': Operation not permitted 
 
I could go on, but I'll stop now. I can provide additional details if needed. 
 
All clues appreciated. 
 
Best Rgds,
z

---

