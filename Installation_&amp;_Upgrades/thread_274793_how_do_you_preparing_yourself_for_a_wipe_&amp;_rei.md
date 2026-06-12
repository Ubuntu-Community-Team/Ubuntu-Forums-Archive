---
title: "how do you preparing yourself for a wipe &amp; reinstall?"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2006-10-10
I was thinking of doing a wipe & install for various reasons once stable edgy is announced, but the idea of having to reinstall each one of my apps is kind of a turn-off. Is there a way to generate a list of all installed programs and reinstall them through synaptic? 

I have a separate partition for my /home folder so that makes things easier for my personal conf files. And I'll probably will have to copy over sources.list and xorg.conf... anything else I might have forgotten? by the way, is there a way to see all the files in / (except /media and /home) that has been "touched" by my user?

Thanks!

---

### Post by eeGhoong0ais on 2006-10-10
> **KhaaL said:**
> Is there a way to generate a list of all installed programs and reinstall them through synaptic?

dpkg -l will list all installed packages, so you could do something like ...

Before wipe/reinstall: ```
dpkg -l | sed '1,5d;/^rc  /d;/^ii  /{s/^....//;s/ .*//}' > old_list
```After wipe/reinstall: ```
dpkg -l | sed '1,5d;/^rc  /d;/^ii  /{s/^....//;s/ .*//}' > new_list
diff old_list new_list
```... to tell you what's changed (the sed command strips out the header and information about removed packages, version numbers and descriptions that you don't care about). I don't think blindly reinstalling every package from the previous install is likely to be a great idea though.

---

### Post by TheWizzard on 2006-10-10
etoil is righ, but it can be simpler:

```
$ dpkg --get-selections | grep -v deinstall > installed-software.log
```

to put everything back in place:

```
# dpkg --set-selections < ~/installed-software.log
```

source:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

