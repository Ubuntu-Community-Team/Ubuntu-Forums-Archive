---
title: "Wubi Ubuntu Installtion - Will it work"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2012-04-04
Hello, i have done a Wubi installtion of Ubunut through a Windows Vista-   BUT Have saved it onto another Partion

The windows Vista partion is going to be deleted  BUT NOT THE other Partion 

So, will Ubunut still work? or will i have to re set up everything again?

Thank You

---

### Post by Mark Phelps on 2012-04-04
If will not work on its own because it requires the Windows boot loader to get to it. 

If you were planning on replacing MS Windows with another version of MS Windows, you might be able to save off the current wubi install and reload it later.

But, if you remove MS Windows and don't replace it with another MS Windows version, you will not be able to get the wubi version back.

---

### Post by fiatveritas on 2012-04-04
It sounds like you're doing a clean install of Ubuntu because after you install Ubuntu you're going to get rid of the Vista Partition. If so, it might be just be easier to do a clean install with Ubuntu. If you're still planning on playing it safe, then you can run Ubuntu off a live CD/USB, create a partition from the installation option, and then delete the Vista partition in Ubuntu.

---

### Post by balkrish999 on 2012-04-04
> **Mark Phelps said:**
> If will not work on its own because it requires the Windows boot loader to get to it. 

If you were planning on replacing MS Windows with another version of MS Windows, you might be able to save off the current wubi install and reload it later.

But, if you remove MS Windows and don't replace it with another MS Windows version, you will not be able to get the wubi version back.


How do i  save off the current wubi install and reload it later.???

---

### Post by Mark Phelps on 2012-04-04
> **balkrish999 said:**
> How do i  save off the current wubi install and reload it later.???

I'm not an Wubi expert (don't really LIKE it), but from what I've read, you should be able to do the following:
1) Save the root.disk file to an external drive
2) Reinstall MS Windows -- which will erase that file
3) Reinstall Wubi -- which recreates that file
4) Plug in the external drive and copy the "old" root.disk file, over the top of the "new" root.disk file.

As I said, it might work -- but I've not actually tried it.

---

