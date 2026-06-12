---
title: "One BIG PROBLEM!...recovering old installation settings from new install..."
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by padmanabh on 2007-06-26
I had asked before also...how do I do this?

I upgraded my old install(7.04) and it's KDM got corrupted..however...I still have lot of packages on that installation...not to mention my desktop settings...i'd like to keep.

But it simply won't recover...so Iinstalled a 6.10 on a new partition. Now I can boot into it and all and see the old install plus the new install....

Now what do I do to get this new install to use  settings from my old install...or rather how do I recover my old install from here?:(

---

### Post by padmanabh on 2007-06-26
i forgot to mention...my dpkg and apt is corrupted in the old install ... :)

---

### Post by EndPerform on 2007-06-26
If you mean settings for applications you use, most of those are stored in hidden files and directories under your home directory.  If you open a terminal and type:

```
ls -la
```

you'll see a whole slew of different files and directories which contain configuration information as well as other things.

---

### Post by padmanabh on 2007-06-27
I have those....But I mean...how do i get the packages I had installed through apt,  on previous install....do I have to reinstall all of them again?! also how do then I update apt and dpkg configuration to reflect those packages?

---

### Post by EndPerform on 2007-06-28
> **padmanabh said:**
> I have those....But I mean...how do i get the packages I had installed through apt,  on previous install....do I have to reinstall all of them again?! also how do then I update apt and dpkg configuration to reflect those packages?

Your safest bet would be to reinstall them on the new install.  I'm not sure exactly where apt keeps all of it's databases and the like, but reinstallation would be the safest bet.   As far as getting a list of what's currently installed, I'm not sure of a command-line way to do that, but you can still get into your desktop without KDM

Try this.  Create a file called .xinitrc in your home directory (note the starting dot, that's important), and put this line in it:

```

exec startkde

```

then save the file.  At the prompt, type startx and it should load up KDE for you.  Once in you can use Adept or Synaptic to see what you have installed if you still want to reinstall.

---

### Post by padmanabh on 2007-06-30
OK thanks ...I'll try that... :)

---

