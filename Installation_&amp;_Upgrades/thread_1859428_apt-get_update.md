---
title: "apt-get update"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by 02darkRS on 2011-10-13
When I run update & upgrade in terminal..... why do I still have updates listed in update manager after they complete?

---

### Post by Old_Grey_Wolf on 2011-10-13
Enter this command and see if you still have the same problem:```
sudo apt-get dist-upgrade
```

Just doing an apt-get upgrade doesn't install some packages.

---

### Post by 02darkRS on 2011-10-13
should i do the same with update? ```
sudo apt-get dist-update 
```I should clarify.... I was not trying to upgrade to the new release. if that is what this does?
```
sudo apt-get dist-upgrade
```

---

### Post by BazookaAce on 2011-10-13
```
sudo update manager -d 
```

Edit: Oh, i read your post again, lol. I don't know :p

---

### Post by varunendra on 2011-10-14
> **02darkRS said:**
> I should clarify.... I was not trying to upgrade to the new release. if that is what this does?
By default, it doesn't upgrade the distro itself, it is just a more intelligent form of "apt-get upgrade".

Here is some detailed clarification to your doubts, and explanation of the command that *Old_Gray_Wolf *suggested:

[http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/](http://www.linuxquestions.org/questions/fedora-35/apt-get-question-dist-upgrade-vs-upgrade-219920/)
[http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/](http://www.ghacks.net/2010/03/11/what-is-it-with-the-dist-upgrade-option-of-apt-get/)

---

### Post by 02darkRS on 2011-10-14
thank you

---

