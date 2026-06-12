---
title: "saving updates so only download once"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by dorhelp on 2006-10-14
I am setting up several computers with ubuntu. Is there away I can have it save the update source file so I can copy them to a CD and update all but the first from the CD. I tried looking around in preference but didn't have any luck.
                       Thanks
                       Linda

---

### Post by taurus on 2006-10-14
All your downloads are in /var/cache/apt/archives.

---

### Post by dorhelp on 2006-10-14
Thank you I found them all there. I am planning to write them to a CD. I saw you could chose a CD as a repository when I was hunting for how to have it leave updates on the machine. Then I will update all the other machines from the CD. Hope it works so far ubuntu is fantastic. My kids will be busy for months trying all the games!
                       Linda

---

### Post by taurus on 2006-10-14
Just add CD-ROM to your /etc/apt/sources.list and you are all set...

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install <package name>
-or-
sudo aptitude upgrade

```

---

