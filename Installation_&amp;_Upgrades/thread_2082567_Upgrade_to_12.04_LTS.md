---
title: "Upgrade to 12.04 LTS"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by gigster77 on 2012-11-09
I installed 10.04 LTS using Wubi.  There is 12.04 LTS and I want to upgrade.  Can I just upgrade using Update Manager in Ubuntu and not cause any issues with my current Windows setup?

---

### Post by critin on 2012-11-09
> **gigster77 said:**
> I installed 10.04 LTS using Wubi.  There is 12.04 LTS and I want to upgrade.  Can I just upgrade using Update Manager in Ubuntu and not cause any issues with my current Windows setup?

I would't, but it probably can be done.  If you possibly can, it's best to install into a new, separate partition.  If you absolutely can't deal with partitions, there are instruction in this link that should help.  Read carefully and fully before actually doing anything.

Will it cause issues with Windows?  Possibly.  Windows is pretty sensitive.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by ibjsb4 on 2012-11-09
Hi gigster77, welcome to the forum  :)

That's the way its set up to work, but there is no guarantee that will happen.

Have a plan "B" (backup).  Do you have a restore CD for windows?  Backup any files stored in your wubi install.

Your going from Gnome2 (10o4) to Gnome3 (12o4); having to cleanup/repair afterward is common.

Have you considered going to a dual boot setup?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=dual+boot&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by gigster77 on 2012-11-09
Thanks!  :)

Yeah the only reason I haven't done a dual boot is because this is my work laptop.

It was already set up with Windows, so I didn't want to interrupt the current setup since I need this on a daily basis.

I was hoping I can just do the update via update manager.  Has anyone tried this before?  Any experiences?

---

### Post by ibjsb4 on 2012-11-09
Keep in mind that usually people with problems post in the forum and not the people with success stories  :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wubi+upgrade+to+12.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=wubi+upgrade+to+12.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by critin on 2012-11-09
> **gigster77 said:**
> Thanks!  :)

Yeah the only reason I haven't done a dual boot is because this is my work laptop.

It was already set up with Windows, so I didn't want to interrupt the current setup since I need this on a daily basis.

I was hoping I can just do the update via update manager.  Has anyone tried this before?  Any experiences?

Long ago, (years) I used wubi and was glad to see the upgrade offered.  I upgraded but lost the ability to log into windows.  I'd used it about a year but never had any problems--thus had no idea how to fix it and didn't know who to ask.    I just went to dual booting after a while of no ubuntu.  

Now, you can get good help here on the forums, so I wouldn't worry too  much.

---

### Post by bcbc on 2012-11-10
You need at least 3GB of free space. The upgrade manager doesn't check properly. If you backup your \ubuntu\disks directory beforehand, then you can just move it back later if the upgrade failed.

---

