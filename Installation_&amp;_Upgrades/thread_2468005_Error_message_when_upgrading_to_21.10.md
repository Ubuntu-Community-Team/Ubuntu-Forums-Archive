---
title: "Error message when upgrading to 21.10"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by matthewbaynham on 2021-10-15
I got an error when upgrading to 21.10, a pop up appeared and then when I continued then the other pop up appeared, I've attached them below.

What does this mean?

Is this important?  Should I do anything?  Should I report it to whoever is working on the 21.10 upgrade?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289279&stc=1[/IMG]

[INDENT][I]Could not install '/tmp/apt-dpkg-install-ZnuDOm/605-linux-headers-5.13.0-19_5.13.0-19.19_all.deb'

The upgrade will continue but the '/tmp/apt-dpkg-install-ZnuDOm/605-linux-headers-5.13.0-19_5.13.0-19.19_all.deb' package may not be in a working state. Please consider submitting a bug report about it.
[/I][/INDENT]
[INDENT][/INDENT]
[INDENT][I]unable to create new file '/var/lib/dpkg/info/linux-headers-5.13.0-19.list-new': Operation not permitted
[/I][/INDENT]


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289280&stc=1[/IMG]

[INDENT][I]Could not install the upgrades

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).[/I]
[/INDENT]

---

### Post by MAFoElffen on 2021-10-16
Did you do as suggested?

```

sudo dpkg --configure -a

```
If it also says that you have broken packages and unmet dependencies, you might also do 
```

sudo apt install -f

```

---

