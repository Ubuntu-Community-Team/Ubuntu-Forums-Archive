---
title: "Jaunty Update Manager hangs"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by peakshysteria on 2009-04-16
It only offers a Partial upgrade. When proceeding with this after the promtp nothing happens. How do I update?

As far as I canremember I ran into the same problem in an earlier release as well. Can't remember the fix.Iguess the fixfor this is different anyway. If it exists.

---

### Post by Therion on 2009-04-16
How exactly are you trying to upgrade?

---

### Post by peakshysteria on 2009-04-16
System --> Administration --> Update Manager (I'm just trying to update. The prompt says it can only do a partial *Upgrade* though. But as mentioned,nothing seems to happen).

---

### Post by Therion on 2009-04-16
I'm not sure you can go that route with Jaunty being RC1 at this point.  

Instead, open a Terminal and Copy and Paste:
```
sudo apt-get -u dist-upgrade
```

---

### Post by go7Ul1ai on 2009-04-16
> **peakshysteria said:**
> System --> Administration --> Update Manager (I'm just trying to update. The prompt says it can only do a partial *Upgrade* though. But as mentioned,nothing seems to happen).

Yes we got that, but *what* packages are you trying to upgrade?

---

### Post by Therion on 2009-04-16
Oh, geez... Total brainfart.  I thought you wanted to do a distribution UPGRADE.  

Belay my last!

---

### Post by peakshysteria on 2009-04-16
> **Therion said:**
> Oh, geez... Total brainfart.  I thought you wanted to do a distribution UPGRADE.  

Belay my last!

Tried to warn you there man. I got that you might misunderstand my post.

> **lee.jarratt said:**
> Yes we got that, but *what* packages are you trying to upgrade?

As you se jarratt not all did. But I do apreciate peoplehelping. Thanks guys. There are not any specific packages I know of.Only a random update. But all ready there are some 156 packages I think, since monday. But as mentioned it seems todo nothing. Each time I open the Update Manager and start it I get promptedfora partial upgrade with the same number of packages.I tried to take a screenshot of it but it seems to save it to another place than the usual place, my desktop.

---

### Post by nandemonai on 2009-04-16
Try marking all updates in Synaptic and applying it there.

---

### Post by go7Ul1ai on 2009-04-16
Maybe you should clean the cache if the upgrade is failing?

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by peakshysteria on 2009-04-16
> **nandemonai said:**
> Try marking all updates in Synaptic and applying it there.

Nice man. It did the trick. My system is no up todate it says.Made my week man. Thanks a million.


> **lee.jarratt said:**
> Maybe you should clean the cache if the upgrade is failing?

```
sudo dpkg --clear-avail && sudo apt-get update
```

Can you tell me some more about this command even though my system is no up to date?

---

### Post by go7Ul1ai on 2009-04-16
> **peakshysteria said:**
> Nice man. It did the trick. My system is no up todate it says.Made my week man. Thanks a million.




Can you tell me some more about this command even though my system is no up to date?

Clears out corrupted packages in the cache, hopefully solving the problem.

---

