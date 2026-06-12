---
title: "Copy OS partition from one disk to another? Make it bootable?"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-17
I spend the vast majority of my time in Ubuntu, but every so often I still encounter the odd errand that requires a free copy of Windows that came with my hardware.

So I have Windows 7 on my laptop which I like slightly better than XP and a whole lot better than Vista. I am not in there a lot besides that its required for a web design class and sometimes for a few stubborn games, but I would very much like to copy my Windows 7 partition to a 100gb partition on my TB HDD.

Can it be done? How do I do it? Keep in mind, I am barely two tiers above noob on a scale of 1 to 20. I am working on it though.


I also want this partition to be bootable. I dont care if I lose the rest of the data on the disk. I want to redo everything anyway. I definitely want it to boot though, not just for the data to exist.

---

### Post by albandy on 2010-07-17
Better ask in a Windows forum, you can copy linux with a simple tar with permissions, but I don't know how to do it with windows.

Try backing-up the partition with partimage and restoring it in the new disk, but I don't know if it will work.

---

### Post by Nick_Jinn on 2010-07-17
Can I make a backup of a windows partition from Ubuntu on a USB? Where would I save it to?

---

### Post by albandy on 2010-07-17
Yes, with partimage you can copy any partition and restore it, but I think you should regenerate boot with windows install cd (I remember something like fixboot and fixmbr commands, but there are a lot of years since I don't use Windows).

Also if you only use Windows to do some little task you can virtualize it inside Ubuntu using virtualbox.

---

### Post by Nick_Jinn on 2010-07-17
How is gaming inside virtualbox?

It might work for my class though.



I was really hoping that I could just copy the whole partition the same way I would move a file. Is there a tool that does this?

---

### Post by Rubi1200 on 2010-07-17
Not sure if it will do exactly what you want, but check out Clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Nick_Jinn on 2010-07-17
> **Rubi1200 said:**
> Not sure if it will do exactly what you want, but check out Clonezilla:

[http://clonezilla.org/](http://clonezilla.org/)


Awesome. Thank you.


I may switch gears with how I approach this though. I created a new thread just to keep it neat and so anyone else can be helped by my questions.

[http://ubuntuforums.org/showthread.php?t=1532960](http://ubuntuforums.org/showthread.php?t=1532960)



Hmmm. Is Clonezillia an app I can run in Ubuntu? it looks cool but I would even resort to a less efficient app if it was something simple I could add from synaptic.

---

### Post by Rubi1200 on 2010-07-17
> **Nick_Jinn said:**
> Awesome. Thank you.


I may switch gears with how I approach this though. I created a new thread just to keep it neat and so anyone else can be helped by my questions.

[http://ubuntuforums.org/showthread.php?t=1532960](http://ubuntuforums.org/showthread.php?t=1532960)



Hmmm. Is Clonezillia an app I can run in Ubuntu? it looks cool but I would even resort to a less efficient app if it was something simple I could add from synaptic.

Clonezilla is/should be run as a LiveCD:

[http://www.clonezilla.org/clonezilla-live/](http://www.clonezilla.org/clonezilla-live/)

---

### Post by Nick_Jinn on 2010-07-17
I just read that. Thanks.

Hey, if I reinstall Ubuntu, will grub detect the operating systems on the other hard drive and add it? Currently it is not detecting it.

---

### Post by Rubi1200 on 2010-07-17
> **Nick_Jinn said:**
> I just read that. Thanks.

Hey, if I reinstall Ubuntu, will grub detect the operating systems on the other hard drive and add it? Currently it is not detecting it.

What do you have installed on the other drive?

And, yes, in theory, GRUB will detect and add an entry for other operating systems if it is installed after those systems.

---

### Post by C.S.Cameron on 2010-07-17
If you are still looking at cloning a bootable partition look at the dd command.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

