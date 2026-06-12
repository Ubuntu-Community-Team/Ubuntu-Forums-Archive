---
title: "Install kubuntu-desktop to Ubuntu from the Kubuntu CD/DVD?"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by KeeperOS on 2007-03-07
(Advanced Windows user, just started exploring Linux)

Well, just that.

I downloaded both the Ubuntu and Kubuntu CD isos and after a test run of both I decided that I'd want to try the Ubuntu installation but with the eye candy and functionality of Kubuntu until I find out which will suit me best.

However after DLing about 700 mb I'd prefer installing the kubuntu-desktop from the CD instead of re-downloading 203MB that I already have (perhaps not the latest ones but I can always update later) using the "sudo aptitude install kubuntu-desktop" command.

So, is it possible and if so, how?

P.S.
Why is it that when I use the "sudo aptitude install kubuntu-desktop" I get a 203MB worth package while when I use the "sudo apt-get install kubuntu-desktop" command I get a 198MB package?

Thanks!

---

### Post by zvacet on 2007-03-08
```
sudo apt-cdrom add
```
```
sudo aptitude install kubuntu-desktop
```

---

### Post by KeeperOS on 2007-03-08
Thanks!

Do you think you could tell me why the apt-get and aptitude commands result in different size packages? Are they from different pools or sth?

---

