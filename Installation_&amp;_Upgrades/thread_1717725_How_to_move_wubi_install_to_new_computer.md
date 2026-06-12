---
title: "How to move wubi install to new computer"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by StutteringJohnSmith on 2011-03-30
I have installed ubuntu desktop on my computer using wubi and its running great but I am about to get a new computer and I dont want to reinstall, reconfig and setup everything again..   Can someone please tell me the steps of moving my wubi install to the new computer

---

### Post by Mark Phelps on 2011-03-30
Don't use Wubi, but what I've been told will work is the following:
1) Backup your existing Wubi file (root.disk) to an external drive
2) Install Wubi as usual in the new PC
3) Plugin the external file and copy the old file over the new one.

I believe that you do this with only the root.disk file, but perhaps someone with actual Wubi experience can provide more details ...

Also, you should really post this in the Wubi subforum -- as folks there are more likely to be able to provide detailed answers.

---

### Post by Rubi1200 on 2011-03-30
> **Mark Phelps said:**
> Don't use Wubi, but what I've been told will work is the following:
1) Backup your existing Wubi file (root.disk) to an external drive
2) Install Wubi as usual in the new PC
3) Plugin the external file and copy the old file over the new one.

I believe that you do this with only the root.disk file, but perhaps someone with actual Wubi experience can provide more details ...

Also, you should really post this in the Wubi subforum -- as folks there are more likely to be able to provide detailed answers.
It's not quite as simple as that.

> Also, you should really post this in the Wubi subforumWhat Wubi subforum? 

@StutteringJohnSmith
the following link is by bcbc, an expert on Wubi installs. It describes what you need to do in this situation:
[http://ubuntuforums.org/showpost.php?p=10584729&postcount=4](http://ubuntuforums.org/showpost.php?p=10584729&postcount=4)
Obviously, change drive letters for the relevant ones on your computer. In this situation, you want to save the root.disk to an external medium as Mark Phelps described above. Then, follow the steps to reinstall Wubi on the new computer and get the old root.disk back.

---

