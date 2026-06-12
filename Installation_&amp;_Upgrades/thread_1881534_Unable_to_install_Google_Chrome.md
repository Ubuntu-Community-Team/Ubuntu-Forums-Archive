---
title: "Unable to install Google Chrome"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2011-11-15
Tonight I just reinstalled my OS from 32 bit to 64 bit, and I put the OS on a new drive (my old drive is slowly dying).

I've just completed the install, and I've downloaded the google-chrome-stable_current_amd64.deb from the Google website. But when I double click the file, Software Center simply says *The file "/home/patrick/Downloads/google-chrome-stable_current_amd64.deb" could not be opened.*

One important things of note: I encrypted my home folder, so this *might* be related to that (my dmesg output is constantly getting spammed with encryptfs errors). But I also tried running the file from an unencrypted folder, and I had no luck.

---

### Post by dniMretsaM on 2011-11-15
What is the output of this command:
```
sudo dpkg -i /home/patrick/Downloads/google-chrome-stable_current_amd64.deb
```

By the way why not just use Chromium?

---

### Post by patman0623 on 2011-11-15
> **dniMretsaM said:**
> What is the output of this commandUm, it installed after I did that. I'm kind of embarassed I didn't think of that.

> **dniMretsaM said:**
> By the way why not just use Chromium?AFAIK Chrome was forked from Chromium a while ago, and it has a lot of different features.

---

### Post by dniMretsaM on 2011-11-15
> **patman0623 said:**
> AFAIK Chrome was forked from Chromium a while ago, and it has a lot of different features.

The only differences are that Chrome adds some non-free things (PDF viewer, non-free media codec support, etc.). All of which can be emulated with software (some free, some non-free) from the Ubuntu repositories.

---

