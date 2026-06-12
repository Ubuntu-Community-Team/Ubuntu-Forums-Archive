---
title: "how i can make upgrade instlation size?"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by abo3azzoz on 2010-07-10
hi
please i'm instled ubuntu 10.4 and instlation size 3GB and at this time when i want to instaling a softwere ubuntu told me there is no space.
can i make upgrade for installation size or i must to reinstalling Ubuntu and put installing size 12GB?


thank u

---

### Post by oldfred on 2010-07-10
3GB is pretty small. 

I generally recommend 10-20GB for the install, 2GB for swap or RAM memory size if you want to hibernate and the rest of the space you want to allocate to /home. 

It depends a lot on what you want to do, how much you are installing and saving. Are you sharing with windows, if most of your data is in a shared partition then less space is required. If you have a large hard drive you can easily allocate more.

---

### Post by abo3azzoz on 2010-07-10
thank u for replying

but when i open the hard disk from windows visita  i saw free space 9 GB (for the other drive that i instaling ubuntu }

that mean i have to reinstalling Ubuntu and put the installation size 12GB as the max number n the menu


thank u again .

---

### Post by oldfred on 2010-07-10
If all you have is 9GB free you do not have enough room. Windows (and Ubuntu) needs about 20% free space to keep working well.

From the liveCD mount all your partitions by clicking on them to view and then in the terminal run this. It only shows use on mounted drives.

df -Th | sort

---

