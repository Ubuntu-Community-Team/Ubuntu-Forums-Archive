---
title: "creating md5 checksum"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by Papillonrus on 2007-01-29
root@darrell-laptop:/home/darrell/Desktop/Folder# md5sum file.iso > file.iso.md5
md5sum: file.iso: No such file or directory
root@darrell-laptop:/home/darrell/Desktop/Folder#


What is the story here?  Following the Edgy guide @ [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_generate_MD5_checksum_files](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_generate_MD5_checksum_files)

If this doesn't work how are you supposed to create or check md5sum?

Looking for a Solution.

---

### Post by kidders on 2007-01-29
Hi there,

To checksum a file, it has to exist first. Are you sure **file.iso** is the right filename?

---

### Post by Papillonrus on 2007-01-29
I replaced the file name with file to protect the innocent.  I'm new to Linux not editing conf or reading manuals.  Darrell

---

### Post by kidders on 2007-01-29
> I replaced the file name with file to protect the innocent.Hehe... even so, the filename you specify must be correct.> md5sum: file.iso: No such file or directoryYou can take this message at face value ... it simply means you were trying to md5sum a file that's not there.

md5sum computes a hash of a file. For it to work, the you must specify the name of a file that actually exists.

---

### Post by Papillonrus on 2007-01-29
Well then tell me the path to the .iso in mandriva-one-2007-free-gnome folder.  The path tree has me confused.  I can use a file browser and locate the file.  When I use the terminal to locate the file it tells me "No such file or directory".  Attached is a screen shot to the folder.

---

### Post by kidders on 2007-01-29
> **Papillonrus said:**
> Well then tell me the path to the .iso in mandriva-one-2007-free-gnome folder.  The path tree has me confused.  I can use a file browser and locate the file.  When I use the terminal to locate the file it tells me "No such file or directory".  Attached is a screen shot to the folder.

Well, it looks as though you might be referring to a file somewhere in ~darrell/Downloadz/New-Saves/mandriva-one-2007-free-gnome, but I'm only reading what I see on your screenshot ... so I'm probably not telling you anything you don't already know. :confused: I can't see from the pic if there's an ISO image in there or not. Maybe you're just getting thrown off by a spelling error or something. Try copying & pasting the file path, rather than typing it ... or maybe moving the file somewhere less tedious to type.

---

