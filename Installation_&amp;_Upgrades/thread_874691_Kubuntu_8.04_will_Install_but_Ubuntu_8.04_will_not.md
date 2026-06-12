---
title: "Kubuntu 8.04 will Install but Ubuntu 8.04 will not."
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Benkrishman on 2008-07-30
Earlier today I installed Kubuntu 8.04 to check out KDE 4.0.  Wasn't for me, so I decided to go with Ubuntu 8.04.  However during the install, at about 48-50% the install fails due to an i/o error(I don't have more information about the error on hand).  It said it could be due to a bad burn, or potentially a damaged harddrive.  I burned several new discs of ubuntu but none worked(all at 2x and used multiple downloads to see if the mirror was the issue) and I have the same problem.  I've tried installing 3 or 4 times and it always stops in the same place.  After many failed attempts I decided to try Kubuntu again and it installed no problems.  

Does anyone know what the issue could be?  I've tried to eliminate all the variables but I still can't figure it out.

---

### Post by Sef on 2008-07-30
Did you md5sum the download?

---

### Post by Benkrishman on 2008-07-30
> **Sef said:**
> Did you md5sum the download?

I didn't the first time.  When I went back to download again I used a torrent instead of one of the mirrors.  I pointed the torrent towards the iso that I already downloaded it and when it checked it it only showed 99.9% downloaded so I figured that was the issue.  I let the download finish and tried again but I got the same error in the same place.

Right now I'm trying the alternate cd to see if I have any luck with that.  Could that make a difference?

---

### Post by abn91c on 2008-07-30
leave kubuntu alone then usen adept-manager  or a konsole to install the ubuntu-desktop
sudo aptitude install ubuntu-desktop

---

