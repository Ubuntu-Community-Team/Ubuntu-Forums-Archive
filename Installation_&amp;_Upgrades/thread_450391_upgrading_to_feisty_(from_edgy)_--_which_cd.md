---
title: "upgrading to feisty (from edgy) -- which cd?"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by whoKnew on 2007-05-21
i'm trying to decide whether or not i should upgrade to feisty.

i've been having a hell of a time figuring out how to get my wifi pcmcia card to work (linksys WPC54g v. 2), and i just read on the wiki that it apparently works "out of the box" using Feisty.

That being said, I'm kind of nervous about the upgrade because i JUST upgraded to Edgy from Dapper without severely screwing anything up (newbie), and i've been reading a lot of posts with people having issues upgrading to Feisty.

Which cd should i use for the upgrade if i decide to do it?
The desktop cd, or the alternate install cd?

I don't have an internet connection to my linux comp, so the upgrade manager won't work out.

Thanks!

---

### Post by kragen on 2007-05-21
If you want to upgrade from edgy to feisty, I think the command is:

```
update-manager -c
```

This will check to see if a new version of Ubuntu is available, and start the upgrade once you confirm it. That's definitely the easiest way to do it, I'm not even sure if the upgrade CD is capable of upgrading an existing Ubuntu installation.

As for people having problems after upgrading, I'm afraid I can't help you there. I've certainly not had any problems anyway.

---

