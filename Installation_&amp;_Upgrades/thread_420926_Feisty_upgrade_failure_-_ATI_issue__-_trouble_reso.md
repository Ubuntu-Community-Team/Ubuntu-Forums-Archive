---
title: "Feisty upgrade failure - ATI issue ? - trouble resolving"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by geog_eric on 2007-04-24
After upgrading to Feisty, I get a black screen before even reaching the login prompt. No error, just a black screen. I believe I've encountered the common ATI card error addressed in [http://ubuntuforums.org/showthread.php?t=414194]("http://ubuntuforums.org/showthread.php?t=414194") but I've not been able to run the fix. Here's what happens when I try to run this fix:

1) Booting into recovery mode and trying ```
sudo apt-get update
```. For each server I get the error "could not resolve"
2) Thinking there was a network problem (I'm behind a proxy), I tried:
```
export http_proxy=http://username:password@proxy:port/
```
with my particulars and reran the ```
sudo apt-get update
```. Now for each server I get the error "network is unreachable"
3) I've also looked for **/var/log/Xorg.0.log** hoping to find some insight or post it, and it doesn't exist.

So, several questions:
[LIST]
[*]Do I have a network problem along with a video card problem?
[*]Or, am I using the recovery mode incorrectly?
[*]What else should I try?
[/LIST]

Thanks for any help,

-Eric

---

### Post by geog_eric on 2007-04-25
Running ```
dpkg-reconfigure xserver-xorg
``` as suggested by another post and accepting all defaults and rebooting (twice!) fixed the problem. 

Wonder if I should still run the suggested ATI fix?

-Eric

---

