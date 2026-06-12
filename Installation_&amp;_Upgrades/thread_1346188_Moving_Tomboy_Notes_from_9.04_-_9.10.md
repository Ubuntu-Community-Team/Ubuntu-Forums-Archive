---
title: "Moving Tomboy Notes from 9.04 - 9.10 ??"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by maxweld on 2009-12-04
I have a brand new Karmic system running now, the upgrade from 9.04 having trashed my old system. I can access the drives, but can only start the old system without X. 

How can I move my old Tomboy Notes to the new system. The file structures seem entirely different. 

Thanks

---

### Post by Swagman on 2009-12-06
Bump!

I'd be interested in this as well.

---

### Post by plucky on 2009-12-06
> **maxweld said:**
> I have a brand new Karmic system running now, the upgrade from 9.04 having trashed my old system. I can access the drives, but can only start the old system without X. 

How can I move my old Tomboy Notes to the new system. The file structures seem entirely different. 

Thanks

```
cd <location of old tomboy notes>
ls
cp *.note ~/.local/share/tomboy
cd ~/.local/share/tomboy
ls
# The .notes files should now all be in your tomboy folder in your home directory
```

ls= make sure you are in the correct directory
cp= copy the .note files into new tomboy directory

Log out and log in and the notes should appear.


Good Luck

---

### Post by maxweld on 2009-12-06
Many thanks.
I had actually already copied them there, but had not logged out and back in before checking for them.
Low and behold, when I now looked, they had appeared.:redface:

Thanks again

---

