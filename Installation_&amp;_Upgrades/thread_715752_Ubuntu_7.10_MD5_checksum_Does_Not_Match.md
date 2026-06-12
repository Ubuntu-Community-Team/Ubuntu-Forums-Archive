---
title: "Ubuntu 7.10 MD5 checksum Does Not Match"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by scotbuff on 2008-03-05
A co-worker came to me with the intention of trying Ubuntu.  He downloaded the ISO file from two different servers/mirrors and then ran a Windows based MD5 Checksum utility to validate the checksum matches the Ubuntu hashes page.

The UBUNTU site says the MD5 Checksum should be:
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
 

But what he gets on BOTH of the files he downloaded is:
D2334DBBA7313E9ABC8C7C72D2AF09C

It’s not easy to see but there is 1 character different:
d2334dbba7313e9abc8c7c**0**72d2af09c

The 0 is missing in his checksum.  Has anyone encountered this before and is this a result of the Windows based checksum he used?  Is this anything to be concerned about considering these are mirrors?  Thanks in advance.

---

### Post by arkara on 2008-03-05
if you are unsure about the things that you have downloaded you can always 
re-download the iso.

---

### Post by zvacet on 2008-03-05
Download same iso with torrent and point download to the folder with existing iso.That way torrent will just check your iso for errors and replace corrupted files with good ones.Run md5sum again and if it is O.K. burn it on disc on lower possible speed.

---

### Post by LeoSolaris on 2008-03-17
Huh, I did not know that bittorrent had that ability...  learn something new every day!

Thanks,
Leo

---

