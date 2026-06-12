---
title: "Suspicious about update"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by DarthSudaka on 2010-02-18
Hi, this may be a stupid question but I`m kind of suspicious.

I`m using Ubuntu 9.10 and since last week the Update Manager wants to updates some packages and make a new installation of another few, among others there are: alien, bsd-mailx, build-essential, html2text, lib-sendmail-perl, lsb and mailx.
I don`t have an older version of any of those packages so it seemed to me kind of suspicious that a regular ubuntu update would try to install them.
Is that ok? I mean, any of you also get those packages for install in package manager?

Sorry if that is too paranoid :P

Thanks

---

### Post by howefield on 2010-02-18
Are you running google chrome ?

This is likely the application that wants to update with these dependancies.

---

### Post by Enigmapond on 2010-02-18
Definitely. You have applications that needs these. It OK to let it do it. Anything that pops up like that let it update. No need for the paranoia...it's all good..:)

---

### Post by howefield on 2010-02-18
> **Enigmapond said:**
> Definitely. You have applications that needs these. It OK to let it do it. Anything that pops up like that let it update. No need for the paranoia...it's all good..:)

Actually, maybe not in this case.

---

### Post by crlang13 on 2010-02-18
If you are paranoid about updates though, check the source.  Although in this case you're fine, if you do feel paranoid about an update, check to make sure a random repository has been added sending you updates from an unknown source.  This is highly highly unlikely seeing you have to have admin privileges to add the repository...  But, if you're paranoid, I suppose it doesn't hurt to double check :p

---

### Post by DarthSudaka on 2010-02-18
Like howefield said, it was chrome. More specifically this repo:
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) STABLE MAIN

Thank you very much guys!! :D

---

### Post by howefield on 2010-02-18
> **DarthSudaka said:**
> Like howefield said, it was chrome. More specifically this repo:
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) STABLE MAIN

Thank you very much guys!! :D

Chrome is updating from version 5.307.7 to 5.307.9, but wants to install some really strange dependancies which as I understand it, will be fixed in the next update.

---

