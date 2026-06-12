---
title: "How do you install Zend Studio?"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by ezcakes on 2008-11-19
Hey guys I'm kind of a newbie in the Linux world. I am having so much trouble just installing Zend Studio 5.5. Could anyone please tell me how to extract the files and install it? Thanks, I really appreciate any help.

---

### Post by dgoosens on 2008-11-19
what kind of trouble are you running into ?

I might be wrong, but isn't there some explanation on the Zend website ?
I can't recall having any issues installing Zend Studio...

just so you know, there is a little bug...
here is how to solve it:
[http://www.zend.com/forums/index.php?t=msg&goto=13573&S=3e0417c64806b5f759e3d79040f3f48d]("http://www.zend.com/forums/index.php?t=msg&goto=13573&S=3e0417c64806b5f759e3d79040f3f48d")
> Add the line 'options="$options -Dawt.toolkit=sun.awt.motif.MToolkit"' on line 1695 in ZDE start file in /bin/

you will find there is some explanation on the installation as well on that website...

hope it helps,
dGo

---

