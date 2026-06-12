---
title: "Gnome panel trying to open places in dolphin"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by crazybus on 2008-10-16
I just installed ibex from the alternate cd over a hardy home directory partition.  There must be a old config file because loading a folder from the gnome-panel tries to load dolphin. (the computer, cd/dvd creator and a few others still load in nautilus)

Also if I drag a folder into the panel and load it then it comes up with the same error.  All folder loaded from the desktop or anywhere else work find and the Open Folder setting is set to "nautilus --no-desktop %U"

When I installed konqeuror (after getting the errors) the gnome-panel folders now open in dolphin while desktop ones open in nautilus.  It's really annoying so I hope someone can help me.  Thanks everyone in advance.

The exact error I get is 

Could not open location file://home/user

Failed to execute child process "kfmclient (No such file or directory)"

---

### Post by taavikko on 2008-10-16
How about doing little searching before posting, that's a known bug
[https://bugs.launchpad.net/bugs/260492](https://bugs.launchpad.net/bugs/260492)

---

### Post by crazybus on 2008-10-16
I did search and found a 2 year old bug and tried it's fixes.  But I missed the newer ones.  Sorry.  Will try searching harder next time :)

---

### Post by taavikko on 2008-10-16
> **crazybus said:**
> I did search and found a 2 year old bug and tried it's fixes.  But I missed the newer ones.  Sorry.  Will try searching harder next time :)

Yeah, this is a bit confusing bug, for people generally refers it as an 
gnome-panel, since the launcher resides in it.

But I hope you were able to fix it, by the workarounds explained in launchpad.

---

