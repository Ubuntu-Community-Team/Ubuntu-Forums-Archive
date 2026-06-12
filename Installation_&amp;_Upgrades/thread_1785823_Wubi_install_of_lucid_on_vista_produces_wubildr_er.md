---
title: "Wubi install of lucid on vista produces wubildr error"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by J V on 2011-06-18
A wubi install of 10.04.2-amd64 is causing an error on boot:
```
Try hd(0,0): NTFS5 no wubildr
```From what I've read it seems like an error caused by a hidden partition (The recovery partition most likely) that needs to be manually corrected. Of course it isn't this easy as I can't access the relevant file (It doesn't exist in C:\ubuntu\* and I can't get into the lvp)

How do I fix this?

PS: I've got maybe 9 hours till they wake up, it's taken me 3 years and the luck of hotmail screwing up to convince the female portion of my house to even **try** to switch so please help me fix this!

Edit: Oh my it's way too late... I could just mount the disk file and edit in there couldn't I? But now that I think of it the file in question *should* have been in C:\ubuntu but I can't find it. Where is it?

Edit: 6 hours left tick tock! (Defragging... pretty much every file on that POS was ripped to shreds)

---

### Post by bcbc on 2011-06-19
> **J V said:**
> Try hd(0,0): NTFS5 no wubildr

That's not an actual error. Most likely you have problem #2 and need solution#1 as described in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

---

