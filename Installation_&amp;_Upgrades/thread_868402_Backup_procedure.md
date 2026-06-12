---
title: "Backup procedure"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Javawag on 2008-07-23
Hi,

This is probably quite an obvious question (the answer being "no"), but basically, in Windows, I used to backup my documents manually and restore them if i changed computer etc. I was unable to backup literally everything on my pc as it's hard to take a decent backup of the registry and so on. However in ubuntu this is not the case as everything is stored as files. So my question is, if i take a backup of the root folder and restored it to a new computer, would my entire linux install be restored correctly?

- Javawag

---

### Post by xen-uno on 2008-07-23
If you check System State in NTbackup under Windows, the registry & hives will be backed up correctly. In Linux, assuming you back up / (root) and all sub directories + all hidden files/directories, you should be able to move that to another machine, but only if it's hardware identical (especially in the video and hard drive partition makeup).

---

### Post by Javawag on 2008-07-23
> **xen-uno said:**
> If you check System State in NTbackup under Windows, the registry & hives will be backed up correctly. In Linux, assuming you back up / (root) and all sub directories + all hidden files/directories, you should be able to move that to another machine, but only if it's hardware identical (especially in the video and hard drive partition makeup).

Ahh cool, ok by hardware identical, would it be ok if the hard drive was of a  different size, as long as the partitions were the same i.e. hda1 being / (root) and i think on mine its hda5 as /windows, and the graphics card was different (although still nvidia)?

I guess if not, i could just copy over my home directory, most of my settings and files would be there anyway. If i do that, is there some way i can export a list of installed packages such that i can import then later rather than having to reinstall each one separately through synaptic?

- Javawag

EDIT: Thanks for the quick reply by the way! Sorry, my manners have left as it's almost 3am where I am xD

---

### Post by xen-uno on 2008-07-23
I think if the vid card is in the same "family", you shouldn't have problems there. Differences in partition sizes wouldn't matter too much either (worst case is you have to rebuild grub's menu.lst). I've done what your trying to do with Windows a few times ... most of the time successfully.

---

### Post by Javawag on 2008-07-24
> **xen-uno said:**
> I think if the vid card is in the same "family", you shouldn't have problems there. Differences in partition sizes wouldn't matter too much either (worst case is you have to rebuild grub's menu.lst). I've done what your trying to do with Windows a few times ... most of the time successfully.

Cool... well i'll do a full backup then and try restoring all of it and if that fails i'll just restore my home folder!

Thanks for the advice!
- Javawag

---

