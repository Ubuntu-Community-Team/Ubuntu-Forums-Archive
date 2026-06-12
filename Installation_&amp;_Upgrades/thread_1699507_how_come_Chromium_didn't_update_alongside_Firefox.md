---
title: "how come Chromium didn't update alongside Firefox?"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-03-03
Both firefox and Chromium released updates on the same day (1 march). I got an automatic update for Firefox but Chromium still shows as being the old version. I just checked Synaptic and it shows the new Chromium is present. How come it didn't auto-update alongside Firefox?

I installed Chromium from the Ubuntu Software Center.

---

### Post by Frogs Hair on 2011-03-03
If it is in synaptic go ahead and install it. I use Opera and my updates are not automatic as with Firefox I have to check for the new version . But Opera did not come from repository .

---

### Post by nrundy on 2011-03-03
I figured it out. Auto update only occurs for "default" applications. Make the application default and it will auto update.

Anybody know if there is a way to add an application to the auto-update list even if it isn't the default?

---

### Post by Frogs Hair on 2011-03-03
System > Preferences > Preferred applications only allows you to choose one browser . There is a custom option that allows a terminal command , but I have not used it.

---

### Post by mörgæs on 2011-03-03
> **nrundy said:**
> Make the application default and it will auto update.


That can not be true. I have Firefox and Chromium, and they both get updates. 

If you have a delay in the updates, it must be due to another reason.

---

### Post by nrundy on 2011-03-03
Well I had Firefox at default since installing Ubuntu. This morning Auto update updated firefox. Chromium didn't get updated. It was still at the old version. I ran manual update a couple times throughout the day and it said my system was up to date. I ran manual update again--no updates. A minute later I made Chromium the default browser and then ran manual update again and it updated chromium.

Any ideas about why there'd be a delay?

---

### Post by nrundy on 2011-03-03
> **Frogs Hair said:**
> System > Preferences > Preferred applications only allows you to choose one browser . There is a custom option that allows a terminal command , but I have not used it.

I use EXAILE as my default music player. But it doesn't show up in System Preferred Applications. So I chose Custom > Command and put in the command that the Exaile icon shows in Properties. Will this insure that exaile gets updated if an update is released?

---

### Post by mörgæs on 2011-03-04
> **nrundy said:**
> 
Any ideas about why there'd be a delay?

There can be many reasons. The packages are not released at the same time, the mirrors are updated with a delay and so on.

Remember that for most packages in Ubuntu there is no such thing as 'default', meaning the preferred application (among several options) for a particular file type. For example, the packages taking care of network connections do not have any association to files.

---

### Post by oldos2er on 2011-03-04
Preferred applications has nothing at all to do with system updates. Did you install chromium from a PPA or from the universe repo?

---

### Post by nrundy on 2011-03-04
I said in my original post that i installed Chromium from the Ubuntu Software Center.

---

### Post by oldos2er on 2011-03-04
Software Center is a package manager, not a repository.

---

### Post by nrundy on 2011-03-04
Are you saying that you can download stuff from the Software Center that does not come from one of the official ubuntu Repos?

---

