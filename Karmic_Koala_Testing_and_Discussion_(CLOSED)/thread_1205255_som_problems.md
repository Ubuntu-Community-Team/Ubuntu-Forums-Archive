---
title: "som problems"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hgergo on 2009-07-05
I have installed karmic on my laptop acer aspire 5100 and i have som problems
I cant update to kernel 2.6.31 while is a partial update.
With the partial update i have a big problem when i instaling it it is saing at the end sarting hal or somting and the pc is freesing and i get a black screen.
I can resolve the isue i tyried in recovery mode nothing.
I have now 2.6.30.8 kernel and the powermanager is not working is not recognizing batery.

P.S. I there some way to update to the latest kernel?

P.S.S i cant mount any ntfs drive i get this error         DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus

---

### Post by budluva04 on 2009-07-06
you can download the newest kernel going right now...2.6.31-rc2

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/")

download all the debs and install them with sudo dpkg -i xxxxxxxx.deb

---

### Post by psyke83 on 2009-07-06
> **budluva04 said:**
> you can download the newest kernel going right now...2.6.31-rc2

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc2/")

download all the debs and install them with sudo dpkg -i xxxxxxxx.deb

That's a waste of time. This is the vanilla packaged version of the kernel (of which the i386 build wasn't completed). This is not the equivalent of upgrading to the 2.6.31-1-generic kernel, and won't resolve the inconsistent state of hgergo's updates.

hgergo, I can guarantee that all of your issues have been discussed, you should search the forum. Don't allow partial upgrades without doing proper research into whether each package to be removed is supposed to be removed! You need to browse the recent posts in this forum.

---

### Post by hgergo on 2009-07-06
The wired hing was that i installed both x86 and x64 and both versions krashed by updating.
First i tryed upgrade from 9.04 to 9.10 and same stuff.

---

