---
title: "deb and deb-src cli commands"
date: 2021-11-12
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2021-11-12
What are equivalents for the [FONT=Courier New]deb[/FONT] and [FONT=Courier New]deb-src[/FONT] commands under Ubuntu?

I found the following being advised to do under Ubuntu 18.04:
```

deb http://ppa.launchpad.net/vbernat/haproxy-1.8/ubuntu bionic main 
deb-src http://ppa.launchpad.net/vbernat/haproxy-1.8/ubuntu bionic main 

```

but my system doesn't know these. AFAIK these are debian package commands.

---

### Post by coffeecat on 2021-11-12
deb and deb-src are not commands. Those two lines are lines to be added to a source list, not commands to be issued from a terminal. You have already set up a source list with those lines with the add-apt-repository command you highlighted in red in your [other thread.](https://ubuntuforums.org/showthread.php?t=2468855) 

I suggest you add some information to your other thread so that others can help you resolve the problem. For example, what actual problems are you seeing with your package manager?

---

### Post by Krischu on 2021-11-13
Sorry, forgot about these deb, deb-src entries in sources.list totally. Thanks for helping my memory.

---

