---
title: "how to extract rar files?"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by abhilashm86 on 2008-10-07
i am not able to extract rar files...............is it possible to extract in ubuntu linux?please help...............

---

### Post by jerome1232 on 2008-10-07
Yes you just need a package installed, unrar, and rar. After installing those you should be able to extract and create rar's using fileroller (that's the default program for graphically extracting archives)
```
sudo apt-get install unrar rar
```

---

### Post by Liviu-Theodor on 2008-10-07
Also the [FONT="Courier New"]Archive Manager[/FONT] program can do it, from the [FONT="Courier New"]Applications->Accessories[/FONT] menu. Just install it first if you don't have it. This is good if you want a graphic interface. The [FONT="Courier New"]rar[/FONT] and [FONT="Courier New"]unrar[/FONT] programs work in the command line.

---

### Post by zvacet on 2008-10-07
After installing rar and unrar just right click on rar file you want to extract and select **extract here**.

---

### Post by Liviu-Theodor on 2008-10-07
> **zvacet said:**
> After installing rar and unrar just right click on rar file you want to extract and select **extract here**.

This is one of the many things I like about a modern and well-thought Linux distribution: we can find many solutions to the same problem, and one can choose whatever he/she likes, even more than one, because it is not chained in thinking by some "big brother". Of course your solution is valid, as it is mine. I will not say which one is better, because that is a matter of personal preferences.

---

### Post by jerome1232 on 2008-10-07
Liviu-Theodor is correct in saying rar and unrar are command line only programs but they are integrated into another gui program

Just for clarification rar and unrar integrate into file roller (the default archive manager), which means (after installing rar/unrar) you do have a gui to create/extract rar files. 
.

You will notice there are just about always 50 different ways to accomplish a task :)

---

