---
title: "how to go back to original packages after upgrade/install"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2010-12-14
Hi, I just did a fresh install from 8.04 to 10.04 with separate "/" and /home partitions. 


I really wanted a new 10.04 system to start from scratch and rebuild it again & differently. Instead I got a really messed up system. 


Is there any way to change it to a fresh new 10.04 install. That nothing has been added to yet?


This is very important because on 10.04 my video card won't handle all the mods that I had on 8.04 and my system freezes very soon after I log on.


Thank you in advance.

---

### Post by dabl on 2010-12-14
The hidden "dot" files in the partition you are now using for /home carry the settings from your prior system.  This is the big disadvantage of using a /home partition, versus symlinking your data folders into the /home partition.

To get rid of the settings, you can delete all of the files in that partition that begin with ".", such as ".adobe", ".alsaplayer", ".audacity-data", etc. etc.

Then, reformat (make a new ext4 filesystem) on the partition that you are using for "/", but don't reformat the one for /home.

Now you should be able to install 10.04, selecting the second partition for /home, and end up with a clean new 10.04 system.

---

### Post by Dutch70 on 2010-12-14
Great!!! I was beginning to think it was unheard of. 
Is there any "." files that I wouldn't want to delete, 
Or can I just highlight every single one of them & select delete?

---

### Post by dabl on 2010-12-14
Technically there are a couple of the dot files that support your current X session, including .ICEauthority and .Xauthority.  But, since you are reinstalling, there's no downside to selecting them all, and deleting them.  I would advise doing it from a Live CD session.

---

### Post by Dutch70 on 2010-12-17
Ok...where do I find those "hidden" .dot files? I know I've ran across them before, but can't seem to find them now.

---

### Post by efflandt on 2010-12-17
To see hidden dot files in **Places** press **Ctrl**+**H**, or in terminal or console do **ls -a** or **ls -al**

---

### Post by Dutch70 on 2010-12-17
Wonderful, Thank you very much dabl & efflandt. :)

---

