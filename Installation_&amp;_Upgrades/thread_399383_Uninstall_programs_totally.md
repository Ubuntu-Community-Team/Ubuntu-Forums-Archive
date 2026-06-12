---
title: "Uninstall programs totally"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2007-04-02
I'm quite new to Xubuntu and I've got one question.

 When I uninstall a program it seems that only the selected program is uninstalled and not the bundle of stuff that was installed with the program. My question is firstly if I'm correct and secondly if so, how do I uninstall the whole bundle that was installed with a program.

I'm also using envy and automatix.

---

### Post by gborzi on 2007-04-02
> **1/0 said:**
> I'm quite new to Xubuntu and I've got one question.

 When I uninstall a program it seems that only the selected program is uninstalled and not the bundle of stuff that was installed with the program. My question is firstly if I'm correct and secondly if so, how do I uninstall the whole bundle that was installed with a program.

I'm also using envy and automatix.

You are correct, the bundle of stuff (i.e. the dependencies) installed with the program are not uninstalled when you remove the program, as long as you use apt-get even through one of its GUI (synaptic, adept). I have read in the forums that it is possible to uninstall the dependencies if you use aptitude. I dont' know how to use this package manager, but you can find informations on these forums.

---

### Post by 1/0 on 2007-04-02
Thanks! Then I know its that way and what to look for.

---

### Post by schmandr on 2007-06-15
> **gborzi said:**
> You are correct, the bundle of stuff (i.e. the dependencies) installed with the program are not uninstalled when you remove the program, as long as you use apt-get even through one of its GUI (synaptic, adept). I have read in the forums that it is possible to uninstall the dependencies if you use aptitude. I dont' know how to use this package manager, but you can find informations on these forums.
Is there a reason for this behaviour of the GUI programs? Will this change in the future?

Andreas

---

