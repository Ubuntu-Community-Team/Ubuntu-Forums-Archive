---
title: "Can t copy hidden files/folders"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by locutuz on 2006-12-22
I am currently using Kubuntu Edgy 64 on my new system, but I have some weird problems. Some settings files looks like the are not writable; like the nvidia settings tool but when I open them I can write them with kate. I am the owner of the files and folder. I am hassling with this for two weeks now.  So I quit for now. I go back to dapper 32 bit.

Now there real problem: I want to reinstall dapper, so I want to make a back up of my home dir. That works fine with 

```
sudo cp -avx /home /anotherhd
```

But it wont copy my hidden folders like .kde and .mozilla. I have done this trick before in the past. What am I doing wrong?

---

### Post by MrHorus on 2006-12-22
How do you know it doesn't, just from the output of ls?

By default ls won't show the hidden files but they are still there.

From the command line, try opening one of these "missing" hidden files that you know *should* be there - it will probably be there :)

---

### Post by locutuz on 2006-12-22
I use konqueror with the show hidden files option on. Anyways: I see them in my home dir and if I navigate to the backup drive I don't see them. Weird eh?

---

