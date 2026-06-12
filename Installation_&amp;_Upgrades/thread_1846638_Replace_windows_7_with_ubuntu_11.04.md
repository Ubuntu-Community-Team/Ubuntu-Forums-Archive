---
title: "Replace windows 7 with ubuntu 11.04"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by naikmanoj1991 on 2011-09-19
Currently I m using windows 7. Now want to replace windows 7 with ubuntu 11.04. In my machine already have 4 partition..i want install ubuntu 11.04 on the first partition where windows 7 is install. Because i don't want to lost my other data which is included in other partition....I was try to do this....but during boot installation its take my whole disk space...plz suggest me how to install this........

---

### Post by dino99 on 2011-09-19
follow my way:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by naikmanoj1991 on 2011-09-20
> **dino99 said:**
> follow my way:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)
hey i dont want dual boot...just i want to replace windows with ubuntu..by keeping windows partition...and want to install ubuntu on windows loader partition(i.e. C: drive in C)

---

### Post by mörgæs on 2011-09-20
Welcome to the fora.

You can run Gparted in a live boot and delete the Windows partition(s) you don't want, that is everything except the data partition (I guess).

After this you can just run the normal Ubuntu install. It will suggest to install in the empty space.

---

### Post by naikmanoj1991 on 2011-09-22
k...thxxx

---

### Post by Mark Phelps on 2011-09-22
You DO realize, of course, that not ALL of your "data" exists on the data partition, right?  MS Windows stores quite a lot of data (personal and otherwise) in various directories that are now down under C:\Users\<username>\ ...

IF you downloaded or copied music, video, or picture data to your PC and allowed it to default to where to store that, it's most likely down under \Users ... somewhere.

So, BEFORE you remove your Win7 OS partition, you might want to go through there and back off the data contained in the \Users area.

---

### Post by naikmanoj1991 on 2011-09-22
> **Mark Phelps said:**
> You DO realize, of course, that not ALL of your "data" exists on the data partition, right?  MS Windows stores quite a lot of data (personal and otherwise) in various directories that are now down under C:\Users\<username>\ ...

IF you downloaded or copied music, video, or picture data to your PC and allowed it to default to where to store that, it's most likely down under \Users ... somewhere.

So, BEFORE you remove your Win7 OS partition, you might want to go through there and back off the data contained in the \Users area.

**Ok.Thx..I was replaced Ubuntu 11.10 with Windows 7 before 2-3 days**

---

