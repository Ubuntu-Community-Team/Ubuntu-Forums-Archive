---
title: "Non existent broken package"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by tashimee2 on 2016-12-19
I am using xunbuntu 16.04. I am trying to install nemo, but it says that I am holding broken packages. 

Using the command: sudo apt-mark showhold 
nothing 

How do I find a broken package that it says is not there?

---

### Post by Bashing-om on 2016-12-19
tashimee2; Hello;

The package manager tells all, but ya got to ask it the right question(s).

Let's look and see what the package manager relates:
Post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see where we go from here .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-12-19
> **tashimee2 said:**
> [...]but it says that I am holding broken packages. 

Using the command: sudo apt-mark showhold 
nothing 

'held broken packages' does NOT mean apt-hold.
Instead, it usually means you have a version conflict that the package manager cannot resolve.
Follow Bashing-om's instructions, and he will help you quickly put your system right.

---

