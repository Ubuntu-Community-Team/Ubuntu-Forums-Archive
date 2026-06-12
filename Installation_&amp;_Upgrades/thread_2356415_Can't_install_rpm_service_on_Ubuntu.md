---
title: "Can't install rpm service on Ubuntu"
date: 2017-03-23
forum: Installation &amp; Upgrades
---

### Post by mr.mm9 on 2017-03-23
Hi

I try to install rpm service because my backup agent installation require its. I stuck with some problems. [Like in the picture]

[IMG]http://i.imgur.com/g2UOQDT.jpg[/IMG]

I try many ways such as use [apt-get -f update] or change repo but It still have the error. How can I solve this?

My OS: Ubuntu 14.04.2 LTS 64bit run on Physical Machine

Thank you

---

### Post by Impavidus on 2017-03-23
I don't think your problem has anything to do with installing rpm. It just shows up now because you use the package manager. There is an inconsistency in your installed kernel packages.

Show us the complete output of```
sudo apt-get update
sudo apt-get -f install
uname -r
```
Put your output in[noparse]```
code tags
```[/noparse]It's better readable than screenshots.

I see you used a root shell and prefixed your commands with sudo. This is redundant. You only need one of those.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

