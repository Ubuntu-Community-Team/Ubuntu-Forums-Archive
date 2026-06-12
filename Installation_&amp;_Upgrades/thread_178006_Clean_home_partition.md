---
title: "Clean home partition"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2006-05-17
I'm going to upgrade to Dapper soon, and since I play with programs from time to time I'd like to have a fresh reinstall. Since I have my home on a separate partition I shouldn't have problems in keeping my datas and settings.
The problem is: maybe I will have too much old settings and won't be able delete them. I'd like to clean something of all those hidden files, but I don't know what. Of course I can simply throw away folders of old programs I'm not going to  reinstall, but what else? Are there files kept on my home by some software which belongs to the os and maybe is not installed anymore with Dapper? In short, how should I keep my home clean?
Thank you

---

### Post by Sef on 2006-05-17
> Are there files kept on my home by some software which belongs to the os and maybe is not installed anymore with Dapper?

As Far As I Know (AFAIK), no.  Only your personal files that you save to your home partition are saved there.

> In short, how should I keep my home clean?

Delete the files that you do not have no use for nor want any more.

---

### Post by barbarian on 2006-05-17
hi, 

.deb files from installed packages you may remove with those magic commands:
 
sudo apt-get autoclean

sudo apt-get clean

:)

---

### Post by Nonno Bassotto on 2006-05-18
[QUOTE=Sef]As Far As I Know (AFAIK), no.  Only your personal files that you save to your home partition are saved there.[/QUOTE]

Are you saying that only my personal datas are stored in my home folder? Surely no: have a look at your home and make sure to see hidden files. You will find that most programs store there your personal settings. This is actually useful: if you reinstall Linux, you don't lose your configurations.

The problem is that I don't know what I can remove form there. I suspect (please, can anyone confirm?) you can safely remove all, and every program will reinstall a copy of the folder when needed (of course you lose your settings this way).

I also suspect that your home fills with garbage in the long run. Of course I can recognize a lot of names of apps I use, and I don't want to remove these. I was just wondering what to do with the others.

---

### Post by aysiu on 2006-05-18
If you see a hidden folder for a program you know you installed and then removed and no longer use any more, feel free to just delete it.

If you're unsure about a file, keep it.

If you're unsure about a folder, rename to *foldername*_old. For example, if you no longer use Firefox, rename /home/username/.mozilla to /home/username/.mozilla_old.

If you see no adverse effects after renaming it, then go ahead and delete it.

---

