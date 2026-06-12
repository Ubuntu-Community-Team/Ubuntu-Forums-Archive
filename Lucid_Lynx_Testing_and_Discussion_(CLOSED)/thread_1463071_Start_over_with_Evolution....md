---
title: "Start over with Evolution..."
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by beow on 2010-04-26
Did a fresh install with Lucid. When starting Evolution it starts the new account wizard. Is it not supposed to pick up the settings from ~/.evolution ?

---

### Post by Merk42 on 2010-04-26
You did a fresh install, unless you kept /home on a different partition, it got erased thus there is no setting in ~/evolution.

---

### Post by beow on 2010-04-27
> **Merk42 said:**
> You did a fresh install, unless you kept /home on a different partition, it got erased thus there is no setting in ~/evolution.

Sorry, I did keep /home on a separate partition, just upgraded the / partition. The .evolution directory is there.

---

### Post by beow on 2010-04-28
Is it possible somehow to skip the wizard and "attach" to the existing profile (i.e. the existing ~/.evolution)? I have not backed up the settings and can thus not restore the backup.

---

### Post by bennachie on 2010-04-28
I have just completed a clean install, formatting only the "/" partition, and replacing an earlier version of Lucid. The process worked perfectly. However, I assume that you had Karmic installed previously - it's just possible that moving to a later version of Evolution has something to do with the problem.

You might want to try re-installing Karmic in the "/" partition, and see if the Karmic version of Evolution picks up the settings properly. That would at least allow you to backup those settings (and restore them after the second installation of Lucid) without too much messing around.

If that doesn't work, I guess that you'll have to re-establish the account settings manually and import the older messages from the various mbox files you find in the .evolution directory. That's tedious work, and sufficient, I imagine, to guarantee that you use the backup facility regularly in future!

---

### Post by ankspo71 on 2010-04-28
Silly question but...
Are your other settings still there? (like gnome theme settings, firefox settings, bookmarks, etc) If not, did you remember to tell the partitioner to use your /home partition (but not format it) when doing the installation?  

The good news is, if you forgot to tell the partitioner to use the /home partition, you should be able to find all of your settings on an unmounted partition on your drive somewhere, and be able to copy them over to your current home partition. Edit: It would probably be better to reinstall in this case and telling the partitioner to mount your /home partition (but not format it).

If you told it to format your /home partition then that would mean bad news.

---

### Post by bennachie on 2010-04-28
That's a very good question indeed. However, if he didn't mount his old home partition as "/home", the destination for his various settings under your proposed solution would have to be his "/" partition - which may not be large enough for the purpose. It might therefore be better to rerun the Lucid installation (and, of course, to mount, but avoid formatting, the "/home" partition).

---

### Post by ankspo71 on 2010-04-28
> **bennachie said:**
> That's a very good question indeed. However, if he didn't mount his old home partition as "/home", the destination for his various settings under your proposed solution would have to be his "/" partition - which may not be large enough for the purpose. It might therefore be better to rerun the Lucid installation (and, of course, to mount, but avoid formatting, the "/home" partition).

That's a very good point to consider. I forgot what it's like to have limited free space.

---

### Post by beow on 2010-04-28
> **ankspo71 said:**
> Silly question but...
Are your other settings still there? (like gnome theme settings, firefox settings, bookmarks, etc) If not, did you remember to tell the partitioner to use your /home partition (but not format it) when doing the installation?  


That may be the case. I erased my gnome settings (erased the infamous .gnome .gnome2 .gconf .gconfd .metacity directories). Does evolution setup depend on these directories? Thought keeping .evolution would be enough.

There is no problem with the /home partition, it is correctly mounted.

---

### Post by philinux on 2010-04-28
> **beow said:**
> That may be the case. I erased my gnome settings (erased the infamous .gnome .gnome2 .gconf .gconfd .metacity directories). Does evolution setup depend on these directories? Thought keeping .evolution would be enough.

There is no problem with the /home partition, it is correctly mounted.

Personally I would do a clean install. Just done one and evo picked up my old settings on first run. I do back it up too to ubuntuone.

---

### Post by beow on 2010-04-28
> **philinux said:**
> Personally I would do a clean install. Just done one and evo picked up my old settings on first run. I do back it up too to ubuntuone.

I did a clean install, but kept the old /home partition, See no difference between this and erasing and restoring everything on the /home directory.

---

