---
title: "Cannot copy files to remote xubuntu using rsync"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-17
I have tried this command on the source xubuntu machine and wanting to copy all the files to remote machine:

sudo rsync -v -u -a -r --delete --rsh=ssh /var/cache/apt/archives/ ubuntu@192.168.1.20:/var/cache/apt/archives 

when I type the remote user's password it gives me this prompt:

building file list ... done
./
rsync: failed to set times on "/var/cache/apt/archives/.": Operation not permitted (1)

with rsync error like this:

rsync error: received SIGUSR1 or SIGINT (code 20) at rsync.c(163)

I have tried this before but now it doesn't work. Hope you might help

---

