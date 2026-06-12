---
title: "What to backup before upgrade"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by luvshines on 2010-10-12
I recently shifted from Fedora 11 to Ubuntu 10.04, in september, and simply loving it :D

Now that new release is out, I am really excited about upgrading to 10.10

Just wanted to know what all to backup before update:
1. I did some tweaking in Ambience them xml files for some look
2. Made samba shares
3. Installed new fonts for conky
4. Lot of other tweaking ;)

[B]Will I loose any of the above after upgrade ?
I am planning to upgrade using alternate iso to cdrom mount method. Is it safe ??
Since I am always running out of disk space I did not opt for upgrading through network[/B]

---

### Post by acreech on 2010-10-12
I am also looking for some advise. I found this thread and used it as an example. [HTML]http://ubuntuforums.org/showthread.php?t=35087&highlight=properly+backup[/HTML]

I am trying to do a good backup of my system before making a clean install of Maverick. This is the command that I was using to do the backup but I get errors. I tried it with and without sudo. Can you please tell me what i have done wrong and if this will backup and restore like I want. I am mainly interested in my /home and /Creech (second drive mounted at that location, written into fstab) as well my /var and /etc. After I do my clean install, then I am going to restore this backup. I am hoping that won't mess up the new operating system, but will give me all my files, settings, etc. 

So I cd into the external drive where my backup will be stored. Then I ran this command:
```

sudo tar -cvpzf backup.tar.bz2 -–exclude=/media/Creech_1_5t/10122010_Backup/Home_Backup/backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/proc /

```

I get the following error in the terminal after that. 

```

tar: invalid option -- 
Try `tar --help' or `tar --usage' for more information.

```

Thanks for the help.

---

### Post by luvshines on 2010-10-12
> **acreech said:**
>  

So I cd into the external drive where my backup will be stored. Then I ran this command:
```

sudo tar -cvpzf backup.tar.bz2 -&#8211;exclude=/media/Creech_1_5t/10122010_Backup/Home_Backup/backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/proc /

```

I get the following error in the terminal after that. 

```

tar: invalid option -- 
Try `tar --help' or `tar --usage' for more information.

```

Thanks for the help.

Can't understand why this particular --exclude is different **-&#8211;exclude=/media/Creech_1...**. Is it a typo or something is wrong with the hyphen just before e?

Also, if it's z then should not you name it .gz instead of .bz2

---

### Post by acreech on 2010-10-12
> **luvshines said:**
> Can't understand why this particular --exclude is different **-–exclude=/media/Creech_1...**. Is it a typo or something is wrong with the hyphen just before e?

Also, if it's z then should not you name it .gz instead of .bz2

I just noticed that one exclude looked different. It must have been an error in the copy paste. I will retype that and try it. also that z should be a j. I will post back if that works. Thanks for the proofread.

---

### Post by acreech on 2010-10-12
> **acreech said:**
> I am also looking for some advise. I found this thread and used it as an example. [HTML]http://ubuntuforums.org/showthread.php?t=35087&highlight=properly+backup[/HTML]

I am trying to do a good backup of my system before making a clean install of Maverick. This is the command that I was using to do the backup but I get errors. I tried it with and without sudo. Can you please tell me what i have done wrong and if this will backup and restore like I want. I am mainly interested in my /home and /Creech (second drive mounted at that location, written into fstab) as well my /var and /etc. After I do my clean install, then I am going to restore this backup. I am hoping that won't mess up the new operating system, but will give me all my files, settings, etc. 

So I cd into the external drive where my backup will be stored. Then I ran this command:
```

sudo tar -cvpzf backup.tar.bz2 -–exclude=/media/Creech_1_5t/10122010_Backup/Home_Backup/backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/proc /

```

I get the following error in the terminal after that. 

```

tar: invalid option -- 
Try `tar --help' or `tar --usage' for more information.

```

Thanks for the help.


Thanks for the proofread. I had two errors. That one character that was wrong in front of the first exclude. I think that was from it not copying correctly off of a web page and the then in the options I needed to change the "z" to a "j". It works perfect now. I hope that it restores like I expect it to.  

```

sudo tar -cvpjf backup.tar.bz2 --exclude=/media/Creech_1_5t/10122010_Backup/Home_Backup/backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/proc /

```

---

### Post by luvshines on 2010-10-13
Just marking it as SOLVED for now since exploring 10.10 on Virtual Machine :D

**Will backup and upgrade only when I like the new release**

---

