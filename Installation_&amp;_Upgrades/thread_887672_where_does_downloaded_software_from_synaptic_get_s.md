---
title: "where does downloaded software from synaptic get saved"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by ranjithnair on 2008-08-12
Where does downloaded software from synaptic get saved so that I can have a backup and give it to my friends..

---

### Post by christianxxx on 2008-08-12
I'm not really sure here, but I always believed they where just installed. Sure, there will be temporary files, but I think part of the installation process is to clean this up. 
Anyways, they can always install it from their own synaptic as it is available to all ubuntu-users.

For other distributions there will be other repositories, and for other OS, there will be other sources.

---

### Post by zchenyu on 2008-08-12
I believe programs are stored in /usr, but you should confirm that.

And you can't just "give" programs like that. There are loads of stuff like dependencies, settings, etc that need to be transferred as well. Its really not worth it IMO. Just ask them to redownload the programs.

---

### Post by bedbug on 2008-08-12
/var/cache/apt/archives/

---

### Post by myle on 2008-08-12
And to clean them up, use
```
sudo apt-get clean
```

---

### Post by ranjithnair on 2008-08-12
thank you bedbug you are awesome

---

