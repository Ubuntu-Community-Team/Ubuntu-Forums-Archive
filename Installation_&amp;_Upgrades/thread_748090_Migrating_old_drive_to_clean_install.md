---
title: "Migrating old drive to clean install"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by BobBlec on 2008-04-07
Greetings,
  My main drive (40 gig Maxtor) has been giving me a SMART error msg on boot, so I decided to get a new drive. I found an 80 gig Seagate pull, which solved *that* problem.

  For some reason, though, my old 7.04 CD keeps dropping me into busybody while it's booting, and a 7.10 CD that I got hold of crapped out about halfway through the install. I wound up having to stick the 80 in a different machine and do a clean install of 7.04 there (it worked).

  The problem now is that I need to get stuff - apps I've installed, etc. - from my old drive to the new one. I drag-n-dropped the stuff from the Home folder, but I need to get the other stuff, too.

  Is there a good way to either transfer stuff, or generate a diif, etc., in the file/app listings, so that I can transfer or reinstall, so I don't miss anything?

  Thanks!

  -BobBlec

---

### Post by asbjorne08 on 2008-04-07
If you are thinking on the /etc /usr and /var and so on, the safest choice is to copy it to a temporary folder, and then update the files needed one at a time. Just copying over I would assume could break things.

Unless you have a heavy modified setup, there shouldn't be that many files that need to be updated.

-- 
A

---

### Post by BobBlec on 2008-04-09
> **asbjorne08 said:**
> If you are thinking on the /etc /usr and /var and so on, the safest choice is to copy it to a temporary folder, and then update the files needed one at a time. Just copying over I would assume could break things.

Unless you have a heavy modified setup, there shouldn't be that many files that need to be updated.

-- 
A

asbjorne08,
  Thanks!  :-)

  I want to do this in GNOME, just because my Linux skills are still a bit rusty, and I don't want to shoot myself in the foot. The only problem at this point is that I need to be able to login to GNOME as root, or at least have su access, because I don't have perms to access some of the folders, etc., on the new drive while running off the old drive.

  -BobBlec

---

