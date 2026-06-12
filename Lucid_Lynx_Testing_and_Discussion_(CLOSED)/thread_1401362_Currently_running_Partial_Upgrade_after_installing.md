---
title: "Currently running Partial Upgrade after installing Lucid Lynx A2"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kenny_Strawn on 2010-02-08
As strange as this sounds, on the Lucid Lynx Live CD (or USB stick in this case) has 566 obsolete packages on it when it installs.

I am doing a partial upgrade because of it, and I want your opinion: Should dev releases of Ubuntu have that many obsolete packages? Isn't the purpose of "dev release" that the packages are actually up-to-date?

---

### Post by juancarlospaco on 2010-02-08
No, because is a release for testing only, lots of change happend under the hood.

---

### Post by FuturePilot on 2010-02-08
Partial upgrade usually == broken system

---

### Post by Kenny_Strawn on 2010-02-08
> **juancarlospaco said:**
> No, because is a release for testing only, lots of change happend under the hood.

Yes, that's true. But what about the fact that Lucid Lynx repositories have been updated most, if not beta software on them, given their constant updates from the team?

---

### Post by Paqman on 2010-02-08
> **FuturePilot said:**
> Partial upgrade usually == broken system

Absolutely! [Don't do it!]("http://ubuntuforums.org/showthread.php?t=1343434")

If you get offered a partial upgrade, open Synaptic instead and take a look at what it's suggesting. If you aren't 100% happy with what is going on, wait a day or so before running any updates.

As for the 566 outdated packages: on the testing branch you should expect to be doing sizeable updates every day. If you're using an iso image several weeks old that means a lot of updates after installing.

---

### Post by jocko on 2010-02-08
> **Kenny_Strawn said:**
> As strange as this sounds, on the Lucid Lynx Live CD (or USB stick in this case) has 566 obsolete packages on it when it installs.

I am doing a partial upgrade because of it, and I want your opinion: Should dev releases of Ubuntu have that many obsolete packages? Isn't the purpose of "dev release" that the packages are actually up-to-date?

> **Kenny_Strawn said:**
> Yes, that's true. But what about the fact that Lucid Lynx repositories have been updated most, if not beta software on them, given their constant updates from the team?
You don't seem to understand that 10.04 is still under development. That means packages are **constantly** being updated and therefore replaced with newer versions.
If You install with an alpha 2 live cd (which was released 3 weeks ago), you will install the packages that were in the repo 3 weeks ago. Many of those packages have been updated in the repos since then, which means that you will need to upgrade to get the current packages.

And, as the other people have said: Be careful when the update manager offers a partial upgrade. Use synaptic to "mark all upgrades" or "apt-get upgrade", they will only install updates that don't cause removal of packages. Then you can try installing the remaining updates one by one and see what error messages you get.

Often partial upgrades are caused by packages that need to install one package that in turn wants to remove another package. Yesterday I was offered a partial upgrade, so I opened up synaptic to track down the problem. It turned out that some of the updated packages wanted to install the new packages libdbusmenu-glib1 and libdbusmenu-gtk1, but that was not possible because those packages wanted to remove libdbusmenu-glib0 and libdbusmenu-gtk0.
If I had run the partial upgrade half my system would have been uninstalled to circumvent the problem, but using synaptic and some common sense I managed to simply install libdbusmenu-glib1 and libdbusmenu-gtk1 (and remove the older, obsoleted packages) and then install all updates without problem.
Or I could have waited for a while until the devs would have released another update that would have cleared it up automatically.

---

### Post by ranch hand on 2010-02-08
Update Mangler is not a good tool for upgrading stable releases in my opinion.  I would never use it in testing.

I go with apt-get.  It is safe (no dist-upgrade until researched).  Synaptic is the next best in my book and where I do my research on packages.

I have a bunch of packages that my box claims can be removed.  Does not look like a good idea to me.

---

### Post by Kenny_Strawn on 2010-02-09
The reason why I performed the partial upgrade was because of the overflow of obsolete packages, a whopping 566.

---

### Post by OrangeCrate on 2010-02-09
<duplicate post removed, see below>

---

### Post by OrangeCrate on 2010-02-09
> **Kenny_Strawn said:**
> The reason why I performed the partial upgrade was because of the overflow of obsolete packages, a whopping 566.

Have you ever seen this?

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

They're great housekeeping tools.

Plus, this combination of commands will keep things nice and tidy...

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get clean && sudo apt-get autoclean
sudo apt-get autoremove
```

(Oh, and stay away from partial upgrades for the reasons already mentioned.)

---

### Post by markbuntu on 2010-02-12
I have been doing partial updates lately using update manager. I look through the packages that are held back, it has been the same list now for weeks, brasero, empathy, gdm, firefox, linux-kernel, open office. and some micellaneous other stuff that changes. Usually get almost 200 updates at a time and have not had any problems yet but this is just a testing machine anyway so nothing to lose in a disaster and I am not really inclined to wade through Synaptic to check all the dependencies on some 200 packages every few days. 

That does not mean that you won't have any problems.

---

