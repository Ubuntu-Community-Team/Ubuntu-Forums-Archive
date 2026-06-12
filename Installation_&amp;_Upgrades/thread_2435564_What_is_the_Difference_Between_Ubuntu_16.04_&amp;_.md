---
title: "What is the Difference Between Ubuntu 16.04 &amp; 18.04"
date: 2020-01-22
forum: Installation &amp; Upgrades
---

### Post by johnsingam on 2020-01-22
Hi All,

Right now iam using Ubuntu 16.04 for my webserver. I want to know the major difference between Ubuntu 16.04 & 18.04.

If i continue with 16.04, my websites will get any issues? or update to newer version is must important?

Thank You!

---

### Post by CatKiller on 2020-01-22
The big change is the switch from Unity to Gnome, which isn't really relevant for a server with no GUI. Other than that, it's just new versions of stuff.

You'll have to upgrade to 18.04 or 20.04 at some point; 16.04 will reach end of life in April 2021. You don't need to upgrade until then if you don't need any of the new stuff, but after that you'll have to upgrade to keep getting security updates.

---

### Post by johnsingam on 2020-01-22
> **CatKiller said:**
> The big change is the switch from Unity to Gnome, which isn't really relevant for a server with no GUI. Other than that, it's just new versions of stuff.

You'll have to upgrade to 18.04 or 20.04 at some point; 16.04 will reach end of life in April 2021. You don't need to upgrade until then if you don't need any of the new stuff, but after that you'll have to upgrade to keep getting security updates.

Hello CatKiller,

Thank you for your information. How to upgrade to 20.04 from my current running version? Is there any tutorial available?


[COLOR=#000000]**CatKiller**[/COLOR][COLOR=#000000]CatKiller[/COLOR]

---

### Post by CelticWarrior on 2020-01-22
My recommendation is to wait at least one month after the release date to upgrade. So, around May-June would be a good idea.

You can upgrade online with ```
sudo do-release-upgrade
```

---

### Post by CatKiller on 2020-01-22
> **johnsingam said:**
> How to upgrade to 20.04 from my current running version?

20.04 isn't released yet: it will be released in April 2020 - that's how the version numbers work. It's just that it will be released before 16.04 loses support, so it's an option to consider.

You can't upgrade directly from 16.04 to 20.04, when it's released. You'd either need to go through 18.04 first or do a fresh install of 20.04 and restore your data from backups.

To upgrade from 16.04 to 18.04 you just need to run *sudo do-release-upgrade*, as CelticWarrior says, and then the same to go from 18.04 to 20.04 when you're ready for that.

The release notes for 18.04 are available [here]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") if you want more information about the changes.

---

### Post by johnsingam on 2020-01-22
Thank you for your responses. If i upgrade using this command **sudo do-release-upgrade**, it won't affect my current running websites?

---

### Post by CatKiller on 2020-01-22
It won't deliberately affect your running websites, but only you can do the necessary testing.

---

### Post by CelticWarrior on 2020-01-22
> **sneazzy95 said:**
> Hey, no it won't affect your current running websites, you can do it it's safe

How can you guarantee that?

---

### Post by deadflowr on 2020-01-22
The differences are highlighted here:
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

Edit: I missed catkiller's (tinny tiny) link.

---

### Post by johnsingam on 2020-01-23
> **CatKiller said:**
> It won't deliberately affect your running websites, but only you can do the necessary testing.

I will download the backup before start the backup for data safety.

---

