---
title: "Switching from netbook remix to xubuntu"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by morenogabr on 2011-02-18
NBR sucks. Its laggy, buggy, and I cant wait another two months to hide the loader on the left. Im assuming Xubuntu is a smart option for an HP 210 netbook, advice? Ive been using linux for a little while, but I always get spooked when I have to play with partitions, install, uninstall, and whatnot.

What basic steps should I follow to achieve a smooth xubuntu install?

---

### Post by ajgreeny on 2011-02-18
Just add xubuntu-desktop ```
sudo apt-get install xubuntu-desktop
``` to your current UNR (10.10 I assume) and then at the login screen chose xfce4 from the session menu, which will appear after choosing the username.

---

### Post by morenogabr on 2011-02-18
> **ajgreeny said:**
> Just add xubuntu-desktop ```
sudo apt-get install xubuntu-desktop
``` to your current UNR (10.10 I assume) and then at the login screen chose xfce4 from the session menu, which will appear after choosing the username.
Does this delete netbook remix?

---

### Post by morenogabr on 2011-02-19
Cool! That was easy, thanks. I notice though when I log into xfce session that there is still available the netbook environment as well as xubuntu and ubuntu desktop as options. Seeing as how the purpose of getting xub is that it is a "leightweight" environment, does it defeat the purpose to still have these others sitting around? How will this affect performance? Can I/ Should I get rid? How?

Thanks again!

---

### Post by ajgreeny on 2011-02-19
No, they will not affect your performance in any noticeable way; they will simply take space on your hard disk.  If you have enough hard disk space I would not bother about them.

Each desktop environment will run totally separately from the another, and none of the UNE or xfce-desktop packages will be involved in any way when you run gnome, and vice-versa.

To get the full feel of xubuntu, choose xubuntu-desktop, rather than xfce, if both are listed at the session menu.  I've never used xfce/xubuntu so I am not sure what the session menu will contain.  Sorry if I mislead you originally about the options available.

---

### Post by morenogabr on 2011-02-19
No, I appreciate the help. I do notice though that there appear to be some redundant apps. It seems that some of gnome apps migrated over and I have two different word processors for example. I have two battery icons on my tool bar. I guess this is not that big a deal, now I just have to clean out my app menu...

I was using xfce for a while because I really liked the simple look but after about an hour or so, it slowed waaaay down. It became unusably slow. At this point I switched over to xubuntu and I think I'll stick with it. But I was wondering if anyone has a clue why that happened, an hour into my session.

Thanks again.

---

