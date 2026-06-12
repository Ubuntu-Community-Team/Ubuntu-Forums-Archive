---
title: "what happens to modified configuration files during upgrade?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by ittayd on 2008-10-30
Hi,

I'm sorry if this is a FAQ, 

I want to upgrade to 8.10. I have modified some system configuration files, mostly with hacks trying to get stuff (special keyboard keys, bluetooth, hibernate, etc.) to work.

What happens to these files during upgrade?

Optimally, I would like the upgrade process to move the modified files and write "vanilla" files instead, so as to allow me to sort through the changes I've made to determine which is no longer needed. If the upgrade doesn't do that, is there another way in which this can be done (before the upgrade)?

Ittay

---

### Post by Partyboi2 on 2008-10-30
You should have an option during the upgrade to view, keep  or overwrite the modified files.

---

### Post by ittayd on 2008-10-30
If I choose 'overwrite', are my files lost? If so, is there a way of creating backup copies before?

---

### Post by satellite360 on 2008-10-30
> **ittayd said:**
> If I choose 'overwrite', are my files lost? If so, is there a way of creating backup copies before?

They are lost but you can create a backup.  The upgrade will stop and wait for you to tell it what to do with the file at which point you can make your backup before continuing.

---

### Post by ittayd on 2008-10-30
Thank you for your replies. 

Sounds like the process is slow (waiting to be prompted per file, then going to a shell to backup). Is there a way of backing up all modified files before starting the upgrade?

Ittay

---

### Post by Partyboi2 on 2008-10-30
> **ittayd said:**
> Thank you for your replies. 

Sounds like the process is slow (waiting to be prompted per file, then going to a shell to backup). Is there a way of backing up all modified files before starting the upgrade?

Ittay
Not really, unless you already know the files you have modified. But you can make the backups  during the upgrade as mentioned.

---

