---
title: "Severe graphics corruption on 15.10"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by fujiama on 2015-10-24
I've been trying outUbuntu 15.10 on two of my computers. On my newer machine it works as expected but on an older machine with a gma 4500 intel GPU I am getting these severe graphics corruption (attached).

---

### Post by ajgreeny on 2015-10-24
Is the corruption only within windows?  Your desktop and panel, and window decorations look OK.

---

### Post by fujiama on 2015-10-24
It's primarily within windows, but there is some corruption affecting destop elements as well, such as volume icons when hovered over.

---

### Post by fujiama on 2015-10-24
I found a partial fix here: [http://fedoramagazine.org/solution-graphics-issues-intel-graphics-chipsets-fedora-22/](http://fedoramagazine.org/solution-graphics-issues-intel-graphics-chipsets-fedora-22/)
It appears to be a kernel issue which can be remedied by setting the intel acceleration to uxa from sna. The problem is that this results in a noticable reduction in performance which is kinda sad since the machine was quite acceptable for basic internet browsing until now.

---

