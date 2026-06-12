---
title: "Error updating software"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by tridephysique on 2014-10-04
Hello,
I've got an error when run software update.
How can I solve this?
Thanks.

---

### Post by Impavidus on 2014-10-04
You try to upgrade shotwell to version 0.20 whilst keeping shotwell-common at version 0.18. There is a conflict between those versions of those packages. Usually the packages shotwell and shotwell-common should both be at the same version. I don't see shotwell 0.20 in the trusty repos. Did you get it from somewhere else?

BTW, instead of posting screenshots somewhere external you an also attach them to your forum posts. In case of terminal output (and please, also include the exact command that generated that output), you can copy the text to your post in [noparse]```
code tags
```[/noparse].

---

### Post by tridephysique on 2014-10-05
I just ran the update codes: ```
sudo apt-get update && sudo apt-get upgrade
```
I figure out that the problem occurred after installing geary 0.8.
How can I fix the problem and keep geary 0.8?

---

### Post by Vladlenin5000 on 2014-10-05
How did you installed Geary 0.8?

---

### Post by tridephysique on 2014-10-06
I add yorba repository: ```
sudo add-apt-repository ppa:yorba/ppa && sudo apt-get update && sudo apt-get install geary
```

---

### Post by tridephysique on 2014-10-09
I found the solution. I use this code to solve my problem:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
```

---

