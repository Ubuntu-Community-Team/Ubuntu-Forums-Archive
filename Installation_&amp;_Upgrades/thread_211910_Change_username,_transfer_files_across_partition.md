---
title: "Change username, transfer files across partition"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by pteron on 2006-07-09
I'm dual booting to Windows XP and Ubuntu 6.06 on my laptop. I've had Windows on my laptop for far longer, but am trying to transfer over most if not all of my computing to Ubuntu. I have two questions:

1) Is it possible for me to change my username in Ubuntu? When I go to System  > Administration > Users and Groups, select my name, and hit properties, the username field is grayed out and unalterable.
2) I'd like to transfer files from my XP partition to my Ubuntu partition. My USB drive works in both OS's, but I'd prefer a faster solution than booting up Windows, copying files to my drive, shutting down Windows, booting Ubuntu, copying the files, and repeating. Specifically, I'd like to see my XP files and folders while in Ubuntu, and be able to transfer them back and forth. Would Samba be useful here? ftp? Qtparted?
2a) When I did try to get qtparted working, it said that it could not find my partitions, perhaps because I wasn't root. Is it possible to get it working using sudo?

Thanks in advance for any help.

---

### Post by aysiu on 2006-07-09
2) [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

NTFS is read-only. FAT32 is read/write for both OSes.

3) ```
kdesu qtparted
``` in Kubuntu or ```
gksudo qtparted
``` in Ubuntu.

---

### Post by majed on 2006-07-09
1) For changing your username, Did you try running this command from a terminal?

```
sudo usermod -l <olduser> <newuser>
```

Good luck!

---

### Post by pteron on 2006-08-03
I hadn't tried any of those things yet, but they should all do the trick. Thank you both very much, and score one for the forums. :)

---

