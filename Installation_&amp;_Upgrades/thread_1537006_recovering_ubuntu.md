---
title: "recovering ubuntu"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by madeel on 2010-07-23
I was trying to install djvupdf. In that process I was recommeded by the system following command:

sudo apt-get install -f

It seems that it has destory the desktop envoirnment. I can now log in only at the command prompt. I don't know how to recover it. Moreover, I have also windows in one partition. I could access my the files on Ubuntu from windows but not any more. I can re-install ubuntu, but I have a lot of important data which I would like to copy first. 

Any help is greatly appreciated.

---

### Post by staf0048 on 2010-07-23
Ok, first of all, what type of media do you want to burn your files to?  USB drive, cd rom, external HDD, or just the windows partition?

---

### Post by utnubuuser on 2010-07-23
here's a *how-to* on restoring the desktop to default state, though I'm kinda guessing that's not really what you're looking for> [http://sazeit.com/articles/restoring-ubuntu]("http://sazeit.com/articles/restoring-ubuntu")

P.S. It's also possible to re-install Ubuntu without loosing documents/data.

It's especially easy if you've created a separate /home partition when you installed Ubuntu.
There are several good tutorials around on re-installing without formatting.

Basically, when you're doing an install, once you reach the stage of the installation process concerning partitioning, simply select manual partitioning, then select your Ubuntu / (root) partition, keep the settings as they are and UN-CHECK 'format this partition'.
Ubuntu will then be re-installed while documents/data are retained. (I've only done this on installations with separate /home partitions, but something tells me it works in single partition installations as well.

---

### Post by madeel on 2010-07-23
Thanks all of you for your help. Ubuntu has resotred now!!

---

