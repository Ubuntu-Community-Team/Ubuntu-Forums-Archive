---
title: "Segmentation faulterne... 0%"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by falkenberg_cph on 2007-02-21
Hi
i got this strange problem. 
1. Whenever i try to open the update-manager it closes down.
1.a [edit]: Synaptics also closes down
2. if i use apt in terminal, whatever i do, it ends up writing "Segmentation faulterne... 0%"
3. i cannot install anything, not even reinstall apt
4. alt-f2 -> gksu &#8220;update-manager -d&#8221; - doesnt do anything
5. gksu &#8220;update-manager -d&#8221; in terminal gives me the following:
> 
gksu &#8220;update-manager -d&#8221;
gksu: invalid option -- 
GKsu version 1.9.3
Usage: gksu [-u <user>] [options] <command>

+ a long description of how to use gksu

6. [edit]: The problem is very close to [ this](http://www.ubuntuforums.org/showthread.php?t=366598&highlight=reinstall+synaptic) guys problem. but the solution doesnt help me. i am not able to reinstall synaptics.

I have no idea how to find a solution. Searched the forum and google for "Segmentation faulterne... 0%" - ZERO hits

Hope you can help me
/Carsten

---

### Post by falkenberg_cph on 2007-02-21
Phew. Through [ this](http://www.ubuntuforums.org/showthread.php?t=333146&highlight=Segmentation+fault) post, i found [this](http://www.techiegroups.com/showpost.php?p=602599&postcount=3) post, that told me to erase the apt cache.

/Carsten

---

