---
title: "Problems with Samba After Upgrade to 14.04"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by stephen67 on 2015-07-15
Background

I was using 12.04 for a long time and never experienced these problems.

I have a separate partition on which I back up my photography files from my Windows machine. I have ownership of the partition and Others have Create and Delete access.

On the partition I have a folder "photography". Using a right click in Nautilus I shared the folder, allowed others to create and delete files, and allowed guests access. When I created the share I told Nautilus to apply these settings to files in the folder.

Problem 1) I can access the shared photography directory and copy files to it. I cannot navigate to a nested folder. I get access denied. This is new with 14.04. How can I share the entire tree?

Problem 2) When I copy files from Windows to Ubuntu, they are created  with an owner of "Nobody". WTF??? Worse, when I delete, as root, the files are no longer visible, but they still take up space! 

/var/lib/samba/usershares/photography has:

#VERSION 2
path=/big0/photography
comment=
usershare_acl=S-1-1-0:F
guest_ok=y
sharename=photography

Any and all help appreciated!

---

