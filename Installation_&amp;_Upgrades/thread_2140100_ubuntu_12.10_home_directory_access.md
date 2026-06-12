---
title: "ubuntu 12.10 home directory access"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by Rumman2013 on 2013-04-28
hello 
I am a simple ubuntu user. Recently I 've **upgraded **my **ubuntu 12.04 to ubuntu 12.10**, but in my new ubuntu** i can not access my previous **directory which is shown under the home directory. I can see there is two locked file, one is titled "access-your-praivre-data.desktop" (if i click on it, it launches a terminal but wihtout showing anything it got closed immediately) and another is titled "readme.txt".
The readme.txt says:
 ("THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private"). 

I did as it said here, but it didnt do anything and I still can not access to my previous important data. Is there anyone can help me with this problem. It would be highly appreciated. Please help me.
Thanks
Rumman

---

### Post by darkod on 2013-04-28
ecryptfs sounds like encryption. Did you have your home folder encrypted, or similar?

---

### Post by Rumman2013 on 2013-04-28
I think it is encrypted or something like that automatically

---

### Post by darkod on 2013-04-28
Automatically it's not, only if you select it.
I hope you have the encryption passphrase because there is no way to access the data without it.

If you have the passphrase you can try accessing the data from live mode with this:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by Rumman2013 on 2013-04-29
thank you for ur quick reply, i am reading the link right now, and then i will try to implement that. I will let you know the result afterwards.

---

