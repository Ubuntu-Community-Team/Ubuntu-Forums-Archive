---
title: "Does it make sense to place /usr somewhere other than /?"
date: 2019-01-10
forum: Installation &amp; Upgrades
---

### Post by psklenar on 2019-01-10
Good afternoon,

I'm currently playing with Ubuntu in a Virtualbox VM on my Win10 PC.

On Win10 I have a 250GB SSD (C: with OS), 1TB (D: with 'Apps and Data' & 550GB in use) and 500GB (E: with Steam and 250GB in use) and I have my "Program Files" and "Program Files (x86)" on the D: drive keep applications and the OS as separate as possible after issues losing applications in earlier Windows updates over the years).

I've got the same sizes of drives available for my Ubuntu install (attempting to replace/minimize my need for Windows).  I'm currently planning to place ...

   250GB - /efi, /swap (16GB) and the balance to /
   1000GB - /home
   500GB - /steam

16GB swap should be overkill on a 64GB PC where I'm unlikely to *need* it, but I don't want to risk *no* swap.  Given my history leading me to want to keep apps separate from the OS, does it make sense to place /usr on a different drive than / or am I massively over thinking the design & I should just leave it on the / partition?

Thank you,
***pat----***

---

### Post by CatKiller on 2019-01-10
> **psklenar said:**
> does it make sense to place /usr on a different drive than /? 

No.

Swap partitions aren't used these days, either - swap files are just as good.

Having /home as a separate partition *is* useful, in case of reinstalls. There's not a lot of point having Steam on a different partition.

/ on your SSD and /home on your HDD will be fine.

---

### Post by ajgreeny on 2019-01-10
Judging by the title you chose for this thread I wonder if you believe that the /usr folder is where all your personal files and folders are  placed, ie, the data from all the applications used in Ubuntu.

That is not where they sit, and as CatKiller suggests it makes more sense to have a separate partition for /home, which will then contain all your personal data files in a sub-folder called /home/***username***.  Confusingly Windows calls these partitions drives, eg C:\ and D:\.
You can see the full hierarchy of the Linux filesystem at [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) so you can see that /usr is very different from what I think you are expecting.
> **/usr** contains the majority of user utilities and applications, and partly replicates the root directory structure, containing for instance, among others, /usr/bin/ and /usr/lib.

---

### Post by psklenar on 2019-01-10
> **ajgreeny said:**
> Judging by the title you chose for this thread I wonder if you believe that the /usr folder is where all your personal files and folders are  placed, ie, the data from all the applications used in Ubuntu. ...

No, actually what I believed/suspected, after looking at [http://blog.danyll.com/linux-directory-map/](http://blog.danyll.com/linux-directory-map/), is that "/usr contains the majority of user utilities and applications" and that "/home contains the personal data (documents, music, pictures, save files, data files, etc)".

On Windows, after multiple issues over the years, I started installing all applications separate from the OS and was wondering if it made sense to do the same thing under Linux.  Based on yours and **CatKiller**'s responses, it sounds like I'm overthinking the design. :)

Thank you for responding so quickly!
***pat----***

---

### Post by CatKiller on 2019-01-10
The main difference is that Windows separates things by *origin* - each program has a separate "install directory" - and *nix separates things by *function*. Binaries go in one of the /bins, configuration files go in /etc, documentation goes in /usr/share/doc, personal settings and files go in /home, and so on.

There's no benefit to only having some bits and not others in case of disaster, other than your own stuff. Replacing all the installed programs is just an apt install away. 

Using different partitions for the parts of the filesystem tree was useful when you were trying to eke out the last drop of performance from your Winchesters by using one filesystem for teeny tiny files and another for big datasets, and /var/spool was on some completely different machine on the other side of campus. Not so much for a single modern machine.

---

### Post by psklenar on 2019-01-10
Thank you very much **CatKiller**, it's been over a decade since I played with *nix and I guess it shows. :)

***pat----***

---

