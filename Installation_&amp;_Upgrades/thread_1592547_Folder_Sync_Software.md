---
title: "Folder Sync Software?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by csharpplus on 2010-10-10
I a newbie, so thanks in advance for any help.

I have a folder (let's call it folder**A**) that have its contents changed every day. I would like to keep an _exact copy_ of the contents that are in folder**A** in a different folder (let's call it folder**B**).

What is the simplest program (running from the command line) that will achieve this?

_Note:_ folder**A **can change by either of the following:
           (i)  new files are added to it.
           (ii) existing files are deleted from it.

folder**B** will have to reflect these changes (so new files must be added to it; and old files -- that were removed from folder**A** -- must be removed also from it). thanks for helping!

---

### Post by mikewhatever on 2010-10-10
Rsync.

```
rsync -av /folderA/ /folderB/
```

---

### Post by Dex73 on 2010-10-10
> **mikewhatever said:**
> Rsync.

```
rsync -av /folderA/ /folderB/
```

You beat me to the answer. Although, if you would like to save the command for frequent use, (so it will just be there) luckybackup uses gui and has rsync as it's backend. I'm not sure if the command line would offer this.

---

### Post by csharpplus on 2010-10-10
that you both!

Would rsync know to delete from folder**B** files that are no longer in folder**A**?

Also, can I define that 'copying' must be done only from folder**A **tofolder**B** (meaning, folder**A** 'determines' how folder**B** would look like -- not vice versa)?

---

### Post by mikewhatever on 2010-10-10
To delete the files, use the --delete switch:

rsync -av --delete /source /destination

Look at 'man rsync' for more options.

---

### Post by csharpplus on 2010-10-10
great, thank you!

---

