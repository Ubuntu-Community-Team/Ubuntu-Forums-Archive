---
title: "noob help required Duplicates"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by gallagj8 on 2013-02-18
Hi, I am new to ubuntu. I found an old laptop in the cupboard and dusted it down to try out the operating system. I am hearing loads of great thing about it. But it just doesnt seem to work. I installed version 12.04 LTS but anytime I try to install anything by fallowing instructions to the tee I still get errors mainly this one.

W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

and each time I do as it says, (run apt get update) but it just continues to give me this error.

Any help would be appreciated. Thanks

---

### Post by MrKaliman on 2013-02-18
Where in the install progress you receive this error?
Did you choose erase and install Ubuntu?

---

### Post by oldos2er on 2013-02-18
> **gallagj8 said:**
> nd each time I do as it says, (run apt get update) but it just continues to give me this error.


Can you run these two commands in a terminal, and post all the output here? ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by manishiitg on 2013-04-30
whats the laptop config

---

