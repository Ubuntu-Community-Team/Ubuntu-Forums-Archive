---
title: "Samba fails to start"
date: 2018-07-10
forum: MINT
---

### Post by alansecker on 2018-07-10
This is actually on Mint 19 Cinnamon (which is based on Ubuntu 18.04). 
After spending many hours trying to get samba to work, I am desperate for some inspiration.

I have two virtual machines both installed on Mint 19 under VMware.

They were cloned from a separate pluggable drive successfully running on the same machine under Mageia 5.

Both will come up under Mint 19 but they will not connect with the samba shares representing five of the host's folders. 

# systemctl smbd status reports --foreground --no-process-group (five times, presumably one for each share).
# systemctl nmbd status the same, although only once.

Every folder assigned a share has had its 'sharing options' flag set.

I am only familiar with samba as a user going back over 15 years. This is the first time for at least ten that I have had any seemingly insoluble problem.

All five shares have been mounted on smb4k and can be accessed from it..

smb.conf has been checked under testparm. 
A replacement has been created from scratch.

I would appreciate some suggestions to overcome what is a real blocker right now.

TIA

---

### Post by howefield on 2018-07-10
Thread moved to the "*MINT*" forum.

---

