---
title: "Hard upgrade frm 8.1 to 10.4LTS WHILE PRESERVING /home folder - Is this possible?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Paulzy on 2010-08-10
I know I'm using NON-Linux language..but whaaaat I **want** to do is upgrade **DIRECTLY** from my *broken* 8.10 to 10.04 LTS (or 9.04LTS, whichever is the **MOST VERIFIABLY** stable).

When I upgraded from 8.04LTS to 8.10 something during the package upgrade severly broke the system to the point where I cannot use many System Preferences without Ubuntu crashing and forcing the system back to the login screen. So....

I want to **DUMP** 8.10 and go straight to 10.04LTS (or 9.04LTS, whichever is the **MOST VERIFIABLY** stable).

BUT, I **WANT** to *preserve my /home folder in the process.*

So I want to also know how can I preserve my /home folder during the upgrade from 8.10 to 9.04/10.04.
[COLOR="Blue"]**FOR EXAMPLE:**[/COLOR] if I were to say install 10.04LTS [COLOR="Red"]DIRECTLY[/COLOR] over 8.10 without a re-format, will this preserve my /home folder - **WITHOUT** going through the automatic upgrade process as desribed on the official Ubuntu site? (Like with the CD install).

Thank you for your answers and understanding.

PaulJC

---

### Post by mörgæs on 2010-08-10
If 8.10 is broken, it is not a good starting point for an update. The fast and safe solution is a backup copy of /home and a clean install.

---

### Post by Paulzy on 2010-08-10
Wow, fast reply...OK how can I back it up via the **Archive Manager** or **Keep**? I also have **Ark** on my system for some reason, a possible left overfrom the kunbuntu-desktop install.

What would you suggest?

---

### Post by mörgæs on 2010-08-10
If the files are not big, I would just copy them to a USB drive of some sort. Don't worry about compressing the files unless it is necessary.

---

### Post by smilingfrog on 2010-08-10
> **Paulzy said:**
> BUT, I **WANT** to *preserve my /home folder in the process.*

So I want to also know how can I preserve my /home folder during the upgrade from 8.10 to 9.04/10.04.
[COLOR="Blue"]**FOR EXAMPLE:**[/COLOR] if I were to say install 10.04LTS [COLOR="Red"]DIRECTLY[/COLOR] over 8.10 without a re-format, will this preserve my /home folder - **WITHOUT** going through the automatic upgrade process as desribed on the official Ubuntu site? (Like with the CD install).
  
PaulJC

Before you do anything, backup you /home directory to a USB flash drive, or external drive. If you have not partitioned your harddrive, reinstalling overtop of 8.10 will format or at least erase your home partition.  If you installed Ubuntu without choosing partitions, most likely your /home folder is on the same partition that you are planning to wipe. You need to copy the /home folder to preserve it during a clean install.

You can boot your machine with a disk copy of Ubuntu, and then backup your /home folder to a DVD or Flash disk. Then use gparted (System>>Administration>> on the liveCD) to make a new partition for your /home directory. Copy your home directory into the new partition, and when you re-install Ubuntu, choose custom options, and mount the new partition as /home. All your settings and data (but not your programs) will be preserved.

---

### Post by Paulzy on 2010-08-18
Thanks. My /home folder is over 35gb - so it ownt fit on a USB drive :lolflag: - and niether of my externals have that much space. So I opting to wait and buy another external (1tb) - these are pretty cheap now. :p

While I woud hate to to have to re-install all my programs, it seems likely I'll have to.

---

### Post by Paulzy on 2010-08-18
It seems the issues wasn't that Ubuntu was broken, but that the **gnome-accessibilty-themes** package was broken under 8.10. But the dropping to login has stopped when i network upgraded to 9.04.

I submitted a bug report regarding the gnome-accessibilty-themes package.

---

### Post by mörgæs on 2010-08-18
It is good that people submit bug reports, but in this case I don't think it will matter much. 8.10 is unsupported, and support for 9.04 runs out in a few months. My guess is that the developers are using their effort elsewhere.

---

