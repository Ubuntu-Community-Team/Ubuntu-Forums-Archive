---
title: "how to back-out updates installed by Update Manager"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by convert_mrta on 2008-09-03
I have not had a problem so far, but want to be prepared.

I've been blithely (blindly?) installing all updates recommended by Update Manager.  Now should my machine abruptly go south after an update, I would reasonably suspect one of the updates.  So I would want to back-out the last batch, get stable again, and then investigate.

How can I determine what was included in the last batch, and individually back each out until I reach the apparent troublemaker?

No flames, please, but if I was still using Windows, I'd go into add/remove programs, filter for updates, sorting by date and be able to see what my last installed updates were -- and back each out.

How do I do the same in Ubuntu?

Thanks much!  BTW, I'm dual booting Vista / Ubuntu 8.04 now, but haven't booted Vista in about 3 weeks. Well on my way, folks!  :)

---

### Post by Partyboi2 on 2008-09-03
You can view what updates where installed by looking at your /var/log/apt/term.log
```
gksudo gedit /var/log/apt/term.log
```

The idea for a update undo feature has been suggested at [[COLOR=Blue]ubuntu brainstorm[/COLOR]]("http://brainstorm.ubuntu.com/idea/6267/")

---

