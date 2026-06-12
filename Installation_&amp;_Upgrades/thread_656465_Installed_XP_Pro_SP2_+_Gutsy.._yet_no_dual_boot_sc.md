---
title: "Installed XP Pro SP2 + Gutsy.. yet no dual boot screen..."
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2008-01-02
I decided to redo my desktop and get rid of Win 2k Pro since I have a version of XP Pro SP2 now. Well, I formatted the whole darn thing, put XP on, then put on Gutsy.

Well when I rebooted it went right into XP. WTF?

So I reinstalled Gutsy... same issue...

My partitions are set up like this...

30gb NTFS Win XP Pro
1gb Swap
15gb /
200gb /home

Never did I have this happen before. Every time I've done fresh installations with Windows first and Ubuntu second have I had an issue... I'm befuddled.

---

### Post by Craigus on 2008-01-02
Where are you installing grub ?

---

### Post by zvacet on 2008-01-02
Maybe [this](http://ubuntuforums.org/showthread.php?t=224351&highlight=ubuntu) will help you.

---

### Post by Roasted on 2008-01-03
> **Craigus said:**
> Where are you installing grub ?

Wherever the default is, I guess. I've NEVER specified where to install grub, ever. I'm positive I've done nothing different during this install than I did with the previous installs, hence why I'm completely confused.

---

### Post by Craigus on 2008-01-03
See if supergrub can assist:


[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Roasted on 2008-01-03
I booted to supergrub. I selected ubuntu, got error 21... I forget the message. Something about something being nonexistent. I got the same thing with my windows partition, too.

So I decided to just reinstall ubuntu and watch a springer rerun on tv. Sure enough, everything works great now. Yet I'm positive I changed nothing... I used the same exact ubuntu gutsy cd, same settings, same installation, etc....

---

