---
title: "Cannot boot nor install ubuntu 7.10 (xfer issue)"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Tribis on 2007-10-27
I have been trying to boot/install ubuntu 7.10, I've been using the Live CD and the regular install DVD. Now I know both these disc were burned properly, because they worked fine on my laptop. But the problem is on my PC, I receive a "failed to set xfer mode" error, which does not seem to be rare.

Now I tried the  fix of:

Press: F6
add: irqpoll
Press: Enter

That did not work, I did not try "irq=nopoll" as I saw someone post because I am not sure if it is a typo. 

My specs are:
[Abit ic7-G motherboard]("http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=4")
1GB Ram
2.8Ghz

---

### Post by hexstar on 2007-10-27
If this is simply a issue of X failing you should be able to resolve it via the following:

1) sudo X -configure

2) sudo cp /location/of/xorg.conf.new /etc/X11/xorg.conf

3) startx

---

### Post by Tribis on 2007-10-29
I'm not sure I understood that? X failing?

---

### Post by Tribis on 2007-11-02
Bumping once, before I give up.

---

