---
title: "Roll-back Install"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by Mochabuntu on 2008-01-21
Hi guys,
Been a fan of Ubuntu for a while, having tried openSUSE, Fedora, and coming back to Ubuntu every time. But I have a few questions I was hoping someone could help me with.:confused.
Where do I find all the changes I made to my system? I been crawling through /var/log/dpkg.log but I can't make head nor tail of the thing. I use terminal for all my installs because I just feel better doing it that way. Does Ubuntu keep a record of all these transactions? If so, where can i find it?
Barring that, is it possible to "fix" Ubuntu so that it keeps all it's updated components but I can revert to something like a fresh install?

Thanks in advance.

---

### Post by zvacet on 2008-01-21
You can find what you installed in synaptic>file>history but if you prefer terminal

```
dpkg --get-selections > installed-software
```

and you will find file in your home directory with list of all installed programs.

---

### Post by Mochabuntu on 2008-01-21
Thank you zvacet, that worked great. :KS
Do you or anyone else, know how to find the components updated in Update Manager? For example, I have exceeded my bandwidth for my net connection, and want to reinstall Ubuntu (I did something very silly and want to create a "virgin" system but can't d/l the updates). Is it possible to get the updated packages to their packaged state to put on a CD?
Or am I SOL? :(
Thanks again.

---

