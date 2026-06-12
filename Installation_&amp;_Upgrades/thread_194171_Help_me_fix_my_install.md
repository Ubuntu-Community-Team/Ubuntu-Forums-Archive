---
title: "Help me fix my install"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by ottothecow on 2006-06-11
My kubuntu install failed.  Proper things simply arent installed.

I cant get x to start but I dont think it is becasue of the problems other users have, I think it is because half of the packages it needs are simply missing.

I think I had a bad source in my sources file (a mirror that hadnt updated or somethign, I ran upgrade very soon after 6.06 came out).  I think my problems might get fixed by simply running the upgrade again.
I cant get my network up (not sure on the commands I shoudl be using but the ones I tried all failed) so I cant run the upgrade from there again.

Is there anyway to set a CD as a source so that I can fix the install (or at least get my network up so that I can do the rest).  I have some breezy disks but it is absolutely no trouble to get dapper disks downloaded.

---

### Post by aysiu on 2006-06-11
If you use the Dapper disk, you'll need the Alternate Install CD, **not** the Desktop CD.

Pop the CD in and type ```
sudo apt-cdrom add
```

---

### Post by ottothecow on 2006-06-12
thanks much, that was what I was looking for.

it wasnt pretty but doing that, I managed to get a working system that didnt start x.  got x back up and running, put back the real repositories, upgraded to the most recent files, installed the automatix stuff again and put back my kubuntu-desktop files.  

It books up looking exactly as I left it (better actually, a program that I was having trouble with was marked as running and so kde ran it again when it tried to restore state...only this time, my program seemed to start just fine).  Only problem, it is now convinced that the right hand side of my keyboard is the numpad as if I were pressing the function key.  No worries...I will solve that tomorrow

---

