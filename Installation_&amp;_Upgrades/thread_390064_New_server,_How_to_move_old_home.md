---
title: "New server, How to move old /home?"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by knichel on 2007-03-21
I just built a new server.  Core 2 Duo 2.13, 2GB Ram, 160GB HD...  My old server was running Gentoo (not my choice). I want to move the users /home directories to the new server.  As my limited knowledge tells me, I have 2 choices...

1)  have users log in and use ...
       scp -r oldUserName@oldFileServer: ./

or

2) use tar on the old server for each user and then move files to the new file server.

Which   method is better for preserving ownership perms etc... and which is easier?

I am using NIS and NFS on new server... So accounts are already created for students on the new server and the home directories are being shared from the new server.  

Thanks in advance for the help.

Mike

---

### Post by wonk-o-matic on 2007-03-21
Well, the big surprise when you do this kind of things it when you find out that file permissions are based on UID, not username.  

There are ways around that.  A friend here says that you could copy /etc/password from the old box, because that's the file that has the UID.  I was thinking that a script could do the deed, but I have to admit, his way is cleaner.  

Have you already set up the accounts on the new box?

---

### Post by knichel on 2007-03-21
Yes, I have already set the accounts up on the new box.  I could write a perl script to go through the directory tree and set the uid and gid I guess.  The new accounts (usernames) are the same on both boxes, so I could create an associative array to hold UID and GID since I only have 10 users to deal with.

Another possible issue is that the server (new) is running Feisty and the workstations are currently running 6.06 (breezy I think that is?).  I am not sure how the older version will deal with newer conf files like for gnome etc....

You have given me some guidance, thanks.   I will look into the set uid in perl.  Now, how should I move the files?

Mike

---

