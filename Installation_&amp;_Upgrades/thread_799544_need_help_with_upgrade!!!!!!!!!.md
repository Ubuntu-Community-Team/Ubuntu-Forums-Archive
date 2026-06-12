---
title: "need help with upgrade!!!!!!!!!"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by pkpmoa1536 on 2008-05-19
I am currently running feisty and want to upgrade all the way to hardy, but I am having a little trouble with my upgrade from feisty to gutsy.  When I go to the upgrade manager and click install updates" it begins to run through the motions, but an "Error during update" window pops up and it says that a problem occured whild trying to fetch :  

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz) 404 Not Found


:confused:I don't know what to do now and need any help I can get.  Thanks.

---

### Post by Thanoulis on 2008-05-19
Seems that it is a user-defined repository...edit */etc/apt/sources.list* and comment these two lines.

---

### Post by Bubba64 on 2008-05-19
If you have over 389 ram you can download a daily ISO of Hardy CD desktop. Now I know people go from Dapper to Gutsy I think with the upgrade manager install, but I am not sure about doing the same with Feisty. Here is the daily download link.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
And here is the alternative daily link.
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)
From your post though it looks like you have a 3rd party repository open in software sources, located in either synaptic or system-administration-software sources. I could be totally wrong though I am not an expert. I have seen other people suggest another mirror or the main repository in this sort of situation as well. So you want to make sure you can go from Feisty to Hardy directly with the desktop CD or just use the alternative fresh install which will overwrite the whole distribution except for anything you want to save in a partition that wont be changed by the alternative install. Good Luck and look around for more answers.

---

### Post by pkpmoa1536 on 2008-05-20
so, I would be able to do a fresh install of Hardy without losing all me pictures, files, music, and videos?  How exactly does that work...I am not still pretty new and learning as I go.

---

### Post by Bubba64 on 2008-05-20
> **pkpmoa1536 said:**
> so, I would be able to do a fresh install of Hardy without losing all me pictures, files, music, and videos?  How exactly does that work...I am not still pretty new and learning as I go.

Yes, there are several ways to backup what you want to save, although not ever needing to do that myself I can't give you the definitive answers you will need. This is a big topic on the forums so the database is full of these instructions, and the web can probably help you as well. Hopefully somebody can post the answers you need. It may be that you have 3rd party repository access and you need to tick that off in software sources update Feisty and just do a upgrade via the update manager, but as I said I don't know about a Feisty to Hardy upgrade this way. But the common advice is that no matter what, do a backup of what you don't want to possibly lose.

---

### Post by zvacet on 2008-05-20
@ **pkpmoa1536**

Do you have separate home partition?If you don´t make one using [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.That way home wil be intact if you do fresh install and you will save your files keeping them on home partition.If ypi want to upgrade you have to uncheck third party repos in system>admin>software sources>third party.Upgrade goes Feisty>Gutsy>Hardy,meaning you can not directly upgrade from Feisty to Hardy.If you decide to make fresh install **do not format home partition.**

---

