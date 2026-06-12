---
title: "non-english character problem with smbfs"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by gugus on 2005-04-27
Hello all,
I have a problem with my smbfs directory and the non-english character: The file with accents don't display correctly.

Here is my /etc/fstab line:
//srv/directory  /mnt/share/srv/directory smbfs   rw,user,credentials=/root/.smbcred,dmask=777,fmask=77700,utf8,codepage=cp850

But I can display the non-english character correctly if I use Nautilus with the "smb://srv/directory" command.

How can I have non-english directory with smbfs ?

---

### Post by ian! on 2005-04-27
Doesn't it work on console as well?
Did you try adding *iocharset=<charset>* to the mount command options?

---

### Post by gugus on 2005-04-27
No, it doesn't work at console too.

I try with this new line:
//srv/directory        /mnt/share/srv/directory       smbfs   rw,user,credentials=/root/.smbcred,dmask=777,fmask=77700,utf8,codepage=cp850,iocharset=iso8859-15

But no change...

---

### Post by gugus on 2005-05-13
I found the solution of my problem in this [post!](http://ubuntuforums.org/showthread.php?t=33039&highlight=windows+utf8)

---

