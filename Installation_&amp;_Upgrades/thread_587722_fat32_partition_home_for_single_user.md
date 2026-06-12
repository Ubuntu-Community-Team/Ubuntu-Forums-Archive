---
title: "fat32 partition /home for single user"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by inflamous on 2007-10-23
I've heard about a lot of things going wrong if you use your /home as a fat32, but I'm curious as to know what...

I'm the only person who uses this computer so I'm not exactly worried about other users (there are none) accessing my files.  But would there be other problems that that are being overlooked if I used /home as a fat32?

---

### Post by yabbadabbadont on 2007-10-23
FAT32 doesn't support the permission/owner/group settings that are required of a /home filesystem.  There will probably also be issues with upper/lower case and special characters.  (fat32 doesn't support the same set of them as do the native filesystems)  Stick with a native linux filesystem or you will just be asking for trouble.  However, there is nothing wrong with setting up an extra partition that is fat32 for sharing files between Linux and Windows.  In my case, I just read from and write to my Windows partition.  (it is fat32)

---

### Post by inflamous on 2007-10-23
Thanks for the reply

Thats the thing: I can read and write to NTFS partitions (where windows and another shared drive are in) with linux, but when I'm in windows I have to use other software (LTools) to get stuff thats sometimes in my /home folder because I forgot to transfer it over to the shared drive.  I'm thinking a fat32 as my /home would be easier for me to get all the files I need for both OSs.

I'm just curious for what kind of trouble I'd run into when I do (I'm not really worried about the permissions because I'm the only user on this lappy, and whenever I get off I lock it).

---

### Post by inflamous on 2007-10-23
I would also mention that on windows, I use a limited user account so things like fs-driver would be a huge pain to use

---

### Post by yabbadabbadont on 2007-10-23
Without the proper permissions on your /home/username/.dmrc file, GDM will not let you login...  have fun.  ;)

---

### Post by Sef on 2007-10-23
Windows can read [ext2 and ext3]("http://www.google.co.kr/search?q=ext3+and+windows&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

---

### Post by inflamous on 2007-10-23
ahh ic, I guess KDE would work the same way too then right?

Sef, I already know about how windows can read it with fs-driver, its just that with a limited user account on windows, it would be annoying to first set it up, then try to make the drives accessible on the limited user account because windows sucks at doing stuff like that.

ie. I can run install programs with different credentials but in some cases the program doesn't work properly because it needs to write to something on the C: (as with ApexDC++).  And if I'm pretty sure windows explorer can't be run with different credentials, and even if it could, that would mean that since I'm in a different user, even though they have administrative powers, I can't access my files in the My Documents folder.  Theres gonna be so much transferring that its just a huge hassle I don't want to worry about.

---

