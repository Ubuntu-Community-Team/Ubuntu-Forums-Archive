---
title: "Nautilus Won't Run in 8.04"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by liquidypoo on 2008-05-23
Long story short, before upgrading, I managed to accidentally delete my Desktop folder.  It was bugged into the Trash bin, never able to permanently delete, or properly restore.  But, that's all it did, and never caused me any other troubles otherwise.

But now that I've successfully upgraded to 8.04, it has become a major issue.  Now I can't browse my files through Nautilus.  Trying to go to Places > Home folder just brings up this message box:

[img]http://img396.imageshack.us/img396/522/screenshotnautilusru2.png[/img]

Any ideas?  Terminal commands I can do?  Make sure to be really step-by-step, as I'm still really new to Linux and Ubuntu.

---

### Post by joselin on 2008-05-23
Open a terminal and give your home directory the following perms:

```
chmod 755 /home/ed
```

Hope that helps.

Regards

---

### Post by liquidypoo on 2008-05-23
That didn't seem to make a difference.  Am I missing something when I'm typing that in?  I tried it by itself, and I also tried slapping sudo in front of it, but that didn't do anything either.  It asked me for my password, but it didn't do anything after that.

---

### Post by liquidypoo on 2008-05-24
Bumping because my problem still isn't solved.

---

### Post by RATM_Owns on 2008-05-24
```
sudo mkdir -p /home/ed/.Trash/Desktop
```

---

### Post by liquidypoo on 2008-05-25
> **RATM_Owns said:**
> ```
sudo mkdir -p /home/ed/.Trash/Desktop
```

THANK YOU!

That was the easiest thing in the world, and I wish I actually knew my terminal commands so I wouldn't have to bother the forum with such a stupid problem.

---

### Post by liquidypoo on 2008-05-26
Is there a way for me to fix this permanently by moving the Desktop folder out of .Trash?  I just restarted because of a system update, and I had to go to the terminal again to type that one line of code.

---

