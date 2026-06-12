---
title: "Debootstrap error while installing"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by Addaone on 2005-11-14
Hi all, I'm trying to install Ubuntu on my 1 Ghz Compaq. I had a useless System Restore partition that I formatted in fat32, and made it /. After formatting, I get this error:

```
The test of the file system with type fat32 in partition #1 
of IDE1 master (hda) found uncorrected errors. If you do 
not go back to the partitioning menu and correct these 
errors, the partition will be used as is. Go back to the 
menu and correct errors?

Go Back/Yes/No
```

This is puzzling because the installer shouldn't even be touching partition #1 (my Windows partition)...the partition I created is #5. I select "No", and the base install starts. When it's about 33% done, I get a red screen and this message:

```

The debootstrap program exited with an error (return 
value 1). Check /target/var/log/bootstrap.log for the 
details.

Go Back/Continue

```

After selecting either choice:
```

The base system installation into /target/ failed. Check
/target/var/log/bootstrap.log for the details.

```

There is no /var/log/bootstrap.log file in the partition.

When I press ALT+F3, this is the only error message (it's the last one):
```
tar: ./usr/share/man/man3/Locale::gettext.3pm.gz: Invalid argument
```

The ISO's MD5 is OK, the CD-ROM checked said the CD was valid, and I burned it on a different kind of media, at 4X each time. I'm stumped. Any ideas, guys? Let me know if you need more info. Thanks.

Nick Rogers

---

### Post by Addaone on 2005-11-15
I tried the netinstall ISO and got the same result. Grrr.

---

### Post by Oiko on 2005-11-16
I have the same debootstrap problem on my Acer Travelmate 8000. I've checked the MD5 of the ISO download. I've also validated the CD burn. Moreover I have exact the same problem with the 5.04 release which I have on a pressed disk. So I don't think it is a CD problem.

Then I have activaded DMA on my CD drive during the installation with no effect. I also tried the "acpi=off noacpi nolapic" parameters.

I really think te problem lies in the error message:
> tar: ./usr/share/man/man3/Locale::gettext.3pm.gz: Invalid argument

---

### Post by Oiko on 2005-11-16
Well, I'm pretty new to Linux, but I expected it would be possible to install Ubuntu on a FAT32 partition. I found out the hard way it's not possible. I'm writing this message from a fresh Ubuntu 5.10 install on a ReiserFS partition. :)

---

### Post by Addaone on 2005-11-16
That worked, thank you. Darn, I was hoping to use fat32 so I could access the drive from Windows, but oh well. Thanks again!

---

### Post by Abracon on 2006-01-15
Why would it give you the option of selecting the FAT32 File System if it does not support it? Also, what alternate file system should i format the primary partion with?

---

### Post by corvairbob on 2006-01-15
just where do you find this reiserFS partition.  i'm trying to install this 5.10 breezy badger disk and i get the check/target/var/log/bootstrap.log    error  what gives when i got this disk they said it took 5 min to install and was automatic?  looks harder that xp pro  may have to go back.

---

