---
title: "Unable to update"
date: 2015-08-04
forum: MINT
---

### Post by shoaib2 on 2015-08-04
sir, now in linux mint 17.2, i m getting this issue while updating or upgrading.. :(

need urgent help

---

### Post by howefield on 2015-08-04
Thread moved to the *"MINT"* forum.

Your thumbnail is difficult to read.

---

### Post by shoaib2 on 2015-08-04
okay.. 

i m getting error that how unable to lock the administator directory(/var/lib/dpkg/)??
any help ???

---

### Post by howefield on 2015-08-04
Are you sure, your image above is difficult to read but it doesn't look like that error to me. Post a more legible image.

Looks like an issue with apt-get looking for a cd-rom.

---

### Post by shoaib2 on 2015-08-04
here is the clear picture of error which i am facing...

---

### Post by coffeecat on 2015-08-04
No, that's a different error. As howefield said, the image in your first post tells us that apt is trying and failing to read from a CD-ROM, but it's near impossible to make out the details.

The error in your more recent post concerns an interruption in running dpkg, and tells you what to do. What happens when you run "sudo dpkg --configure -a"?

---

### Post by shoaib2 on 2015-08-04
[COLOR=#000000]after running "sudo dpkg --configure -a" i gpt this messgae, now what should i do ??[/COLOR]

now i am hangging up with this error, need urgent help of this this eoroor plzZzZ...!!

---

### Post by deadflowr on 2015-08-04
Press enter.
(If the default option doesn't work re-run the command again and try Y, then enter)

---

### Post by QIII on 2015-08-04
Hello, shaoib2

Please be patient.  You started this thread only an hour ago, you have had responses and only a few minutes ago you provided what was asked for.

Demanding that volunteers be at your immediate beck and call is not likely to make friends.

---

### Post by buzzingrobot on 2015-08-04
The CDROM error in the first image occurs when the sources list contains an entry for the medium used to do the install in the first place. That could have been with a DVD or a CD or USB stick, but the error will still say "CDROM". The package manager can't find it because it isn't there.  After a normal installation, that entry should not appear in the list of sources used by the updater to find relevant updates.  As I recall, Mint has a GUI tool to edit entries in the sources list.  Use that to delete or disable the CDROM entry.

The second image was produced because the package manager noticed it was interrupted before it completed, leaving things in a confused state. 

The third entry is the package manager telling you that one of the scripts it is about to install is different from the one it is about to replace. It then gives you several options. This is important if you are a user who has modified one or more of these scripts and do not want them overwritten.

---

