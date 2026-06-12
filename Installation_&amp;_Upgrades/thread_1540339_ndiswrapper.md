---
title: "ndiswrapper"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Azuremein on 2010-07-27
I imagine that you've all heard this question a million times before, which is why I feel bad even posting this here, but I would like some help installing ndiswrapper. I've used Windows all my life and I just made the jump to Ubuntu a couple days ago, I had someone online help me install native drivers for my card, but at the end of the list of like 25 packages there are 4 packages that won't install because they all say they have dependencies upon each other. Now, I'm trying ndiswrapper and I don't understand it in the least little bit... can someone help me, and give me step by step instructions for this? I know I'm an utter noob, but the OS seems amazing, I'd just like to connect to the internet with it. Even the ethernet port doesn't work! :/

---

### Post by spcwingo on 2010-07-27
As far as the packages you're trying to install just move them all into a folder in your home directory.  After that it's just two commands to install them even if they are dependent of each other.  For example, if you made a folder in your home folder named "install" you would:

```
cd install && sudo dpkg -i ./*.deb
```

For future reference that means

cd = change directory
install = folder to change directory to
&& = when you're done with that do this (what follows)
sudo = super user do
dpkg = package management
-i = switch for dpkg meaning install
./ = current directory
* = wildcard
.deb = Debian (also Ubuntu and many other distros) package

---

