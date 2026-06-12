---
title: "Changing Folder Write/Read Permissions"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-18
I just set up ubuntu on my laptop, and I have a shared ext3 drive between windows XP and ubuntu. Problem is, the folders I created under windows for storage of documents, music, etc. are only writable by root. How can I permanently change it such that I can write to these folders to store stuff? Currently they also show a little padlock icon beside them.

I will have the output of the fstab file from my laptop in a couple minutes.

-Dan

---

### Post by taurus on 2007-08-18
Since it's ext3, you can just change the ownership of the mount point for that partition from root to your login name and you can write to it whenever you want.  _Assuming_ your login name is **soundman** and it is being mounted to /media/storage. run

Applications -> Accessories -> Terminal
```
sudo chown -R **soundman**:**soundman** /media/storage
ls -la /media
```

---

### Post by dbsoundman on 2007-08-18
Excellent, thanks! The drive is actually my ubuntu /home directory, so I simply changed ownership of /home/dan to dan. All is well now.

-Dan

---

