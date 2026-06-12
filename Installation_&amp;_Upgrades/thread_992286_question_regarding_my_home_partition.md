---
title: "question regarding my /home partition"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by anon_uroih on 2008-11-24
I wanted to install 8.10, but I decided to do a full install instead of an upgrade.  In my previous installation of 8.04, I had only one partition, and this time around, I wanted a separate partition for home.

To prepare, I shrunk the main partition, created a new partition, formatted the new partition as ext3 and copied the files I wanted to keep to the new partition.  After I copied the files to the new partition, I did a 'chown -R jeff:jeff *' in the top directory of that partition.

When I installed 8.10, I reformatted my own partition and mounted it on '/', and I chose to mount my new partition on '/home'.  The first time I booted, I brought up the terminal, and things went like this:

```

jeff@the-laptop:~$ cd ..
jeff@the-laptop:/home$ ls -al
total 68
drwxr-xr-x 14 root root  4096 2008-11-23 15:05 .
drwxr-xr-x 20 root root  4096 2008-11-23 15:07 ..
drwxr-xr-x  5 jeff jeff  4096 2008-11-23 19:38 Books
drwxr-xr-x 10 jeff jeff  4096 2008-11-23 19:46 Desktop
drwxr-xr-x  2 jeff jeff  4096 2008-11-23 19:46 Documents
drwxr-xr-x 29 jeff jeff  4096 2008-11-24 14:58 jeff
drwx------  2 jeff jeff 16384 2008-11-23 19:14 lost+found
drwxr-xr-x 40 jeff jeff  4096 2008-11-23 19:42 Music
drwx------  2 jeff jeff  4096 2008-11-23 19:46 PDF
drwxr-xr-x  4 jeff jeff  4096 2008-11-23 19:46 Pictures
drwxr-xr-x  5 jeff jeff  4096 2008-11-23 19:47 School
drwx------  2 jeff jeff  4096 2008-11-23 20:24 .TrueCrypt
drwxr-xr-x  3 jeff jeff  4096 2008-11-23 19:45 Videos
drwxr-xr-x  7 jeff jeff  4096 2008-11-23 19:50 virtualmachines
jeff@the-laptop:/home$ mv PDF/ jeff/
mv: cannot move `PDF/' to `jeff/PDF': Permission denied
jeff@the-laptop:/home$ mv School/ jeff/
mv: cannot move `School/' to `jeff/School': Permission denied
jeff@the-laptop:/home$ sudo mv School/ jeff/
```

So what I want to do is move the folders for PDF, School, Music, etc into jeff.  I had already deleted the empty /home/jeff/Music, etc in the /home/jeff folder.  

Just wondering why I had to invoke sudo to do it.  "jeff" is the owner of the folder PDF and the owner of the /home/jeff folder.  Shouldn't he be able to move files that he owns into his own folder?  Or is this not allowed since root is the owner of '.'?

When I use sudo, things work fine, so I'm just trying to learn a little bit about linux here.  On my old system, my user-name was jeff as well, so maybe both files are owned by jeff but these are really two different users?

---

### Post by taurus on 2008-11-24
Boot into recovery mode and at the prompt, run

```
chown jeff:jeff /home/jeff
shutdown -r now
```

---

### Post by anon_uroih on 2008-11-24
I followed your directions, and I still have the same issue.  I'm not sure if they did anything or not because jeff was already the owner of /home/jeff.  I think I'll just forget about it, because it easy to just move them by invoking sudo.  

I still wonder why this is happening.  Maybe it is just b/c root owns the /home folder and you can't move stuff around in it unless you are root, even if you are the owner of the files moving those files into a directory you own.

---

### Post by taurus on 2008-11-24
> **anon_uroih said:**
> 
```

jeff@the-laptop:~$ cd ..
jeff@the-laptop:/home$ ls -al
total 68
**[COLOR="Blue"]drwxr-xr-x 14 root root  4096 2008-11-23 15:05 .[/COLOR]**
drwxr-xr-x 20 root root  4096 2008-11-23 15:07 ..
drwxr-xr-x  5 jeff jeff  4096 2008-11-23 19:38 Books
drwxr-xr-x 10 jeff jeff  4096 2008-11-23 19:46 Desktop
drwxr-xr-x  2 jeff jeff  4096 2008-11-23 19:46 Documents
drwxr-xr-x 29 jeff jeff  4096 2008-11-24 14:58 jeff
drwx------  2 jeff jeff 16384 2008-11-23 19:14 lost+found
drwxr-xr-x 40 jeff jeff  4096 2008-11-23 19:42 Music
drwx------  2 jeff jeff  4096 2008-11-23 19:46 PDF
drwxr-xr-x  4 jeff jeff  4096 2008-11-23 19:46 Pictures
drwxr-xr-x  5 jeff jeff  4096 2008-11-23 19:47 School
drwx------  2 jeff jeff  4096 2008-11-23 20:24 .TrueCrypt
drwxr-xr-x  3 jeff jeff  4096 2008-11-23 19:45 Videos
drwxr-xr-x  7 jeff jeff  4096 2008-11-23 19:50 virtualmachines
jeff@the-laptop:

I followed your directions, and I still have the same issue.  I'm not sure if they did anything or not because jeff was already the owner of /home/jeff.  I think I'll just forget about it, because it easy to just move them by invoking sudo.  

I still wonder why this is happening.  Maybe it is just b/c root owns the /home folder and you can't move stuff around in it unless you are root, even if you are the owner of the files moving those files into a directory you own.

That's right.  Root owns /home/jeff so you need to change the ownership of /home/jeff to jeff again.  Doesn't matter if you own every single file under /home/jeff, only root can write to /home/jeff.

Again, what happens when you run this command from a terminal?

[code]sudo chown jeff:jeff /home/jeff
```
Does jeff actually show up as owner now if you run this command?

```
ls -la /home
```

---

