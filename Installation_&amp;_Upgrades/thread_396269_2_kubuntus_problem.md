---
title: "2 kubuntus problem"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by qoqosz on 2007-03-29
I have installed second kubuntu on my laptop, just to test it. Unfortunately I encountered some problems while booting an older version - it doesn't mount my /home partition. Here is an error mesaage

```
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=82138455-bd74-4353-a174-b113b8d63f45'
fsck died with exit status 8
```

And I dunno what to do with it. I have to manually mount unfortunate partition and continue booting process.
Both kubuntus are 7.04.

---

### Post by rillip on 2007-03-29
I don't have any experience with Fiesty, you might want to post this in the Development (Feisty Fawn) > Feisty Fawn Discussions, as the thread below was a similar issue and has been move

---

### Post by confused57 on 2007-03-29
> **qoqosz said:**
> I have installed second kubuntu on my laptop, just to test it. Unfortunately I encountered some problems while booting an older version - it doesn't mount my /home partition. Here is an error mesaage

```
fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=82138455-bd74-4353-a174-b113b8d63f45'
fsck died with exit status 8
```

And I dunno what to do with it. I have to manually mount unfortunate partition and continue booting process.
Both kubuntus are 7.04.
The UUID identification in your /etc/fstab probably has changed for your /home partition.  This link should help you determine the new UUID and how to edit your fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)
this was written for Edgy, but I would think the same applies for Feisty.

---

### Post by qoqosz on 2007-03-30
Thanks for great link!

---

