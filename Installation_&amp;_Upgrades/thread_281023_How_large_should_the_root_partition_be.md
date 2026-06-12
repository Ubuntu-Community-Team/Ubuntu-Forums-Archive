---
title: "How large should the root partition be?"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Aleksandersen on 2006-10-20
Hi,

How large should the root partition be? My current partition is 6 GB and I was surprised to find that it got full so fast. I believed that my home partition should be as large as possible. Therefor I did not dedicate enought storage to the root partition.

Anyhow: I am going to need to correct this now and I am therefore asking how large the root partition should be?

I only have one 40 GB hard drive.

---

### Post by aysiu on 2006-10-20
I'm surprised you filled it up. With Xubuntu, Ubuntu, Kubuntu, and IceWM, and all my programs, mine's never gotten larger than 3.5 GB.

---

### Post by taurus on 2006-10-20
If you have a seperate /home and your / eats up almost 6GB, it means that you probably install everything there is, including a kitchen sink!  You can clean out your /tmp and the archives from synaptic/apt-get/aptitude...  That would save you some space on /.

---

### Post by Aleksandersen on 2006-10-20
taurus: That gave me one gigabyte free space. Thanks!

I really does not know what is taking so much storage on that partition. :/

---

### Post by taurus on 2006-10-20
Did you install all the window managers like Gnome, KDE, XFce4, etc.?

---

### Post by Aleksandersen on 2006-10-20
I have Gnome (Default) and KDE (required to run some apps).

---

### Post by taurus on 2006-10-20
Maybe you should remove some apps that you don't use to free up more space for /!

---

### Post by jpmrblood on 2006-10-20
You could clean up your /var/lib/dpkg/archives/ from packages.
```
#> sudo apt-get clean 
```

If you could see, the /usr is the culprit, especially in /usr/share . Uninstall any unuseful programs should do the trick.

---

### Post by H.E. Pennypacker on 2006-10-22
> **Aleksandersen said:**
> taurus: That gave me one gigabyte free space. Thanks!

I really does not know what is taking so much storage on that partition. :/

I know there's something called Boab (sp?) or something that tells you what directory is taking up what amount of space.  It's very useful, but you may have dependency problems, as I did.

Let me know if you find the name.

---

### Post by H.E. Pennypacker on 2006-10-22
Sorry about that...it turns out its called Baobab.  If you download the .deb from its website, you'll likely get dependency problems.  Just download and install it through the terminal by using sudo aptitude install baobab.    Then look for it under Accessories!

---

### Post by Aleksandersen on 2006-10-24
Should seven gigabytes be a safe size?

---

