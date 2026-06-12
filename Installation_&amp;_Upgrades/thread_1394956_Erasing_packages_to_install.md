---
title: "Erasing packages to install"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by Fiontie on 2010-01-31
Greetings, everyone!

I was going to install a certain application, and apt-get said I had unsatisfied dependencies. So I typed

```
sudo apt-get install -f
```But the overall size of the packages it was going to install was quite substantial, so I renounced this idea and chose "No".

Now I've got problems installing software - I keep getting "Software index is broken" message. I found [this]("http://ubuntuforums.org/showthread.php?t=493107") thread which suggests I use 'apt-get install -f'. But as I've said, the problem is that I no longer need those tons of packages that would be installed in this case.

Is there a way to erase the list of packages marked for installation or maybe there's some other way to fix that?

Thanks in advance!

---

### Post by MelDJ on 2010-01-31
update through update manager and uncheck the packages you don't want?

---

### Post by Fiontie on 2010-01-31
> **MelDJ said:**
> update through update manager and uncheck the packages you don't want?

Forgot to mention that it doesn't load either, quitting with "Software index is broken" error.

---

