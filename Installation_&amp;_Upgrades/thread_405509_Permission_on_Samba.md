---
title: "Permission on Samba"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-04-09
I have setup Samba and found that user are unable to download a file due to its permission. What permission do I need to set so users are able to download a file thru http access?

---

### Post by moffa on 2007-04-10
You have to setup the samba user for their permissions.  If you make the file readable by all it should work (ie chmod a+r)

---

### Post by textguru on 2007-04-12
> **moffa said:**
> You have to setup the samba user for their permissions.  If you make the file readable by all it should work (ie chmod a+r)

Will it propagate on the whole subfolder of the folder?

---

### Post by moffa on 2007-04-12
if you add a "-R" it changes the files and directories recursively
ie. chmod a+r -R folderName

---

