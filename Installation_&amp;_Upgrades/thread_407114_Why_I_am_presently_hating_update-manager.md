---
title: "Why I am presently hating update-manager"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by Isaac Dupree on 2007-04-11
Although I can watch the messages logged while updating my system, they vanish as soon as the update is finished!  Furthermore, I haven't been able to find them in any log-file on my system.  Even when I was watching closely to see what it says....

It looks like using command-line tools is going to be more reliable for this purpose; for example, in this case, I could have used
```
sudo aptitude upgrade
```
to get my log-messages, such as
```
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-11.37 was configured last, according to dpkg)
```

However, update-notifier, which is very convenient itself, starts up update-manager when clicked on, suggesting use of a nuisance GUI tool.  I hope the tool might become less of a nuisance sometime ^_^

BTW the way I got that log-message back that I had only got a glimpse of was:
```
sudo aptitude reinstall linux-image-2.6.17-11-powerpc
```
which I figured out what to try using information about what was updated recently from the end of /var/log/dpkg.log

---

### Post by TheWizzard on 2007-04-12
what is your problem exactly? 
and if you don't like the update manager, why don't you just make a cron job for it?

cheers

---

